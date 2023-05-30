# dos2unix and unix2dos

```bash
man dos2unix
man unix2dos
```

```
$ dos2unix -h
Usage: dos2unix [options] [file ...] [-n infile outfile ...]
 --allow-chown         allow file ownership change
 -ascii                convert only line breaks (default)
 -iso                  conversion between DOS and ISO-8859-1 character set
   -1252               use Windows code page 1252 (Western European)
   -437                use DOS code page 437 (US) (default)
   -850                use DOS code page 850 (Western European)
   -860                use DOS code page 860 (Portuguese)
   -863                use DOS code page 863 (French Canadian)
   -865                use DOS code page 865 (Nordic)
 -7                    convert 8 bit characters to 7 bit space
 -b, --keep-bom        keep Byte Order Mark
 -c, --convmode        conversion mode
   convmode            ascii, 7bit, iso, mac, default to ascii
 -f, --force           force conversion of binary files
 -h, --help            display this help text
 -i, --info[=FLAGS]    display file information
   file ...            files to analyze
 -k, --keepdate        keep output file date
 -L, --license         display software license
 -l, --newline         add additional newline
 -m, --add-bom         add Byte Order Mark (default UTF-8)
 -n, --newfile         write to new file
   infile              original file in new-file mode
   outfile             output file in new-file mode
 --no-allow-chown      don't allow file ownership change (default)
 -o, --oldfile         write to old file (default)
   file ...            files to convert in old-file mode
 -q, --quiet           quiet mode, suppress all warnings
 -r, --remove-bom      remove Byte Order Mark (default)
 -s, --safe            skip binary files (default)
 -u,  --keep-utf16     keep UTF-16 encoding
 -ul, --assume-utf16le assume that the input format is UTF-16LE
 -ub, --assume-utf16be assume that the input format is UTF-16BE
 -v,  --verbose        verbose operation
 -F, --follow-symlink  follow symbolic links and convert the targets
 -R, --replace-symlink replace symbolic links with converted files
                         (original target files remain unchanged)
 -S, --skip-symlink    keep symbolic links and targets unchanged (default)
 -V, --version         display version number
```

```
$ unix2dos -h
Usage: unix2dos [options] [file ...] [-n infile outfile ...]
 --allow-chown         allow file ownership change
 -ascii                convert only line breaks (default)
 -iso                  conversion between DOS and ISO-8859-1 character set
   -1252               use Windows code page 1252 (Western European)
   -437                use DOS code page 437 (US) (default)
   -850                use DOS code page 850 (Western European)
   -860                use DOS code page 860 (Portuguese)
   -863                use DOS code page 863 (French Canadian)
   -865                use DOS code page 865 (Nordic)
 -7                    convert 8 bit characters to 7 bit space
 -b, --keep-bom        keep Byte Order Mark (default)
 -c, --convmode        conversion mode
   convmode            ascii, 7bit, iso, mac, default to ascii
 -f, --force           force conversion of binary files
 -h, --help            display this help text
 -i, --info[=FLAGS]    display file information
   file ...            files to analyze
 -k, --keepdate        keep output file date
 -L, --license         display software license
 -l, --newline         add additional newline
 -m, --add-bom         add Byte Order Mark (default UTF-8)
 -n, --newfile         write to new file
   infile              original file in new-file mode
   outfile             output file in new-file mode
 --no-allow-chown      don't allow file ownership change (default)
 -o, --oldfile         write to old file (default)
   file ...            files to convert in old-file mode
 -q, --quiet           quiet mode, suppress all warnings
 -r, --remove-bom      remove Byte Order Mark
 -s, --safe            skip binary files (default)
 -u,  --keep-utf16     keep UTF-16 encoding
 -ul, --assume-utf16le assume that the input format is UTF-16LE
 -ub, --assume-utf16be assume that the input format is UTF-16BE
 -v,  --verbose        verbose operation
 -F, --follow-symlink  follow symbolic links and convert the targets
 -R, --replace-symlink replace symbolic links with converted files
                         (original target files remain unchanged)
 -S, --skip-symlink    keep symbolic links and targets unchanged (default)
 -V, --version         display version number
```