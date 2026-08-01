Motivation:
1) Numerous best quality non-detectable cleaning events were tagged as OOC by X-bar chart or median-chart (bootstrap derived). 
2) Practioners replace ND by worst LOD/LOQ conveniently with the logic that if the worst case shows the cleaning process stable and capable, then the other imputation of ND would also stable and capable. This is regulatory authorities' expectation.

Contribution:

We designed d-heterogeneity index CV data median-MAD charts by cluster-calibrated-stratified-smoothed-bootstrap method. The introducing of ordered cluster  and d-heterogeneity index are the innovation part which solved ND events being OOC problem and provide the stability analysis tool for cleaning process validaiton.

# d-CCSSBU-L, d-CCSSBU-S, and Poisson $u$ Chart Code and Output for Equipment A and B

This repository contains the Quarto file `d_ccssbu_l_and_s_charts_and_poisson_u_chart_code_and_output_EqAB.qmd`, which provides the functions, analyses, and outputs used to construct the d-CCSSBU-L and d-CCSSBU-S charts, select the heterogeneity index $d$, and illustrate the Poisson $u$ chart for microbial bioburden (Mic) data from Equipment A and B.



## How to Use the Quarto File

Open `d_ccssbu_l_and_s_charts_and_poisson_u_chart_code_and_output_EqAB.qmd` and search for the function name corresponding to the required analysis. The five main parts are listed below.

### 1. d-CCSSBU-L Chart Design Algorithm

Search for:

```r
d_ccssbu_l()
```

The `d_ccssbu_l()` function implements the d-CCSSBU-L chart design algorithm for a specified value of $d$. It constructs the location calibration dataset, performs the stratified smoothed bootstrap procedure, estimates the center line and upper control limit, and identifies location-chart OOC events.

### 2. Selection of $d$ for the d-CCSSBU-L Chart

Search for:

```r
d_ccssbu_l_d_selection_arl1()
```

The `d_ccssbu_l_d_selection_arl1()` function applies `d_ccssbu_l()` across all candidate values $d=1,\ldots,q$. It evaluates each candidate using:

- ND events classified as OOC;
- nominal Stage 3A events classified as OOC; and
- ARL$_1$ performance relative to the conventional $\bar{X}$ chart.

The following supporting functions format the results:

```r
make_d_ccssbu_l_arl1_wide_tbl()
render_d_ccssbu_l_arl1_tbl()
render_d_ccssbu_l_recommendation_tbl()
```

- `make_d_ccssbu_l_arl1_wide_tbl()` converts the d-selection output into a wide-format summary table.
- `render_d_ccssbu_l_arl1_tbl()` renders the ARL$_1$ summary table and adjusts it to the available page width.
- `render_d_ccssbu_l_recommendation_tbl()` renders the recommended $d$ table for DAR, CAR, and Mic.

### 3. d-CCSSBU-S Chart Design Algorithm

Search for:

```r
d_ccssbu_s()
```

The `d_ccssbu_s()` function implements the d-CCSSBU-S chart design algorithm for a specified value of $d$. It constructs the scale calibration dataset, performs the stratified smoothed bootstrap procedure, estimates the center line and upper control limit, and identifies scale-chart OOC events.

### 4. Selection of $d$ for the d-CCSSBU-S Chart

Search for:

```r
d_ccssbu_s_d_selection_arl1()
```

The `d_ccssbu_s_d_selection_arl1()` function applies `d_ccssbu_s()` across all candidate values $d=1,\ldots,q$. It evaluates each candidate using:

- ND events classified as OOC;
- nominal Stage 3A events classified as OOC; and
- ARL$_1$ performance relative to the conventional $S$ chart.

The following supporting functions format the results:

```r
make_d_ccssbu_s_arl1_wide_tbl()
render_d_ccssbu_s_arl1_tbl()
render_d_ccssbu_s_recommendation_tbl()
```

- `make_d_ccssbu_s_arl1_wide_tbl()` converts the d-selection output into a wide-format summary table.
- `render_d_ccssbu_s_arl1_tbl()` renders the ARL$_1$ summary table and adjusts it to the available page width.
- `render_d_ccssbu_s_recommendation_tbl()` renders the recommended $d$ table for DAR, CAR, and Mic.

### 5. Poisson $u$ Chart for Mic Data

Search for the following functions:

```r
prepare_mic_data()
poisson_gof_test()
poisson_overdispersion_test()
poisson_mic_u_chart()
```

These functions provide the complete Poisson $u$ chart workflow:

- `prepare_mic_data()` prepares the Mic data for analysis.
- `poisson_gof_test()` evaluates the goodness of fit of the Poisson distribution.
- `poisson_overdispersion_test()` evaluates whether the Mic data exhibit overdispersion relative to the Poisson model.
- `poisson_mic_u_chart()` constructs the Poisson $u$ chart using the prepared data and supporting diagnostic results.

The Poisson assumptions should be evaluated before interpreting the resulting $u$ chart.

## Recommended Workflow

1. Open the Quarto file and load the required packages and input data.
2. Use `d_ccssbu_l()` or `d_ccssbu_s()` to inspect a chart constructed for a specified value of $d$.
3. Use `d_ccssbu_l_d_selection_arl1()` or `d_ccssbu_s_d_selection_arl1()` to evaluate all candidate values of $d$ and select the optimized heterogeneity index.
4. Use the corresponding `make_*` and `render_*` functions to generate the ARL$_1$ and recommendation tables.
5. For Mic data evaluated under a Poisson model, prepare the data, assess goodness of fit and overdispersion, and then construct the Poisson $u$ chart.

## Residue Types

- **DAR:** drug active residue
- **CAR:** cleaning agent residue
- **Mic:** microbial bioburden

## Key Terms

- **ND:** non-detectable
- **OOC:** out-of-control
- **ARL$_1$:** out-of-control average run length
- **$q$:** heterogeneity index of the calibration-eligible dataset
- **$d$:** heterogeneity index of the calibration dataset used to construct the chart
