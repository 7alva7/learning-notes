# Notes

## Run a test file
```bash
npm test -- --findRelatedTests src/components/Note.test.js
```

## Config tsconfig.json
```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "jsx": "react",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "baseUrl": "./src",
    "paths": {
      "@/*": ["./*"] // This allows you to use absolute imports in your project
    }
  },
  "include": ["src/**/*"], // This includes all files in the src directory
  "exclude": ["node_modules", "**/*.spec.ts"] // This excludes test files from being compiled
}
```

## where is create-react-app webpack config and files?

The webpack config files are located in the `node_modules/react-scripts/config` directory. 

### How to config webpack

#### 1. Eject the configuration files from `react-scripts` to your project. This will create a `config` directory in your project root with all the necessary configuration files.

```bash
npm run eject
```

> **Note:** Ejecting is a one-way operation. Once you eject, you can't go back to using `react-scripts` without starting a new project.

#### 2. Using `react-app-rewired`. If you want to avoid ejecting, you can use `react-app-rewired` to override the default configuration without ejecting. This allows you to customize the webpack configuration while still using `react-scripts`.

1. Install `react-app-rewired` as a dev dependency:

```bash
npm install react-app-rewired -D
```

2. create a `config-overrides.js` file in the root of your project and add your custom webpack configuration there.

```javascript
module.exports = function override(config, env) {
  // Modify the Webpack config here
  return config;
};
```
3. Update your `package.json` scripts to use `react-app-rewired` instead of `react-scripts`. For example, change the start script from:

```json
"start": "react-scripts start"
```
to:

```json
"start": "react-app-rewired start"
```

