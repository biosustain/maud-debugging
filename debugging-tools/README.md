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


## Changing simulate to optimize to approach MAP faster
Rather than simulating until you reach the typical set using the optimal 
lead to faster turnovers. Replace the `simulate` funciton in `Maud/src/maud/running_stan.py`
return line with this.

```
    return model.optimize(
        output_dir=output_dir,
        # iter_sampling=n,
        iter=2000,
        data=os.path.join(output_dir, "input_data_train.json"),
        inits=os.path.join(output_dir, "inits.json"),
        algorithm="LBFGS",
        init_alpha=1e-4,
        tol_param=1e-12,
        history_size=10,
        show_console=True,
        refresh=1,
        save_profile=True,
        save_iterations=True,
    )
```
