# Feature: Word-like Custom Text Styles & Semantic Integration

## Overview

Implemented a dynamic, fully functioning "Custom Text Styles" engine for the Tiptap editor to allow users to save and easily apply predefined rich CSS formats. Furthermore, integrated the semantic logic (H1-H6, Blockquote, etc.) so that applying styles maintains proper document structure and Table of Contents (TOC) mappings.

## Key Changes

### 1. Dynamic Settings Configuration (`Prefs.ts` & `SettingsView.tsx`)

-   Migrated hard-coded CSS styles into the application's global `Prefs` (`EditorPrefs`), allowing styles to be dynamically configurable entirely by the end user.
-   Added a `Custom Text Styles` settings section under Editor Options, equipped with a dedicated JSON `Textarea`.
-   Created robust UI state management to prevent typing clobbering, enforcing strict JSON checks without disturbing the user's cursor while editing.

### 2. Tiptap Engine Semantic Adaptation (`CustomStyle.ts`)

-   Rebuilt the `CustomStyle` Tiptap extension to read styles directly on the fly.
-   Taught the `CustomStyle` parser to strip out internal semantic keywords (like `"tag"`) directly from CSS conversion (`renderHTML`).
-   Configured dynamic initialization and destruction through `EditorExtensions.ts` and `EditorView.tsx`.

### 3. Smart Unified Toolbar (`Toolbar.tsx`)

-   Removed the old, redundant, and messy 1-to-6 heading split component from the Top Toolbar to centralize styling.
-   Bound the internal behavior of the Styles `<Select>` element to dynamically execute core Tiptap structural commands (`editor.chain().focus().setHeading({ level: 1 }) `... etc.) depending entirely on the matched user-defined `"tag"` attribute within their configurations.
-   Seamlessly reverts standard `setParagraph` toggling on `Default` reset.

### 4. Table of Contents Scroll Upgrade (`TableOfContents.tsx`)

-   Wrapped the automatic index nodes (Anchors) with a Mantine `<ScrollArea>` and assigned a fixed responsive height (`h={300}`) to explicitly unlock the vertical scrollbar.
-   Re-engineered the TOC overlay wrapper using CSS `resize: "both"` and `display: "flex"`, allowing the user to seamlessly resize the entire box with the mouse.
-   Ensured the inner scroll area resizes flawlessly (`flexGrow: 1`) alongside the wrapper, enforcing clean `minWidth`/`maxWidth`/`height` containment settings.
