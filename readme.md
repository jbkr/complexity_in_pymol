# About

The aim is to roll out [TMSOC](http://tmsoc.bii.a-star.edu.sg/) like function into 3D protein structures. This allows us to study the role of anchors (identified by TMSOC as simple TMHs), as well as TMHs with function beyond anchorage (twilight and complex TMHs), in 3D space.

Currently, **the software is available for Linux distributions only** since it is dependent on the `decodeanhmm` file underlying [Phobius](http://software.sbc.su.se/cgi-bin/request.cgi?project=phobius).

The script uses Phobius to estimate TMH boundaries. TMSOC is then used to assess complexity and the results are viewable in Pymol. The TMH regions are coloured accordingly:

- None-TMH loops = dark blue
- Complex TMH = light blue
- Twilight TMH = green
- Simple TMH = orange
- Signal peptide = red

![alt text](demo.png "Logo Title Text 1")

# Installation

This software requires Linux, python3, biopython, Phobius, and Pymol.

## Phobius

For copyright reasons, the Phobius package cannot be distributed alongside this software. To install Phobius, follow [this link](http://software.sbc.su.se/cgi-bin/request.cgi?project=phobius) and enter your details. The package will be emailed to you at an academic email address. Extract the files and copy them into the `complexity_in_pymol/pymol/` folder so it looks that the Pymol folder now has these additional files:

```
pymol/decodeanhmm
pymol/phobius.model
pymol/phobius.options
pymol/phobius.pl
pymol/README
```

# Running the script

## Overview

Move the pdb file into the `complexity_in_pymol/pymol/` directory and then run `bash runme.sh` in a terminal from the complexity_in_pymol/pymol/ folder. In Pymol, navigate to the complexity_in_pymol/pymol/ and after loading the structure enter `run bfactors.py` and then `complexb YOURSTRUCTURENAME, start position of strcutre, bfactors_YOURSTRUCTURENAME_SUBCHAIN.txt`.

## Step by step instructions

1. Move the PDB file you wish to work on into the Pymol directory. For example `cd Downloads/complexity_in_pymol/pymol/1a91.pdb`
2. In a terminal, navigate to the Pymol folder. For example: `cd Downloads/complexity_in_pymol/pymol`
3. In a terminal, run the `runme.sh`. This runs a series of commands in order and manages and logs the various input and output files. For example: `bash runme.sh`.
4. Enter the PDB filename when prompted. If you experience an error during this process, please log it by creating a [new issue](https://github.com/jbkr/complexity_in_pymol/issues/new) on GitHub.
5. Check that the B-factor files were generated, for example, is there a new file called `bfactors_1a91_A.txt`?
6. Load up the Pymol application.
7. Navigate in the application Pymol to the complexity_in_pymol/pymol directory. For example: `cd Downloads/complexity_in_pymol/pymol`
8. In Pymol load the structure. For example: `load 1a91.pdb`
9. In Pymol, load the B-factors script. Use `run bfactors.py`
10. In Pymol run the bfactor function on your desired molecule. For example `complexb 1a91,1, bfactors_1a91_A.txt`. `complexb` is the command. `1a91` is te molecule name in Pymol, `1` means the starting position on that molecule is 1 (this is different for some molecules, be sure to check in the sequence viewer), and `bfactors_1a91_A.txt` is the text file generated by the shell script for that chain. The text file contains a series of numbers corresponding to loop, complex, twilight, or simple.

---

# Status

[![Code Issues](https://www.quantifiedcode.com/api/v1/project/8a4ca942e31146de8448bb69a75c384f/badge.svg)](https://www.quantifiedcode.com/app/project/8a4ca942e31146de8448bb69a75c384f)

- [ ] Consensus TMH definition.
  - [ ] PDBTM integration.
  - [ ] TMHMM integration.
  - [ ] SignalP filter
  - [x] Phobius integration.
- [x] TMSOC integration.
- [x] PyMol compatible scipt.
- [x] b-factor PDB generator indicating complexity.

These scripts are in development and are provided as is. Use at your own risk.
