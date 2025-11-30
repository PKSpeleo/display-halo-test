# Display Halo / Backlight Test

Live demo: https://pkspeleo.github.io/display-halo-test/

This tiny tool is designed to **visualize backlight behavior, halos and blooming** on different display types  
(**IPS / miniLED / OLED**).

Because it is a single self-contained HTML file, it can be hosted for free on **GitHub Pages** and opened directly in any modern browser.

---

## What this tool shows

- How a screen handles **small bright objects on a black background**
- How strong the **halo / blooming** is around tiny pixels and around larger shapes
- How **local dimming zones** react to:
    - moving points of light,
    - different colors (R/G/B/W),
    - multiple simultaneous sources,
    - short “flashes” (explosion waves)
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

---

## Notes

- The app runs entirely in the browser – **no installation** required.
- The project is intentionally a **single HTML file**, so it can be hosted easily and for free via **GitHub Pages**.
- For the most sensitive tests, use a **dark room** and avoid other bright windows around the browser.

Happy halo hunting! 🌈💡🕵️‍♂️