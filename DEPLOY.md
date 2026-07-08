# Deploy notes for Render

If you want Render to build using your `Dockerfile`, add `render.yaml` to the repo (already added) and push to `main`. Render will detect the `env: docker` service and use the `Dockerfile` for build and deploy.

To deploy locally to the repository (trigger Render):

```bash
git add render.yaml DEPLOY.md
git commit -m "Add Render Docker service config and deploy notes"
git push origin main
```

If you prefer not to use Docker, configure the build environment to include Java (set `JAVA_HOME` and add Java to `PATH`), or make the build command install Java before running `./gradlew`.
