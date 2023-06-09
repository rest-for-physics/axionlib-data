
## Description

This data directory contains the description of different solar hidden photon flux tables that can be accessed using the `TRestAxionSolarFlux` object. To learn on how to use `TRestAxionSolarFlux` visit the [REST-for-Physics API](https://sultan.unizar.es/rest/).

## Basic conventions

- **File contents**: Each value inside the file corresponds to the calculated axion flux on Earth for the average Sun-Earth distance.

- **Filename**: hiddenPhoton_DATA_AUTHOR_YYYYMM.dat, where DATA stands for the contents of the file, which can be:

	+ `flux`: The solar hidden photon flux without the dependence on the mixing parameter chi, the hidden photon mass m, the plasma frequency wp and the resonance width wG. A function of solar radius and hidden photon energy.

	+ `plasmaFreq`: The solar plasma frequency as a function of solar radius.

	+ `omegaGamma`: The width of the hidden photon resonant production as a function of solar radius and hidden photon energy.

- The flux is then calculated using the formula `chi^2 x m^4 x wG x flux / ( (m^2 - wp^2)^2 + (wG)^2 )`.

- We will find different file extensions, `.dat` files in text format and `.N200f` in binary format.

	+ `.dat` ASCII tables: The format of the tables is fixed to 1000 lines. Each line inside the file corresponds to one integrated solar ring, the first line corresponding to the inner ring (Rtop = 0.001 x Rsun), and the last line corresponding to the outer ring (Rbottom=0.999 x Rsun). Each column value corresponds to the integrated energy spectrum in steps of 100 eV. The first value in each row corresponds to the contribution to the solar axion flux from 0 to 100 eV. The energy range goes to 20 keV.

	+ `.N200f` binary tables: It is a float binary table with 200 columns. The format of the tables is fixed to 100 rows. Each line inside the file corresponds to one integrated solar ring, the first line corresponding to the inner ring (Rtop = 0.001 x Rsun), and the last line corresponding to the outer ring (Rbottom=0.999 x Rsun). Each column value corresponds to the integrated energy spectrum in steps of 100 eV. The first value in each row corresponds to the contribution to the solar axion flux from 0 to 100 eV. The energy range goes to 20 keV.

- **Units**:
	+ *Flux*: The solar flux given in the `.dat` and `.flux` tables will be measured in `cm-2 s-1 keV-1`.

## List of solar flux tables available

The original `.flux` files produced originally have been translated into tables (N200f,dat,spt) using the following recipe:

```
TRestAxionSolarFlux flux("fluxes.rml", "FluxName");
flux.LoadTables();
flux.ExportTables();
```

The resulting tables will found at `~/.rest/export/` directory. For additional details check the [TRestAxionSolarFlux documentation](https://sultan.unizar.es/rest/classTRestAxionSolarFlux.html).

- `hiddenPhoton_*_OShea_202306.dat/.N200f` : Generated using [tomasoshea/darkphoton](https://github.com/tomasoshea/darkphoton). Credit: Tomas O'Shea

