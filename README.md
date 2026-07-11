# CI and CD with Render

This repository contains a simple Node.js backend using Express. It is designed as a minimal example for learning and building a basic continuous integration / continuous deployment workflow.

## Project Structure

- `.github/workflows/ci.yml` - GitHub Actions workflow for CI checks
- `Backend/index.js` - Express server entrypoint
- `Backend/package.json` - backend package metadata and scripts

## Setup

1. Open a terminal in `Backend`
2. Install dependencies:
   ```bash
   npm install
   ```

## Run

Start the server with:

```bash
npm start
```

Then open `http://localhost:3000` in your browser. The app responds with `hello world`.

## Learning

- Learned how to set up a minimal Express server with a single route.
- Learned how to configure `package.json` for running the app with `npm start`.
- Learned that Express 5 can be used with modern ES module syntax by setting `type": "module"`.
- learned the basics rule about the CI and CD.
- learned about the importance of path and working directory.
- learned the importance of webhook URL stored in the repository secrets.

## Notes

- The server listens on port `3000`.
- The current project is a starting point and can be extended with routes, middleware, and API behavior.
- Always take care of indentation and singular plural for writing the workflow file.
