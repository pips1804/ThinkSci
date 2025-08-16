# ThinkSci Website

A modern, responsive website for ThinkSci - an interactive science e-learning Android application designed for Grade 7 students.

## Features

- 🎨 **Custom Color Palette**: E8E8CC (cream), FFCC1D (yellow), 116530 (dark green)
- 📱 **Mobile Responsive**: Optimized for all device sizes
- 🌙 **Dark/Light Mode**: Toggle between themes with smooth transitions
- ⚡ **Vue.js 3**: Built with the latest Vue.js and Composition API
- 🎯 **Tailwind CSS**: Utility-first CSS framework for rapid styling
- 🔧 **Lucide Icons**: Beautiful, consistent iconography
- 🎮 **Child-Friendly Design**: Engaging interface for 10-13 year olds

## Sections

- **Hero**: Eye-catching introduction with download buttons
- **About**: Six feature cards highlighting app benefits
- **Developers**: Team profiles and contact information

## Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn

### Installation

1. Clone or download the project
2. Install dependencies:
   \`\`\`bash
   npm install
   \`\`\`

3. Start the development server:
   \`\`\`bash
   npm run dev
   \`\`\`

4. Open your browser and visit `http://localhost:3000`

### Build for Production

\`\`\`bash
npm run build
\`\`\`

## Project Structure

\`\`\`
thinksci-website/
├── src/
│   ├── App.vue          # Main application component
│   ├── main.js          # Application entry point
│   └── style.css        # Global styles and Tailwind imports
├── public/
│   └── atom-icon.svg    # Favicon
├── index.html           # HTML template
├── package.json         # Dependencies and scripts
├── tailwind.config.js   # Tailwind configuration
├── vite.config.js       # Vite configuration
└── postcss.config.js    # PostCSS configuration
\`\`\`

## Customization

### Colors
The custom color palette is defined in `tailwind.config.js`:
- `cream`: #E8E8CC
- `yellow`: #FFCC1D  
- `green-dark`: #116530

### Content
All content can be easily modified in the `App.vue` file. The component is well-structured with clear sections for easy editing.

## Technologies Used

- **Vue.js 3** - Progressive JavaScript framework
- **Vite** - Fast build tool and development server
- **Tailwind CSS** - Utility-first CSS framework
- **Lucide Vue** - Beautiful icon library
- **PostCSS** - CSS processing tool

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## License

This project is created for ThinkSci educational application.
