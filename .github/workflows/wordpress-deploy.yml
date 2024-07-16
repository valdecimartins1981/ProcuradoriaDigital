name: Deploy WordPress

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Build Docker image
        run: docker build -t my-wordpress .

      - name: Deploy to server
        run: |
          docker login -u ${{ secrets.DOCKER_USERNAME }} -p ${{ secrets.DOCKER_PASSWORD }}
          docker tag my-wordpress my-docker-registry/my-wordpress:latest
          docker push my-docker-registry/my-wordpress:latest
