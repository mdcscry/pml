---
title: "Movement Prediction Model based on gyroscopic sensors."
author: "Matthew Cryer"
date: "Saturday, April 25, 2015"
output: html_document
---

Movement Prediction Model based on gyroscopic sensors.

I've utilized a standard random forest model with bootstrapping for cross-validation.

I used 43 of the metrics.  I eliminated all metrics with mostly NAs.  I also standardized the various gyro metrics.
They were centered about the axis with mean 0 but spread far.  I saw these as indicators.  I decoded these to 1 or 0.
I played around with pca but couldn't find the answer.

You can see that the model achieved 94 percent accuracy. I missed #18.  


### Data Preparation


```
##       num_window roll_belt pitch_belt yaw_belt total_accel_belt
## 17444        169       129       9.61       56               17
##       gyros_belt_x gyros_belt_y gyros_belt_z accel_belt_x accel_belt_y
## 17444            0            1            0          -19           62
##       accel_belt_z magnet_belt_x magnet_belt_y magnet_belt_z roll_arm
## 17444         -150            27           617          -287    -80.1
##       pitch_arm yaw_arm total_accel_arm gyros_arm_x gyros_arm_y
## 17444       -18    35.3              34           1           0
##       gyros_arm_z accel_arm_x accel_arm_y accel_arm_z magnet_arm_x
## 17444           1         142        -157        -261          589
##       magnet_arm_y magnet_arm_z roll_dumbbell pitch_dumbbell yaw_dumbbell
## 17444         -151         -332      114.9687       41.76528     5.072376
##       total_accel_dumbell gyros_dumbbell_x gyros_dumbbell_y
## 17444                   2                1                0
##       gyros_dumbbell_z accel_dumbbell_x accel_dumbbell_y accel_dumbbell_z
## 17444                0                8               18                1
##       magnet_dumbbell_x magnet_dumbbell_y magnet_dumbbell_z roll_forearm
## 17444              -249               563                28        -72.2
##       pitch_forearm yaw_forearm gyros_forearm_x gyros_forearm_y
## 17444         -14.3         175               1               0
##       gyros_forearm_z accel_forearm_x accel_forearm_y accel_forearm_z
## 17444               0            -382            -412             -46
##       magnet_forearm_x magnet_forearm_y Classe
## 17444             -268             -538      E
```

```
##   num_window roll_belt pitch_belt yaw_belt total_accel_belt gyros_belt_x
## 1         74       123         27    -4.75               20            0
##   gyros_belt_y gyros_belt_z accel_belt_x accel_belt_y accel_belt_z
## 1            0            0          -38           69         -179
##   magnet_belt_x magnet_belt_y magnet_belt_z roll_arm pitch_arm yaw_arm
## 1           -13           581          -382     40.7     -27.8     178
##   total_accel_arm gyros_arm_x gyros_arm_y gyros_arm_z accel_arm_x
## 1              10           0           1           0          16
##   accel_arm_y accel_arm_z magnet_arm_x magnet_arm_y magnet_arm_z
## 1          38          93         -326          385          481
##   roll_dumbbell pitch_dumbbell yaw_dumbbell total_accel_dumbell
## 1     -17.73748       24.96085      126.236                   9
##   gyros_dumbbell_x gyros_dumbbell_y gyros_dumbbell_z accel_dumbbell_x
## 1                1                1                0               21
##   accel_dumbbell_y accel_dumbbell_z magnet_dumbbell_x magnet_dumbbell_y
## 1              -15               81               523              -528
##   magnet_dumbbell_z roll_forearm pitch_forearm yaw_forearm gyros_forearm_x
## 1               -56          141          49.3         156               1
##   gyros_forearm_y gyros_forearm_z accel_forearm_x accel_forearm_y
## 1               0               0            -110             267
##   accel_forearm_z magnet_forearm_x magnet_forearm_y
## 1            -149             -714              419
```
knit2html("PA1_template.Rmd","PA1_template.html")

