# DevOps
Seminario

name: CI/CD with Security Checks

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2

      # Aquí se incluyen los pasos para construir tu aplicación
      # Por ejemplo, si es una aplicación Node.js:
      - name: Install Dependencies
        run: npm install

      - name: Build
        run: npm run build

      # Comprobaciones de seguridad
      - name: Static Code Analysis
        run: npm run analyze-code

      - name: Dependency Vulnerability Scan
        run: npm audit

      - name: Check for Secrets
        run: npm run check-secrets

      - name: Container Security Scan
        run: npm run scan-containers
