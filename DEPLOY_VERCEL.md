# Deploy to Vercel

## Quick Start

1. **Install Vercel CLI** (if not already installed):
   ```bash
   npm i -g vercel
   ```

2. **Login to Vercel**:
   ```bash
   vercel login
   ```

3. **Deploy** (from the navigation_page directory):
   ```bash
   vercel
   ```

4. **Production Deployment**:
   ```bash
   vercel --prod
   ```

## Deploy via GitHub

### Option 1: Vercel Dashboard (Easiest)
1. Go to [vercel.com](https://vercel.com)
2. Click "Add New Project"
3. Import your GitHub repository
4. Vercel will automatically detect the static site
5. Click "Deploy"

### Option 2: Push to GitHub then Deploy
1. **Add and commit all files**:
   ```bash
   git add .
   git commit -m "Deploy to Vercel"
   git push origin main
   ```

2. **Go to Vercel Dashboard**:
   - Sign up at [vercel.com](https://vercel.com)
   - Click "Import Project"
   - Select your GitHub repository
   - Click "Deploy"

## Project Structure
```
navigation_page/
├── index.html          # Main app
├── path-editor.html    # Path editor
├── location-editor.html
├── camera-editor.html
├── floor-editor.html
├── path.json          # Data file
├── styles.css
├── logo.jpeg
├── person.glb         # 3D model
├── nwssu.glb          # Campus model
├── threejs/           # Three.js libraries
│   ├── three.min.js
│   ├── GLTFLoader.min.js
│   └── OrbitControls.js
└── vercel.json        # Vercel config
```

## Important Notes

### File Size Limits
- **Vercel free tier**: 100 MB per file
- Your `path.json` (16582 lines) and model files should be fine

### CORS Headers
Your code already uses a proxy for loading the GitHub model:
```javascript
const modelUrls = [
  "https://corsproxy.io/?" + encodeURIComponent(
    "https://github.com/SidLD/SidLD.github.io/releases/download/nwssu/nwssu.glb"
  )
];
```

### Static File Serving
All files in the root directory are served as static files, which is what you need for:
- HTML files
- CSS files
- JSON data
- GLB models
- Images

## Environment Variables
No environment variables needed for this static site.

## Build Command
No build step needed - this is a static site.

## Output Directory
Root directory (current setup)

## Custom Domain
After deployment, you can add a custom domain in Vercel settings.

