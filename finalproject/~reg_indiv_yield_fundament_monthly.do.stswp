version 17.0
clear all
cap log close
set more off
set matsize 11000

// cap cd "/Users/ygnmax/Dropbox (Personal)/Library/Economics/UCSD/Econ281MacroTopics/Macro281/finalproject/"   // Mac path

use "data.dta", clear


******************
* forecast level
******************
foreach v of varlist federal_funds_rate treas_bills_6mo treas_bills_1yr  treas_notes_5yr treas_notes_10yr   {

bys unique_id quarter (yearmonth): gen lag_`v' = `v'[_n-1]

dis "`v'"

local rowid = 0
mat all_coef = J(403, 10, .)
forvalues ymid = 337(1)730 {
	display "Year-Month pair `ymid'"
	local rowid = `rowid' + 1
	mat all_coef[`rowid', 1] = `ymid'
	
	cap reg `v' lag_`v' real_gdp cons_price_index if yearmonth == `ymid'
	
	mat all_coef[`rowid', 2] = e(b)[1, 1]
	mat all_coef[`rowid', 3] = e(V)[1, 1]
	mat all_coef[`rowid', 4] = e(b)[1, 2]
	mat all_coef[`rowid', 5] = e(V)[2, 2]
	mat all_coef[`rowid', 6] = e(b)[1, 3]
	mat all_coef[`rowid', 7] = e(V)[3, 3]	
	mat all_coef[`rowid', 8] = e(N)
	mat all_coef[`rowid', 9] = e(r2)
	mat all_coef[`rowid', 10] = e(r2_a)	
}


putexcel set "output/reg_fct_level_monthly.xlsx", sheet(`v') modify
putexcel A1 = matrix(all_coef), names
putexcel B1 = ("ymid")
putexcel C1 = ("coef_lag")
putexcel D1 = ("var_lag")
putexcel E1 = ("coef_gdp")
putexcel F1 = ("var_gdp")
putexcel G1 = ("coef_cpi")
putexcel H1 = ("var_cpi")
putexcel I1 = ("N")
putexcel J1 = ("r2")
putexcel K1 = ("r2a")

putexcel save

}


**************************
* forecast level: pooled
**************************
local j = 0
foreach v of varlist federal_funds_rate treas_bills_6mo treas_bills_1yr treas_notes_5yr treas_notes_10yr  {
	
	cap drop lag_`v'
	bys unique_id quarter (yearmonth):  gen lag_`v' = `v'[_n-1]

	dis "`v'"
		
	reghdfe `v' lag_`v' real_gdp cons_price_index , absorb(yearmonth qt_ahead)
	local j = `j' + 1

	est store m`j'


}

esttab m1 m2 m3 m4 m5 using "output/reg_fct_level_monthly_pooled.csv", ///
	replace scalar(r2 N) compress nobaselevels nogaps star(* 0.1 ** 0.05 *** 0.01) ///
    b(%6.4f) se(%6.4f)  label mtitles("FFR" "6 Mo" "1 Yr" "5 Yr" "10 Yr")

	
*******************************
** plot
*******************************

foreach v in "federal_funds_rate" "treas_bills_6mo" "treas_bills_1yr" "treas_notes_5yr" "treas_notes_10yr" {
	display "`v'"
	import excel "output/reg_fct_level_monthly.xlsx", sheet("`v'") clear firstrow
	merge m:1 ymid using "data_ymid.dta", keep(3) nogen 

	line coef_lag  yearmonth, aspect(0.5) legend(label(1 "Lag term") position(6) col(3)) 
	graph export "output/plot/coef_`v'_level.png", replace
	
	line coef_gdp coef_cpi yearmonth, aspect(0.5) legend(label(1 "Real GDP") label(2 "CPI") position(6) col(3)) 
	graph export "output/plot/coef_`v'_level2.png", replace
}


