# Lab-5_202001270
Git Repository for Lab 5

Tool Used MyPy

Errornous Code:
```
import imp
from tkinter import *
import tkinter.messagebox
from PIL import Image, ImageTk
import socket, threading, sys, traceback, os
from RtpPacket import RtpPacket
import time 
CACHE_FILE_NAME = "cache-"
CACHE_FILE_EXT = ".jpg"
```
Error Flagged:
```
client.py:4: error: Library stubs not installed for "PIL"  [import]
client.py:4: note: Hint: "python3 -m pip install types-Pillow"
client.py:4: note: (or run "mypy --install-types" to install all missing stub packages)
client.py:4: note: See https://mypy.readthedocs.io/en/stable/running_mypy.html#missing-imports
client.py:4: error: Name "Image" already defined (possibly by an import)  [no-redef]
Found 2 errors in 1 file (checked 1 source file)    
```

Analysis:
Above errors in import are false positives; These errros get flagged because mypy was not able to find the module that was tired to be imported, whether it comes bundled with type hints or not, there are no actual errors as these libraries were imported and used in the program.

Errornous Code:
```
self.serverAddr = serveraddr
self.serverPort = int(serverport)
self.rtpPort = int(rtpport)
self.fileName = filename
self.rtspSeq = 0
self.sessionId = 0
self.requestSent = -1
self.teardownAcked = 0
self.connectToServer()
self.frameNbr = 0
#new variables for stat calculation
self.statExpRtpNb = 0 
self.statCumLost = 0
self.lastHighSeqNb = 0  
self.statTotalPlayTime = 0 
self.statTotalBytes = 0 
self.statDataRate = 0
self.statFractionLost = 0
self.lastCumLost = 0
```

Errors Flagged:
```
client.py:34:2: C0103: Attribute name "serverAddr" doesn't conform to snake_case naming style (invalid-name)                                                            client.py:35:2: C0103: Attribute name "serverPort" doesn't conform to snake_case naming style (invalid-name)
client.py:36:2: C0103: Attribute name "rtpPort" doesn't conform to snake_case naming style (invalid-name)
client.py:37:2: C0103: Attribute name "fileName" doesn't conform to snake_case naming style (invalid-name)
client.py:38:2: C0103: Attribute name "rtspSeq" doesn't conform to snake_case naming style (invalid-name)
client.py:39:2: C0103: Attribute name "sessionId" doesn't conform to snake_case naming style (invalid-name)
client.py:40:2: C0103: Attribute name "requestSent" doesn't conform to snake_case naming style (invalid-name)
client.py:41:2: C0103: Attribute name "teardownAcked" doesn't conform to snake_case naming style (invalid-name)
client.py:43:2: C0103: Attribute name "frameNbr" doesn't conform to snake_case naming style (invalid-name)
client.py:45:2: C0103: Attribute name "statExpRtpNb" doesn't conform to snake_case naming style (invalid-name)
client.py:46:2: C0103: Attribute name "statCumLost" doesn't conform to snake_case naming style (invalid-name)
client.py:47:2: C0103: Attribute name "lastHighSeqNb" doesn't conform to snake_case naming style (invalid-name)
client.py:48:2: C0103: Attribute name "statTotalPlayTime" doesn't conform to snake_case naming style (invalid-name)
client.py:49:2: C0103: Attribute name "statTotalBytes" doesn't conform to snake_case naming style (invalid-name)
client.py:50:2: C0103: Attribute name "statDataRate" doesn't conform to snake_case naming style (invalid-name)
client.py:51:2: C0103: Attribute name "statFractionLost" doesn't conform to snake_case naming style (invalid-name)
client.py:52:2: C0103: Attribute name "lastCumLost" doesn't conform to snake_case naming style (invalid-name)
client.py:118:3: C0103: Attribute name "statStartTime" doesn't conform to snake_case naming style (invalid-name)
client.py:121:3: C0103: Attribute name "playEvent" doesn't conform to snake_case naming style (invalid-name)
client.py:204:2: C0103: Attribute name "rtspSocket" doesn't conform to snake_case naming style (invalid-name)
client.py:248:2: C0103: Attribute name "numPktsExpected" doesn't conform to snake_case naming style (invalid-name)
client.py:249:2: C0103: Attribute name "numPktsLost" doesn't conform to snake_case naming style (invalid-name)
client.py:315:2: C0103: Attribute name "rtpSocket" doesn't conform to snake_case naming style (invalid-name)     
```

Analysis:
Such errors (Naming style errors) are true positives but its convention depends from programmer to programmer due to the existance of many naming styles like camel case, kebab case, snake case, pascal case. If the programmer has been using a specific naming style since the inception then it does not make sense to later change to snake case style that is specifically expected by mypy in the code.

Errornous code:
```
	INIT = 0
	READY = 1
	PLAYING = 2
```

Errors Flagged:
```
client.py:18:0: W0311: Bad indentation. Found 1 spaces, expected 4 (bad-indentation)
client.py:19:0: W0311: Bad indentation. Found 1 spaces, expected 4 (bad-indentation)
client.py:20:0: W0311: Bad indentation. Found 1 spaces, expected 4 (bad-indentation) 
```

Analysis:
A good practice to use tab (4 whitespaces in code) instead of a Whitespace mypy correctly flags this particular thing. This is not some error that breaks the code; It is just a good programming etiquette that simplifies the codes redability and maike it understandable, helping keep track of braces and what code block belongs to which particular section.

Errors Flagged:
```
Unused import(s) sys, enum, types, TclError, re, wantobjects, TkVersion, TclVersion, READABLE, WRITABLE, EXCEPTION, EventType, Event, NoDefaultRoot, Variable, StringVar, IntVar, DoubleVar, BooleanVar, mainloop, getint, getdouble, getboolean, Misc, CallWrapper, XView, YView, Wm, Tk, Tcl, Pack, Place, Grid, BaseWidget, Widget, Toplevel, Canvas, Checkbutton, Entry, Frame, Listbox, Menu, Menubutton, Message, Radiobutton, Scale, Scrollbar, Text, OptionMenu, PhotoImage, BitmapImage, image_names, image_types, Spinbox, LabelFrame, PanedWindow, NO, FALSE, OFF, YES, TRUE, ON, NW, SW, NE, SE, NS, EW, NSEW, CENTER, NONE, X, Y, BOTH, LEFT, TOP, RIGHT, BOTTOM, RAISED, SUNKEN, FLAT, RIDGE, GROOVE, SOLID, HORIZONTAL, VERTICAL, NUMERIC, CHAR, WORD, BASELINE, INSIDE, OUTSIDE, SEL, SEL_FIRST, SEL_LAST, END, INSERT, CURRENT, ANCHOR, ALL, NORMAL, DISABLED, ACTIVE, HIDDEN, CASCADE, CHECKBUTTON, COMMAND, RADIOBUTTON, SEPARATOR, SINGLE, BROWSE, MULTIPLE, EXTENDED, DOTBOX, UNDERLINE, PIESLICE, CHORD, ARC, FIRST, LAST, BUTT, PROJECTING, ROUND, BEVEL, MITER, MOVETO, SCROLL, UNITS and PAGES from wildcard import of tkinter (unused-wildcard-import)
```

Analysis: It is not a viavle option to import libraries that are not intended to be used, this leads to extraneous memory consumption and high compilation time. The user should import only the required and necessary libraries. However, it is not a critical error but shows good programming etiquette.
