## An Eddy-Zonal Flow Feedback Model for Propagating Annular Modes (Lubis and Hassanzadeh, 2021)

We introduce a reduced-order model for coupled EOF1 and EOF2 that accounts for potential cross-EOF eddy-zonal flow feedbacks in the propagating annular mode (PAM). Using the analytical solution of this model, we derive conditions for the existence of the propagating regime based on the feedback strengths. The detail of the model can be found from (see Section 3):

Lubis, S. W., & Hassanzadeh, P. (2021). An Eddy–Zonal Flow Feedback Model for Propagating Annular Modes, Journal of the Atmospheric Sciences, 78(1), 249-267. [link](https://journals.ametsoc.org/view/journals/atsc/78/1/jas-d-20-0214.1.xml)

1. Data folder includes the netcdf files of vertically averaged zonal mean zonal wind (u.col.anom.erainterim.nc) and vertically averaged eddy momentum flux convergence (duepy.col.anom.erainterim.nc), from ERA-Interim with the period of 1979-2013.

2. cal_cross_eof_feedbacks.ncl includes the codes to calculate single-EOF feedbacks (<img src="https://render.githubusercontent.com/render/math?math=b_{11}"> and <img src="https://render.githubusercontent.com/render/math?math=b_{22}">) and cross-EOF feedbacks (<img src="https://render.githubusercontent.com/render/math?math=b_{12}"> and <img src="https://render.githubusercontent.com/render/math?math=b_{21}">) from Eqs. (9) and (10) in Lubis and Hassanzadeh (2021).

3. cal_cross_eof_feedbacks.ncl also includes the codes to calculate the periodicity (frequency) and decay time scale of the annular modes from the theory (see Eqs. (23) and (24) in Lubis and Hassanzadeh (2021)).

4. cal_one_point_lag_correlation_map.ncl includes the codes to calculate one-point lag-correlation maps of the vertically averaged zonal-mean zonal wind anomalies reconstructed from projections onto two leading EOFs.


<p align="center">
  <img src="https://github.com/sandrolubis/Cross-EOF-Eddy-Feedback-Model/blob/main/example/one_point_lag_correlation_map.png" width="500">
</p>

5. cal_tau_LH01.ncl includes the codes to calculate damping time scale following Appendix A, Lorenz and Hartmann (2001).

6. cal_cross_spectrum_LH01.ncl includes the codes to calculate cross-spectrum following Lorenz and Hartmann (2001).

7. cal_cross_mz.ncl includes the codes to calculate autocorrelation between z1 and z2 and cross-correlations between m and z.


<p align="center">
  <img src="https://github.com/sandrolubis/Cross-EOF-Eddy-Feedback-Model/blob/main/example/ccr_erainterim_full_grid.png" width="500">
</p>

[**Caption**] Lagged-correlation analysis for the Southern Hemisphere, calculated from year-round ERA-Interim data. (a) Autocorrelations of z1(blue) and z2(red), (b) cross-correlation z1 z2, (c) cross-correlation m1 z1, (d) cross-correlation m2 z2, (e) cross-correlation m1 z2, and (f) cross-correlation m2 z1 at different lags. The two leading EOFs contribute to 45.1% and 23.2% of the total variance, respectively. The e-folding decorrelation time scales of z1 and z2 are 10.3 and 8.1 days, respectively. Gray shading represents 5% significance level according to the test of Bartlett.

## The basic assumptions of the model:
1. A linear representation of the feedbacks is sufficient
2. The eddy forcing <img src="https://render.githubusercontent.com/render/math?math=m"> does not have long-term memory independent of the variability in the jet (represented by <img src="https://render.githubusercontent.com/render/math?math=z_1"> and <img src="https://render.githubusercontent.com/render/math?math=z_2">)

The second assumption means that at sufficiently large positive lags (beyond the timescales over which there is significant autocorrelation in <img src="https://render.githubusercontent.com/render/math?math=\tilde{m}">) the feedback component of the eddy forcing will dominate the <img src="https://render.githubusercontent.com/render/math?math=m_jz_k"> cross correlations, i.e., <img src="https://render.githubusercontent.com/render/math?math=reg_l(\tilde{m}_j,z_k) \approx 0"> at "large-enough" positive lags. Note that one cannot use a lag that is too long because then <img src="https://render.githubusercontent.com/render/math?math=reg_l(z_j,z_j)"> would be small and inaccurate. To find the appropriate lag to use, one must look for nonzero <img src="https://render.githubusercontent.com/render/math?math=m_jz_k"> cross correlations at positive lags beyond an eddy lifetime. Here, the strengths of the individual feedbacks are averaged over positive lags of 7–14 days using ERA-Interim data.
