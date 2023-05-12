This is a collection of script for scanning from my Brother DCP-7065DN
scanner from Debian linux.

# Installation

Copy the scripts to any directory on your path.

For example, if ~/bin is on your path, copy them to ~/bin, otherwise
/usr/local/bin is likely to be on your path.

You will probably have to update the device. For my system, it is
`brother4:net1;dev0`.

To get a list of devices for your system run: `scanimage -L`, then update
the scripts with the name of your device.

# Dependencies

These scripts depend on:

 * scanimage: from package `sane-utils`
 * bc: from package `bc`
 * convert: from package `imagemagick`

# scan-duplex

This scans multiple pages of double sided documents, producing a single PDF.

Load the documents into the feeder then run `scan-duplex`. It will read
the front side of all pages then prompt you to flip the documents and
re-feed them. It will then read the back side of all documents and produce
a single PDF document as output.

Default output file name is YYYY-MM-DD-scan.pdf.

The output file name may be specified on the command line.

For example: `scan-duplex my-file.pdf`

# scan-multi

This scans multiple pages of single sided documents, producing a single PDF.

Load the documents into the feeder then run `scan-multi`. It will read
the front side of all pages then produce a single PDF document as output.

Default output file name is YYYY-MM-DD-scan.pdf.

The output file name may be specified on the command line.

For example: `scan-multi my-file.pdf`

# Errors

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
