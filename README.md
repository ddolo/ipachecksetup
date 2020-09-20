# IPACHECKSETUP

## Overview

ipachecksetup is a stata program that prefills the IPA HFC inputs template.


## Installaion
```stata
* ipachecksetup can be installed from github

net install ipachecksetup, all replace ///
	from("https://raw.githubusercontent.com/PovertyAction/ipachecksetup/master")
```

## Syntax
```stata
ipachecksetup using filename, template(string) outfile(string) [replace long wide]

options
	using           - SurveyCTO XLS form
	template     	- template file for HFC inputs
	outfile 		- save prefilled inputs file as
	replace			- replace outfile if neccesary
	long 			- assume data is in long format. Only needed if forms has repeat groups
	wide            - assume data is in wide format. Only needed if forms has repeat groups

```

## Example Syntax
```stata
* Long Formatted Dataset
ipachecksetup using "Endline Survey.xlsm", ///
	template("hfc_inputs.xlsm") ///
	outfile("hfc_inputs_endline.xlsm") ///
	long 

* Wide Formatted Dataset
ipachecksetup using "Endline Survey.xlsm", ///
	template("hfc_inputs.xlsm") ///
	outfile("hfc_inputs_endline.xlsm") ///
	wide
```

Please report all bugs/feature request to the [github issues page](https://github.com/PovertyAction/ipachecksetup/issues)
