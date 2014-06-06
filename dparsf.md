---
layout: page
title: dparsf
---

# The preprocessing in DPARSF

**Data Processing Assistant for Resting-State fMRI (DPARSF) is a convenient plug-in software based on SPM and REST.**

All volume slices were corrected for different signal acquisition times by shifting the signal measured in each slice relative to the acquisition of the slice at the mid-point of each TR. Then, the time series of images for each subject were realigned using a six-parameter (rigid body) linear transformation with a two-pass procedure (registered to the first image and then registered to the mean of the images after the first realignment). Individual structural images (T1-weighted MPRAGE) were co-registered to the mean functional image after realignment using a 6 degrees-of-freedom linear transformation without re-sampling. The transformed structural images were then segmented into grey matter (GM), white matter (WM) and cerebrospinal fluid (CSF) (Ashburner and Friston, 2005)[^1]. The Diffeomorphic Anatomical Registration Through Exponentiated Lie algebra (DARTEL) tool (Ashburner, 2007)[^2] was used to compute transformations from individual native space to MNI space.

Recent work has demonstrated that “micro” head pmovements, as small as 0.1mm between time points, can introduce systematic artifactual inter-individual and inter-group variability in R-fMRI measures (Power et al., 2012a, b; Satterthwaite et al., 2012; Van Dijk et al., 2012)[^5]'[^6]'[^9]'[^10]. Here we utilized the Friston 24-parameter model (Friston et al., 1996)[^3] to regress out head motion effects from the realigned data (i.e., 6 head motion parameters, 6 head motion parameters one time point before, and the 12 corresponding squared items) based on recent reports that higher-order models demonstrate benefits in removing head motion effects (Satterthwaite et al., 2013; Yan et al., 2013)[^8]'[^12]. The signals from WM and CSF (standard masks warped back form MNI space to native space) were regressed out to reduce respiratory and cardiac effects. In addition, linear and quadratic trends were also included as regressors since the blood oxygen level dependent (BOLD) signal demonstrates low-frequency drifts. 

Global signal regression (GSR), a commonly used yet controversial practice in the R-fMRI field, yields substantial increases in negative correlations (Murphy et al., 2009; Weissenbacher et al., 2009)[^4]'[^11] and may distort group differences in intrinsic functional connectivity (iFC) (Saad et al., 2012)[^7]. We performed the preprocessing for both with and without GSR.

Temporal filtering (0.01 - 0.1 Hz) was then performed on the time series except for the frequency-based R-fMRI indices: amplitude of low frequency.

Most of the indices were calculated in native space based upon the preprocessed timeseries, and corresponding maps were then registered into MNI space with XX mm3 cubic voxels by using transformation information acquired from DARTEL. The maps were further smoothed by a kernel of XX mm. 

ReHo and DC were directly calculated in MNI space to ensure the same voxel size across sites in ReHo and DC calculation. Spatial maps of these measures were then spatially smoothed with the same Gaussian filter.

VMHC requires that data are first registered in MNI space and smoothed. For better correspondence between symmetric voxels, the individual structural image was reregistered to a group averaged symmetric template (all normalized T1 images were averaged to create a mean normalized T1 image, and then this image was averaged with its left–right mirrored version), and then this refined transformation was applied to the functional data before VMHC calculation (Zuo et al., 2010)[^13]. 

##References

[^1]: Ashburner, J., 2007. A fast diffeomorphic image registration algorithm. Neuroimage 38, 95-113.
[^2]: Ashburner, J., Friston, K.J., 2005. Unified segmentation. Neuroimage 26, 839-851.
[^3]: Friston, K.J., Williams, S., Howard, R., Frackowiak, R.S., Turner, R., 1996. Movement-related effects in fMRI time-series. Magn Reson Med 35, 346-355.
[^4]: Murphy, K., Birn, R.M., Handwerker, D.A., Jones, T.B., Bandettini, P.A., 2009. The impact of global signal regression on resting state correlations: are anti-correlated networks introduced? Neuroimage 44, 893-905.
[^5]: Power, J.D., Barnes, K.A., Snyder, A.Z., Schlaggar, B.L., Petersen, S.E., 2012a. Spurious but systematic correlations in functional connectivity MRI networks arise from subject motion. Neuroimage 59, 2142-2154.
[^6]: Power, J.D., Barnes, K.A., Snyder, A.Z., Schlaggar, B.L., Petersen, S.E., 2012b. Steps toward optimizing motion artifact removal in functional connectivity MRI; a reply to Carp. Neuroimage.
[^7]: Saad, Z.S., Gotts, S.J., Murphy, K., Chen, G., Jo, H.J., Martin, A., Cox, R.W., 2012. Trouble at rest: how correlation patterns and group differences become distorted after global signal regression. Brain Connect 2, 25-32.
[^8]: Satterthwaite, T.D., Elliott, M.A., Gerraty, R.T., Ruparel, K., Loughead, J., Calkins, M.E., Eickhoff, S.B., Hakonarson, H., Gur, R.C., Gur, R.E., Wolf, D.H., 2013. An improved framework for confound regression and filtering for control of motion artifact in the preprocessing of resting-state functional connectivity data. Neuroimage 64, 240-256.
[^9]: Satterthwaite, T.D., Wolf, D.H., Loughead, J., Ruparel, K., Elliott, M.A., Hakonarson, H., Gur, R.C., Gur, R.E., 2012. Impact of in-scanner head motion on multiple measures of functional connectivity: Relevance for studies of neurodevelopment in youth. Neuroimage 60, 623-632.
[^10]: Van Dijk, K.R., Sabuncu, M.R., Buckner, R.L., 2012. The influence of head motion on intrinsic functional connectivity MRI. Neuroimage 59, 431-438.
[^11]: Weissenbacher, A., Kasess, C., Gerstl, F., Lanzenberger, R., Moser, E., Windischberger, C., 2009. Correlations and anticorrelations in resting-state functional connectivity MRI: a quantitative comparison of preprocessing strategies. Neuroimage 47, 1408-1416.
[^12]: Yan, C.G., Cheung, B., Kelly, C., Colcombe, S., Craddock, R.C., Di Martino, A., Li, Q., Zuo, X.N., Castellanos, F.X., Milham, M.P., 2013. A comprehensive assessment of regional variation in the impact of head micromovements on functional connectomics. Neuroimage 76, 183-201.
[^13]: Zuo, X.N., Kelly, C., Di Martino, A., Mennes, M., Margulies, D.S., Bangaru, S., Grzadzinski, R., Evans, A.C., Zang, Y.F., Castellanos, F.X., Milham, M.P., 2010. Growing together and growing apart: regional and sex differences in the lifespan developmental trajectories of functional homotopy. J Neurosci 30, 15034-15043.
