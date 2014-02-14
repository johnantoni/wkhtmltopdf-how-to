### wkhtmltopdf binary for osx

Currently works on OSX 10.9.1 Mavericks

original article [http://stackoverflow.com/a/10931279](http://stackoverflow.com/a/10931279)

#### install

First download, open and drag to Applications

Then:

    cd /usr/local/bin && sudo ln -s /Applications/wkhtmltopdf.app/Contents/MacOS/wkhtmltopdf wkhtmltopdf

#### notes

* will not support images from https locations
* does support background-image replacement
* margin attribute issues
* position: absolute issues

For complex layouts suggest using inline styling or less complex styles, for table data use tables rather than inline lists.

Rather than downloading each file again and again and getting ...(1).pdf, ...(2).pdf you can use wget to download the pdf and overwrite the original

    wget -N http://localhost:3000/report/pdf.pdf
    => outputs to pdf.pdf
    
