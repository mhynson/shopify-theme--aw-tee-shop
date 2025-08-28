# Tracking Changes

## Issues

1. The slideshow uses large images

- Fix:
  - reduce the width of the slideshow container to a max-with of 1280px (ds-slideshow.css, slideshow.css)
  - reduce the width of the images to a max-width of 2560px (affinity designer)
- Result:
  - Mobile Lighthouse
    - Performance changed from 75 -> 80
    - Best Practices changed from 79 -> 100
  - Desktop Lighthouse
    - Performance changed from 88 -> 91
    - Best Practices changed from 78 -> 100
  - Improved the consistency of the look of the hero slideshow image across devices

2. Lazy Load isn't needed on the hero image

- Fix:
  - Remove the loading: lazy tag from the template (ds-slideshow.liquid)
- Result:
  - Mobile Lighthouse
    - Performance changed from 80 -> 97
    - Best Practices changed from 79 -> 100
  - Desktop Lighthouse - unchanged

3. Attempted: preload slideshow images

- Fix:
  - Added the following to line 120 inside the block
    `<link rel="preload" href="{{ block.settings.image | image_url: width: 3840 }}" as="image">`
- Result (failed):
  - This change actually negatively affected performance. It could be in the way that it was implemented (inside of a for-loop). Is there a way to pull out the images and put the preload statement higher up on the page?
