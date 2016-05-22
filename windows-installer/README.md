# Building #

1. Install [Microsoft Visual Studio][ms-vs].
2. Install [WiX Toolset][wix].
3. Open `windows-installer\WindowsInstaller.sln` in Visual Studio.
4. Build the project using `Ctrl+Shift+B`.

[ms-vs]: https://www.visualstudio.com/
[wix]: http://wixtoolset.org/releases/

# Information about the Windows system Spell Checking #

## Which versions of windows? ##

The Windows system spell checker has existed since Windows 8.

## Where do you install dictionaries? ##

You can add dictionaries to it by adding them to `%appdir%\Microsoft\Spelling\<language>\`. There will be a file `default.dic` already in this directory. Other `.dic` file can be added, and the spell checker will use the words in them. Any number of other files can be added.

## What file format is used? ##

The `.dic` files are text files with one word per line. They must be encoded in UTF-16 LE with a valid BOM.

## What other rules are there about dictionaries? ##

The maximum number of lines in all of the `.dic` files in the spelling directory is 44502. If there are any more lines than this, the additional files will be ignored. For example:

- If you have a `medicine.dic` file with 4402 words in, all these words will be used with by the spell checker.
- If you have a `medicine.dic` file with 4403 words in, none of these these words will be used by the spell checker.
- If you have a `medicine.dic` file with 4402 words in, and a `medicine2.dic` file with one word in, the all words in `medicine.dic` will be used, but none of the words in `medicine2.dic` will be used.

# References #

- [MSDN: About the Spell Checking API][win-spell-api]

[win-spell-api]: https://msdn.microsoft.com/en-us/library/windows/desktop/hh869748(v=vs.85).aspx#dictionary_files "About the Spell Checking API"
