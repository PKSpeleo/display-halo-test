# Display Halo / Backlight Test

Live demo: https://pkspeleo.github.io/display-halo-test/

This tiny tool is designed to **visualize backlight behavior, halos and blooming** on different display types  
(**IPS / miniLED / OLED**).

Because it is a single self-contained HTML file, it can be hosted for free on **GitHub Pages** and opened directly in any modern browser.

---

## Table of contents

- [What this tool shows](#what-this-tool-shows)
- [Basic usage](#basic-usage)
- [Controls](#controls)
    - [Frame (edges of the panel)](#frame-edges-of-the-panel)
    - [Pixel modes](#pixel-modes)
    - [Pixel size / halo scale](#pixel-size--halo-scale)
    - [Fun interaction mode (catch & kick pixels)](#fun-interaction-mode-catch--kick-pixels)
- [How to use it in practice](#how-to-use-it-in-practice)
- [Disclaimer](#disclaimer)
- [Notes](#notes)

---

## What this tool shows

- How a screen handles **small bright objects on a black background**
- How strong the **halo / blooming** is around tiny pixels and around larger shapes
- How **local dimming zones** react to:
    - moving points of light,
    - different colors (R/G/B/W),
    - multiple simultaneous sources,
    - short “flashes” (explosion waves),
    - pixels that are **pushed and kicked around** by a bright square “paddle”
- How the panel behaves near the **screen edges** (with a white frame)

Use it in a dark room, set brightness as you like, and watch how light spreads or stays contained around the pixels.

---

## Basic usage

1. Open the page:  
   https://pkspeleo.github.io/display-halo-test/
2. Make the browser window **full screen** (for example `F11` on many systems).
3. You will see:
    - a completely **black screen**,
    - a set of **animated color pixels** (mode `6`) starting from the center.

Move closer and observe:
- the shape and size of the **halo** around each pixel,
- how halos change when pixels move or collide,
- how the background black level behaves.

---

## Controls

### Frame (edges of the panel)

- **Space** – toggle a white frame along the inside edge of the screen.
    - Use this to check **edge glow / backlight bleed**.
    - When bright pixels hit screen edges, the frame briefly **flashes** in their color.

---

### Pixel modes

All modes can be combined. Press the same key again to turn that mode off.

#### Single test pixels

- **`1`** – single red pixel `1 (R)`
- **`2`** – single green pixel `2 (G)`
- **`3`** – single blue pixel `3 (B)` (saturated blue)
- **`4`** – single white pixel `4 (W)`

Each pixel:
- starts from the **center of the screen**,
- moves in a **random direction**,
- **bounces from the screen edges**,
- causes the frame to flash in its **own color** on each hit.

Use these for clean, isolated R/G/B/W halo tests.

#### Multi-pixel colour modes

- **`5`** – toggle **10 vivid static colour pixels**  
  Label: `5 (10 colour pixels)`
    - All pixels have different bright colors.
    - Useful to see how halos from different colors interact.

- **`6`** – toggle **10 animated colour pixels** (this mode is **ON by default**)  
  Label: `6 (10 animated colours)`
    - Pixels constantly change their hue (smooth rainbow animation).
    - Great for testing **local dimming** and how the panel handles slow color transitions.

All pixels:
- move independently,
- start from the center,
- collide with each other,
- create short-lived **square “explosion” waves** on collisions (to simulate brief bright flashes).

---

### Pixel size / halo scale

You can change the **physical size** of the pixels to see how blooming behaves for different object sizes.

- **`+`** – increase pixel size  
  (Use the `=`/`+` key or numpad `+`, no Shift required.)
- **`-`** – decrease pixel size  
  (Use the `-` key or numpad `-`.)

Each step changes the size proportionally to the `devicePixelRatio`, so the scale is tied to **real physical pixels** as closely as the browser allows.

When the frame is visible, the small HUD in the bottom-right corner shows:
- which modes are active (with colored labels),
- current viewport size,
- `devicePixelRatio`,
- current **pixel scale** (approximate number of physical pixels).

---

### Fun interaction mode (catch & kick pixels)

Besides “static” observation, there is a small **entertainment / interaction mode** that is also useful for testing:
you can catch pixels with a bright square and **launch** them to see how halos behave during fast motion.

#### Desktop (mouse)

- Press and hold the **left mouse button** anywhere on the screen.
    - A bright **square “paddle”** with a rainbow frame appears under the cursor.
    - Any pixel inside this square at the moment of click is **captured** and moves together with the square.
- Move the mouse while holding the button:
    - the captured pixel(s) travel with the square.
- Release the mouse:
    - captured pixels are **flung away** with the speed and direction of the square at the moment of release.

When pixels **hit** this square:

- they bounce off with reduced elasticity (so the impact is softer than from the screen edge),
- a short **explosion wave** appears at the collision point,
- the explosion color mixes the pixel color and the current color of the rainbow frame.

This lets you see how halos and blooming behave when bright objects are:
- moved quickly through dark areas,
- suddenly accelerated or stopped,
- clustered around a larger bright shape (the square).

#### Mobile / tablet (multi-touch)

On touch devices the same logic works with fingers:

- Touch and hold with **one finger** – a square appears under that finger and captures any pixels inside.
- Touch with **two or more fingers at once**:
    - each finger gets its **own square**,
    - you can catch and launch pixels with **two fingers in different places**,
    - collisions with each square also create explosion waves.

This is a handy way to:
- interactively “push” pixels through different parts of the screen,
- see how halos follow moving lights,
- compare backlight behaviour under quick, chaotic movement.

---

## How to use it in practice

Some ideas for testing:

- Compare **IPS vs miniLED vs OLED**:
    - Enable one or two small white pixels (`4`) and look at the halo.
    - Add animated pixels (`6`) and see how fast the background returns to **deep black**.
- Check **local dimming zones** on miniLED:
    - Use several colors (`5`) and animated pixels (`6`) at the same time.
    - Watch how zones follow the moving lights and how large the halos are.
- Test **edge bleed**:
    - Turn on the frame (Space) and one bright pixel.
    - Watch what happens when the pixel hits the edges and corners.
- Explore **blooming with larger objects**:
    - Increase size with `+` until pixels become small squares.
    - Observe how halos grow and how well the screen controls large bright areas.
- Use the **fun interaction mode**:
    - Catch a pixel with the square, fling it across the screen and follow the halo.
    - On mobile, use **two fingers** to bounce pixels between two squares and watch how local dimming reacts.

---

## Disclaimer

Yes, this is one big single-file **code monster** with a lot of “not-the-best-architected” JavaScript inside.  
It was written **very quickly, on the fly**, just to solve a concrete task:

> “Show bright pixels on an absolutely black background and let me watch how the backlight / halos behave.”

It does exactly that, it already served its purpose well, and it is **very unlikely to receive serious refactoring or future updates**.  
Treat it as a useful hack / lab tool rather than a reference implementation of clean code. 😉

---

## Notes

- The app runs entirely in the browser – **no installation** required.
- The project is intentionally a **single HTML file**, so it can be hosted easily and for free via **GitHub Pages**.
- For the most sensitive tests, use a **dark room** and avoid other bright windows around the browser.

Happy halo hunting! 🌈💡🕵️‍♂️