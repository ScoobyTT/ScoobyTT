# Christian Amós

**`Desenvolvedor FullStack`**

Me chamo Christian Amós, tenho 25 anos e sou natural de Salvador-Bahia-Brasil. Atualmente, estou cursando Sistemas de informação.
<p align="left">
  <a href="https://github.com/ScoobyTT" target="_blank">
    
  </a>
</p>

<p align="left">
  <a href="mailto:christianamosa@gmail.com" target="_blank">
    <img 
      alt="Email" 
      title="Me envie um email" 
      src="https://custom-icon-badges.demolab.com/badge/Email-christianamosa%40gmail.com-236ad3?style=for-the-badge&logo=gmail&logoColor=white"
    />
  </a>
</p>


---

### 🤖 Linguagens e Tecnologias

<img 
  align="left" 
  alt="C++" 
  title="C++"
  width="30px" 
  style="padding-right: 10px;"
  src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/cplusplus/cplusplus-original.svg"
/>
<img
  align="left" 
  alt="C" 
  title="C"
  width="30px" 
  style="padding-right: 10px;"
  src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/c/c-original.svg"
/>
<img
  align="left" 
  alt="R" 
  title="R"
  width="30px" 
  style="padding-right: 10px;"
  src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/r/r-original.svg"
/>
<br/>
<br/>

name: Generate pacman animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate pacman-contribution-graph.svg
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}


      - name: push pacman-contribution-graph.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}



