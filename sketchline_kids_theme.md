# Sketchline Kids Theme Reference

This document serves as the ground truth for the "Sketchline Kids" theme, as established in the design sessions. If the user asks to "do as we did before" or refers to the "kids theme", strictly adhere to the following specifications:

## 1. Global UI & Buttons (The "Picnic" Theme)
- **Background Pattern:** All main UI buttons (like "Start a new page", "Continue", and the canvas tools) use the `.picnic-bg` class.
- **Picnic CSS:** It's a red-and-white checkered pattern created with repeating linear gradients (using `rgba(244, 63, 94, 0.6)` for the red squares).
- **Text Readability:** Text or icons inside picnic buttons must have a solid white background with a border (e.g., `bg-white border-2 border-gray-900 rounded-xl`) so they stand out clearly against the checkers.

## 2. Audio & Ambient Sounds
- **Background Music:** The ambient tone is a slow, warm, swelling synth pad (Cmaj7 chord: Do, Mi, Sol, Ti) using triangle waves and a low-pass filter (800Hz). It must NEVER be a sharp "Minecraft chime".
- **Mute Button:** A global mute button exists in the Top Nav Bar. It correctly suspends and resumes the `AudioContext`.

## 3. The Canvas Layout (Jungle Theme)
- **Canvas Frame:** The canvas is surrounded by a massive green border (`#15803d` / green-700) with overlapping circles (radial gradients), a thick `12px` gray-900 border, and `40px` border-radius.
- **Decorations:** There are four giant leaf emojis (`🌿`) placed absolutely in the four corners of the frame.
- **Animals:**
  - Elephant (`🐘`): Bottom left, pulsing animation.
  - Tiger (`🐯`): Top right, pulsing animation, positioned at `right: 150px` (away from the tools).
  - Owl (`🦉`): Top center, bouncing animation.
- **The Train:** A train (`🚂🚃🚃...`) sits at the bottom of the canvas, continuously slithering from right to left (`translateX(100vw)` to `translateX(-100%)`). Its cars have a bouncing "chooChoo" wave animation. When clicked, it pauses for exactly `0.5s` and then resumes.

## 4. Canvas Tools & Interaction
- **Peeking Tools:** The tools are positioned on the right edge using `.peeking-btn` (`translateX(15px)`). When hovered or selected (`.active`), they slide fully into view (`translateX(0)`).
- **Musical Tools:** Each of the 7 tools acts as a musical note (Do, Re, Mi, Fa, Sol, La, Ti). When clicked:
  - It plays its specific frequency using a soft triangle wave.
  - A permanent small popup (`🎵`) attaches to the active tool to show it is currently selected.
- **Sticker Tool (⭐):** Clicking the stamp tool opens a floating `#stickerPicker` menu with 10 emojis. Clicking an emoji updates the active stamp for the canvas.
- **Magic Wand (🪄):** Draws colorful circles/orbs along the stroke path and randomly drops `⭐` emojis (20% chance).

## 5. Canvas Coordinate Math (Critical)
- **Fullscreen Fit:** In kids mode, the canvas internal resolution (`width` and `height`) dynamically matches its container's physical pixel size (`object-fit: fill`) to eliminate letterboxing, ensuring 100% of the green border area is drawable.
- **Pointer Accuracy:** The `getPos()` function meticulously calculates the pointer offset by subtracting the canvas's 4px border from `getBoundingClientRect()`, ensuring the stroke appears perfectly under the crosshair cursor.
