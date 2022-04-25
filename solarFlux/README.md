
## Description

This data directory contains the description of different solar axion flux tables that can be accessed using the `TRestAxionSolarFlux` object. To learn on how to use `TRestAxionSolarFlux` visit the [REST-for-Physics API](https://sultan.unizar.es/rest/).

Each axion solar table (due to different production mechanisms) provides the pre-integrated(+) solar disc axion flux as a function of the solar radius and energy.

(+) The effective solar axion flux is integrated to the corresponding solar disk (ring) area.

## Basic conventions

- `File contents` : Each value inside the file corresponds to the calculated axion flux on Earth for the average Sun-Earth distance. 

- `Filename` : MODEL_AUTHOR_YYYYMM.dat, where MODEL stands for the solar axion production mechanism.

- We will find different file extensions, the original `flux` files, the continuum `.dat` and `.N200f` files in text and binary format respectively, and the `spt` files containning the monocrohmatic lines flux as a function of the solar ring.
	
    + `.flux` ASCII tables: It defines the original format using 3-columns (inner solar disk radius, energy and flux).

	+ `.dat` ASCII tables: The format of the tables is fixed to 100 lines. Each line inside the file corresponds to one integrated solar ring, the first line corresponding to the inner ring (Rtop = 0.01 x Rsun), and the last line corresponding to the outer ring (Rbottom=0.99 x Rsun). Each column value corresponds to the integrated energy spectrum in steps of 100 eV. The first value in each row corresponds to the contribution to the solar axion flux from 0 to 100 eV. The energy range goes to 20 keV.

	+ `.N200f` binary tables: It is a float binary table with 200 columns. The format of the tables is fixed to 100 rows. Each line inside the file corresponds to one integrated solar ring, the first line corresponding to the inner ring (Rtop = 0.01 x Rsun), and the last line corresponding to the outer ring (Rbottom=0.99 x Rsun). Each column value corresponds to the integrated energy spectrum in steps of 100 eV. The first value in each row corresponds to the contribution to the solar axion flux from 0 to 100 eV. The energy range goes to 20 keV.

	+ `.spt` tables: The format of the tables is fixed to 101 lines. The first line defines the energy of the monochromatic line in keV. Lines from 2 to 101 inside the file corresponds to the intensity of the spectral line integrated to a particular solar ring, the first line corresponding to the inner ring (Rtop = 0.01 x Rsun), and the last line corresponding to the outer ring (Rbottom=0.99 x Rsun). Any number of columns might be found inside the file in order to introduce a set of monochromatic lines including its solar radius dependency.

- `Units` :
	+ "**Flux**: The solar flux given in the `.dat` and `.flux` tables will be measured in `cm-2 s-1 keV-1`. The solar flux given in the `.spt` tables will be measured in `cm-2 s-1`.
    + "**Coupling**: The default units for `g_ag` coupling are `GeV-1`, `g_ae` coupling is adimensional. The coupling strength used in the table calculation will be defined as a parameter in the RML definition.

## List of solar flux tables available

The files available have been produced with the `fluxToTable.py` script. Simply used as:

```
python3 fluxToTables.py --f input_file.flux
```

For additional options and adapt to different specifications inside the flux file check the different options using:

```
python3 fluxTables.py -h
```

### Continuum tables
- `Primakoff_Gianotti_201904.dat`.

- `Primakoff_LennertHoof_202203.dat` : Generated using [SolarAxionFlux](https://github.com/sebhoof/SolarAxionFlux) library. Calculated with newer BP04 solar model, includes electron degeneracy in comparison to `Primakoff_Gianotti_201904.dat`.

### Monochromatic tables
- `Dummy_Galan_202202.spt` : It contains two monochromatic lines. A 3keV line emitted at about 0.25 solar radius, and a 5keV line emitted at 0.75 solar radius.
