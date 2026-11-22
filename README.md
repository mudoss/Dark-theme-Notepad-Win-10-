# Notepad Dark (Windows 10)

<img width="1181" height="832" alt="715155799-ba68a6cb-a1cd-4142-9a24-002eb0b6800c" src="https://github.com/user-attachments/assets/c9185ace-c3ac-48cc-a398-886d0ccf2841" />


A **feature-by-feature recreation of Windows 10 Notepad with a dark
theme**. A standalone application that replaces `notepad.exe`: no DLL
injection and no system files are modified.

It uses Windows' official `Image File Execution Options` mechanism, just
like the Task Manager Dark Mode project.

Everything that launches Notepad opens Notepad Dark, including
`Win+R → notepad`, "Open with / Edit," right-click → editing a new text
document, and commands such as `notepad file.txt`.

## Installation

1.  Extract the folder and double-click **`Activate Notepad Dark.cmd`**
    (administrator permission is requested once). The application is
    compiled using the .NET Framework 4.x compiler already included with
    Windows; no additional downloads are required.
2.  To undo the installation, run **`Revert to Windows Notepad.cmd`** (a
    copy is also included in the installation folder).

`build.ps1` parameters: `-Shell Apply | Revert | Clean`, `-NoBuild`.

The installer copies two executables to `%ProgramFiles%\NotepadDark` and
writes a `Debugger` value under
`HKLM\...\Image File Execution Options\notepad.exe` (both 64-bit and
32-bit registry views). Any pre-existing `Debugger` value (for example,
one used to redirect Notepad to Notepad++) is saved and restored when
reverting.

## Features

-   **File:** New, New Window, Open, Save, Save As (with **Encoding**
    selection), Page Setup, Print, Exit
-   **Edit:** Undo, Cut/Copy/Paste/Delete, Search with Bing, Find / Find
    Next / Find Previous (Match case, Wrap around, Up/Down), Replace /
    Replace All, Go To, Select All, Time/Date (F5)
-   **Format:** Word Wrap, Font
-   **View:** Zoom (Ctrl +/-/0, Ctrl+mouse wheel, 10%--500%), Status Bar
    (Ln/Col, zoom, line endings, encoding)
-   **Help:** View Help, About
-   Detects and saves ANSI / UTF-16 LE / UTF-16 BE / UTF-8 / UTF-8 BOM;
    preserves CRLF / LF / CR line endings (these can be changed by
    clicking the corresponding fields in the status bar)
-   `.LOG` on the first line, word deletion with Ctrl+Backspace,
    8-character tab stops, and opening files via drag and drop
-   Command line: `notepad file`, `/p`, `/pt`, `/a`, `/w`; prompts
    whether to create a file if it does not exist
-   Printing: header/footer codes `&f &d &t &p &l &c &r`
-   Dark title bar, menus, status bar, scroll bars, and all custom
    dialogs
-   Settings are stored under `HKCU\Software\NotepadDark`; on first
    launch, the original Notepad's font, scrolling, and margins are
    imported

## Differences from the Original

-   **Open/Save, Font, and Print** windows are standard Windows dialogs.
    They are drawn by the system and therefore cannot be made dark.
-   Undo is single-level (like the EDIT control in Windows 10 Notepad).
-   "Show Unicode control characters," IME/reconversion, and "Send
    Feedback" are not available.
-   Page Setup does not include printer source (paper tray) selection or
    a preview.
-   Additional feature: encoding and line endings can be changed from
    the status bar.

## Troubleshooting

Error log: `%APPDATA%\NotepadDark\errors.log`. The target is Windows 10,
as the Store version of Notepad in Windows 11 works differently.

This is an independent open-source project and is not affiliated with
Microsoft. License: MIT.
