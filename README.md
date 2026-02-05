# PC Hardware Inventory & Health Checker

This project includes a Python CLI that scans host hardware details and exports a clean report in **JSON**, **HTML**, or both.

## Requirements
- Python 3.9+
- Optional (recommended): `psutil` for richer CPU/RAM/storage/temperature data
- Optional: `smartctl` (from smartmontools) for disk SMART health
- Optional: `nvidia-smi` for NVIDIA GPU details/temperature

Install optional Python dependency:

```bash
python3 -m pip install psutil
```

## How to run
From the project root:

```bash
python3 hardware_inventory_health_checker.py --format both --output-dir reports
```

That creates timestamped files like:
- `reports/hardware_report_YYYYMMDD_HHMMSS.json`
- `reports/hardware_report_YYYYMMDD_HHMMSS.html`

### Common examples
Generate JSON only:

```bash
python3 hardware_inventory_health_checker.py --format json --output-dir reports
```

Generate HTML only:

```bash
python3 hardware_inventory_health_checker.py --format html --output-dir reports
```

Show help:

```bash
python3 hardware_inventory_health_checker.py --help
```

## What it scans
- CPU model, core counts, usage, and frequency
- RAM totals and current usage
- GPU details (NVIDIA when available, with fallback detection)
- Temperatures (system sensors and NVIDIA GPU temps when available)
- Storage usage plus SMART health status (if `smartctl` exists)

## Notes
- The script works without `psutil`, but output may be less detailed.
- SMART checks may require elevated permissions depending on your OS.
