# Fizzy Feature Selection Tool

Fizzy is a subset selection tool that uses [FEAST](http://www.cs.man.ac.uk/~gbrown/fstoolbox/) in the background to run feature selection. Fizzy processes [BIOM](http://biom-format.org/) and mapping files, which are a standard in metagenomics data analysis. `fizzy.py` will run feature selection on taxanomic abundances obtained from the biom file given a set of categorical labels obtained form the the mapping file.  

# Options 
* `-l`, `--label`: name of column of the mapping file that indicates the labels
* `-n`, `--select`: number of taxonomic features to select
* `-f`, `--fs-method`: Feature selection method. Available: CIFE CMIM CondMI, Condred ICAP JMI MIM MIFS mRMR
* `-i`, `--input-file`: biom format file
* `-m`, `--map-file`: CSV mapping file
* `-o`, `--ouput-file`: output file where selected taxonimic IDs are saved

Getting help with `fizzy.py`:
```bash 
  fizzy.py -h
```

# General Usage Example

A general useage example for Fizzy would be something along the lines of
```bash
  fizzy.py -i my-data.biom -o results.txt -m mapping-file.txt -f JMI -l BODY-SITE
```
where `BODY-SITE` is a column in the mapping file.

# Installation and Dependencies

You need to install the [PyFeast](https://github.com/EESI/PyFeast) feature selection library in order to run the tools in Fizzy; however, PyFeast has its own dependencies - namely FEAST. Install the [MIToolbox](https://github.com/Craigacp/MIToolbox) and [FEAST](https://github.com/Craigacp/FEAST) prior to installing PyFeast. For example, you may need to do
```shell
  git clone https://github.com/Craigacp/MIToolbox.git
  cd MIToolbox
  make 
  sudo make install
  cd ../
  git clone https://github.com/Craigacp/FEAST.git
  cd FEAST
  make
  sudo make install
  cd ../
  git clone https://github.com/EESI/PyFeast.git
  cd PyFeast
  python setup.py build 
  sudo python setup.py install 
```

The above code will install all of the dependencies. To run `fizzy.py` either: (a) always run the `fizzy.py` from a working directory, or (b) add the script to `/usr/local/bin/`

# Credits

* [Calvin Morrison](http://mutantturkey.com/), [Gregory Ditzler](http://gregoryditzler.com), and [Gail Rosen](http://www.ece.drexel.edu/gailr/) 
