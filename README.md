# TEXT FILE LAB
by Michel Clasquin-Johnson

=================

Public Domain software for Haiku, written in yab using the Yabadabbadoo IDE
 
This program allows you to convert between various encodings of text files (and that includes HTML). It is essentially a GUI front-end to iconv.
 
![Text File Lab](textlab.png)

TFL will never allow you to save your changes back to your original file. This is a safety measure. In fact, it does not even work on your file but on a copy in the TEMP directory. You can save your new, converted file with another name and once you are satisfied, you can use Tracker to delete the original and rename your new file to the old name.
 
TFL deals with one file at a time. There is no batch mode and I have no plans to introdue one. If you need that, you will have to use iconv in Terminal.
 
LOAD a file:
=======
 
Drop a file anywhere on the TFL window, use the OPEN button in the bottom left-hand corner, or seleft File | Open from the menu. If you try to load a non-text file, maybe something that got corrupted, it will offer to extract the textual information from it. You can also force this to happen manually with the \"Force open\" menu command.
 
TFL will also open a file from the command line or from Tracker's \"Open with ...\" context menu.
 
VIEWING different encodings
==================
 
At the top of the window you will see various attempts to figure out the files current encoding. Please note that these can be incorrect. Text files that have their encoding set incorrectly are one of the main reasons for this program.
 
Manipulating the INPUT FORMAT dropdown selector allows you to see what the file looks like if we assume different encodings. This dropdown always starts with US-ASCII encodings, it is not automatically set to the results at the top of the window (because they might be wrong). If you know that the file you want to decode comes from Japan, try setting this to EUC-JP. If it comes from Russia, try CYRILLIC or MACCYRILLIC. These encodings come in many names and synonyms. TFL will internally convert the file from your chosen encoding to UTF-8 and display the results.
  
I have tried to use the most user-friendly synonyms. For example, ISO-IR-149 is also known as KS-C-5601. Or we can simply call it KOREAN. Iconv understands these as equivalents and it makes the dropdown a lot simpler.However, there are a few encodings without a user-friendly sysnonym. You can find them all here: https://en.wikipedia.org/wiki/Category:Character_sets
 
You can view the file as normal text or in hexadecimal format, using the tabs. These tabs are non-editable, and for display only.
 
There is a button to view the directory in which your file resides. Note that  the file is not locked in any way, but any edits you make will not be reflected unless you reopen the file, which you can do just like you would open it in the first place. TFL will attempt every few seconds to see if the file has been changed and ask you if it should reload (this will happen when TFL regains focus), but this should not be relied upon.
 
SAVING the new file
============
 
Select the OUTPUT FORMAT. In 99% of situations today, you can just leave this at UTF-8. Only change this if you actually know what you are doing. UTF-8 is the standard for Unicode files and the format Haiku uses internally.
 
You can now choose to save your file as either a DOS/Windows text file or as a UNIX/Haiku file. The difference lies in whether lines are terminated by a Carriage Return (CR) and a Line Feed (LF) characters, as in Windows, or by just a LF, as in Unix, Linux and Haiku. There was an older standard for Macs, which only used a CR, but that was before OS X and we don't use those anymore: OS X uses the UNIX standard. It's not the train smash it used to be, by the way. Most text editors, on most platforms, are capabable of handling both types of files these days and auto-convert between them. Still, saving a file meant for Haiku in the proper Haiku format is more elegant and saves a few bytes.
 
If you intend to use this recoded file in Haiku, select the UNIX/Haiku option from the button or the menu. A file selector will come up and you can specify a new filename. If the file you are examining, is in a read-only directory e.g. most of the /boot/system and /boot/home/config hierarchies, you will have to save it somewhere else.
 
PLEASE NOTE that TFL will NOT let you overwrite the original file, even if the Haiku file selector does. This is a conscious design decision on my part. If you are going to overwrite the file, you will have to do it from Tracker, Terminal or your favourite file manager. You can overwrite OTHER files on your system, as many times as you like, but not the original file that you loaded into TFL
 
HELP
===
 
Well, you're reading this, so that is pretty much sorted ;-)
 
EXITING the program
==============
 
TFL is a bit of a CPU hog, constantly shelling out to the system to see if its file has changed. I suggest you close it down when it is not in use. Alternatively you can use the \"Clear\" command from the File menu to stop the app from polling for changes.
 
EXAMPLES
======
 
This HPKG contains two example files, borrowed from my other ports, to illustrate the use of TFL.
 
Butterfly-ru.html - change the input encoding to CYRILLIC-ASIAN
ElvenEdit_jaJP_Ctt.htm - change the input encoding to MS-KANJI
 
Note how the document is translated. If you can read Russian or Japanese, you should be able to tell if this is the correct encoding. If not, feed the resulting UTF-8 text into Google Translate and see what it spits out. Accuracy may be improved as we get new versions of iconv.
 
However, these are HTML documents. To export them to UTF-8 see them in a browser, you will have to edit them a little further in a text editor like StyledEdit or PE. Remove the META tags at the top of the document and try the result in WebPositive.

Get it here: https://github.com/clasqm/TextLab

