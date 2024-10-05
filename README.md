# Learning Three.js with React and Vite - Day 3

On Day 3, I learned how to integrate **Three.js** into a React application using **Vite** as a build tool. 

Below is a summary of the concepts and steps I covered, along with a brief introduction to Three.js and how to set up a basic spinning cube animation.

## Topics Covered
1. **Setting Up the Environment:**
   - Installed `vite`, `react`, and `three` to kickstart a project.
   - Created a basic React component to render a Three.js scene.

2. **Three.js Basics:**
   - Understanding the essentials of Three.js, which includes:
     - **Scene**: Where all objects (cubes, spheres, etc.) are added and manipulated.
     - **Camera**: Helps view the scene (PerspectiveCamera was used).
     - **Renderer**: Renders the scene from the camera's perspective onto the DOM.

3. **Rendering a Spinning Cube:**
   - Created a simple 3D cube using `BoxGeometry` and added basic rotation in the animation loop.
   - Set up event listeners to handle window resizing to keep the Three.js canvas responsive.

## Project Setup

### Prerequisites
- **Node.js** and **npm** installed.
- Basic understanding of **React** and **JavaScript**.

### Installation

1. Clone the repository:

   
   git clone https://github.com/your-username/my-threejs-app.git
   cd my-threejs-app
Install the necessary dependencies:



npm install
Start the Vite development server:



npm run dev
Open the project in your browser at http://localhost:3000.

Structure
index.html: The HTML file where the Three.js canvas is rendered.
src/main.jsx: The main entry point of the React app where the Three.js scene and animation loop are set up.
src/App.jsx: Main React component handling the Three.js logic.
Code Breakdown
Setting Up the Scene
In the main App.jsx component, we set up the Three.js scene, camera, and renderer:

## jsx

import * as THREE from 'three';
import { useEffect } from 'react';

const App = () => {
  useEffect(() => {
    // Scene, Camera, Renderer Setup
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement);

    // Creating a Cube
    const geometry = new THREE.BoxGeometry(1, 1, 1);
    const material = new THREE.MeshBasicMaterial({ color: 0x800080 }); // Purple cube
    const cube = new THREE.Mesh(geometry, material);
    scene.add(cube);

    // Camera Position
    camera.position.z = 5;

    // Animation Loop
    const animate = () => {
      requestAnimationFrame(animate);

      // Rotating the Cube
      cube.rotation.x += 0.01;
      cube.rotation.y += 0.01;

      // Rendering the Scene
      renderer.render(scene, camera);
    };
    animate();

    // Handle window resizing
    window.addEventListener('resize', () => {
      const width = window.innerWidth;
      const height = window.innerHeight;
      camera.aspect = width / height;
      camera.updateProjectionMatrix();
      renderer.setSize(width, height);
    });
  }, []);

  return null;
};

export default App;
Animation
The cube is rotated by updating its rotation.x and rotation.y properties inside the animate function:

js

cube.rotation.x += 0.01;
cube.rotation.y += 0.01;
Handling Window Resize
To make the canvas responsive, I added an event listener for window resizing:

js

window.addEventListener('resize', () => {
  const width = window.innerWidth;
  const height = window.innerHeight;
  camera.aspect = width / height;
  camera.updateProjectionMatrix();
  renderer.setSize(width, height);
});
### Key Learnings
Three.js Integration in React: I learned how to use Three.js inside a React component and animate 3D objects.
Animation Loops: Used requestAnimationFrame to create a smooth animation loop.
Responsive 3D Rendering: Adjusted the canvas size and aspect ratio to keep the scene responsive when resizing the browser window.
Conclusion
This was a fun introduction to Three.js and 3D rendering within React using Vite. Moving forward, I plan to explore more complex shapes, lighting, materials, and interactions to build more immersive 3D experiences!

### Future Goals
Experiment with different geometries and materials.
Add lighting to the scene for more realistic rendering.
Explore user interaction, such as rotating the cube with mouse input.
Feel free to clone this project and play around with it!

### Resources
Three.js Documentation
Vite Documentation
React Documentation
vbnet


### Key Points:
- This README includes a project description, setup instructions, code snippets, and explanations of key concepts.
- It's structured to make it easy for others to understand what you've learned and replicate your project.





