# MyWalletBankData

Public repository for financial institution data used by the [MyWallet](https://github.com/mdrahim/MyWallet_App) Android app.

## Structure

```
data/
├── BD.json      # Bangladesh (64 institutions)
├── IN.json      # India (28 institutions)
├── US.json      # United States (25 institutions)
├── GB.json      # United Kingdom (16 institutions)
├── AE.json      # UAE (14 institutions)
├── SA.json      # Saudi Arabia (13 institutions)
├── MY.json      # Malaysia (19 institutions)
├── SG.json      # Singapore (12 institutions)
├── AU.json      # Australia (14 institutions)
├── CA.json      # Canada (14 institutions)
└── GLOBAL.json  # Global top institutions (44 institutions)
```

## JSON Format

Each country file follows this schema:

```json
{
  "version": 1,
  "lastUpdated": "2026-05-25",
  "country": "BD",
  "institutions": [
    {
      "code": "DBBLBDDH",
      "name": "Dutch-Bangla Bank Limited",
      "shortName": "DBBL",
      "type": "bank",
      "aliases": "ডাচ বাংলা ব্যাংক,Dutch Bangla"
    }
  ]
}
```

### Fields

| Field | Description | Required |
|-------|-------------|----------|
| `code` | Unique institution identifier. Preferably SWIFT/BIC code. | ✅ |
| `name` | Full official name | ✅ |
| `shortName` | Commonly used short name or abbreviation | ✅ |
| `type` | One of: `bank`, `mfs`, `fintech`, `investment`, `cooperative` | ✅ |
| `aliases` | Comma-separated alternative names (incl. native script) | Optional |

### Institution Types

| Type | Description |
|------|-------------|
| `bank` | Traditional commercial bank |
| `mfs` | Mobile Financial Service (bKash, GPay, etc.) |
| `fintech` | Digital-only financial service |
| `investment` | Investment/brokerage firm |
| `cooperative` | Cooperative bank/credit union |

## How the App Uses This Data

1. **Bundled**: Country files are bundled in the app's `assets/institutions/` folder for offline access
2. **Remote**: The app downloads `https://raw.githubusercontent.com/mdrahim/MyWalletBankData/main/data/{COUNTRY_CODE}.json` for updates
3. **Merged**: New entries are added, existing entries are updated, user customizations are preserved

## Contributing

To add institutions for a new country or update existing ones:

1. Create/edit the country JSON file in `data/`
2. Ensure `code` values are unique (preferably SWIFT/BIC codes)
3. Include native-script aliases for search
4. Submit a Pull Request

### Adding a New Country

```json
{
  "version": 1,
  "lastUpdated": "2026-01-01",
  "country": "XX",
  "institutions": [
    {
      "code": "BANKXXXX",
      "name": "Example Bank",
      "shortName": "ExBank",
      "type": "bank",
      "aliases": "Alternative Name,নেটিভ নাম"
    }
  ]
}
```

## Data Sources

- [Bangladesh Bank](https://www.bb.org.bd/) — List of scheduled banks
- [Reserve Bank of India](https://www.rbi.org.in/) — List of scheduled banks
- [SWIFT/BIC Directory](https://www.swift.com/standards/data-standards/bic)
- Central bank websites for each country

## License

This data is provided for use with the MyWallet application. The institution names and codes are public information sourced from official financial regulatory bodies.
