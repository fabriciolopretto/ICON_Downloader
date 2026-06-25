[README_ICON_Downloader.md](https://github.com/user-attachments/files/29341029/README_ICON_Downloader.md)
# ICON Downloader

Python downloader for selected surface-level ICON global model GRIB2 files from DWD Open Data. The script downloads 2-meter temperature and 10-meter wind components for the current operational cycle.

## Objective

Automate downloads of selected ICON global single-level forecast variables.

The script downloads:

- `T_2M`: 2-meter temperature.
- `U_10M`: 10-meter zonal wind component.
- `V_10M`: 10-meter meridional wind component.

For each variable, it downloads forecast lead times `000` through `078`.

## Repository Structure

```text
ICON_Downloader/
├── README.md
└── Descarga/
    ├── Descarga_AUTO_ICON_SUP.py
    ├── T_2M/
    │   └── icon_global_icosahedral_single-level_2024012100_000_T_2M.grib2.bz2
    ├── U_10M/
    │   └── icon_global_icosahedral_single-level_2024012100_000_U_10M.grib2.bz2
    └── V_10M/
        └── icon_global_icosahedral_single-level_2024012100_000_V_10M.grib2.bz2
```

## Data Source

The downloader uses DWD Open Data:

```text
https://opendata.dwd.de/weather/nwp/icon/grib/
```

Generated URL pattern:

```text
https://opendata.dwd.de/weather/nwp/icon/grib/HH/<variable>/icon_global_icosahedral_single-level_YYYYMMDDHH_FFF_<VARIABLE>.grib2.bz2
```

## Technologies Used

- Python 3
- requests

## Installation

Clone the repository:

```bash
git clone https://github.com/fabriciolopretto/ICON_Downloader.git
cd ICON_Downloader/Descarga
```

Install dependencies:

```bash
pip install requests
```

## Usage

Run:

```bash
python Descarga_AUTO_ICON_SUP.py
```

Downloaded files are saved by variable:

```text
Descarga/T_2M/
Descarga/U_10M/
Descarga/V_10M/
```

## Notes

The script chooses the current UTC `00Z` or `12Z` cycle and removes previous `.grib2` and `.grib2.bz2` files before downloading new files.

The downloaded files are compressed with `bz2`. You may need to decompress them before using them with some GRIB tools.

