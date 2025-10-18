# JMP

### A game that doesn't just run *in* your browser—it runs *on* your browser.

![JMP Gameplay GIF](https://github.com/gmirsky2/JMP/blob/main/gameplay.gif)

> **JMP** transforms the browser's URL address bar into a minimalist, 4-pixel-high display, creating a survival game where the screen is a single, constantly changing line of text.

**[▶️ Play it Live Here](https://gmirsky2.github.io/JMP/index.html)** _(You will want to open Incognito)_

---

## How to Play

1.  **Open `index.html`** in an incognito/private window using a modern web browser (Chrome, Firefox, Edge).
2.  **Look up!** The entire game takes place in the URL address bar at the top of your screen.
3.  Press **`Arrow Up`** to jump.
4.  Navigate the player character through the gaps in the scrolling pipes to increase your score.

**⚠️ Important:**  
Every frame of animation updates the browser’s URL.  
**Previously:** This created a new entry in your browser’s history for every frame.  
**Now: Still a work in progress** The game uses advanced techniques to update the URL without polluting your history.  
It is still **recommended** to play in an Incognito or Private window for the cleanest experience.

---

## The Technical Elegance: How It Works

`JMP` is a creative "hack" that subverts the intended purpose of several standard web features to create an interactive experience. The entire engine is self-contained in a single HTML file with zero dependencies.

#### The URL as a Framebuffer
The game's animation is not a video or a GIF. It's achieved by rapidly updating the URL's hash fragment (`window.location.hash`) within a `requestAnimationFrame` loop.  
**Now:** The game uses `history.replaceState` and `location.replace` to update the URL without creating new history entries.

#### Braille Characters as a GPU
To achieve a vertical dimension on a single line of text, `JMP` uses the Unicode Braille character set (`U+2800` to `U+28FF`). Each Braille character is a programmable 2x4 dot matrix. By performing bitwise operations to control which of the 8 dots are active, the game can "draw" shapes with a 4-pixel height. When these characters are placed side-by-side, they form a continuous, albeit extremely low-resolution, display canvas.

#### Vanilla JavaScript as the Game Engine
All game logic—from physics and procedural generation to input handling and collision detection—is managed by a lean, dependency-free JavaScript engine. The state of every object is calculated in memory and then "rendered" into a string of Braille characters, which is then pushed to the URL for display.

---

## Constraints as a Canvas

This project is an exercise in finding creativity within severe constraints. The Limitations are not bugs to be fixed, but rules that define the medium:

*   **Monochrome Display:** The game has no color, embracing the stark, high-contrast aesthetic of its text-based environment.
*   **Extreme Low-Resolution:** The 4-pixel vertical height forces a minimalist art style and gameplay that is simple to parse at a glance.
*   **Silence:** With no audio, the player's focus is entirely on the visual rhythm and flow of the game.

---
