gemtc 1.0-2
===========

Released 2023-06-21

 * Fix compatibility with latest igraph (1.5.0)
 * Fix covariateEffectPlot on older versions of R

gemtc 1.0-1
===========

Released 2021-05-14

 * Changed reference arm prior for relative risk (binom/log) models as
   the old prior was more informative than intended (issue #64)

gemtc 1.0-0
===========

Released 2021-04-30

 * Removed ability to read legacy ".gemtc" XML files
 * Fixed incompatibility with "tibbles"
 * Fix JAGS warnings that "om.scale" was unused in some models
 * Fix plotCovariateEffect

gemtc 0.8-8
===========

Released 2020-11-29

 * Fix compatibility with latest / upcoming R version

gemtc 0.8-7
===========

Released 2020-08-07

 * Allow setting the standard deviation for the relative effect priors
   explicitly
 * Study names on the key outputs of mtc.deviance for contrast-level
   data (data.re)
 * Add documentation on how to obtain reproducible results
 * More user-friendly messages for common errors

gemtc 0.8-6
===========

Released 2020-06-23

 * Fix automated tests on previous versions of R
 * Add journal article citations to the package description

gemtc 0.8-5
===========

Released 2020-06-20

 * Adapt to breaking changes relating to factor/numeric conversions, get
   package re-instated on CRAN (it was removed 2020-05-29)

gemtc 0.8-4
===========

Released 2020-03-31

 * Adapt to the new stringsAsFactors=FALSE default

getmc 0.8-3
===========

Not released (2018-05-21)

 * Update DOIs to https://dois.org/ resolver
 * Register native code

gemtc 0.8-2
===========

Released 2016-12-23

 * Update maintainer email

gemtc 0.8-1
===========

Released 2016-09-06

New features:

 * mtc.deviance() for convenient access to deviance statistics and
   plots. Additional deviance statistics calculated.

Bugfixes and improvements:

 * Depend on rjags >= 4-0, as JAGS 4 features are being used.
 * Fix node-splitting models with down-weighted studies.
 * Additional sanity checking of input data.
 * More appropriate default limits on plotCovariateEffect.
 * Corrections to atrialFibrillation dataset.

gemtc 0.8
=========

Released 2016-03-01

New features:

 * Network meta-regression using study-level covariates. Shared,
   per-class, exchangeable, or unrelated coefficients.
 * Allow adjusting relative effects and rank probabilities to a specific
   covariate level. Plot treatment effects versus covariate levels.
 * Down-weighting (variance inflation or likelihood adjustment) of
   studies (e.g. for inclusion of lower quality evidence).
 * Add example datasets for new regression features, as well as examples
   for contrast-based data and rate data.
 * Improved model fit diagnostics including per-arm or per-study
   deviance.

Removed features:

 * Removed "write.mtc.network" function to write the deprecated GeMTC
   XML format, as most networks can't be saved in that format anyway.

Bugfixes:

 * Fixed degrees of freedom in ANOHE I^2 computations.

gemtc 0.7-1
===========

Released 2015-10-12

 * Update for compatibility with JAGS 4.0

gemtc 0.7
=========

Released 2015-09-09

Removed features:

 * Support for WinBUGS and OpenBUGS was removed due to their various
   problems (lack of portability, lack of support for selecting blocks
   from arrays, bugs in setting monitors, and the constant need to track
   minor differences in syntax between JAGS and BUGS).

New features:

 * Added binom/log (risk ratio) support.
 * Ability to generate n * n relative effects table, and to generate
   plots directly from the table, bypassing the time-consuming
   computation of the quantiles.
 * Added residual deviance statistics (replaces and improves upon the
   DIC previously computed by JAGS).
 * Example datasets are now standard R data, and can be accessed using
   the variables `depression', `parkinson', `thrombolytic', and
   `smoking'.

Enhancements:

 * Forest plots: allow treatment descriptions to be displayed instead of
   IDs.
 * Network plot: make proportional line width optional.
 * Additional validations to catch obvious data entry mistakes.
 * Better safeguards for starting values, and alternative approach to
   baseline priors for scales without infinite support.
 * The XML package is no longer required to install gemtc, and will be
   loaded only if needed to read/write legacy .gemtc XML files.

gemtc 0.6-2
===========

Released 2015-04-18

New features:

 * Network plot: line width is now proportional to the number of
   studies.

Enhancements:

 * Forest plots: new options 'draw.no.effect' and 'center.label'. See
   ?blobbogram for documentation.
 * Better validation of network properties and more helpful reporting of
   validation failures.
 * Prevent zero prior heterogeneity variance (because it causes JAGS
   errors).
 * Clear error when asked to parse non-existant XML file.

gemtc 0.6-1
===========

Released 2014-12-12

Enhancements:

 * Use the '.Call' interface for C code
 * Better detect invalid treatment names
 * Better detect the likelihood / link

Bugfixes:

 * Fix node-splitting models in sparse networks (#31)

gemtc 0.6
=========

Released 2014-03-11

New features:

 * Customizable prior distribution for heterogeneity. The prior can be
   set on the standard deviation, variance, or precision. It can use any
   distribution supported by BUGS/JAGS. Informative priors for the log
   odds ratio (based on Turner et al. 2012) are also available.
 * Variance of the vague normal distributions for all other parameters
   can be controlled using 'om.scale'. By default it is still
   heuristically determined.
 * Change handling of 4+-arm trials in node-splitting models and ANOHE
   summary
 * Enable linearModel='fixed' for mtc.anohe()
 * Add literature references for various methods to gemtc-package
 * Add mtc.data.studyrow() to convert the one-study-per-row format often
   used in BUGS models to the one-arm-per-row format used by GeMTC

Enhancements:

 * Upgrade unit testing infrastructure to testthat >= 0.8
 * Move validation tests into testthat infrastructure
 * Add regression test suite that tries all summaries and plots on all
   models to check whether they crash.
 * General clean up of example and test data files

Known issues:

 * Models with relative-effect data from trials with 4 or more arms
   can't be run using WinBUGS or OpenBUGS (#28). This seems to be due to
   a BUGS-bug. A warning is produced, saying to use JAGS instead.

Bugfixes:

 * Fix empty first page on PDF output of some plots (#12)
 * Fix ordering of generated data / initial values in models for
   relative effect data (#21)
 * Fix generating node-splitting models for relative effect data (#22)
 * Fix mtc.nodesplit.comparisons getting confused when both relative
   effect and arm-based data are present (#25)
 * Fix duplicated parameters in UME models (#26)

gemtc 0.5-3
===========

Released 2013-02-08

 * Fix incompatibility with igraph 0.7
 * Fix node-splitting model generation bug

gemtc 0.5-2
===========

Released 2013-12-02

 * Remove Matrix dependency by not using the Matrix-dependent parts of
   igraph.
 * Correctly use C99 "inline" facility

gemtc 0.5-1
===========

Released 2013-10-30

Improvements:

 * Converted several plots to use the standard R mechanism of asking for
   the next page, rather than our own hack.
 * The plot() for the summary() of mtc.anohe() now has a nicer default
   scale range.
 * Import Matrix package because of igraph changes.

Bugfixes:

 * mtc.anohe() mixed up treatments or studies in some extraordinary
   circumstances, due to automatic conversions to/from factor.
 * blobbogram() would crash when it could not find reasonable scales and
   none were specified.
 * blobbogram() created an empty first page when plotting to off-screen
   devices.
 * mtc.anohe() called sd() on a matrix, which is deprecated.
 * mtc.nodesplit() used "A vs B" for d.A.B instead of "B vs A" like the
   other plots.

gemtc 0.5
===========

Released 2013-09-24

New features:

 * node-splitting models
 * mtc.nodesplit() wrapper to run multiple node-splitting models
 * calculate DIC model fit (JAGS only)
 * add preferredDirection to rank.probability()
 * default plot() for rank.probability()

gemtc 0.4
===========

Released 2013-08-09

New features:

 * fixed effect models
 * poisson/log likelihood/link for survival data
 * allow std.err instead of std.dev + sampleSize in continuous data sets

Changes:

 * refuse to generate models when treatments are duplicated in
   multiple arms of the same study, since the code does not take this
   into account.
 * network$data is now network$data.ab for consistency with
   network$data.re
 * likelihood/link implementations can now define their data
   requirements
 * export ll.call for programmatic access to likelihood/link specific
   functions

Bugfixes:

 * multi-arm trial decomposition sometimes resulted in NA standard
   errors
 * WinBUGS and OpenBUGS had complaints about the relative effect code
 * safer matrix indexing: explicit 'drop='
 * safer data frame indexing: use [['x']] instead of $x

gemtc 0.3
===========

Released 2013-07-16

Many additional features:

 * support for relative effect data
 * support for mixed arm-based and relative effect data
 * binom/cloglog likelihood/link for rate data
 * unrelated mean effects (UME) model
 * unrelated study effects (USE) model
 * analysis of heterogeneity with heterogeneity plot (EXPERIMENTAL)
 * full access to generated code, data structures, and parameters
 * guard against "impossible" initial values

Also, bugfixes and documentation updates.

gemtc 0.2
===========

Released 2013-02-18

Dropped Java dependency by rewriting core algorithms in R. 

 * Remove dependency on rJava
 * Use own forest plot methods instead of meta package
 * Fix bug in rank.probabilities when only two treatments in network
 * Various bugfixes
 * Compatibility note: inconsistency models are no longer supported by
   this package
 * Compatibility note: the argument order of mtc.network has changed
 * Compatibility note: the YADAS sampler is no longer available

gemtc 0.1-2
===========

Released 2013-01-21

Bugfix release. Addresses the following issues: 

 * Correct the initial values generation for the random effects standard
   deviation parameter
 * Do not fail on relative.effect when saving and loading samples
 * Make Java open tab-completed paths
 * Use correct column name for continuous data
 * When only YADAS available, run YADAS by default

gemtc 0.1-1
===========

Released 2012-10-30

 * Fix compatibility issue with Java on 32bit Mac OS X. 

gemtc 0.1
===========

Released 2012-10-25

First official release of the GeMTC R package. The  package enables
Bayesian network meta-analysis (also known as MTC, Mixed Treatment
Comparisons) in R. Network meta-analysis models can be generated and
then run using MCMC software: JAGS (using the rjags package), OpenBUGS
(using the BRugs package), WinBUGS (using the R2WinBUGS package) or
YADAS (provided by GeMTC). The GeMTC GUI can be used instead of or in
conjunction with the R package.
