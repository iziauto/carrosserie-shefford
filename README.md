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
