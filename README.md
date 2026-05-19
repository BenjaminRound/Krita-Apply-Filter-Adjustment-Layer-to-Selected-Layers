# Apply Filter to Selected Layers

<span style="font-size: 18px;">**This Krita script applies a single filter layer to multiple paint layers individually while preserving their unique properties like blend mode, opacity, and Inherit Alpha.**</span>

---

### 🚀 How to Use

*   **Step 1:** Create or select **ONE** filter layer (e.g., HSV Adjustment, Blur, Color Adjustment, etc.).
*   **Step 2:** Hold `Ctrl` (or `Cmd` on Mac) and select all the paint layers you want to apply the filter to.
*   **Step 3:** Go to `Tools` → `Scripts` → `Apply Filter to Selected Layers`.
*   **Step 4:** Wait for the script to process. Check the **Scripter** output for real-time progress.

---

### 🛠️ Requirements

*   Select **exactly ONE** filter layer.
*   Select **one or more** paint layers.

> ⚠️ **Warning:** This operation handles destructive flattening and cannot be undone easily with a single `Ctrl+Z`. Consider duplicating your layers or saving your document before running the script.

---

### 🧠 How It Works

For each selected paint layer, the script automatically performs the following loop:
1. Temporarily disables **Inherit Alpha** (if enabled) to preserve the image data cache.
2. Creates an isolated, temporary group containing the target layer and a duplicate of the filter.
3. Flattens the group to cleanly bake the filter effect into those pixels alone.
4. Restores all original properties, including snapping **Inherit Alpha** back on.

> ℹ️ **Note:** The original filter layer itself is **NOT** modified or deleted. It is only used as a master template to duplicate from.

---

### ✨ What Gets Preserved

*   **Blend Mode:** The layer's original blending mode stays the same.
*   **Opacity:** The layer's exact opacity percentage is preserved.
*   **Inherit Alpha:** Alpha inheritance/clipping mask settings are completely maintained.
*   **Lock State:** Locked layers will be safely re-locked after processing.
*   **Layer Names:** Your original layer names are kept perfectly intact.

---

### 📖 Example Workflow

**Scenario:** You have 10 character/shading layers and want to apply the exact same color adjustment filter to all of them while keeping their current clipping setup and Inherit Alpha settings.

1. Create a native Krita Adjustment filter layer.
2. Tweak the filter settings until your art looks exactly how you want it.
3. Select that filter layer in the docker.
4. Hold `Ctrl` and click each of your 10 artwork layers.
5. Run the script: `Tools` → `Scripts` → `Apply Filter to Selected Layers`.
6. **Result:** All 10 layers will have the filter baked directly into them with their properties completely preserved!

---

### 💡 Tips

*   The script processes layers in reverse order (bottom to top) to maintain stack and layer hierarchy integrity.
*   Check Krita's script logs for detailed step-by-step progress information.
