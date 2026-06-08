# Source Code

This folder contains reusable Python modules for the Gaia–LAMOST Galactic Archaeology Project.

## Purpose

The `src/` folder is used to organize stable and reusable code that was originally developed or tested in notebooks.

Moving reusable functions from notebooks into Python modules helps improve reproducibility, readability, and long-term maintainability.

## Planned Modules

    data_query/        Gaia and LAMOST query utilities
    crossmatch/        Cross-matching and catalogue matching utilities
    features/          Feature construction functions
    visualization/     Plotting and figure generation utilities
    utils/             General helper functions

## Development Notes

At the current stage, most analysis is still developed in Jupyter notebooks.

As the project matures, repeated logic should be gradually moved into this folder.
