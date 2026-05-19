# Shaders

## Quick reference

| Task | What to do |
|---|---|
| Use a built-in shader | Open a game, press `Menu`, then go to `Options` → `Shaders`. |
| Add a loose shader file | Copy the `.glsl` file to `SDCARD_ROOT/Shaders/glsl/`. |
| Add a shader preset | Copy the `.cfg` preset file to `SDCARD_ROOT/Shaders/`. |
| Use shader parameter presets | NextUI v6.10.0 and newer can load shader parameter values from `.cfg` preset files. |
| Use `.glsp` presets | `.glsp` preset files are not supported. Use `.cfg` presets instead. |

## Where shader files go

NextUI loads files from two distinct locations.

Loose `.glsl` shader files belong in:

```text
SDCARD_ROOT/Shaders/glsl/
```

Shader preset `.cfg` files belong in:

```text
SDCARD_ROOT/Shaders/
```

Example layout:

```text
Shaders/
├── handheld-lcd.cfg
└── glsl/
    └── lcd3x.glsl
```

Then open a game and choose the shader or preset from:

```text
Menu → Options → Shaders
```

## Shader preset `.cfg` files

NextUI v6.10.0 added support for loading shader parameter values from `.cfg` preset files.

A `.cfg` preset is a text file that stores shader settings and parameter values. If the preset references external `.glsl` files, those files must also be present in the expected path.

Common layout:

```text
Shaders/
├── handheld-lcd.cfg
└── glsl/
    └── lcd3x.glsl
```

`.cfg` preset files use `minarch_` prefixed key=value pairs. Example:

```ini
minarch_nrofshaders = 2
minarch_shader1 = pixellate.glsl
minarch_shader1_filter = NEAREST
minarch_shader1_srctype = source
minarch_shader1_scaletype = source
minarch_shader1_upscale = screen
minarch_shader2 = lcd3x.glsl
minarch_shader2_filter = NEAREST
minarch_shader2_srctype = source
minarch_shader2_scaletype = source
minarch_shader2_upscale = screen
minarch_scale_filter = NEAREST
```

Available filter values: `NEAREST`, `LINEAR`
Available srctype values: `source`, `relative`
Available scaletype values: `source`, `relative`
Available upscale values: integer `1`-`4`, or `screen`

If a preset does not appear or does not load correctly:

- confirm you are on NextUI v6.10.0 or newer;
- confirm the referenced `.glsl` files exist;
- check filename case;
- try a simple loose `.glsl` first;
- do not use `.glsp` presets; they are not supported.

## Performance notes

Shaders cost GPU time. If a game stutters after enabling shaders:

1. Turn shaders off and test again.
2. Reduce the number of shader passes.
3. Use a simpler shader.
4. Lower emulator enhancement settings.
5. For arcade or higher-end systems, prioritize performance over heavy visual effects.

---

## Shader Tutorial

**A Little Introduction**

In today's world, most of us have screens with resolutions of at least 1920×1080 and higher. However, back in the days of our favorite retro games, this was far from the case. Older TVs operated at around 720×525 resolution, and handheld devices like Game Boys had even lower resolutions.

While we enjoy our collections of retro games today, there's one big problem: our modern screens usually have resolutions far beyond what these games were originally designed for. In practice, this means we either play our games in a tiny square in the middle of our screens to preserve their original resolution, or (what most of us prefer) we scale the image up to better fit our modern, high-resolution displays.

There are three main scaling modes you can choose from in the frontend options under Screen Scaling:

- Native—This keeps the game at its original resolution, resulting in that tiny box in the center of your screen.  
- Aspect—This scales the image to your screen while maintaining the original aspect ratio, so nothing looks distorted (no "fat" Super Mario). It scales the image up until either the width or height reaches the screen size. This often leaves empty space on the sides or top and bottom, unless you're lucky enough to have a screen that matches the original aspect ratio exactly.  
- Full Screen Stretch—This simply stretches the image to fill the entire screen without preserving the aspect ratio. While it fills the screen nicely, it can make things look strange if the original and screen aspect ratios don't match.  

Ultimately, the choice is yours based on what you prefer. However, understanding screen scaling is important because it plays a big role in how shaders are used — although scaling isn't the only reason shaders are popular, it is a major one.

## Lets Get Shady!

**Options → Frontend → Screen Sharpness**

First, let’s talk a little about this option.  
The GPU in your device basically has two modes to upscale an image to the final screen size.

The first is **NEAREST**, which is faster because it’s less complex. It simply upscales the image by doubling each pixel. This looks very sharp, but it can make an image look *too* sharp, especially if the input (the output of your emulator core) is at a very small resolution. NEAREST just doubles the pixels until it reaches the desired size.

The second option is **LINEAR**. This costs a little more performance-wise, but instead of just doubling pixels, it applies linear interpolation between pixels, creating a smoother, softer look.  
This can definitely create a more even, pleasant image — but again, it depends heavily on what the original source image looks like. If your emulator is outputting a very small image, LINEAR interpolation has to invent a lot of new pixels to fill the screen, and the result can look very blurry.

![NEAREST](https://github.com/user-attachments/assets/7ba31112-f778-4426-860f-2b39b7966121)
![LINEAR](https://github.com/user-attachments/assets/21fd9408-2d80-429b-9bf8-9114baeb6f6b)

The takeaway here is simple:  
**The smaller the original image the GPU receives to upscale to your screen’s resolution, the worse it will look.**  
Neither NEAREST nor LINEAR can magically make a tiny 320×240 image look amazing on a big 1024×768 screen.  
That’s just been a fact of life since the early days of computers.

---

Now, if you really just want to *rawdog* the tiny emulator output directly to the screen for maximum performance, I recommend using **NEAREST**.  
LINEAR usually just ends up looking too blurry, while NEAREST faithfully replicates the pixels from the source, simply making the image bigger — simple and sharp.

---


So, does that mean old games will *always* look like crap on modern screens?

**Well, no, not really! Welcome to the world of shaders!**

---

## A Note on the Word "Shader"

Before we dive in, a quick note:  
The word *shader* is actually kind of wrong in this context. In emulation, "shaders" have become synonymous with "effects," but technically speaking, shaders are just small programs that tell your GPU what to do with pixel data.  
**Every image you see on your screen — even a simple one without effects — is being drawn by a shader.**  
Even the most basic output still runs a shader that simply says: "draw a rectangle the size of the screen and fill it with the emulator's pixel data."

Okay, with that out of the way — since we already use shaders to draw the screen, **we can also use them to alter the look of the image!**

---

## Making LINEAR Look Good

Let's start with a very basic idea that already looks great for most systems and might even be all you need:

Remember how I said NEAREST is better because LINEAR gets too blurry?  
Well, **LINEAR can actually be awesome — if we prepare the image a little first.**

Here’s the problem:  
When you scale a small image directly up to a big resolution with LINEAR interpolation, the GPU has to invent a *lot* of made-up pixels, which makes everything blurry.  
(For example, scaling a 320×240 image up to 1024×768 — almost two-thirds of the final pixels are *imaginary!* No wonder it looks so bad.)

---

**So what if we first scale the image sharply with NEAREST — and *then* apply LINEAR interpolation afterward?**

In other words:  
First, double (or triple) the sharp pixels with NEAREST, then let LINEAR smooth out only the small leftover gaps.  
Best of both worlds!

Example:

- Emulator outputs 320×240.  
- First, upscale to 640×480 using NEAREST (or even 960×720 if you want).
- Then, apply LINEAR interpolation when stretching it the rest of the way to your screen’s full resolution.

**Result?**  
It looks *way* better!
This is because LINEAR now only has to invent half as many pixels as it’s working with a bigger starting point.

![LINEAR with 2x NEAREST prescale](https://github.com/user-attachments/assets/a4c9b575-d010-493b-93c8-d1dd7b666b79)

Pay special attention to how all the pixels on the ground are now equeally square sized, compared to the previous example without shaders where the pixels where unequal because of the stretching. The shaders now made sure everything stretches nicely and the pixels don't deform even though the image is stretched to a different aspect ratio/size than the game's original ones. 

---

## How to Set This Up

First, let’s set a shader to upscale the image 2× using NEAREST:

**Go to:**
> Options → Shaders

And set the following:  
- **Number of shaders:** 1 (we only need one)  
- **Shader 1:** `stock.glsl` (basic shader that just outputs the input image)  
- **Filter:** NEAREST (very important — we want a sharp, clean NEAREST upscale first!)  
- **Source type:** Relative or Source (doesn’t matter — they’re the same for the first shader)  
- **Texture type:** Relative or Source  
- **Scale:** 2 or 3  (Use 2× for SNES, MD, etc., or 3× for very small images like GB/GBC.)

---

**What this shader does:**  
It takes the emulator's output, scales it up 2× or 3× using NEAREST, and passes it on to the next stage (in this case, directly to the screen, since we’re only using one shader).

---

Now, let’s apply the final LINEAR smoothing when outputting to the screen:

**Go to:**
> Options → Frontend → Screen Sharpness

And set this to **LINEAR**.

---

**So now:**

- First, the shader upscales the image 2× or 3× sharply with NEAREST.
- Then, the frontend upscales the rest of the way using LINEAR to smooth it out slightly.

**And the result already looks MUCH better, right?**

The first image below is without shaders, just straight NEAREST upscaling to fullscreen. The second one uses the above settings to make things a little  smoother and nicer. This looks really good on the Brick's high DPI screen.
![Super Mario World 2025-04-26-16-27-31](https://github.com/user-attachments/assets/7e3f42b3-e73f-4bf0-b8c2-6b9c98be56fb)
![Super Mario World 2025-04-26-16-27-21](https://github.com/user-attachments/assets/fd6907b0-ee21-46d6-a07d-b51c33bd9b01)





---

## A Few Final Notes

The "world of shaders" is all about **chaining small steps together** — each shader alters the image slightly before passing it along.

- **Choosing NEAREST or LINEAR only matters when the step involves resizing.**  
If a shader step uses a Scale of 1 (no scaling), the NEAREST or LINEAR setting has no effect at all. The same goes for the screen sharpness setting in frontend options. If an image already is at screen size before it reaches this final step then the  final filter does nothing because it doesn't have to up or downscale anymore. NEAREST and LINEAR only apply when the image has to resize either up or down. It's not a filter applying to the image, it just tells the GPU what method to use when up (or down) scaling an image. 

But like I said shaders are not only used for scaling, since they are just little programs that run on your GPU they can do anything. There are tons of shaders out there (`.glsl` files) that do all kinds of fun things:

- Simulate CRT screens  
- Mimic Game Boy Advance LCD looks  
- Apply different smoothing/sharpening algorithms  
- Add scanlines, fake grid patterns  
- Distort the screen or enhance colors, etc.  

**Feel free to experiment!**  
Try different shaders, different combinations, and find the look that feels best for your games. You can download any `.glsl` file and place it in the `/Shaders/glsl` folder on your SD card to use it within NextUI. For shader presets, place `.cfg` files in `/Shaders` as described in the quick reference above.

**Enjoy! 🎮**

## BONUS: GB/GBC/GBA Tip!

Want to make your Game Boy, Game Boy Color, and Game Boy Advance games look even cooler? Here's a quick bonus trick!

Set everything up the same way as above, **but now set the number of shaders to 2** and configure the second shader like this:

- **Number of shaders:** 2  
- **Shader 2:** `lcd3x.glsl` (a shader that overlays a pixel grid, simulating old handheld screens)  
- **Filter:** NEAREST (NEAREST recommended for a sharp grid, but LINEAR could work more for you)  
- **Source type:** Source (important — I’ll explain why below)  
- **Texture type:** Source  
- **Scale:** Screen  

---

### What This Does

This setup applies an additional shader called `lcd3x`, which overlays a grid on the image to mimic the look of original Game Boy, Game Boy Color, and GBA screens.  
It’s a simple effect, but it adds a lot of nostalgic charm!

![lcd3x](https://github.com/user-attachments/assets/6ef9bd8c-e192-4861-975f-00d2ec165649)


---

### Why Use **Source** and **Screen**?

Here's the idea:

- Setting **Source** as the **Source/Texture Types** tells the shader to use the original dimensions from the emulator output — the real, original pixel layout. However, for the actual pixel data, it still uses the output from the previous shader step.  
- While we're at it: **Relative** means "use the dimensions of the previous shader step," and **Screen** means "use the dimensions of the screen" (with aspect ratio correction applied).
- Setting the **Scale** to **Screen** means the shader will output an image with a grid drawn over it (where the grid itself is based on the original pixel size) at the screen’s resolution. The upscaling happens here, and no further upscaling is needed.

So, the `lcd3x` shader creates a grid based on the original pixel size but with an output size that covers the entire screen.  
You end up with an LCD-style grid that perfectly matches the original pixel layout, giving each pixel a distinct look — while in reality, the image is being upscaled to your screen’s full resolution.  
It looks like your Game Boy screen suddenly has four times as many pixels. If that ain't cool I don't know what is! 


---

### Important Note About Filtering

Since Shader 2 is already stretching the image up to full screen, **the frontend's Screen Sharpness setting no longer matters.**  
At this point, the image is already at its final size before it even reaches the frontend’s final filter.

That means:

> **The final image sharpness is controlled inside Shader 2 itself, not by the frontend option anymore.**


---

That's it — now you’ve got a sharp, beautiful pixel grid overlay just like an old-school Game Boy screen! 🎮🖤
