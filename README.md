.github/workflows/cliq-reporte-draco.yml
name: Reporte automático de Draco 4

on:
  schedule:
    - cron: '0 * * * *'  # Ejecuta cada hora en punto (UTC)

jobs:
  enviar_mensaje:
    runs-on: ubuntu-latest

    steps:
      - name: Enviar reporte al canal "comunicaciones"
        run: |
          curl -X POST "https://cliq.zoho.com/api/v2/channelsbyname/comunicaciones/message?zapikey=${{ secrets.CLIQ_TOKEN }}" \
          -H "Content-Type: application/json" \
          -d '{"text": "🟢 Buenas Cosaco, reporto la unidad de Draco 4 sin novedad especial."}'