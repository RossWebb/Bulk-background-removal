# Part-Out Vector Engine 🏎️✂️

An ultra-low-cost, high-efficiency batch background clipping application for automotive parts inventory, optimized specifically for deployment on GitHub Pages.

By pivoting away from heavy image-to-image generation models and utilizing **Gemini 2.5 Flash** as a visual segmentation coordinator, this tool drops processing costs from **~10¢ AUD per image down to roughly 0.005¢ AUD per image**—allowing you to map thousands of parts for pennies.

---

## 💡 How It Works (The Sub-Penny Shift)

Instead of paying a premium for an AI server to manipulate pixels and stream back a heavy image payload, this application delegates the heavy lifting directly to your local machine:

1. **Upload:** You drop a batch of high-resolution part photos into the browser interface.
2. **Coordinate Mapping:** The lightweight Gemini 2.5 Flash model scans the image and returns a compact 4-point text coordinate array (`[ymin, xmin, ymax, xmax]`) outlining the exact boundaries of the mechanical part.
3. **Local Canvas Slicing:** Your web browser's native HTML5 Canvas instantly crops the original high-resolution image data down to those exact vector bounds and triggers an automatic PNG download.

---

## 🛠️ GitHub Pages Deployment

Because modern web browsers enforce strict security boundaries (**CORS**), running this file directly off your local hard drive (`file:///`) will block the canvas memory stream and result in empty 0-byte images. Hosting it via GitHub Pages serves it over a secure internet protocol (`https://`), which completely fixes this error.

1. Push your HTML file to a public GitHub repository.
2. Go to the repository's **Settings** tab.
3. Scroll down to **Pages** on the left-hand menu.
4. Set the Source to the `main` or `master` branch and click **Save**.
5. Give it about 60 seconds to build, then open your live `*.github.io` web link to process your batches!

---

## 🔑 API Key Safety & Cost Management

* **Zero Leaks:** Your Gemini API Key is saved strictly within your browser's local cache (`localStorage`). It is **never** committed to the source code, sent to GitHub, or shared over an external network. It is entirely safe to use inside a public repository.
* **Free vs. Paid Tiers:** * **Free Tier:** High-volume public usage might occasionally trigger a `503 Service Unavailable` error during global peak times.
  * **Paid Tier (Recommended for speed):** Because this app requests tiny text fragments instead of heavy image payloads, switching to a billing-linked key provides maximum speed and zero throttling, while keeping your actual bill fractions of a cent per batch.

---

## 🖥️ Features

* **Real-time Status Monitor:** Instantly indicates whether your API key is active or needs reconnection.
* **On-Screen Error Log:** Catches network timeouts, 503 capacity drops, or key restrictions visually on the UI without requiring you to open developer tools.
* **Quick Reset Escape Hatch:** Swap keys instantly between your testing environments using the dedicated interface button.
