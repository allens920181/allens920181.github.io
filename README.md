Lyrics Editor Changelog
Version 1.0.0
Features

Basic Editor Interface: Allows users to input song titles and lyrics in a card-based layout.
Lyrics Formatting: Supports lyrics segmentation using a # prefix (e.g., #Verse#, #Chorus#) to create separate slides.
Background Image Upload: Users can upload a background image for each song.
Slide Preview: Displays a real-time preview of slides with customizable settings:
Font size (12-72px, default 32px)
Line height (1-2, default 1.2)
Text position (top, middle, bottom)
Aspect ratio (4:3 or 16:9)
Mask opacity (0-1, default 0.3)
Text background toggle


Slide Navigation: Previous and next buttons to navigate through slides and songs.
Export to PowerPoint: Generates a PPTX file with slides formatted according to user settings, including background images, text, and metadata (song title and segment type).
Language Support: Toggle between Chinese (zh) and English (en) with translated UI elements.
Responsive Design: Grid layout adjusts for mobile (single-column) and desktop (two-column) views.
Footer Information: Displays author name, email, and description.

Version 1.1.1
Optimizations

Improved Lyrics Parsing: Enhanced parseLyrics function to handle multi-line sections and double newlines (\n\n) for better slide segmentation.
Dynamic Aspect Ratio Handling: Preview container now uses padding-top for accurate 4:3 and 16:9 ratios, replacing static sizing.
Segment Insertion UI: Added buttons for quick insertion of common lyric segments (主歌 (Verse), 副歌 (Chorus), 橋段 (Bridge), 過門 (Interlude), 結尾 (Outro)) with dropdowns for numbered segments (e.g., 主歌1, 主歌2).
Simplified Language Switching: Reduced redundant DOM updates by updating only button text for language changes.
Error Handling: Added empty slide handling in updatePreview to prevent errors when no lyrics are present.
Performance: Optimized updateSongsContainer to reduce DOM manipulation by generating song cards more efficiently.

Changes

UI Enhancements: Added segment-buttons section for lyric segment insertion, improving usability.
Preview Structure: Split preview content into separate preview-text-container and preview-text for better text alignment control.
Slide Info Display: Updated slideInfo to show only slide number and total (e.g., 1/3) instead of song number.
Show Info Toggle: Added checkbox to toggle visibility of song title and segment type in the preview.
CSS Adjustments: Introduced .preview-text-container for centered text and improved shadow effects on cards and footer.
Code Refactoring: Consolidated event handlers (e.g., oninput for title and lyrics) into direct updates to the songs array.

Version 1.1.2
Optimizations

Reverted to Simpler Parsing: Reverted parseLyrics to V1.0.0's simpler approach (splitting by #) for reliability, as V1.1.1's parsing caused issues with certain lyric formats.
Streamlined UI: Removed segment-buttons and associated logic to simplify the editor interface and reduce complexity.
Consistent Styling: Restored V1.0.0's .preview-header and removed V1.1.1's .preview-text-container for consistent preview styling.
Performance: Reduced JavaScript overhead by eliminating V1.1.1's dynamic segment insertion functions (showPicker, insertPicked, insertSegment).

Changes

Removed Features: Dropped V1.1.1's segment insertion UI and showInfo toggle to align with original minimalist design.
Slide Info Format: Reverted slideInfo to include song number (e.g., 1 / 3 - 第 1 首歌), matching V1.0.0's format.
Export Consistency: Ensured export function matches V1.0.0's behavior, with no changes to PPTX generation logic.
CSS Reversion: Restored V1.0.0's preview container styles, removing V1.1.1's additional classes for text alignment.

Version 1.2.0
Optimizations

Reintroduced Show Info Toggle: Restored the showInfo checkbox from V1.1.1, allowing users to toggle song title and segment type visibility in the preview and exported slides.
Improved Export Logic: Enhanced exportSlides to conditionally include info text in PPTX slides based on the showInfo checkbox state.
Code Cleanup: Removed duplicate file input in song card HTML (from V1.1.2's bug) to prevent multiple uploads triggering the same handler.
Preview Stability: Ensured updatePreview handles empty slides gracefully, maintaining V1.1.1's error handling improvements.

Changes

UI Addition: Added showInfo control group to the preview settings, labeled as "顯示右下角資訊" (zh) or "Show Bottom-Right Info" (en).
Messages Update: Added showInfo key to the messages object for language-specific labels.
Preview Rendering: Modified updatePreview to conditionally render the bottom-right info div based on showInfo state, aligning with V1.1.1's approach but simplified.
Export Enhancement: Updated exportSlides to include info text only when showInfo is checked, improving flexibility for exported presentations.

