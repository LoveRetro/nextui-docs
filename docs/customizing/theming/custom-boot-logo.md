# Add Custom Boot Logo

To add a custom boot logo. Place a 24-bit color `.bmp` image under the corresponding folder for your device. Then, select **Tools** > **Bootlogo** to set your custom logo

### Directory Location

```
SD_CARD
├─ Tools/
│  ├─ tg5040/
│  │  ├─ Bootlogo.pak/
│  │  │  ├─ brick/                                  
│  │  │  │  ├─ your_logo.bmp                        *For Brick devices - Add your IMAGE here
│  │  │  ├─ smartpro/                               
│  │  │  │  ├─ your_logo.bmp                        *For SmartPro devices - Add your IMAGE here
```

## Recomended Specs:
- Depth: 24-bit color
- Dimensions: 1024 x 768px (for Brick)

N.B. You can use any of the existing logo options as a template for yoru custom logo if you wish to maintain the same sizing.
