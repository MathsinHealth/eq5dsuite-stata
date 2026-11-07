# eq5dsuite-stata

<!-- badges: start -->
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
<!-- badges: end -->

Stata implementation of [eq5dsuite](https://github.com/MathsInHealth/eq5dsuite) 
— a standardised suite of tools for EQ-5D analysis across R, Stata, and 
Excel. These commands calculate EQ-5D values and analyse and report 
EQ-5D data following the recommendations of Devlin et al. (2020).

## Features

- EQ-5D value calculation for the **EQ-5D-3L** (`eq5d3l`), 
  **EQ-5D-5L** (`eq5d5l`), and **EQ-5D-Y-3L** (`eqy3l`) instruments
- **Published national value sets** for each instrument
- Two **crosswalk methods**: EQ-5D-5L responses to EQ-5D-3L values 
  (`eqxw`) and EQ-5D-3L responses to EQ-5D-5L values (`eqxwr`)
- Support for **user-defined custom value sets**
- **Reporting of EQ-5D data** (`eqreport`): tables and figures for 
  profile analysis, EQ-5D value analysis, and EQ-VAS analysis, for 
  cross-sectional and longitudinal data
- Export of tables to Excel and figures to Stata graph files

## Installation

Install all commands from the Maths in Health Stata site:

```stata
foreach pkg in eq5d3l eq5d5l eqy3l eqxw eqxwr eqreport {
    net install `pkg', from("http://stata.mathsinhealth.com") replace
}
```

Or install a single command:

```stata
net install eq5d3l, from("http://stata.mathsinhealth.com") replace
```

## Quick start

```stata
* Dimensions must be in questionnaire order (mobility, self-care,
* usual activities, pain/discomfort, anxiety/depression) and coded
* 1 (no problems) to 3 (3L, Y-3L) or 5 (5L)

* Calculate EQ-5D-3L values using the UK value set
eq5d3l mo sc ua pd ad, country(GB) saving(utility)

* View available value sets
eq5d3l, display

* Calculate EQ-5D-5L values by group
eq5d5l mo sc ua pd ad, country(ES) by(gender)

* Crosswalk EQ-5D-5L responses to EQ-5D-3L values
eqxw mo sc ua pd ad, country(AR)

* Ten most frequently observed health states
eqreport mo sc ua pd ad, version(3L) table(table_2_3)
```

## Documentation

- Help files for each command: `help eq5d3l`, `help eq5d5l`, 
  `help eqy3l`, `help eqxw`, `help eqxwr`, `help eqreport`
- Full description with worked examples: 
  [Stata guide](docs/eq5dsuite_Stata_guide.docx)

## Value sets repository

Country-specific value sets are maintained at:

**[eq5dsuite-value-sets](https://github.com/MathsInHealth/eq5dsuite-value-sets)**

Value sets not yet included can be added with the `add()` and 
`from()` options. See `help eq5d3l`.

## Cross-platform suite

eq5dsuite is available across three platforms:

| Platform | Repository | Status |
|---|---|---|
| R | [eq5dsuite-r](https://github.com/MathsInHealth/eq5dsuite-r) | Available on CRAN |
| Stata | [eq5dsuite-stata](https://github.com/MathsInHealth/eq5dsuite-stata) | Available |
| Excel | [eq5dsuite-excel](https://github.com/MathsInHealth/eq5dsuite-excel) | Available |

## Issues and feedback

For Stata-specific issues please use the 
[issue tracker](https://github.com/MathsInHealth/eq5dsuite-stata/issues) 
in this repository.

For cross-platform concerns please use the 
[umbrella issue tracker](https://github.com/MathsInHealth/eq5dsuite/issues).

For general enquiries contact 
[info@mathsinhealth.com](mailto:info@mathsinhealth.com).

## License

This package is licensed under the MIT License.
