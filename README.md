# strip-image-metadata-action

Dead simple Github Workflow Action for stripping metadata from all images in a directory. 

All the action does is:
1. Install ImageMagick
2. Run `mogrify -strip` on the folder you present

## How To Use

This action assumes your runner is on `ubuntu` (it installs `ImageMagick` with `apt-get install`).

Pass in your path regex that you want stripped with `path-regex`.

Example `.github/workflows/deploy.yml`:

```.yml
name: deploy-production

on:
  push:
    branches:
      - main

jobs:
  deploy:
    name: deploy my stuff
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository code
        uses: actions/checkout@v3

      # ... whatever else you need

      - name: Strip metadata from images
        uses: joshmenden/strip-image-metadata-action@v1
        with:
          path-regex: ./assets/images/*
      
      # ... deploy your code
```


That's it!