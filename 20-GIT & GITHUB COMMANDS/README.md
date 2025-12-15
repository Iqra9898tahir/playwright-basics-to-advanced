git status
👉 Check which files changed

bash
Copy code
git add .
👉 Stage all changes

bash
Copy code
git commit -m "Add Playwright tests"
👉 Save changes locally

bash
Copy code
git push origin main
👉 Push code to GitHub
⚠️ This push is what triggers CI/CD

🔹 Other Important Commands (Interview-safe)
bash
Copy code
git clone <repo-url>
👉 Download project from GitHub

bash
Copy code
git pull
👉 Get latest changes

bash
Copy code
git checkout -b new-branch

📁 Where CI/CD Code Lives (VERY IMPORTANT)
.github/
 └── workflows/
      └── playwright.yml


📌 Interview line:

“Playwright CI configuration is written in GitHub Actions YAML files inside .github/workflows.”
