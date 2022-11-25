
### Response matrix description

Each of the files found in this directory describes a detector response matrix to photons in the range between 0 and 15keV, for different gas mixtures.

The response matrix has been calculated using a Geant4 MonteCarlo simulation, by launching photons to a gaseous volume of 6x6 cm, and 3cm of drift distance. The setup used to generate that simulation using `restG4` can be found at the following [IAXO repository](https://github.com/iaxo/iaxo-simulations), inside the `simulations/detector` directory. The setup is based on the [14.DetectorResponse](https://github.com/rest-for-physics/restG4/tree/master/examples/14.DetectorResponse) `restG4` example, where additional details can be found.

### Files naming convention

Each file represents the response matrix for a different gas mixture with 2-components, the filename defines those two components, the percentage of the second component and the total pressure of the mixture. Thus, `XenonNeon_20Pct_1.2bar.N150f` defines a xenon-neon mixture with 80% xenon and 20% neon (measured in mass) and a total pressure of 1.2bar. The pressure here is used as a scaling law.

### Response matrix generation

These response files have been generated using the macro `REST_GenerateResponseMatrix.C`, found inside the REST-for-Physics framework. This macro will generate a response matrix using each simulated event initial energy, `g4Ana_energyPrimary`, and its final deposited energy, `g4Ana_totalEdep`.

### Response matrix contents

The matrix contains 150 rows and columns, corresponding to a binning size of 100eV. The contents of each bin have been renormalized so that the efficiency at each matrix cell is measured in keV^-2. Each row contains the response vector to a given initial photon energy. Thus recovering the `d[10]` element of the matrix will return the response vector for the photons with initial energy between 1keV and 1.1keV.

The matrix contents can be inspected inside `restRoot` using:

```
std::vector< std::vector <Float_t> > d;
TRestTools::ReadBinaryTable( "XenonNeon_50Pct_1.2bar.N150f", d );
TRestTools::PrintTable( d, 2, 4 ); // Prints the rows between 2 and 4.
```

or simply writting the row to be printed inside `restRoot`:

```
root [1] TRestTools::ReadBinaryTable( "XenonNeon_50Pct_1.2bar.N150f", d );
root [2] d[10]
(__gnu_cxx::__alloc_traits<std::allocator<std::vector<float, std::allocator<float> > >, std::vector<float, std::allocator<float> > >::value_type &) { 0.000137778f, 0.000164444f, 0.000182222f, 0.000133333f, 7.55556e-05f, 8.44445e-05f, 0.000271111f, 0.000302222f, 0.000395556f, 0.000204444f, 0.661942f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 0.00000f, 
```

