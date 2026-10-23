# Logical T-state preparation: Figure 4 data

Numerical data for Figure 4 of the manuscript *A Resource Comparison of Logical T-State Preparation*, by Jianshuo Gao, Xiao Yuan, and Yuan Yao.

[`Fig4_plot_data.csv`](Fig4_plot_data.csv) contains 3 highlighted profiles and 1,724 scan records: 1,240 distillation parameter triples, 402 cultivation thresholds, and 82 code-switching settings. The numerical values are the saved inputs to the figure, before rounding for the printed tables. The `role` column distinguishes highlighted profiles from scan records. A configuration can appear in both roles; the selected distillation values were also checked at higher precision.

## Columns

| Column | Meaning |
| --- | --- |
| `id`, `protocol`, `role` | Configuration identifier, protocol family, and figure role |
| `p_phys` | Reference physical error rate, 0.001 |
| `d_X`, `d_Z`, `d_m` | Distillation parameters |
| `d_1`, `d_2`, `final_rounds`, `gap_min` | Cultivation parameters and minimum rounded gap |
| `schedule`, `eta` | Code-switching schedule and idle-noise scale |
| `error_or_bound` | Error coordinate; its interpretation is given by `error_kind` |
| `Q_peak` | Peak qubit count |
| `D_over_tau0` | Duration in units of the reference layer time |
| `P_acc` | Preparation acceptance |
| `mean_V_qubit_tau0` | Mean attempt cost in qubit-layer-time units |
| `C_qubit_tau0` | Preparation cost per accepted output in the same units |
| `*_interval_lower`, `*_interval_upper` | Endpoints of the plotted cultivation intervals |
| `error_is_approximate` | Whether the error is a published approximation |
| `source_schedule_condition` | Whether the distillation parameters satisfy the source scheduling condition |
| `missing_coordinates` | Coordinates with no available value |
| `source_reference`, `notes` | Source and interpretation notes |

Empty numerical cells mean unavailable values. In particular, 215 cultivation thresholds have zero accepted samples: their acceptance is zero, while their error and cost per accepted output are unspecified.

Of the distillation scan records, 296 lie outside the source condition `d_X <= 3*d_m`. These are evaluations of the analytical formulae; their costs require a separately justified schedule.

The highlighted code-switching error is the published approximate ED-tomography result. Its preparation resources were reconstructed separately and exclude terminal ED selection. They do not give the cost of retained states at that error. The code-switching scans use EC tomography.

The cultivation scan error coordinate is twice a simultaneous upper bound from S-state samples, conditional on `epsilon_T <= 2*epsilon_S`. The highlighted cultivation profile instead uses direct T-state samples. Its four plotted intervals have at least 95% joint coverage under the model described in the manuscript.

## Plot coordinates

Figure 4 uses the following fixed axes. Costs use the units defined above.

| CSV column | Lower limit | Upper limit | Scale | Angle |
| --- | ---: | ---: | --- | ---: |
| `error_or_bound` | 1e-8 | 1 | logarithmic | 90 degrees |
| `Q_peak` | 10 | 1e5 | logarithmic | 30 degrees |
| `D_over_tau0` | 50 | 2000 | logarithmic | -30 degrees |
| `P_acc` | 0 | 1 | linear | -90 degrees |
| `mean_V_qubit_tau0` | 1e3 | 1e8 | logarithmic | -150 degrees |
| `C_qubit_tau0` | 1e3 | 1e9 | logarithmic | 150 degrees |

For limits `a, b`, use `f = (x-a)/(b-a)` on the linear axis and `f = log(x/a)/log(b/a)` on logarithmic axes. The radius is `0.30 + 0.70*f` for acceptance and `0.30 + 0.70*(1-f)` for the other axes. Convert each radius and angle to Cartesian coordinates and connect adjacent available coordinates within a record. Missing coordinates break the path. The highlighted profiles and their intervals are drawn over the scan curves; the error inset repeats the highlighted errors and cultivation error interval.

Appendix B of the manuscript gives the noise, timing, allocation, postselection, and terminal-diagnostic conventions. Figure 3 uses a separate literature dataset, tabulated in Appendix C, Table III.
