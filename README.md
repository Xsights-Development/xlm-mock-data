# XLM Showcase Mock Data

Mock data configuration for XLM Dashboard showcase/demo farms.

## 📁 Files

- `config.json` - Main configuration file
- `README.md` - This file

## 🚀 Quick Start

1. **Fork/Clone this repo**
2. **Enable GitHub Pages**:
   - Settings → Pages
   - Source: Deploy from branch
   - Branch: `main`, Folder: `/ (root)`
3. **Your URL**: `https://YOUR_USERNAME.github.io/xlm-showcase-mock-data/config.json`

## 📝 Configuration Structure

```json
{
  "version": "1.0.0",
  "last_updated": "2026-02-11T10:00:00Z",
  "showcase_farms": ["pig-farm-x-aNGSmSd2"],
  "showcase_locations": ["nursery-room-6-a9E6VFtE"],
  "showcase_farm_ids": [38],
  "avg_woa": 6,
  "nursery_room_fixed_avgwoa": {},
  "rest_mock_map": {},
  "cube_mock_map": {}
}
```

## 🔄 How to Update

1. Edit `config.json` in this repo
2. Commit and push changes
3. GitHub Pages auto-deploys (30 seconds - 2 minutes)
4. Dashboard app fetches new config on next reload (cache: 1 hour)

## 📚 Documentation

### REST Mock Map

Maps REST API endpoints to mock responses:

```json
"rest_mock_map": {
  "/stats/tags": {
    "scope": "farm",
    "response": {
      "data": {
        "data": [...]
      }
    }
  }
}
```

**Fields:**
- `scope`: `"farm"` or `"location"` - determines which identifier to match
- `response`: Static response data
- `response_fn_name`: Name of generator function (for dynamic data like weather)

**Special function names:**
- `"mockWeatherForecastData"` - Generates 7-day weather forecast with dynamic dates
- `"mockTempHumData"` - Generates 7-day temperature/humidity data

### Cube Mock Map

Maps Cube.js component keys to mock data:

```json
"cube_mock_map": {
  "farm-health-alerts": {
    "scope": "farm",
    "data": {
      "AlertTriggered": [1225, 1090, 1335, 1155],
      "MedicationScheduled": [210, 190, 225, 175]
    }
  }
}
```

**Fields:**
- `scope`: `"farm"` or `"location"`
- `data`: Mock data object/array (matches tablePivot format)
- `data_fn_name`: Name of generator function (for dynamic data)

**Special function names:**
- `"mockTempHumData"` - Generates 7-day room conditions data

### Component Keys

| Key | Scope | Description |
|-----|-------|-------------|
| `farm-health-alerts` | farm | Farm health alerts chart |
| `farm-health-alert-responses` | farm | Farm health alert responses chart |
| `farm-tags-deployed` | farm | Farm tags deployment chart |
| `farm-navigation-animals` | farm | Farm navigation animal counts |
| `room-health-alerts` | location | Room health alerts chart |
| `room-health-alert-responses` | location | Room health alert responses chart |
| `room-tags-deployed` | location | Room tags deployment chart |
| `room-conditions` | location | Room temperature/humidity |

## 🔍 Version History

Track changes via Git commits:

```bash
git log --oneline config.json
```

## 🌐 Live URL

After enabling GitHub Pages, your config will be available at:

```
https://YOUR_USERNAME.github.io/xlm-showcase-mock-data/config.json
```

Test it:
```bash
curl https://YOUR_USERNAME.github.io/xlm-showcase-mock-data/config.json
```

## 📱 Using in Dashboard App

Set environment variables:

```bash
REACT_APP_ENABLE_REMOTE_MOCK=true
REACT_APP_MOCK_DATA_URL=https://YOUR_USERNAME.github.io/xlm-showcase-mock-data/config.json
```

## 🐛 Troubleshooting

### Config not updating?

1. **Clear browser cache**: Hard reload (Cmd+Shift+R / Ctrl+Shift+F5)
2. **Wait for GitHub Pages deploy**: Check Actions tab for deployment status
3. **Check URL**: Ensure `REACT_APP_MOCK_DATA_URL` is correct
4. **Verify JSON**: Use JSONLint to validate `config.json`

### App not using remote config?

Check console logs:
```
[GitHubMock] Fetching from: https://...
[GitHubMock] Remote config loaded successfully
[ShowcaseConfig] Using remote config from GitHub Pages
```

If you see "Falling back to local config", check:
- `REACT_APP_ENABLE_REMOTE_MOCK=true` is set
- URL is accessible (test with curl)
- JSON is valid

## 📄 License

This repository contains mock data for demonstration purposes only.

## 🤝 Contributing

1. Create branch for changes
2. Update `config.json`
3. Update `last_updated` timestamp
4. Increment `version` if major changes
5. Commit and push
6. GitHub Pages auto-deploys

---

**Repository URL**: https://github.com/YOUR_USERNAME/xlm-showcase-mock-data

**Live Config**: https://YOUR_USERNAME.github.io/xlm-showcase-mock-data/config.json

**Dashboard**: https://xlm-dashboard.example.com
