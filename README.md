### Hey, o que há de novo? 👋

Estudante de Sistemas de Informação (UFRPE) focado em back-end. 
Construindo APIs, bancos de dados e sistemas em Node.js, PostgreSQL e C. 
Aprendendo na prática, um projeto de cada vez 🚀

<div style="display: inline_block"><br>
  <img align="center" alt="Diogo-Node" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original.svg">
  <img align="center" alt="Diogo-JS" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
  <img align="center" alt="Diogo-PostgreSQL" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original.svg">
  <img align="center" alt="Diogo-C" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg">
  <img align="center" alt="Diogo-Express" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original.svg">
</div>

<div> 
  <a href="https://www.instagram.com/dioguinho_lopess/" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
  <a href="https://discord.gg/4WgYvU8m" target="_blank"><img src="https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white" target="_blank"></a> 
  <a href="https://linkedin.com/in/diogolopesdev" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
  
</div>

name: Generate Snake

on:
  schedule:
    - cron: "0 */6 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        with:
          github_user_name: dioguinholf
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark

      - uses: actions/upload-artifact@v4
        with:
          name: github-snake
          path: dist/

      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: output
          publish_dir: dist
