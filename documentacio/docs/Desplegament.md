---
sidebar_label: 'Desplegament'
sidebar_position: 4
---

# Desplegament

Quan treballem en els .md estem en el "codi font" de la documentació. Per desplegar i poder consultar-la com una web, cal generar els fitxers estàtics:

    npm run build 

Això genera el directori `build`. 

## Desplegar a Github

Tenim moltes opcions per desplegar. Una de les més simples és a github pages des d'una branca. 

* Creem la branca gh-pages
* Anem a settings > pages > deploy from a branch > gh-pages / root 
* Ara cal automatitzar el desplegament a aquesta branca amb un `action`. 
* Creem el action amb aquest codi:

```yml
name: Your github action

on:
  push:
    branches:
      # NOTE: You may want to limit the trigger branch to be "main" or "master" etc.
      - '*'

jobs:
  publish:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    steps:
      - name: Check out
        # You may use a newer version of https://github.com/actions/checkout
        uses: actions/checkout@v4

      - name: Generate your content
        run: echo "Optional placeholder. Put your project's static website generator command here."

      - name: Install dependencies
        working-directory: documentacio
        run: npm ci
        
      - name: nmp build
        working-directory: documentacio
        run: npm run build

      - name: Publish current workdir (which contains generated content) to GitHub Pages
        uses: rayluo/github-pages-overwriter@v1.3

        with:

          # Optional.
          #
          # Default value "." means the root directory of your project will be published.
          #
          # You can use whatever directory your project uses,
          # for example "wwwroot" (without leading "./").
          # Such a directory does *not* have to already exist in your repo,
          # it could be an output directory created dynamically
          # by your static website builder.
          source-directory: documentacio/build

          # Optional. Default value "gh-pages".
          # It specifies the temporary branch which hosts the static website.
          # Each build will OVERWRITE this branch.
          target-branch: gh-pages

```

Cal modificar les rutes si és necessari. 

D'aquesta manera, utilitzem un action preconfigurat `rayluo/github-pages-overwriter@v1.3` que sobreescriu tota la branca `gh-pages` cada vegada. 

També tenim un script que instal·la les dependències i fà el `build` de docusaurus.

Alternativa: https://github.com/peaceiris/actions-gh-pages

## Desplegar PHP

Es pot fer un action com aquest:

```yaml
name: Deploy 

on:
  push:
    branches:
      - 'master'

jobs:
  publish:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    steps:
      - name: Check out
        uses: actions/checkout@v4

      - name: 📂 Sync files
        uses: SamKirkland/FTP-Deploy-Action@v4.3.5
        with:
          server: ${{ secrets.SFTP_HOST }}
          username: ${{ secrets.SFTP_USER }}
          password: ${{ secrets.SFTP_PASS }}
          local-dir: ./build/
          server-dir: /public_html/materiales/
```


Cal canviar les rutes i crear els secrets.