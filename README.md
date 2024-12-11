To deploy a Vite React project on GitHub Pages, follow these steps:

---

### **1. Prepare Your Project**
1. Ensure you have a Vite React project ready.
2. Add a `homepage` field in your `package.json` file with the URL of your GitHub Pages. For example:
   ```json
   {
     "homepage": "https://<your-username>.github.io/<repository-name>"
   }
   ```

---

### **2. Install `gh-pages`**
1. Install the `gh-pages` package:
   ```bash
   npm install gh-pages --save-dev
   ```

---

### **3. Update `vite.config.js`**
Modify your `vite.config.js` file to include the base path of your repository:
```javascript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

// Replace <repository-name> with the name of your GitHub repository
export default defineConfig({
  plugins: [react()],
  base: '/<repository-name>/', 
});
```

---

### **4. Add Deployment Scripts**
Add the following scripts to your `package.json`:
```json
"scripts": {
  "build": "vite build",
  "predeploy": "npm run build",
  "deploy": "gh-pages -d dist"
}
```

- **`predeploy`**: Builds your app before deployment.
- **`deploy`**: Pushes the `dist` folder (the build output) to the `gh-pages` branch.

---

### **5. Build and Deploy**
1. Run the deployment command:
   ```bash
   npm run deploy
   ```
2. This will:
   - Build your project.
   - Deploy the contents of the `dist` folder to the `gh-pages` branch.

---

### **6. Enable GitHub Pages**
1. Go to your repository on GitHub.
2. Navigate to **Settings > Pages**.
3. Under **Source**, select `gh-pages` as the branch.
4. Click **Save**.

---

### **7. Access Your Deployed Site**
Once GitHub processes your deployment, your site will be available at:
```
https://<your-username>.github.io/<repository-name>
```

---

### **Notes**
- If your app doesn’t load properly, double-check the `base` setting in `vite.config.js` and ensure it matches your repository name.
- For a root-level deployment (without a repository name in the URL), set the `base` to `'/'`.