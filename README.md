# 💫 About Me:
I'm currently learning Cybersecurity👨‍💻<br>I'm student 👨‍💻


## 🌐 Socials:
[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/mahmoud-mahmed-4b4884331?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app) 

# 💻 Tech Stack:
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![MicrosoftSQLServer](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft%20sql%20server&logoColor=white)
# 📊 GitHub Stats:
![](https://github-readme-stats.vercel.app/api?username=M-M-AboArab&theme=dark&hide_border=false&include_all_commits=false&count_private=false)<br/>
![](https://nirzak-streak-stats.vercel.app/?user=M-M-AboArab&theme=dark&hide_border=false)<br/>
![](https://github-readme-stats.vercel.app/api/top-langs/?username=M-M-AboArab&theme=dark&hide_border=false&include_all_commits=false&count_private=false&layout=compact)

## 🏆 GitHub Trophies
![](https://github-profile-trophy.vercel.app/?username=M-M-AboArab&theme=radical&no-frame=false&no-bg=true&margin-w=4)

### ✍️ Random Dev Quote
![](https://quotes-github-readme.vercel.app/api?type=horizontal&theme=radical)

### 🔝 Top Contributed Repo
![](https://github-contributor-stats.vercel.app/api?username=M-M-AboArab&limit=5&theme=dark&combine_all_yearly_contributions=true)

---
[![](https://visitcount.itsvg.in/api?id=M-M-AboArab&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->

name: GitHub Snake Game

on:
  # Schedule the workflow to run daily at midnight UTC
  schedule:
    - cron: "0 0 * * *"
  # Allow manual triggering of the workflow
  workflow_dispatch:
  # Trigger the workflow on pushes to the main branch
  push:
    branches:
      - main
jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      # Step 1: Checkout the repository
      - name: Checkout Repository
        uses: actions/checkout@v3
      # Step 2: Generate the snake animations
      - name: Generate GitHub Contributions Snake Animations
        uses: Platane/snk@v3
        with:
          # GitHub username to generate the animation for
          github_user_name: ${{ github.repository_owner }}
          # Define the output files and their configurations
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
            dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      # Step 3: Deploy the generated files to the 'output' branch
      - name: Deploy to Output Branch
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
          publish_branch: output
          # Optionally, you can set a custom commit message
          commit_message: "Update snake animation [skip ci]"
