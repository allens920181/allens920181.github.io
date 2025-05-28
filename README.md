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


Version 1.3.0
Enhancements

Improved UI Layout: Adopted a grid-based layout using CSS Grid for better responsiveness, with a single-column layout for mobile devices (below 768px) and a two-column layout for larger screens.
Enhanced Styling: Updated the overall aesthetic with a modern, clean design:
Increased border-radius for cards and buttons to 8px for a softer look.
Added subtle box-shadows to cards and footer for depth.
Improved button transitions with hover and active states for better interactivity.


Language Switching: Implemented a toggle switch for seamless language switching between Chinese (zh) and English (en), dynamically updating all UI text and placeholders.
Paragraph Mode: Introduced a paragraph-based editing mode:
Users can toggle between text and paragraph modes using a switch.
Paragraph mode allows drag-and-drop reordering, copying, and deleting of lyric sections.
Added a move menu for precise paragraph repositioning (up/down).


Image Upload and Management: Added support for background image uploads per song, with a context menu for replacing or deleting images.
Slide Preview Controls: Enhanced preview section with controls for font size, line height, position, aspect ratio, mask opacity, text background, and info display.
Export Functionality: Integrated PptxGenJS for exporting slides to PowerPoint, supporting custom backgrounds, text formatting, and layout options.
Tag Menu: Added a context-sensitive tag menu that appears when typing '#', allowing quick insertion of lyric section tags (e.g., Verse, Chorus).

Bug Fixes

Fixed issues with slide navigation to prevent out-of-bounds errors when switching songs or slides.
Ensured proper cursor positioning after tag insertion in textareas.
Resolved issues with drag-and-drop functionality to prevent incorrect paragraph reordering.

Version 1.4.0
Enhancements

Branding and Naming: Renamed the application to "LySlide" with a new tagline, "From Lyrics to Slides, Effortlessly," reflected in the UI and page title.
Material Icons Integration: Replaced SVG icons with Google Material Icons for a more consistent and professional look, used in buttons, toggles, and upload controls.
Refined UI/UX:
Increased padding and margins (e.g., body padding to 24px, card padding to 24px) for better spacing.
Updated button styles with circular outlines for preview controls and a more prominent primary button style.
Improved toggle switch design with Material Icons for text/paragraph modes.
Enhanced input fields and textareas with focus states (green border) and smoother transitions.


Preview Controls:
Added dedicated buttons for previous/next song navigation, refresh preview, and export, improving usability.
Moved export button to the control-buttons section for better accessibility.
Updated slideInfo to always reflect the correct slide and song count, even with empty songs.


Tag Menu Navigation: Added keyboard navigation (Arrow Up/Down, Enter) for the tag menu, with visual selection feedback (selected tag highlighted).
Responsive Design: Adjusted the mobile breakpoint to 767px and ensured all elements (e.g., buttons, menus) scale appropriately on smaller screens.
Error Handling:
Improved parseLyrics to handle empty or invalid lyrics by returning a default empty slide.
Enhanced updatePreview to validate currentSong and currentSlide, preventing crashes with empty song lists.


Performance Optimization:
Optimized updateSongsContainer to reduce DOM manipulations.
Added transition effects for preview refresh to improve visual feedback.



Bug Fixes

Fixed issues with tag menu persistence when clicking outside or switching textareas.
Resolved inconsistencies in slide navigation when switching songs with different slide counts.
Corrected z-index issues with menus (tag, move, image) to ensure they appear above other elements.
Fixed export functionality to skip empty songs and handle edge cases with invalid slide data.


Version 1.5.0

1. UI Layout and Responsiveness
Single-Column Layout: V1.5 adopts a single-column flex layout (.container { display: flex; flex-direction: column; }) instead of V1.4’s grid-based two-column layout (editor and preview side-by-side). This improves mobile usability by stacking sections vertically, reducing horizontal scrolling issues on smaller screens.

Dynamic Container Sizing: The container’s max-width: 50vw; min-width: 600px in V1.5 (vs. V1.4’s max-width: 1400px) ensures better adaptability to various screen sizes while maintaining a minimum width for usability. On mobile (max-width: 767px), max-width: 90vw; min-width: unset further optimizes for small screens.

Font and Element Scaling: V1.5 refines font sizes and padding for mobile devices (e.g., .btn font size reduced to 12px, card padding to 12px in media query), improving readability and touch interaction.

2. Preview Scaling
Dynamic Preview Dimensions: V1.5 calculates the preview height based on the parent container’s width and aspect ratio (previewHeight = availableWidth * heightRatio / widthRatio), ensuring the preview scales proportionally without overflow. V1.4 used a static approach, less responsive to container size changes.

Font Size Normalization: V1.5 normalizes font size to a 1280px base (scaleFactor = availableWidth / 1280), ensuring consistent text scaling across devices. V1.4 lacked this explicit scaling logic.

Resize Event Listener: V1.5 adds window.addEventListener('resize', updatePreview) to re-render the preview on window resize, ensuring responsiveness. V1.4 did not explicitly handle resize events.

3. Performance Improvements
Efficient DOM Updates: V1.5 uses requestAnimationFrame in insertTag to schedule cursor positioning and preview updates, reducing layout thrashing. V1.4 performed these synchronously, potentially causing jank.

Debounced Preview Updates: In handleLyricsChange, V1.5 conditionally updates the preview only when the tag menu is not active or the change isn’t from tag insertion, reducing unnecessary re-renders compared to V1.4’s immediate updates.

Optimized Slide Info: V1.5 updates slideInfo dynamically in updatePreview using template literals, consolidating logic that was scattered in V1.4.

4. Usability Enhancements
Tag Menu Keyboard Navigation: V1.5 improves tag menu interaction by adding Tab prevention and Escape key support to close the menu, enhancing keyboard accessibility. V1.4 supported only ArrowUp, ArrowDown, and Enter.

Toggle Switch Labels: The text/paragraph toggle in V1.5 uses Material Icons (text_fields, short_text) inside the slider, improving visual clarity over V1.4’s plain text labels.

Song Deletion Icon: V1.5 positions the song delete icon statically (position: static) within the song-input-container, making it more predictable than V1.4’s absolute positioning.

Paragraph Block Height: V1.5 sets a fixed height: 50px for .paragraph-block, ensuring consistent drag-and-drop visuals. V1.4 relied on content-driven heights, which could vary.

5. Code Structure
Consolidated Language Messages: V1.5 centralizes all translatable strings in the messages object, including new entries like convertToParagraphs and convertToText. V1.4 had a less comprehensive set, requiring more inline updates.

Modular Menu Handling: V1.5 refactors menu logic (e.g., showMoveMenu, showImageMenu) to use consistent patterns with hide*OnClickOutside functions, improving maintainability over V1.4’s ad-hoc implementations.

Error Handling in Export: V1.5 wraps exportSlides in a try-catch block with a user-friendly alert for errors, improving robustness compared to V1.4’s basic error handling.

Fixes

1. Drag-and-Drop Stability
Drop Index Accuracy: V1.5 improves drop index calculation in dropParagraph by checking event.clientY < rect.top + rect.height / 2, ensuring precise paragraph reordering. V1.4’s logic was less refined, occasionally misplacing paragraphs.

Drag State Cleanup: V1.5 removes the dragging class in dropParagraph after a drop, preventing visual artifacts. V1.4 could leave elements in a dragging state.

Move Menu Sync: V1.5 updates the move menu position (updateMoveMenuPosition) after drag-and-drop or manual moves, fixing V1.4’s issue where the menu could become misaligned.

2. Lyrics Parsing
Empty Lyrics Handling: V1.5’s parseLyrics returns a default empty slide ([{ type: 'Empty', content: '' }]) for blank or undefined lyrics, preventing crashes. V1.4 was less robust, potentially causing undefined behavior.

Section Splitting: V1.5 refines parseLyrics to split content by double newlines (\n\n) and filter empty parts, ensuring accurate slide creation. V1.4’s parsing could include empty slides unnecessarily.

3. Preview Robustness
Index Validation: V1.5 ensures currentSong and currentSlide are within valid ranges in updatePreview (Math.max(0, Math.min(...))), fixing potential out-of-bounds errors in V1.4.

Fallback Background: V1.5 sets a gradient background (linear-gradient(to right bottom, #4a5568, #2d3748)) when no image is provided, improving visual consistency over V1.4’s plain black fallback.

Info Box Scaling: V1.5 enforces a minimum infoFontSize of 14px in the preview, fixing V1.4’s issue where small screens could render unreadable text.

4. Export Reliability
Timestamped Filenames: V1.5 generates PPTX filenames with a timestamp (歌詞投影片_${timestamp}.pptx), preventing overwrites and improving user organization. V1.4 used a generic filename.

Blob-based Export: V1.5 uses pptx.write('blob') with URL.createObjectURL for reliable downloads, fixing V1.4’s less robust export method that could fail in some browsers.

Empty Song Check: V1.5 checks for valid songs before export (songs.some(song => song.lyrics.trim() || song.paragraphs.length)), preventing empty PPTX files. V1.4 lacked this validation.

5. UI Consistency
Button Styling: V1.5 standardizes .btn-outline buttons with a circular shape (border-radius: 50%) and consistent sizing (36px or 32px on mobile), fixing V1.4’s varied button appearances.

Menu Positioning: V1.5 ensures menus (tag, move, image) are positioned relative to their triggers using getBoundingClientRect, fixing V1.4’s occasional misalignment on scroll or resize.

Ver1.5.1
- 在輸入兩個 `#` 時才會顯示 `tagMenu`，而單個 `#` 不會觸發菜單顯示。
- 選擇完標籤後，輸入的兩個 ## 會被替換為一個 #，並插入所選的標籤到文字框中。
