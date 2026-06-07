# 🐱 CEO Cat: Hammer of Productivity

> *"You aren't working hard enough. Let me introduce you to my Productivity Enhancer!"*

A hyper-realistic corporate action comedy game where you step into the polished paws of **Mr. Whiskers**, a serious orange cat CEO on a mission. Save your failing startup by bonking unmotivated employees, shattering corporate furniture, collecting profit coins, upgrading your tactical gear, and conquering epic executive boss battles!

---

## 🎮 Game Concept & Features

Welcome to the ultimate corporate simulator. As Mr. Whiskers, you navigate high-stakes boardroom environments using your trusty "Productivity Enhancer" (otherwise known as a giant golden hammer). 

*   **Hilarious Arcade Action**: Seek out lax employees slacking at their cubicles, smash water coolers for hidden revenue, and restore company synergy!
*   **Upgrades & Customisation**: Visit the dynamic shop to trade hard-earned cash for stronger hammers, speed-boosting business boots, and legendary golden collars.
*   **Destructible Office Environments**: Interactive Physics-inspired office layouts complete with computers, desks, and potted plants to smash for extra budget.
*   **Epic Boss Battles**: Face off against rival directors and demanding board members to secure your company's series-funding!
*   **Polished Styling**: Built with modern typography, satisfying micro-interactions, smooth CSS frame updates, and high-fidelity layouts styled in Tailwind CSS.

---

## 🛠️ Local Development Setup

To run CEO Cat: Hammer of Productivity locally, follow these simple steps:

### Prerequisites
Make sure you have [Node.js](https://nodejs.org/) installed (v18 or newer recommended).

### Steps
1. **Clone the repository**:
   ```bash
   git clone https://github.com/YOUR_USERNAME/ceo-cat-hammer-of-productivity.git
   cd ceo-cat-hammer-of-productivity
   ```

2. **Install all dependencies**:
   ```bash
   npm install
   ```

3. **Start the developer live server**:
   ```bash
   npm run dev
   ```
   *The application will boot at `http://localhost:3000` (or `http://localhost:5173` depending on port availability).*

4. **Compile a production-ready build**:
   ```bash
   npm run build
   ```
   *This outputs optimized, static production bundles inside the `dist/` directory.*

---

## 🚀 Hosting on GitHub Pages (How to Deploy)

Hosting this game on GitHub Pages is incredibly simple. The project's configuration file (`vite.config.ts`) is pre-configured with `base: './'`. This translates built asset links into relative paths, which allows your game to run perfectly under subfolders like `https://username.github.io/repo-name/` without additional customization.

Here are the two ways to host it:

### Option A: Fully Automated Deployment (Highly Recommended)
You can set up a automated GitHub Actions workflow to build and deploy your game code every time you push to your `main` or `master` branch.

1. Create a directory named `.github/workflows` in the root of your project.
2. In that folder, save a file named `deploy.yml` with the following contents:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main, master ]  # Adjust to match your default branch

permissions:
  contents: write

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: 'npm'

      - name: Install Dependencies
        run: npm ci

      - name: Build Application
        run: npm run build

      - name: Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: dist # The folder the build script generates
          branch: gh-pages # Host branch for GitHub Pages
```

3. Commit and push this file to GitHub.
4. On your GitHub Repository webpage, navigate to **Settings** > **Pages**.
5. Under **Build and deployment**, ensure your **Source** is set to **Deploy from a branch**, and select **`gh-pages`** as your publication branch (the folder should be root `/`).
6. Within a minute, your workflow will build and launch your game!

---

### Option B: Manual Command-Line Deployment
If you prefer not to use workflows, you can build and publish the files manually using the `gh-pages` helper package:

1. Install the deployment utility:
   ```bash
   npm install --save-dev gh-pages
   ```

2. Open your `package.json` and add these scripts:
   ```json
   "predeploy": "npm run build",
   "deploy": "gh-pages -d dist"
   ```

3. Deploy with one command:
   ```bash
   npm run deploy
   ```
   *This commands automatically builds your app, creates a local `gh-pages` branch, and pushes your `dist/` files to your GitHub repository.*

---

## 📂 Project Structure

```text
├── index.html          # HTML Shell Container
├── vite.config.ts      # Vite Setup with relative base config
├── package.json        # Dependencies & Game Scripts
├── src/
│   ├── main.tsx        # Render Entrypoint
│   ├── App.tsx         # Primary Routing State Hub
│   ├── types.ts        # Typed Interfaces for inventory & upgrades
│   ├── index.css       # Tailwind Framework and custom marquee keyframes
│   └── components/     # Modulized Interactive Interfaces:
│       ├── IntroScreen.tsx  # Game Pitch and instructions
│       ├── GameCanvas.tsx   # Canvas-based Physics office-smashing simulator
│       ├── UIPanel.tsx      # Persistent upgrade shops & inventory HUD
│       ├── BossBattle.tsx   # Strategic Boardroom Confrontations
│       └── FinalScreen.tsx  # Interactive Victory reports & retry forms
```

---

## 🐈 Core Tech & Credits

*   **React 19 & TypeScript**: High-performance UI rendering and strict, error-free typing.
*   **Vite**: Superb dev tooling and ultra-miniaturized static output bundling.
*   **Tailwind CSS**: Modern utility styles and responsive layout templates.
*   **Lucide React**: Clean vector-graphics for shop icons, hammers, and corporate labels.
*   **Motion**: Graceful screen shifts, fade-ins, and boardroom victory animations.

Made with 🧡 by Mr. Whiskers. Now go and increase that corporate performance!
