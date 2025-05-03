# Text to 3D Model Generator using Gemini API & TripoSR

This project allows users to generate 3D `.obj` models from **text prompts** using an efficient pipeline that combines **text-to-image** generation via the **Gemini API** and **2D-to-3D** model conversion using **TripoSR**.

---

##  Steps to Run


###  If Running Locally

1. **Create a Virtual Environment**
   ```bash
   python -m venv venv
   ```

2. **Activate the Environment**
   - On **Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - On **Linux/macOS**:
     ```bash
     source venv/bin/activate
     ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set Up Gemini API Key**
   - Go to [Google AI Studio](https://makersuite.google.com/app) and generate a free API key.
   - Replace the placeholder key in the notebook with your key.

5. **Edit Paths & Prompt**
   - Open the `.ipynb` notebook.
   - Update file paths and enter your text prompt.
   - Run all cells.

---

###  If Running on Kaggle (Recommended)

1. Upload the notebook to a Kaggle notebook.
2. Enable GPU from the notebook settings.
3. Edit the prompt in the notebook.
4. Run all cells — dependencies are auto-handled on Kaggle.

---

##  Libraries Used

- [TripoSR](https://github.com/VAST-AI/TripoSR) – 2D image to 3D model
- `PIL` – Image handling
- `base64` – Encoding images for API
- `os`, `mimetypes` – File and type handling
- `google.generativeai` – Gemini API for text-to-image generation
- `matplotlib` – Displaying images
- `trimesh` – Rendering `.obj` files in Python

---

##  My Thought Process

Initially, I aimed to build an **image-to-3D modeler**, but challenges arose due to:
- Inconsistent image quality
- Difficulty in object detection from varied images

So I pivoted to a **text-to-3D modeler** approach. However, no robust open-source text-to-3D solution was found.

###  My Hybrid Solution:
1. **Text ➜ Image** using Gemini API (free, stable, and API-based)
2. **Image ➜ 3D model** using TripoSR (open-source & handles preprocessing)

I chose **Gemini** for its ability to generate clean and descriptive images directly from text prompts — eliminating the need for manual preprocessing.

For **3D modeling**, TripoSR proved fast and efficient, automatically removing backgrounds and simplifying the pipeline.

###  Challenges Solved:
- Replaced GPU-intensive local models (like Stable Diffusion + Flux) with API calls
- Handled `.obj` rendering using `trimesh`, which gave the best visual results after trying multiple libraries

---

##  Notes

- Quality of the final `.obj` file depends on the quality of the generated image.
- Both the image generator and 3D converter can be upgraded for better results, but are limited by compute or open-source availability.

---

