# Simply Dice: Roll Anywhere

[Download on the App Store](https://apps.apple.com/us/app/simply-dice-roll-anywhere/id6759136034)

A minimalist, high-performance 3D dice rolling application built with Ionic 8, Vue 3, and Three.js. Experience realistic physics-based dice rolling directly on your mobile device.

## Features

-   **Realistic 3D Physics**: Powered by Three.js for true-to-life dice mechanics and visuals.
-   **Shake to Roll**: utilizes device motion sensors (accelerometer) via Capacitor for a natural rolling experience.
-   **Haptic Feedback**: Subtle vibration feedback on every roll using Capacitor Haptics.
-   **Customizable Settings**: Adjust dice count (1 or 2 dice) and toggle shake-to-roll.
-   **Dark Mode**: Sleek, battery-friendly dark interface.
-   **Cross-Platform**: Built for iOS (and Android ready) using Capacitor.

## Tech Stack

-   **Framework**: [Ionic 8](https://ionicframework.com/) + [Vue 3](https://vuejs.org/) (Composition API)
-   **Build Tool**: [Vite](https://vitejs.dev/)
-   **3D Engine**: [Three.js](https://threejs.org/)
-   **Animations**: [GSAP](https://greensock.com/gsap/)
-   **Native Runtime**: [Capacitor 8](https://capacitorjs.com/)
-   **State/Storage**: [Capacitor Preferences](https://capacitorjs.com/docs/apis/preferences)

## Getting Started

### Prerequisites

-   Node.js (LTS recommended)
-   npm or pnpm
-   Ionic CLI: `npm install -g @ionic/cli`

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/simply-dice.git
    cd simply-dice
    ```
2.  **Install dependencies:**
    ```bash
    npm install
    ```

### Development

Run the development server with hot reload:

```bash
npm run dev
```

The app will be available at `http://localhost:5173`.

### Building for Production

1.  **Build the web assets:**
    ```bash
    npm run build
    ```
2.  **Sync with Native Projects:**
    ```bash
    npx cap sync
    ```

### Running on Device (iOS)

Ensure you have Xcode installed.

1.  **Open the iOS project:**
    ```bash
    npx cap open ios
    ```
2.  **Run directly from CLI:**
    ```bash
    npx cap run ios
    ```

## Project Structure

-   `src/components/ThreeDice.vue`: The core 3D scene handling dice rendering and physics.
-   `src/components/SettingsModal.vue`: The settings interface for configuring app preferences.
-   `src/views/Home.vue`: The main application view.
-   `src/services/`: Services for handling device interactions (Haptics, Shake).
-   `capacitor.config.ts`: Capacitor configuration for native app settings.

## License

All rights reserved.
