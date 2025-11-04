# Documentatiewebsite voor Interne TaakAfhandeling (ITA)
Dit is de broncode waarmee de documentatiewebsite van ITA gegenereerd wordt

## Afhankelijkheden updaten (bijvoorbeeld bij kwetsbaarheden) 
1. Ga in een terminal naar de map `/docs`
1. Verwijder het `requirements.txt` bestand
1. Genereer het `requirements.txt` bestand onpieuw met 
```bash
uv pip install -r requirements.txt
```

### 💡 Installatie-instructies voor `uv`

Dit project gebruikt [`uv`](https://github.com/astral-sh/uv) om Python-afhankelijkheden te beheren en `requirements.txt`-bestanden te genereren.

#### 🧰 Vereisten
- **Python 3.11** of hoger  
- **pip** (standaard meegeleverd bij Python)

Zorg dat Python in je **PATH** staat tijdens de installatie (vink “Add Python to PATH” aan).

---

#### ⚙️ 1. Installeer `uv`
Open een terminal (PowerShell of cmd op Windows) en voer uit:

```bash
pip install uv
```

Controleer daarna of de installatie gelukt is:

```bash
uv --version
```