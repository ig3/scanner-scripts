This is a bash script for scanning duplex documents.

It works for my scanner.

If you get error:

```
attempt to perform an operation not allowed by the security policy PDF
```

This is an ImageMagick restriction.

See
https://stackoverflow.com/questions/52998331/imagemagick-security-policy-pdf-blocking-conversion

Per this, in `/etc/ImageMagick-6/policy.xml` comment out the line that
blocks producing PDF output:

```
  <!-- <policy domain="coder" rights="none" pattern="PDF" /> -->
```
