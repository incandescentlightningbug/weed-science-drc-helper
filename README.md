# weed-science-drc-helper
This contains a .R file with a function to fit data from a weed science dose-response experiment to a 3- or 4-parameter curve using the drc package.

## Description
This is the function:<br>
dr_analysis() – fits both 3‑parameter and 4‑parameter log‑logistic models, compares them using AIC/BIC, returns ED 10, 50, and 90 values, parameter comparisons between populations, and a grouped bar plot.<br>
This function is intended for researchers working with herbicide dose–response bioassay data using the drc package (Knezevic et al. 2007).

## Data Requirements
The dr_analysis() function uses functions from the drc and readxl packages, so make sure they are downloaded before running the dr_analysis() function. If these data requirements are not met, the function will return an error. Be aware, these are case-sensitive.<br>
Your input must be an Excel file (.xlsx) with the following columns:<br>
* population (character): Identifies population/biotype. Example: sensitive, resistant<br>
* dose (numeric): The rate/dose of the herbicide. Units must be consistent for each dose. Dose cannot contain negative values.<br>
* bio.pctrl (numeric): Biomass as a percent of the untreated control (dose = 0 units of herbicide). Should be values ranging from 0 to 100. Values are normalized.<br>

## Output
dr_analysis() returns a list containing:<br>
* Best-fitting model: 3-parameter (LL.3) or 4-parameter (LL.4)<br>
* Model summary<br>
* Effective dose (ED) 10, 50, and 90 values with confidence intervals. ED is essentially the same as I and GR. They all represent the value of the dose that produces a 50% response in phenotype.<br>
* Parameter comparisons between populations<br>
  * slope (b)<br>
  * lower limit<br>
  * upper limit (unless 3-parameter model is selected)<br>
  * ED50<br>
* A dose-reponse curve of predicted responses

## Model Selection Criteria
The function fits two candidate models:<br>
1. 4-parameter log-logistic<br>
2. 3-parameter log-logistic<br>
It selects the 4‑parameter model only if both AIC and BIC are lower; otherwise, it uses the 3‑parameter model.<br>
This approach helps avoid overfitting while still capturing biological asymmetry if strongly supported by the data.

## Questions or Suggestions?
If you are a weed scientist using this tool and have ideas for improvements — new parameters, visualization styles, or support for other model families — please open an Issue or submit a Pull Request. All constructive criticism and friendly advice are welcome!
