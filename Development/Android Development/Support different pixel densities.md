- Android devices have different pixel densities. Which basically means that 1 pixel on different resolution devices will correspond to different physical size.
### Use density-independent pixels
- Design your UI using density-independent pixels (`dp`) as your unit of measurement.
- One `dp` is a virtual pixel unit that's roughly equal to one pixel on a medium-density screen( 160 dpi).
- When defining text sizes, you can instead use scalable pixels (`sp`) as your units. The sp unit is the same size as a dp, but it resizes based on the user's preferred text size.
- 1 dp = (dpi / 160) px

### Prefer vector graphics
- Vector graphics can scale to any size without scaling artifacts, though they're usually best for illustrations such as icons, not photographs.
### Provide alternative bitmaps
- Provide multiple versions of each bitmap in your app , one for each density buckets. Otherwise Android must scale your bitmap so it occupies the same visible space on each screen, resulting in scaling artifacts such as blurring.

| Density Qualifier | Description |
| ---- | ---- |
| ldpi | low-density screen ~120dpi
| mdpi | Resources for medium-density screens ~160dpi. This is baseline density. |
| hdpi | high-density ~240dpi |
| xhdpi | extra-high-density ~320dp |
| xxhdpi | extra-extra-high-density ~480dpi |
| xxxhdpi | extra-extra-extra-high-density ~640dpi |
| nodpi | Resources for all densities. These are density independent resources. The system doesn't scale resources tagged with this qualifier. |
#### Put app icons in mipmap directories