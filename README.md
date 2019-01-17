[![Travis CI build status](https://travis-ci.org/evanmiller/XLSX-Writer.svg?branch=master)](https://travis-ci.org/evanmiller/XLSX-Writer)

Perl 6 wrapper for libxlsxwriter
--

This is not a port of Perl 5's Excel::Writer::XLSX; rather, it's a wrapper for
the [libxlsxwriter](https://libxlsxwriter.github.io/) C library, which itself
was a port of the Perl 5 library. Oh the irony.

Basic usage:

```perl6
    use XLSX::Writer;

    my $workbook = XLSX::Writer::Workbook.new("/path/to/somewhere.xlsx");
    my $worksheet = $workbook.add-worksheet("Sheeeeeeeeet");

    $worksheet.write-value(0, 0, "Hello");
    $worksheet.write-value(0, 1, pi);
    $worksheet.write-value(0, 2, True);
    $worksheet.write-value(0, 3, DateTime.now);
    $worksheet.write-value(0, 4, "http://modules.perl6.org/", :url);
    $worksheet.write-formula(0, 5, "=B1*2", :result(2*pi));

    my $bold-format = $workbook.add-format();
    $bold-format.set-bold();
    $worksheet.write-value(0, 6, "A bold greeting", $bold-format);

    $workbook.close();
```

You need libxlsxwriter installed on your system; this library was tested
against version 0.7.0.

See the `t/` directory for more functions, including custom formatting.
