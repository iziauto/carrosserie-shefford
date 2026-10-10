# Carrosserie & Peinture Shefford — website files

## Files
- `index.html`: complete static website. The HTML, CSS, and JavaScript are all included in this one file.

## Important before going live
The estimate form is currently a demonstration only. It does not send form contents or photos anywhere. Connect it to a secure form service or backend before publishing for customers.

## Cloudflare
Make sure `index.html` is at the root of the GitHub repository. For a static HTML website, use Cloudflare Pages' Git integration rather than a Workers deploy-command flow. Leave the build command blank and set the build output directory to the folder containing `index.html` (usually `.` or `/`, depending on the interface).
