## <a name="tech-stack">⚙️ Tech Stack</a>

- React.js
- Three.js
- React Three Fiber
- React Three Drei
- GSAP (Greensock)
- Vite
- Tailwind CSS

## <a name="features">🔋 Features</a>

👉 **Beautiful Subtle Smooth Animations using GSAP**: Enhanced user experience with seamless and captivating animations powered by GSAP.

👉 **3D Model Rendering with Different Colors and Sizes**: Explore the iPhone 15 Pro from every angle with dynamic 3D rendering, offering various color and size options.

👉 **Custom Video Carousel (made with GSAP)**: Engage users with a unique and interactive video carousel developed using GSAP for a personalized browsing experience.

👉 **Completely Responsive**: Consistent access and optimal viewing on any device with a fully responsive design that adapts to different screen sizes.

and many more, including code architecture and reusability

## <a name="snippets">🕸️ Snippets</a>

<details>
<summary><code>tailwind.config.js</code></summary>

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors: {
        blue: "#2997FF",
        gray: {
          DEFAULT: "#86868b",
          100: "#94928d",
          200: "#afafaf",
          300: "#42424570",
        },
        zinc: "#101010",
      },
    },
  },
  plugins: [],
};
```

</details>

<details>
<summary><code>constants/index.js</code></summary>

```javascript
import {
  blackImg,
  blueImg,
  highlightFirstVideo,
  highlightFourthVideo,
  highlightSecondVideo,
  highlightThirdVideo,
  whiteImg,
  yellowImg,
} from "../utils";

export const navLists = ["Store", "Mac", "iPhone", "Support"];

export const hightlightsSlides = [
  {
    id: 1,
    textLists: [
      "Enter A17 Pro.",
      "Game‑changing chip.",
      "Groundbreaking performance.",
    ],
    video: highlightFirstVideo,
    videoDuration: 4,
  },
  {
    id: 2,
    textLists: ["Titanium.", "So strong. So light. So Pro."],
    video: highlightSecondVideo,
    videoDuration: 5,
  },
  {
    id: 3,
    textLists: [
      "iPhone 15 Pro Max has the",
      "longest optical zoom in",
      "iPhone ever. Far out.",
    ],
    video: highlightThirdVideo,
    videoDuration: 2,
  },
  {
    id: 4,
    textLists: ["All-new Action button.", "What will yours do?."],
    video: highlightFourthVideo,
    videoDuration: 3.63,
  },
];

export const models = [
  {
    id: 1,
    title: "iPhone 15 Pro in Natural Titanium",
    color: ["#8F8A81", "#ffe7b9", "#6f6c64"],
    img: yellowImg,
  },
  {
    id: 2,
    title: "iPhone 15 Pro in Blue Titanium",
    color: ["#53596E", "#6395ff", "#21242e"],
    img: blueImg,
  },
  {
    id: 3,
    title: "iPhone 15 Pro in White Titanium",
    color: ["#C9C8C2", "#ffffff", "#C9C8C2"],
    img: whiteImg,
  },
  {
    id: 4,
    title: "iPhone 15 Pro in Black Titanium",
    color: ["#454749", "#3b3b3b", "#181819"],
    img: blackImg,
  },
];

export const sizes = [
  { label: '6.1"', value: "small" },
  { label: '6.7"', value: "large" },
];

export const footerLinks = [
  "Privacy Policy",
  "Terms of Use",
  "Sales Policy",
  "Legal",
  "Site Map",
];
```

</details>

<details>
<summary><code>index.css</code></summary>

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  color: white;
  width: 100dvw;
  overflow-x: hidden;
  height: 100%;
  background: #000;
  border-color: #3b3b3b;
  user-select: none;
}

canvas {
  touch-action: none;
}

.scrim-max-width {
  margin-inline-start: auto;
  margin-inline-end: auto;
  position: relative;
  max-width: 1120px;
}

@layer utilities {
  .flex-center {
    @apply flex items-center justify-center
  }

  .nav-height {
    @apply h-[calc(100vh-60px)]
  }

  .btn {
    @apply px-5 py-2 rounded-3xl bg-blue my-5 hover:bg-transparent border border-transparent hover:border hover:text-blue hover:border-blue
  }

  .color-container {
    @apply flex items-center justify-center px-4 py-4 rounded-full bg-gray-300 backdrop-blur
  }

  .size-btn-container {
    @apply flex items-center justify-center p-1 rounded-full bg-gray-300 backdrop-blur ml-3 gap-1
  }

  .size-btn {
    @apply w-10 h-10 text-sm flex justify-center items-center bg-white text-black rounded-full transition-all
  }

  .common-padding {
    @apply sm:py-32 py-20 sm:px-10 px-5
  }

  .section-heading {
    @apply text-gray lg:text-6xl md:text-5xl text-3xl lg:mb-0 mb-5 font-medium opacity-0 translate-y-20
  }

  .feature-text {
    @apply text-gray max-w-md text-lg md:text-xl font-semibold opacity-0 translate-y-[100px]
  }

  .feature-text-container {
    @apply w-full flex-center flex-col md:flex-row mt-10 md:mt-16 gap-5
  }

  .feature-video {
    @apply w-full h-full object-cover object-center scale-150 opacity-0
  }

  .feature-video-container {
    @apply w-full flex flex-col md:flex-row gap-5 items-center
  }

  .link {
    @apply text-blue hover:underline cursor-pointer flex items-center text-xl opacity-0 translate-y-20
  }

  .control-btn {
    @apply ml-4 p-4 rounded-full bg-gray-300 backdrop-blur flex-center
  }

  .hero-title {
    @apply text-center font-semibold text-3xl text-gray-100 opacity-0 max-md:mb-10
  }

  .hiw-title {
    @apply text-4xl md:text-7xl font-semibold text-center
  }

  .hiw-subtitle {
    @apply text-gray font-semibold text-xl md:text-2xl py-10 text-center
  }

  .hiw-video {
    @apply absolute w-[95%] h-[90%] rounded-[56px] overflow-hidden
  }

  .hiw-text-container {
    @apply flex md:flex-row flex-col justify-between items-start gap-24
  }

  .hiw-text {
    @apply text-gray text-xl font-normal md:font-semibold
  }

  .hiw-bigtext {
    @apply text-white text-3xl md:text-5xl font-normal md:font-semibold my-2
  }

  .video-carousel_container {
    @apply relative sm:w-[70vw] w-[88vw] md:h-[70vh] sm:h-[50vh] h-[35vh]
  }

  .g_fadeIn {
    @apply opacity-0 translate-y-[100px]
  }
}
```

</details>
