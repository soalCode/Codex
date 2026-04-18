# Codex Changelog

## Recent Feature Updates

### ✨ Features & Enhancements

-   **Text Finder (Search in Page)**

    -   Added a fully functional "Find in Document" overlay accessible via `CTRL+F` / `CMD+F`.
    -   Integrated a custom Tiptap Search extension leveraging ProseMirror Decorations to highlight text seamlessly without hijacking the DOM string selection or the user's cursor focus.
    -   Added auto-scroll to the current match using smooth browser native transitions.
    -   Supported Keyboard Shortcuts within the Finder input box (`Enter` for next, `Shift+Enter` for previous, `Escape` to close).
    -   Safely escaped all RegEx characters to support searching for wildcards and punctuation marks without performance bottlenecks.

-   **Image Cropper Modal**

    -   Integrated a robust Image Cropping sub-routine directly into the Editor.
    -   When selecting an image inside the editor, a new "Crop" button dynamically appears in the toolbar.
    -   The modal supports freeform cropping using an HTML5 Canvas interface and elegantly replaces the old image with the newly cropped Base64 preview.

-   **Dynamic 'Word-Style' Text Styling**

    -   Transitioned from hardcoded tags to a fully dynamic Custom Styles configuration powered by JSON (`Prefs.ts`).
    -   Users can now define entirely customized text and heading rules globally mapped within Codex.
    -   The Editor Toolbar dropdown automatically reads and maps these styles into selectable headings and paragraphs seamlessly.

-   **Auto-Save System**

    -   Implemented an internal interval-based tracker managing the background saving operations of the active note.
    -   Introduced fully granular controls under Settings to disable Auto-Save or configure its intervals (ranging from 1 to 30 minutes).

-   **Settings Menu Redesign & Organization**

    -   Overhauled `SettingsView.tsx` utilizing Mantine's modern Tab-based interface.
    -   Split configurations into three accessible macro-categories: **General**, **Editor**, and **Saving**.
    -   Added a brand new scaling preference (`toolbarSize`) that dynamically alters the size of the Editor Toolbar for accessibility and better clicks.

-   **Table of Contents (TOC) UI Uplift**

    -   Redesigned the TOC container to be scrollable and properly constrained inside the view window, resolving overlap issues for documents spanning many headings.

-   **Localization Coverage**
    -   Added and integrated all strings relating to Auto-Save, Cropper, Editor Width/Border, Text Finder, and Toolbar sizing across all language dictionaries (English `en_US`, Russian `ru_RU`, Simplified Chinese `zh_CN`).

### 🐛 Bug Fixes

-   Prevented `CTRL+F` from causing duplicate component mounts if the finder was already active.
-   Resolved Z-Index overlapping conflicts between the floating Text Finder and the sticky Editor Toolbar.
-   Fixed an issue where the generic Auto-Save feature could crash if trigged while switching components globally.
