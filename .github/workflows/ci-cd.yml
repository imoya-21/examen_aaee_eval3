name: CI/CD Pipeline con Multi-stage Docker

on:
  push:
    branches:
      - '**'

permissions:
  contents: read
  packages: write

jobs:
  build-and-push:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Login to GHCR
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Build and Push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          # Usamos la variable automática para el nombre del repo del examen
          tags: ghcr.io/${{ github.repository }}:latest
