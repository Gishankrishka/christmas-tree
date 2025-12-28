# 🎄 Grand Luxury Interactive 3D Christmas Tree

> A high-fidelity 3D Christmas tree web application based on **React**, **Three.js (R3F)**, and **AI gesture recognition**.

This project is more than just a tree; it's an interactive gallery that holds memories. Hundreds of particles, dazzling lights, and floating Polaroid photos combine to create a luxurious Christmas tree. Users can control the tree's shape (aggregate/spread) and viewpoint rotation with gestures, experiencing a cinematic visual feast.

![Project Preview](public/preview.png)

*(Note: It is recommended to upload a screenshot of your project running here)*

## ✨ Core Features

* **Ultimate Visual Experience**: A tree body composed of 45,000+ glowing particles, combined with dynamic bloom and glow effects, creates a dreamlike atmosphere.

* **Memory Gallery:** Photos float above the tree in a Polaroid style, each a self-contained luminous object, supporting dual-sided rendering.

* **AI Gesture Control:** No mouse required; control the tree's shape (aggregating/scattering) and view rotation via camera-captured gestures.

* **Rich Details:** Includes dynamically flashing colored lights, falling gold and silver snowflakes, and randomly distributed Christmas gifts and candy decorations.

* **Highly Customizable:** Users can easily replace photos with their own and freely adjust the number of photos. **

## 🛠️ Technology Stack

* **Framework**: React 18, Vite

* **3D Engine**: React Three Fiber (Three.js)

* **Library**: @react-three/drei, Maath

* **Post-processing**: @react-three/postprocessing

* **AI Vision**: MediaPipe Tasks Vision (Google)

## 🚀 Quick Start

### 1. Environment Preparation

Ensure your computer has Node.js installed (https://nodejs.org/) (v18 or higher recommended).

### 2. Install Dependencies

Open a terminal in the project root directory and run: ```bash npm install

### 3. Start the Project

npm run dev

### 🖼️ Custom Photos

### 1. Prepare Photos

Locate the public/photos/ folder in the project directory.

Top image/cover image: Name it top.jpg (it will appear on the 3D five-pointed star at the top of the tree).

Tree trunk photos: Name them 1.jpg, 2.jpg, 3.jpg... and so on.

Suggestion: Use square or 4:3 aspect ratio images, and keep file sizes small (ideally under 500kb per image for smooth performance).

### 2. Replace Photos Simply copy your own photos to the public/photos/ folder, overwriting the existing images. Please keep the filename format unchanged (1.jpg, 2.jpg, etc.).

### 3. Modify the Number of Photos (Increase or Decrease) If you add more photos (e.g., from the default 31 to 100), you need to modify the code to instruct the program to load them.

Open the file: src/App.tsx
Find the code around line 19: // --- Dynamically generate a list of photos (top.jpg + 1.jpg to 31.jpg) ---
const TOTAL_NUMBERED_PHOTOS = 31; // <--- Modify this number!

### 🖐️ Gesture Control Instructions

* **This project has a built-in AI gesture recognition system. Please stand in front of the camera to operate (there is a DEBUG button in the lower right corner of the screen to view the camera feed)**:

🖐 Open Palm: Disperse - The Christmas tree explodes into a shower of particles and photos.

✊ Closed Fist: Assemble - All elements instantly assemble into a perfect Christmas tree.

👋 Move Palm Left/Right: Rotate View - Move your hand left, the tree rotates left; move your hand right, the tree rotates right.

👋 Move Palm Up/Down: Pitch View - Move your hand up, the view tilts; move your hand down, the view tilts.

### ⚙️ Advanced Configuration

* **If you are familiar with code, you can adjust more visual parameters in the CONFIG object in src/App.tsx**:

const CONFIG = {
colors: { ... }, // Modify the colors of the tree, lights, and borders
counts: {

foliage: 15000, // Modify the number of leaf particles (may lag on low-end systems)

ornaments: 300, // Modify the number of hanging photos/Polaroids

lights: 400 // Modify the number of fairy lights

},

tree: { height: 22, radius: 9 }, // Modify the size of the tree

// ...

};

### 📄 License
MIT License. Feel free to use and modify for your own holiday celebrations!

### Merry Christmas! 🎄✨
