name: Update GitHub Stats
on:
  schedule:
    - cron: '0 0 * * *' # Atualiza diariamente à meia-noite UTC
  workflow_dispatch:

jobs:
  update-stats:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
        
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '20'
          
      - name: Update README
        uses: anmol098/waka-readme-stats@master
        with:
          GH_TOKEN: ${{ secrets.GH_PAT }}
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
          SHOW_PROFILE_VIEWS: false
          SHOW_LANGUAGE_ICON: true
          SHOW_LOC_CHART: true
          SHOW_PROJECTS: true
          SHOW_OS: true
          THEME: dracula
          
