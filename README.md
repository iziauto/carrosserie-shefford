# Carrosserie & Peinture Shefford

Static website deployed from GitHub to Cloudflare.

## Repository layout

```text
index.html                           Home page and estimate form
debosselage-sans-peinture-dsp.html     DSP service page
protection-pare-pierre-pellicule.html  PPF service page
assets/
  images/
    home/                            Workshop exterior and paint booth
    dsp/                             12 DSP gallery photos
    ppf/                             PPF hero, gallery and package diagrams
_redirects                           Old image URLs redirected to new folders
```

The HTML pages stay at the root to preserve their existing addresses. Styles and scripts remain within each page. Add new pictures to the matching image folder and use paths starting with `/assets/images/` in HTML and CSS. Filenames are case-sensitive on Cloudflare.

Publish image moves and their HTML path updates in the same commit. Keep `_redirects` at the root of the deployed static assets so old image links continue to work. Existing image files have been moved without changing their contents.

## Preview and local review

Preview: https://carrosserie-shefford.iziauto.workers.dev/

Serve the repository root with a local static HTTP server to review it. Opening HTML directly from disk will not resolve the root-relative paths. Cloudflare resolves the service pages at their existing extensionless addresses and processes `_redirects`; a basic local static server may require the `.html` suffix and will not process that file.

## Contact form

The estimate form submits a native multipart POST to FormSubmit for delivery to garageshefford@gmail.com. No email password, API secret, DNS change, or Bluehost change is required.

- Required: name, phone, email, and description. Service selection is optional.
- Optional: up to five JPEG, PNG, or WebP photos, under 10,000,000 bytes combined.
- Photos use separately named file inputs for attachment delivery.
- FormSubmit provides its default reCAPTCHA. A hidden honeypot is also included.
- The customer's email field supplies Reply-To. The email uses a table layout and a French estimate-request subject.
- After successful submission, FormSubmit returns to the Cloudflare preview contact section with the confirmation message.

## Activation and delivery verification

The owner has confirmed activation and successful delivery, including two photo attachments. The following checklist is retained for any future recipient change or reactivation.

1. Submit a test without photos to request FormSubmit's activation email.
2. Confirm the activation at garageshefford@gmail.com. Check Spam if needed.
3. Submit a second clearly marked test with at least two photos.
4. Verify all fields and both attachments arrive in Gmail before considering delivery verified. Uploaded files from an unactivated form are not retained by FormSubmit.

When the production domain is connected, update the form's absolute _next URL to the new production address. Keep the current preview redirect until then.

FormSubmit documentation: https://formsubmit.co/documentation

## SEO and launch checklist

- Each page has a unique French title and description, Canadian French language, canonical URL, social sharing tags and JSON-LD.
- The business is described as AutoBodyShop with its confirmed address, phone, email, social profiles, service area and Monday-Friday 09:00-17:00 hours. No reviews, ratings, coordinates or unconfirmed certifications are invented.
- Service pages include Service and BreadcrumbList structured data. The home page includes WebSite data.
- `_headers` applies `X-Robots-Tag: noindex` only to `carrosserie-shefford.iziauto.workers.dev`. Crawling remains allowed so search engines can see that header. Do not add `Disallow: /` to robots.txt.
- Canonicals and sitemap.xml use https://carrosserieshefford.com. They are prepared for launch; the public domain still serves Bluehost until the owner approves the switch. Do not submit the preview sitemap to Search Console.
- Social sharing images and the business schema image temporarily use the working Cloudflare preview asset URLs so previews load before domain launch.
- Existing WordPress service paths are preserved, with trailing slashes redirected to the new canonical paths. `/contactez-nous` and `/contactez-nous/` redirect to the homepage contact section.
- The homepage hero image is preloaded. The PPF hero has high fetch priority. Existing gallery lazy loading is preserved and image dimensions match the actual files.

When the owner approves domain launch:

1. Complete the separate DNS/hosting migration plan while preserving email service. This SEO change does not modify DNS or Bluehost.
2. Verify the domain serves all three new pages over HTTPS, that the canonical paths return 200, and the previous WordPress URLs redirect correctly. Check both www and the bare domain, and preserve any additional indexed legacy URLs found in Search Console.
3. Replace `https://carrosserie-shefford.iziauto.workers.dev/assets/` with `https://carrosserieshefford.com/assets/` in the three HTML files, updating social/schema image URLs together. Update the form's `_next` URL to the production domain as described above.
4. Confirm the custom-domain responses have no `noindex` header and robots.txt and sitemap.xml load. Keep the host-specific preview noindex rule.
5. Submit `https://carrosserieshefford.com/sitemap.xml` in the owner's existing Google Search Console property and inspect the three canonical URLs. Since the public domain is unchanged, Google's Change of Address tool is not needed.
6. Confirm the existing Google Business Profile uses the correct website, Gmail address and weekday hours. Monitor Search Console indexing, crawl errors and performance after launch.

References: [Google Local Business](https://developers.google.com/search/docs/appearance/structured-data/local-business), [Google noindex](https://developers.google.com/search/docs/crawling-indexing/block-indexing), [Cloudflare static headers](https://developers.cloudflare.com/workers/static-assets/headers/).
