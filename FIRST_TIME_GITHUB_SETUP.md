# GitHub Pages setup

GitHub Pages serves the static student quiz and teacher dashboard from the repository's `docs/` folder. It does not run the live classroom backend.

## Enable Pages for `franku69/Final-Networking-Quiz`

1. Open **Final-Networking-Quiz → Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Select branch **main** and folder **/docs**, then click **Save**.
4. Wait for GitHub to publish the site.

Student site: `https://franku69.github.io/Final-Networking-Quiz/`

Teacher dashboard: `https://franku69.github.io/Final-Networking-Quiz/teacher/`

The Actions workflow validates files and source syntax. GitHub Pages publishes `/docs` using the repository Pages setting.
