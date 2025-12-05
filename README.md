# Husense Node-RED Dashboard

Node-RED aplikace pro vizualizaci dat z Husense API - systém pro sledování návštěvnosti a pohybu osob.

## Funkce

- **Dashboard s vizualizací návštěvnosti**
  - Gauges pro průměrnou návštěvnost (celkový průměr, všední dny, víkendy)
  - Sloupcový graf denní návštěvnosti (posledních 14 dní)
  - Tabulky spaces a devices

- **Heatmapa pohybu**
  - Vizualizace intenzity pohybu v prostoru
  - Parametrizace: výběr prostoru a časového období
  - Barevná škála od modré (nízká) po červenou (vysoká intenzita)

- **API endpointy**
  - Spaces, Devices, Locations
  - Gate visitors (průměr, denní/týdenní souhrn)
  - Heatmapa

## Instalace

```bash
# Klonování repozitáře
git clone https://github.com/ptucek/nred-husense.git
cd nred-husense

# Instalace závislostí
npm install

# Spuštění Node-RED
npx node-red --userDir "./node-red-data" --port 1880
```

## Použití

1. Otevřete Node-RED editor: http://localhost:1880
2. Importujte flow soubor:
   - Menu → Import → vyberte `husense-dashboard-flow.json`
   - Klikněte Deploy
3. Otevřete dashboard: http://localhost:1880/ui

## Konfigurace API klíče

API klíč je načítán z externího souboru `config.json`:

1. Zkopírujte šablonu:
   ```bash
   cp config.example.json config.json
   ```
2. Upravte `config.json` a vložte svůj API klíč:
   ```json
   {
       "husense_api_key": "VÁŠ_API_KLÍČ",
       "spaces": {
           "plzen01": "d25d9824-36e2-4d0f-bf89-caf574620d88",
           "plzen02": "085fbb0f-a394-4e9b-a57b-9398af59e6bb"
       }
   }
   ```
3. Soubor `config.json` je v `.gitignore` - nebude uložen do git

## API Servery

- **Main API:** `https://api.husense.io/api/v1`
- **BFF API:** `https://bff.husense.io`

## Soubory

| Soubor | Popis |
|--------|-------|
| `husense-dashboard-flow.json` | Hlavní dashboard s vizualizacemi |
| `husense-spaces-flow.json` | Základní flow pro testování API |
| `package.json` | Node-RED dependencies |

## Požadavky

- Node.js 18+
- Node-RED 4.x
- node-red-dashboard

## Spaces

- **Plzen-01** - má heatmapu
- **Plzen-02** - bez heatmapy
