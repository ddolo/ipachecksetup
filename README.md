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
	osp
	refusal
	dontknow
	consent
	id
	incomplete
	surveystart
	multiplier
	softmin
	softmax
	r1
	r2
	label
	enumid
	teamid
	bcid
	bcteamid
	backcheck
	survey
	media

```

## Example Syntax
```stata
* Long Formatted Dataset
ipachecksetup using "Endline Survey.xlsx", ///
	template("hfc_inputs.xlsm") ///
	outfile("hfc_inputs_endline.xlsm") ///
	long 

* Wide Formatted Dataset
ipachecksetup using "Endline Survey.xlsx", ///
	template("hfc_inputs.xlsm") ///
	outfile("hfc_inputs_endline.xlsm") ///
	wide

* Using all options
ipachecksetup using "ipa_yop_2017_short_DRAFT.xlsx", ///
 	template("hfc_inputs.xlsm") ///
	outfile("hfc_inputs_yop") 	///
	wide replace ///
		osp(-96) ref(-98) dontk(-99)  ///
		softmin(15) softmax(40) mul(1.3) ///
		id(uid1) consent(consent 1, phone_response 1) ///
		incomplete(consent 1) ///
		surveystart(9/14/2020)  ///
		enumid(enumid) teamid(superid) ///
		survey("ipa_yop_2017_data.dta") ///
		r1(community age father_job) r2(community age father_job, gender)  ///
		media("..\raw\media")
		backcheck("ipa_yop_2017_backcheck.xlsx") 

```

Please report all bugs/feature request to the [github issues page](https://github.com/PovertyAction/ipachecksetup/issues)
