# Debugging Tools
## Printing network properties
Including the lines in the `Maud/src/maud/stan/debug.stan` file prior to the return line 
in the `get_edge_fluxes()` function inside the `Maud/src/maud/stan/functions.stan` file 
will print the defined properties inside your standard output file. An example of where
to place them is defined below:

```
                                              phosphorylation_pme);
    print("free_enzyme_ratio: ", free_enzyme_ratio);
    print("vmax: ", vmax);
    print("reversibility: ", reversibility);
    print("saturation: ", saturation);
    print("allostery: ", allostery);
    print("phosphorylation: ", phosphorylation);
    print("drain_by_edge: ", drain_by_edge);
    return (S * edge_flux)[balanced_ix];
  }
}
```
