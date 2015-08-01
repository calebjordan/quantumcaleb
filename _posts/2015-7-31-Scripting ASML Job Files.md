---
layout: post
title: Scripting ASML job files
tags: Fabrication Software
---

The [ASML](asml-stepper.md) is a powerful tool for quickly and accurately exposing wafers. However, the software used to create the job files is a bit cumbersome. Not only do we have to be present at the tool to actually create the job file, it is very common to make mistakes and therefore have to stip, respin, and reexpose your wafer. To try to save some time in the long run as well as some frustration, I'm developing a macro for [KLayout](http://klayout.de) to automatically export job files straight from the editing environment. 

## Importing/Exporting ASCII files

The ASML job file is stored in binary, but the software located on the ASML computer and import/export job files from/to human readable ascii files. 

## Job File Layout

The job file is in three main parts:

* General
This section lists the properties of the wafer such as cell size, cell offset, and cell spacing

```
START_SECTION GENERAL
   COMMENT                                       ""
                                                 ""
                                                 ""
   MACHINE_TYPE                                  "PAS5500/300"
   RETICLE_SIZE                                  6
   WFR_DIAMETER                                  100.000000
   WFR_NOTCH                                     "N"
   CELL_SIZE                                     8.100000 8.100000
   ROUND_EDGE_CLEARANCE                          1.000000
   FLAT_EDGE_CLEARANCE                           0.000000
   EDGE_EXCLUSION                                1.000000
   COVER_MODE                                    "W"
   NUMBER_DIES                                   3 14
   MIN_NUMBER_DIES                               1
   PLACEMENT_MODE                                "O"
   MATRIX_SHIFT                                  4.050000 4.050000
   PREALIGN_METHOD                               "STANDARD"
   WAFER_ROTATION                                0.000000
   COMBINE_ZERO_FIRST                            "N"
   MATCHING_SET_ID                               "DEFAULT"
END_SECTION
```

* Image Definition
Here we define the images on our mask. This consists of a label, mask name, size, and position. 

```
START_SECTION IMAGE_DEFINITION
       IMAGE_ID                                      "CQLEFT"
       RETICLE_ID                                    "QUBITJPMV2"
       IMAGE_SIZE                                    1.260000 0.480000
       IMAGE_SHIFT                                   18.000000 36.000000
       MASK_SIZE                                     1.264000 0.480000
       MASK_SHIFT                                    18.000000 36.000000
       VARIANT_ID                                    ""
    END_SECTION
```

* Instance Definition
Here the instance of each image is defined. If you want to place the same image in a cell more than once, each needs its own definition. The default for an image is "Default". There should be less than and greater than signs around the word Default, but it looks like HTML and screws up the formatting on this page.

* Image Distribution
Here we define which images get placed in what cells, and where.

```
START_SECTION IMAGE_DISTRIBUTION
   IMAGE_ID                                      "CQLEFT"
   INSTANCE_ID                                   "cq_bottom"
   CELL_SELECTION                                "-3" "4"
   DISTRIBUTION_ACTION                           "I"
   OPTIMIZE_ROUTE                                "N"
   IMAGE_CELL_SHIFT                              -0.227500 -1.000000
END_SECTION
```

* Layer Definition
Here is the definition of layers. As of now, we only shoot one layer, so 'AT' works as a placeholder. I'll need to understand how a multilayer job file looks when we get to those.

```
START_SECTION LAYER_DEFINITION
   LAYER_NO                                      0
   LAYER_ID                                      "0"
   WAFER_SIDE                                    "A"
END_SECTION

START_SECTION LAYER_DEFINITION
   LAYER_NO                                      1
   LAYER_ID                                      "AT"
   WAFER_SIDE                                    "A"
END_SECTION
```

* Process Data
I don't know what this does yet, but there's one entry per layer.

```
START_SECTION PROCESS_DATA
   LAYER_ID                                      "AT"
   LENS_REDUCTION                                4
   CALIBRATION                                   "N"
   OPTICAL_PREALIGNMENT                          "N"
   COO_REDUCTION                                 "D"
   MIN_NUMBER_PULSES_IN_SLIT                     "D"
   MIN_NUMBER_PULSES                             21
   SKIP_COARSE_WAFER_ALIGN                       "N"
   REDUCE_RETICLE_ALIGN                          "N"
   REDUCE_RA_DRIFT                               5.000000
   REDUCE_RA_INTERVAL                            2
   RET_COOL_CORR                                 "D"
   RET_COOL_TIME                                 0
   RET_COOL_START_ON_LOAD                        "Y"
   RET_COOL_USAGE                                "W"
   GLBL_OVERLAY_ENHANCEMENT                      "N"
   LAYER_SHIFT                                   0.000000 0.000000
   CORR_INTER_FLD_EXPANSION                      0.000000 0.000000
   CORR_INTER_FLD_NONORTHO                       0.000000
   CORR_INTER_FLD_ROTATION                       0.000000
   CORR_INTER_FLD_TRANSLATION                    0.000000 0.000000
   CORR_INTRA_FLD_MAGNIFICATION                  0.000000
   CORR_INTRA_FLD_ROTATION                       0.000000
   CORR_INTRA_FLD_TRANSLATION                    0.000000 0.000000
   CORR_INTRA_FLD_ASYM_ROTATION                  0.000000
   CORR_INTRA_FLD_ASYM_MAGN                      0.000000
   CORR_PREALIGN_ROTATION                        0.000000
   CORR_PREALIGN_TRANSLATION                     0.000000 0.000000
   CORR_80_88_MARK_SHIFT                         0.000000 0.000000 0.000000 0.000000
   CORR_LENS_HEATING                             1.000000
   NUMERICAL_APERTURE                            -1.000000
   SIGMA_INNER                                   -1.000000
   SIGMA_OUTER                                   -1.000000
   RTCL_CHECK_SURFACES                           "N"
   RTCL_CHECK_LIMITS_UPPER                       50000 50000 50000
   RTCL_CHECK_LIMITS_LOWER                       50000 50000 50000
   CLOSE_GREEN_LASER_SHUTTER                     "N"
   REALIGNMENT_METHOD                            "D"
   IMAGE_ORDER_OPTIMISATION                      "Y"
   RETICLE_ALIGNMENT                             "T"
   USE_DEFAULT_RETICLE_ALIGNMENT_METHOD          "N"
   CRITICAL_PERCENTAGE                           83
   SHARE_LEVEL_INFO                              "N"
   FOCUS_EDGE_CLEARANCE                          3.000000
   INLINE_Q_ABOVE_P_CALIBRATION                  "M"
   SHIFTED_MEASUREMENT_SCANS                     "N"
   FOCUS_MONITORING                              "D"
   FOCUS_MONITORING_SCANNER                      "D"
   DYN_PERF_MONITORING                           "D"
   FORCE_MEANDER_ENABLED                         "N"
END_SECTION
```

* Reticle Data
This contains the exposure parameters for each image. There is one entry for each placement of each image. If we edit this in the job file, we don't have to enter it on the ASML computer, we can just hit 'run' and be done with it.

```
START_SECTION RETICLE_DATA
   LAYER_ID                                      "AT"
   IMAGE_ID                                      "CQLEFT"
   IMAGE_USAGE                                   "Y"
   RETICLE_ID                                    "QUBITJPMV2"
   IMAGE_SIZE                                    1.260000 0.480000
   IMAGE_SHIFT                                   18.000000 36.000000
   MASK_SIZE                                     1.264000 0.480000
   MASK_SHIFT                                    18.000000 36.000000
   ENERGY_ACTUAL                                 150.000000
   FOCUS_ACTUAL                                  0.000000
   FOCUS_TILT                                    0.000000 0.000000
   NUMERICAL_APERTURE                            -1.000000
   SIGMA_INNER                                   -1.000000
   SIGMA_OUTER                                   -1.000000
   IMAGE_EXPOSURE_ORDER                          0
   LITHOGRAPHY_PROCESS                           "Default"
   IMAGE_INTRA_FLD_COR_TRANS                     0.000000 0.000000
   IMAGE_INTRA_FLD_COR_ROT                       0.000000
   IMAGE_INTRA_FLD_COR_MAG                       0.000000
   IMAGE_INTRA_FLD_COR_ASYM_ROT                  0.000000
   IMAGE_INTRA_FLD_COR_ASYM_MAG                  0.000000
   LEVEL_METHOD_Z                                "D"
   LEVEL_METHOD_RX                               "D"
   LEVEL_METHOD_RY                               "D"
   DIE_SIZE_DEPENDENCY                           "N"
   ENABLE_EFESE                                  "N"
   CD_FEC_MODE                                   "N"
   DOSE_CORRECTION                               "N"
   DOSE_CRITICAL_IMAGE                           "Y"
   GLOBAL_LEVEL_POINT_1                          0.000000 0.000000
   GLOBAL_LEVEL_POINT_2                          0.000000 0.000000
   GLOBAL_LEVEL_POINT_3                          0.000000 0.000000
END_SECTION
```
