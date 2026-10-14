# Carrosserie & Peinture Shefford

Static website deployed from GitHub to Cloudflare.

## Contact form

The estimate form submits a native multipart POST to FormSubmit for delivery to garageshefford@gmail.com. No email password, API secret, DNS change, or Bluehost change is required.

- Required: name, phone, email, and description. Service selection is optional.
- Optional: up to five JPEG, PNG, or WebP photos, under 10,000,000 bytes combined.
- Photos use separately named file inputs for attachment delivery.
- FormSubmit provides its default reCAPTCHA. A hidden honeypot is also included.
- The customer's email field supplies Reply-To. The email uses a table layout and a French estimate-request subject.
- After successful submission, FormSubmit returns to the Cloudflare preview contact section with the confirmation message.

## Activation and delivery verification

1. Submit a test without photos to request FormSubmit's activation email.
2. Confirm the activation at garageshefford@gmail.com. Check Spam if needed.
3. Submit a second clearly marked test with at least two photos.
4. Verify all fields and both attachments arrive in Gmail before considering delivery verified. Uploaded files from an unactivated form are not retained by FormSubmit.

When the production domain is connected, update the form's absolute _next URL to the new production address. Keep the current preview redirect until then.

FormSubmit documentation: https://formsubmit.co/documentation
