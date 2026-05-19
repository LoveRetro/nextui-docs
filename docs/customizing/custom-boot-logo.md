# Add Custom Boot Logo

To add a custom boot logo, place a 24-bit color `.bmp` image under the corresponding folder for your device. Then, select **Tools** > **Bootlogo** to set your custom logo.

### Directory Location

The Bootlogo Pak is available for all supported devices:

```
SD_CARD
├── Tools/
│   ├── tg5040/
│   │   └── Bootlogo.pak/
│   │       ├── brick/
│   │       │   └── your_logo.bmp            *For Brick and Brick Hammer devices - Add your IMAGE here
│   │       └── smartpro/
│   │           └── your_logo.bmp            *For Smart Pro devices - Add your IMAGE here
│   └── tg5050/
│       └── Bootlogo.pak/
│           └── smartpro_s/
│               └── your_logo.bmp            *For Smart Pro S devices - Add your IMAGE here
```

## Recommended Specs

- Depth: 24-bit color

| Device | Dimensions |
|---|---|
| Brick / Brick Hammer | 1024 x 768px |
| Smart Pro | 1280 x 720px |
| Smart Pro S | 1280 x 720px |

You can use any of the existing logo options as a template for your custom logo if you wish to maintain the same sizing.
