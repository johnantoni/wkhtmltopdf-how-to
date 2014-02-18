### wkhtmltopdf binary for osx

Currently works on OSX 10.9.1 Mavericks

original article [http://stackoverflow.com/a/10931279](http://stackoverflow.com/a/10931279)

#### install

First download, open and drag to Applications

Then:

    cd /usr/local/bin && sudo ln -s /Applications/wkhtmltopdf.app/Contents/MacOS/wkhtmltopdf wkhtmltopdf

#### issues

* will not support images from https locations
* does support background-image replacement
* margin attribute issues
* position: absolute issues

For complex layouts suggest using inline styling or less complex styles, for table data use tables rather than inline lists.

#### headers and footers

header and footer html can be added to the pdf via a meta tag

    meta[content="header.html" name="pdfkit-header-html"]
    meta[content="footer.html" name="pdfkit-footer-html"]

this won't work straight off with rails as they will be wrapped with basic auth, so the easiest way to do this is to host those files on s3 outside the system.

    meta[content="http://s3.bucket.com/footer.html" name="pdfkit-footer-html"]

or create the file and run a local webserver to host it

    mkdir pdf
    cd pdf
    vim footer.html
    ...then
    python -m SimpleHTTPServer
    ...
    meta[content="http://localhost:8000/footer.html" name="pdfkit-footer-html"]

#### running

Rather than downloading each file again and again and getting ...(1).pdf, ...(2).pdf you can use wget to download the pdf and overwrite the original

    wget -N http://localhost:3000/report/pdf.pdf
    => outputs to pdf.pdf
    
