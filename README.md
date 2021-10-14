# HowDoesExcelOpenCsv

## The problem

As of this moment (at least on in my current Windows 10-configuration) it seems Excel only parses `.csv`-files correctly if the file is 

- in `cp1252`-encoding
- using semicolons (`;`) as separator

Of course it is always possible to *import data* from inside Excel, as you should probably always do.

## Examples

With these files we can check future version of Excel (or alternative installations).

Simply **double-click** each `.csv`-file or choose **Open with Excel** and check how Excel parsed the file.

> For this to work we depend on `git` to encode the text-files correctly on checkout, using the configuration in `.gitattributes`.

The example-files were encoding using Visual Studio Code's **change file encoding**-feature.

- CodePage 1252 (`windows1252` in VSCode, `windows-1252` in git)

TODO for completeness:

- CodePage 437 (`cp437` in VSCode, `???` in git)
- ISO 8859-1 (`iso88591` in VSCode, `???` in git)

## Manually inspect the bytes of the examples

Use for example this Powershell-snippet:

```powershell
dir *.csv | Format-Hex
```

You should see this:

| character | cp1225-encoding | UTF-8 encoding |
|-----------|-----------------|----------------|
|    `ë`    |      `0xEB`     |   `0xC3 0xAB`  |
|    `ç`    |      `0xE7`     |   `0xC3 0xA7`  |
|    `é`    |      `0xE9`     |   `0xC3 0xA9`  |

## Reference

https://en.wikipedia.org/wiki/Windows-1252

