Codebook
========

Variable list and descriptions
------------------------------

Variable name    | Description
-----------------|------------
activityName     | Activity name
subject          | ID the subject who performed the activity for each window sample. Its range is from 1 to 30.
activityNum      | Activity number   

The remaining columns are described as follows:

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag

The set of variables that were estimated from these signals are: 

mean(): Mean value
std(): Standard deviation

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean
tBodyAccMean
tBodyAccJerkMean
tBodyGyroMean
tBodyGyroJerkMean



featDomain       | Feature: Time domain signal or frequency domain signal (Time or Freq)
featInstrument   | Feature: Measuring instrument (Accelerometer or Gyroscope)
featAcceleration | Feature: Acceleration signal (Body or Gravity)
featVariable     | Feature: Variable (Mean or SD)
featJerk         | Feature: Jerk signal
featMagnitude    | Feature: Magnitude of the signals calculated using the Euclidean norm
featAxis         | Feature: 3-axial signals in the X, Y and Z directions (X, Y, or Z)
featCount        | Feature: Count of data points used to compute `average`
featAverage      | Feature: Average of each variable for each activity and each subject


Dataset structure
-----------------

```r
str(dfSummaryData)
```

```
# Classes ‘grouped_df’, ‘tbl_df’, ‘tbl’ and 'data.frame':	180 obs. of  69 variables:
#  $ activityName                  : Factor w/ 6 levels "LAYING","SITTING",..: 1 1 1 1 1 1 1 1 1 1 ...
#  $ subject                       : int  1 2 3 4 5 6 7 8 9 10 ...
#  $ activityNum                   : num  6 6 6 6 6 6 6 6 6 6 ...
#  $ tBodyAcc_mean_X_mean          : num  0.222 0.281 0.276 0.264 0.278 ...
#  $ tBodyAcc_mean_Y_mean          : num  -0.0405 -0.0182 -0.019 -0.015 -0.0183 ...
#  $ tBodyAcc_mean_Z_mean          : num  -0.113 -0.107 -0.101 -0.111 -0.108 ...
#  $ tBodyAcc_std_X_mean           : num  -0.928 -0.974 -0.983 -0.954 -0.966 ...
#  $ tBodyAcc_std_Y_mean           : num  -0.837 -0.98 -0.962 -0.942 -0.969 ...
#  $ tBodyAcc_std_Z_mean           : num  -0.826 -0.984 -0.964 -0.963 -0.969 ...
#  $ tGravityAcc_mean_X_mean       : num  -0.249 -0.51 -0.242 -0.421 -0.483 ...
#  $ tGravityAcc_mean_Y_mean       : num  0.706 0.753 0.837 0.915 0.955 ...
#  $ tGravityAcc_mean_Z_mean       : num  0.446 0.647 0.489 0.342 0.264 ...
#  $ tGravityAcc_std_X_mean        : num  -0.897 -0.959 -0.983 -0.921 -0.946 ...
#  $ tGravityAcc_std_Y_mean        : num  -0.908 -0.988 -0.981 -0.97 -0.986 ...
#  $ tGravityAcc_std_Z_mean        : num  -0.852 -0.984 -0.965 -0.976 -0.977 ...
#  $ tBodyAccJerk_mean_X_mean      : num  0.0811 0.0826 0.077 0.0934 0.0848 ...
#  $ tBodyAccJerk_mean_Y_mean      : num  0.00384 0.01225 0.0138 0.00693 0.00747 ...
#  $ tBodyAccJerk_mean_Z_mean      : num  0.01083 -0.0018 -0.00436 -0.00641 -0.00304 ...
#  $ tBodyAccJerk_std_X_mean       : num  -0.958 -0.986 -0.981 -0.978 -0.983 ...
#  $ tBodyAccJerk_std_Y_mean       : num  -0.924 -0.983 -0.969 -0.942 -0.965 ...
#  $ tBodyAccJerk_std_Z_mean       : num  -0.955 -0.988 -0.982 -0.979 -0.985 ...
#  $ tBodyGyro_mean_X_mean         : num  -0.01655 -0.01848 -0.02082 -0.00923 -0.02189 ...
#  $ tBodyGyro_mean_Y_mean         : num  -0.0645 -0.1118 -0.0719 -0.093 -0.0799 ...
#  $ tBodyGyro_mean_Z_mean         : num  0.149 0.145 0.138 0.17 0.16 ...
#  $ tBodyGyro_std_X_mean          : num  -0.874 -0.988 -0.975 -0.973 -0.979 ...
#  $ tBodyGyro_std_Y_mean          : num  -0.951 -0.982 -0.977 -0.961 -0.977 ...
#  $ tBodyGyro_std_Z_mean          : num  -0.908 -0.96 -0.964 -0.962 -0.961 ...
#  $ tBodyGyroJerk_mean_X_mean     : num  -0.107 -0.102 -0.1 -0.105 -0.102 ...
#  $ tBodyGyroJerk_mean_Y_mean     : num  -0.0415 -0.0359 -0.039 -0.0381 -0.0404 ...
#  $ tBodyGyroJerk_mean_Z_mean     : num  -0.0741 -0.0702 -0.0687 -0.0712 -0.0708 ...
#  $ tBodyGyroJerk_std_X_mean      : num  -0.919 -0.993 -0.98 -0.975 -0.983 ...
#  $ tBodyGyroJerk_std_Y_mean      : num  -0.968 -0.99 -0.987 -0.987 -0.984 ...
#  $ tBodyGyroJerk_std_Z_mean      : num  -0.958 -0.988 -0.983 -0.984 -0.99 ...
#  $ tBodyAccMag_mean_mean         : num  -0.842 -0.977 -0.973 -0.955 -0.967 ...
#  $ tBodyAccMag_std_mean          : num  -0.795 -0.973 -0.964 -0.931 -0.959 ...
#  $ tGravityAccMag_mean_mean      : num  -0.842 -0.977 -0.973 -0.955 -0.967 ...
#  $ tGravityAccMag_std_mean       : num  -0.795 -0.973 -0.964 -0.931 -0.959 ...
#  $ tBodyAccJerkMag_mean_mean     : num  -0.954 -0.988 -0.979 -0.97 -0.98 ...
#  $ tBodyAccJerkMag_std_mean      : num  -0.928 -0.986 -0.976 -0.961 -0.977 ...
#  $ tBodyGyroMag_mean_mean        : num  -0.875 -0.95 -0.952 -0.93 -0.947 ...
#  $ tBodyGyroMag_std_mean         : num  -0.819 -0.961 -0.954 -0.947 -0.958 ...
#  $ tBodyGyroJerkMag_mean_mean    : num  -0.963 -0.992 -0.987 -0.985 -0.986 ...
#  $ tBodyGyroJerkMag_std_mean     : num  -0.936 -0.99 -0.983 -0.983 -0.984 ...
#  $ fBodyAcc_mean_X_mean          : num  -0.939 -0.977 -0.981 -0.959 -0.969 ...
#  $ fBodyAcc_mean_Y_mean          : num  -0.867 -0.98 -0.961 -0.939 -0.965 ...
#  $ fBodyAcc_mean_Z_mean          : num  -0.883 -0.984 -0.968 -0.968 -0.977 ...
#  $ fBodyAcc_std_X_mean           : num  -0.924 -0.973 -0.984 -0.952 -0.965 ...
#  $ fBodyAcc_std_Y_mean           : num  -0.834 -0.981 -0.964 -0.946 -0.973 ...
#  $ fBodyAcc_std_Z_mean           : num  -0.813 -0.985 -0.963 -0.962 -0.966 ...
#  $ fBodyAccJerk_mean_X_mean      : num  -0.957 -0.986 -0.981 -0.979 -0.983 ...
#  $ fBodyAccJerk_mean_Y_mean      : num  -0.922 -0.983 -0.969 -0.944 -0.965 ...
#  $ fBodyAccJerk_mean_Z_mean      : num  -0.948 -0.986 -0.979 -0.975 -0.983 ...
#  $ fBodyAccJerk_std_X_mean       : num  -0.964 -0.987 -0.983 -0.98 -0.986 ...
#  $ fBodyAccJerk_std_Y_mean       : num  -0.932 -0.985 -0.971 -0.944 -0.966 ...
#  $ fBodyAccJerk_std_Z_mean       : num  -0.961 -0.989 -0.984 -0.98 -0.986 ...
#  $ fBodyGyro_mean_X_mean         : num  -0.85 -0.986 -0.97 -0.967 -0.976 ...
#  $ fBodyGyro_mean_Y_mean         : num  -0.952 -0.983 -0.978 -0.972 -0.978 ...
#  $ fBodyGyro_mean_Z_mean         : num  -0.909 -0.963 -0.962 -0.961 -0.963 ...
#  $ fBodyGyro_std_X_mean          : num  -0.882 -0.989 -0.976 -0.975 -0.981 ...
#  $ fBodyGyro_std_Y_mean          : num  -0.951 -0.982 -0.977 -0.956 -0.977 ...
#  $ fBodyGyro_std_Z_mean          : num  -0.917 -0.963 -0.967 -0.966 -0.963 ...
#  $ fBodyAccMag_mean_mean         : num  -0.862 -0.975 -0.966 -0.939 -0.962 ...
#  $ fBodyAccMag_std_mean          : num  -0.798 -0.975 -0.968 -0.937 -0.963 ...
#  $ fBodyBodyAccJerkMag_mean_mean : num  -0.933 -0.985 -0.976 -0.962 -0.977 ...
#  $ fBodyBodyAccJerkMag_std_mean  : num  -0.922 -0.985 -0.975 -0.958 -0.976 ...
#  $ fBodyBodyGyroMag_mean_mean    : num  -0.862 -0.972 -0.965 -0.962 -0.968 ...
#  $ fBodyBodyGyroMag_std_mean     : num  -0.824 -0.961 -0.955 -0.947 -0.959 ...
#  $ fBodyBodyGyroJerkMag_mean_mean: num  -0.942 -0.99 -0.984 -0.984 -0.985 ...
#  $ fBodyBodyGyroJerkMag_std_mean : num  -0.933 -0.989 -0.983 -0.983 -0.983 ...
#  - attr(*, "vars")= chr "activityName"
#  - attr(*, "drop")= logi TRUE
#  - attr(*, "indices")=List of 6
#   ..$ : int  0 1 2 3 4 5 6 7 8 9 ...
#   ..$ : int  30 31 32 33 34 35 36 37 38 39 ...
#   ..$ : int  60 61 62 63 64 65 66 67 68 69 ...
#   ..$ : int  90 91 92 93 94 95 96 97 98 99 ...
#   ..$ : int  120 121 122 123 124 125 126 127 128 129 ...
#   ..$ : int  150 151 152 153 154 155 156 157 158 159 ...
#  - attr(*, "group_sizes")= int  30 30 30 30 30 30
#  - attr(*, "biggest_group_size")= int 30
#  - attr(*, "labels")='data.frame':	6 obs. of  1 variable:
#   ..$ activityName: Factor w/ 6 levels "LAYING","SITTING",..: 1 2 3 4 5 6
#   ..- attr(*, "vars")= chr "activityName"
#   ..- attr(*, "drop")= logi TRUE
```


Show a few rows of the dataset
----------------------------------------


```r
head(dfSummaryData, n=3)
```

```
# # A tibble: 3 x 69
# # Groups:   activityName [1]
#   activityName subject activityNum tBodyAcc_mean_X_mean tBodyAcc_mean_Y_mean tBodyAcc_mean_Z_mean tBodyAcc_std_X_mean
#   <fct>          <int>       <dbl>                <dbl>                <dbl>                <dbl>               <dbl>
# 1 LAYING             1        6.00                0.222              -0.0405               -0.113              -0.928
# 2 LAYING             2        6.00                0.281              -0.0182               -0.107              -0.974
# 3 LAYING             3        6.00                0.276              -0.0190               -0.101              -0.983
# # ... with 62 more variables: tBodyAcc_std_Y_mean <dbl>, tBodyAcc_std_Z_mean <dbl>, tGravityAcc_mean_X_mean <dbl>,
# #   tGravityAcc_mean_Y_mean <dbl>, tGravityAcc_mean_Z_mean <dbl>, tGravityAcc_std_X_mean <dbl>,
# #   tGravityAcc_std_Y_mean <dbl>, tGravityAcc_std_Z_mean <dbl>, tBodyAccJerk_mean_X_mean <dbl>,
# #   tBodyAccJerk_mean_Y_mean <dbl>, tBodyAccJerk_mean_Z_mean <dbl>, tBodyAccJerk_std_X_mean <dbl>,
# #   tBodyAccJerk_std_Y_mean <dbl>, tBodyAccJerk_std_Z_mean <dbl>, tBodyGyro_mean_X_mean <dbl>,
# #   tBodyGyro_mean_Y_mean <dbl>, tBodyGyro_mean_Z_mean <dbl>, tBodyGyro_std_X_mean <dbl>, tBodyGyro_std_Y_mean <dbl>,
# #   tBodyGyro_std_Z_mean <dbl>, tBodyGyroJerk_mean_X_mean <dbl>, tBodyGyroJerk_mean_Y_mean <dbl>,
# #   tBodyGyroJerk_mean_Z_mean <dbl>, tBodyGyroJerk_std_X_mean <dbl>, tBodyGyroJerk_std_Y_mean <dbl>,
# #   tBodyGyroJerk_std_Z_mean <dbl>, tBodyAccMag_mean_mean <dbl>, tBodyAccMag_std_mean <dbl>,
# #   tGravityAccMag_mean_mean <dbl>, tGravityAccMag_std_mean <dbl>, tBodyAccJerkMag_mean_mean <dbl>,
# #   tBodyAccJerkMag_std_mean <dbl>, tBodyGyroMag_mean_mean <dbl>, tBodyGyroMag_std_mean <dbl>,
# #   tBodyGyroJerkMag_mean_mean <dbl>, tBodyGyroJerkMag_std_mean <dbl>, fBodyAcc_mean_X_mean <dbl>,
# #   fBodyAcc_mean_Y_mean <dbl>, fBodyAcc_mean_Z_mean <dbl>, fBodyAcc_std_X_mean <dbl>, fBodyAcc_std_Y_mean <dbl>,
# #   fBodyAcc_std_Z_mean <dbl>, fBodyAccJerk_mean_X_mean <dbl>, fBodyAccJerk_mean_Y_mean <dbl>,
# #   fBodyAccJerk_mean_Z_mean <dbl>, fBodyAccJerk_std_X_mean <dbl>, fBodyAccJerk_std_Y_mean <dbl>,
# #   fBodyAccJerk_std_Z_mean <dbl>, fBodyGyro_mean_X_mean <dbl>, fBodyGyro_mean_Y_mean <dbl>,
# #   fBodyGyro_mean_Z_mean <dbl>, fBodyGyro_std_X_mean <dbl>, fBodyGyro_std_Y_mean <dbl>, fBodyGyro_std_Z_mean <dbl>,
# #   fBodyAccMag_mean_mean <dbl>, fBodyAccMag_std_mean <dbl>, fBodyBodyAccJerkMag_mean_mean <dbl>,
# #   fBodyBodyAccJerkMag_std_mean <dbl>, fBodyBodyGyroMag_mean_mean <dbl>, fBodyBodyGyroMag_std_mean <dbl>,
# #   fBodyBodyGyroJerkMag_mean_mean <dbl>, fBodyBodyGyroJerkMag_std_mean <dbl>
```



Summary of variables
--------------------


```r
summary(dfSummaryData)
```

```
 #             activityName    subject      activityNum  tBodyAcc_mean_X_mean tBodyAcc_mean_Y_mean tBodyAcc_mean_Z_mean
 # LAYING            :30    Min.   : 1.0   Min.   :1.0   Min.   :0.2216       Min.   :-0.040514    Min.   :-0.15251    
 # SITTING           :30    1st Qu.: 8.0   1st Qu.:2.0   1st Qu.:0.2712       1st Qu.:-0.020022    1st Qu.:-0.11207    
 # STANDING          :30    Median :15.5   Median :3.5   Median :0.2770       Median :-0.017262    Median :-0.10819    
 # WALKING           :30    Mean   :15.5   Mean   :3.5   Mean   :0.2743       Mean   :-0.017876    Mean   :-0.10916    
 # WALKING_DOWNSTAIRS:30    3rd Qu.:23.0   3rd Qu.:5.0   3rd Qu.:0.2800       3rd Qu.:-0.014936    3rd Qu.:-0.10443    
 # WALKING_UPSTAIRS  :30    Max.   :30.0   Max.   :6.0   Max.   :0.3015       Max.   :-0.001308    Max.   :-0.07538    
 # tBodyAcc_std_X_mean tBodyAcc_std_Y_mean tBodyAcc_std_Z_mean tGravityAcc_mean_X_mean tGravityAcc_mean_Y_mean
 # Min.   :-0.9961     Min.   :-0.99024    Min.   :-0.9877     Min.   :-0.6800         Min.   :-0.47989       
 # 1st Qu.:-0.9799     1st Qu.:-0.94205    1st Qu.:-0.9498     1st Qu.: 0.8376         1st Qu.:-0.23319       
 # Median :-0.7526     Median :-0.50897    Median :-0.6518     Median : 0.9208         Median :-0.12782       
 # Mean   :-0.5577     Mean   :-0.46046    Mean   :-0.5756     Mean   : 0.6975         Mean   :-0.01621       
 # 3rd Qu.:-0.1984     3rd Qu.:-0.03077    3rd Qu.:-0.2306     3rd Qu.: 0.9425         3rd Qu.: 0.08773       
 # Max.   : 0.6269     Max.   : 0.61694    Max.   : 0.6090     Max.   : 0.9745         Max.   : 0.95659       
 # tGravityAcc_mean_Z_mean tGravityAcc_std_X_mean tGravityAcc_std_Y_mean tGravityAcc_std_Z_mean
 # Min.   :-0.49509        Min.   :-0.9968        Min.   :-0.9942        Min.   :-0.9910       
 # 1st Qu.:-0.11726        1st Qu.:-0.9825        1st Qu.:-0.9711        1st Qu.:-0.9605       
 # Median : 0.02384        Median :-0.9695        Median :-0.9590        Median :-0.9450       
 # Mean   : 0.07413        Mean   :-0.9638        Mean   :-0.9524        Mean   :-0.9364       
 # 3rd Qu.: 0.14946        3rd Qu.:-0.9509        3rd Qu.:-0.9370        3rd Qu.:-0.9180       
 # Max.   : 0.95787        Max.   :-0.8296        Max.   :-0.6436        Max.   :-0.6102       
 # tBodyAccJerk_mean_X_mean tBodyAccJerk_mean_Y_mean tBodyAccJerk_mean_Z_mean tBodyAccJerk_std_X_mean
 # Min.   :0.04269          Min.   :-0.0386872       Min.   :-0.067458        Min.   :-0.9946        
 # 1st Qu.:0.07396          1st Qu.: 0.0004664       1st Qu.:-0.010601        1st Qu.:-0.9832        
 # Median :0.07640          Median : 0.0094698       Median :-0.003861        Median :-0.8104        
 # Mean   :0.07947          Mean   : 0.0075652       Mean   :-0.004953        Mean   :-0.5949        
 # 3rd Qu.:0.08330          3rd Qu.: 0.0134008       3rd Qu.: 0.001958        3rd Qu.:-0.2233        
 # Max.   :0.13019          Max.   : 0.0568186       Max.   : 0.038053        Max.   : 0.5443        
 # tBodyAccJerk_std_Y_mean tBodyAccJerk_std_Z_mean tBodyGyro_mean_X_mean tBodyGyro_mean_Y_mean tBodyGyro_mean_Z_mean
 # Min.   :-0.9895         Min.   :-0.99329        Min.   :-0.20578      Min.   :-0.20421      Min.   :-0.07245     
 # 1st Qu.:-0.9724         1st Qu.:-0.98266        1st Qu.:-0.04712      1st Qu.:-0.08955      1st Qu.: 0.07475     
 # Median :-0.7756         Median :-0.88366        Median :-0.02871      Median :-0.07318      Median : 0.08512     
 # Mean   :-0.5654         Mean   :-0.73596        Mean   :-0.03244      Mean   :-0.07426      Mean   : 0.08744     
 # 3rd Qu.:-0.1483         3rd Qu.:-0.51212        3rd Qu.:-0.01676      3rd Qu.:-0.06113      3rd Qu.: 0.10177     
 # Max.   : 0.3553         Max.   : 0.03102        Max.   : 0.19270      Max.   : 0.02747      Max.   : 0.17910     
 # tBodyGyro_std_X_mean tBodyGyro_std_Y_mean tBodyGyro_std_Z_mean tBodyGyroJerk_mean_X_mean tBodyGyroJerk_mean_Y_mean
 # Min.   :-0.9943      Min.   :-0.9942      Min.   :-0.9855      Min.   :-0.15721          Min.   :-0.07681         
 # 1st Qu.:-0.9735      1st Qu.:-0.9629      1st Qu.:-0.9609      1st Qu.:-0.10322          1st Qu.:-0.04552         
 # Median :-0.7890      Median :-0.8017      Median :-0.8010      Median :-0.09868          Median :-0.04112         
 # Mean   :-0.6916      Mean   :-0.6533      Mean   :-0.6164      Mean   :-0.09606          Mean   :-0.04269         
 # 3rd Qu.:-0.4414      3rd Qu.:-0.4196      3rd Qu.:-0.3106      3rd Qu.:-0.09110          3rd Qu.:-0.03842         
 # Max.   : 0.2677      Max.   : 0.4765      Max.   : 0.5649      Max.   :-0.02209          Max.   :-0.01320         
 # tBodyGyroJerk_mean_Z_mean tBodyGyroJerk_std_X_mean tBodyGyroJerk_std_Y_mean tBodyGyroJerk_std_Z_mean
 # Min.   :-0.092500         Min.   :-0.9965          Min.   :-0.9971          Min.   :-0.9954         
 # 1st Qu.:-0.061725         1st Qu.:-0.9800          1st Qu.:-0.9832          1st Qu.:-0.9848         
 # Median :-0.053430         Median :-0.8396          Median :-0.8942          Median :-0.8610         
 # Mean   :-0.054802         Mean   :-0.7036          Mean   :-0.7636          Mean   :-0.7096         
 # 3rd Qu.:-0.048985         3rd Qu.:-0.4629          3rd Qu.:-0.5861          3rd Qu.:-0.4741         
 # Max.   :-0.006941         Max.   : 0.1791          Max.   : 0.2959          Max.   : 0.1932         
 # tBodyAccMag_mean_mean tBodyAccMag_std_mean tGravityAccMag_mean_mean tGravityAccMag_std_mean
 # Min.   :-0.9865       Min.   :-0.9865      Min.   :-0.9865          Min.   :-0.9865        
 # 1st Qu.:-0.9573       1st Qu.:-0.9430      1st Qu.:-0.9573          1st Qu.:-0.9430        
 # Median :-0.4829       Median :-0.6074      Median :-0.4829          Median :-0.6074        
 # Mean   :-0.4973       Mean   :-0.5439      Mean   :-0.4973          Mean   :-0.5439        
 # 3rd Qu.:-0.0919       3rd Qu.:-0.2090      3rd Qu.:-0.0919          3rd Qu.:-0.2090        
 # Max.   : 0.6446       Max.   : 0.4284      Max.   : 0.6446          Max.   : 0.4284        
 # tBodyAccJerkMag_mean_mean tBodyAccJerkMag_std_mean tBodyGyroMag_mean_mean tBodyGyroMag_std_mean
 # Min.   :-0.9928           Min.   :-0.9946          Min.   :-0.9807        Min.   :-0.9814      
 # 1st Qu.:-0.9807           1st Qu.:-0.9765          1st Qu.:-0.9461        1st Qu.:-0.9476      
 # Median :-0.8168           Median :-0.8014          Median :-0.6551        Median :-0.7420      
 # Mean   :-0.6079           Mean   :-0.5842          Mean   :-0.5652        Mean   :-0.6304      
 # 3rd Qu.:-0.2456           3rd Qu.:-0.2173          3rd Qu.:-0.2159        3rd Qu.:-0.3602      
 # Max.   : 0.4345           Max.   : 0.4506          Max.   : 0.4180        Max.   : 0.3000      
 # tBodyGyroJerkMag_mean_mean tBodyGyroJerkMag_std_mean fBodyAcc_mean_X_mean fBodyAcc_mean_Y_mean fBodyAcc_mean_Z_mean
 # Min.   :-0.99732           Min.   :-0.9977           Min.   :-0.9952      Min.   :-0.98903     Min.   :-0.9895     
 # 1st Qu.:-0.98515           1st Qu.:-0.9805           1st Qu.:-0.9787      1st Qu.:-0.95361     1st Qu.:-0.9619     
 # Median :-0.86479           Median :-0.8809           Median :-0.7691      Median :-0.59498     Median :-0.7236     
 # Mean   :-0.73637           Mean   :-0.7550           Mean   :-0.5758      Mean   :-0.48873     Mean   :-0.6297     
 # 3rd Qu.:-0.51186           3rd Qu.:-0.5767           3rd Qu.:-0.2174      3rd Qu.:-0.06341     3rd Qu.:-0.3183     
 # Max.   : 0.08758           Max.   : 0.2502           Max.   : 0.5370      Max.   : 0.52419     Max.   : 0.2807     
 # fBodyAcc_std_X_mean fBodyAcc_std_Y_mean fBodyAcc_std_Z_mean fBodyAccJerk_mean_X_mean fBodyAccJerk_mean_Y_mean
 # Min.   :-0.9966     Min.   :-0.99068    Min.   :-0.9872     Min.   :-0.9946          Min.   :-0.9894         
 # 1st Qu.:-0.9820     1st Qu.:-0.94042    1st Qu.:-0.9459     1st Qu.:-0.9828          1st Qu.:-0.9725         
 # Median :-0.7470     Median :-0.51338    Median :-0.6441     Median :-0.8126          Median :-0.7817         
 # Mean   :-0.5522     Mean   :-0.48148    Mean   :-0.5824     Mean   :-0.6139          Mean   :-0.5882         
 # 3rd Qu.:-0.1966     3rd Qu.:-0.07913    3rd Qu.:-0.2655     3rd Qu.:-0.2820          3rd Qu.:-0.1963         
 # Max.   : 0.6585     Max.   : 0.56019    Max.   : 0.6871     Max.   : 0.4743          Max.   : 0.2767         
 # fBodyAccJerk_mean_Z_mean fBodyAccJerk_std_X_mean fBodyAccJerk_std_Y_mean fBodyAccJerk_std_Z_mean
 # Min.   :-0.9920          Min.   :-0.9951         Min.   :-0.9905         Min.   :-0.993108      
 # 1st Qu.:-0.9796          1st Qu.:-0.9847         1st Qu.:-0.9737         1st Qu.:-0.983747      
 # Median :-0.8707          Median :-0.8254         Median :-0.7852         Median :-0.895121      
 # Mean   :-0.7144          Mean   :-0.6121         Mean   :-0.5707         Mean   :-0.756489      
 # 3rd Qu.:-0.4697          3rd Qu.:-0.2475         3rd Qu.:-0.1685         3rd Qu.:-0.543787      
 # Max.   : 0.1578          Max.   : 0.4768         Max.   : 0.3498         Max.   :-0.006236      
 # fBodyGyro_mean_X_mean fBodyGyro_mean_Y_mean fBodyGyro_mean_Z_mean fBodyGyro_std_X_mean fBodyGyro_std_Y_mean
 # Min.   :-0.9931       Min.   :-0.9940       Min.   :-0.9860       Min.   :-0.9947      Min.   :-0.9944     
 # 1st Qu.:-0.9697       1st Qu.:-0.9700       1st Qu.:-0.9624       1st Qu.:-0.9750      1st Qu.:-0.9602     
 # Median :-0.7300       Median :-0.8141       Median :-0.7909       Median :-0.8086      Median :-0.7964     
 # Mean   :-0.6367       Mean   :-0.6767       Mean   :-0.6044       Mean   :-0.7110      Mean   :-0.6454     
 # 3rd Qu.:-0.3387       3rd Qu.:-0.4458       3rd Qu.:-0.2635       3rd Qu.:-0.4813      3rd Qu.:-0.4154     
 # Max.   : 0.4750       Max.   : 0.3288       Max.   : 0.4924       Max.   : 0.1966      Max.   : 0.6462     
 # fBodyGyro_std_Z_mean fBodyAccMag_mean_mean fBodyAccMag_std_mean fBodyBodyAccJerkMag_mean_mean
 # Min.   :-0.9867      Min.   :-0.9868       Min.   :-0.9876      Min.   :-0.9940              
 # 1st Qu.:-0.9643      1st Qu.:-0.9560       1st Qu.:-0.9452      1st Qu.:-0.9770              
 # Median :-0.8224      Median :-0.6703       Median :-0.6513      Median :-0.7940              
 # Mean   :-0.6577      Mean   :-0.5365       Mean   :-0.6210      Mean   :-0.5756              
 # 3rd Qu.:-0.3916      3rd Qu.:-0.1622       3rd Qu.:-0.3654      3rd Qu.:-0.1872              
 # Max.   : 0.5225      Max.   : 0.5866       Max.   : 0.1787      Max.   : 0.5384              
 # fBodyBodyAccJerkMag_std_mean fBodyBodyGyroMag_mean_mean fBodyBodyGyroMag_std_mean fBodyBodyGyroJerkMag_mean_mean
 # Min.   :-0.9944              Min.   :-0.9865            Min.   :-0.9815           Min.   :-0.9976               
 # 1st Qu.:-0.9752              1st Qu.:-0.9616            1st Qu.:-0.9488           1st Qu.:-0.9813               
 # Median :-0.8126              Median :-0.7657            Median :-0.7727           Median :-0.8779               
 # Mean   :-0.5992              Mean   :-0.6671            Mean   :-0.6723           Mean   :-0.7564               
 # 3rd Qu.:-0.2668              3rd Qu.:-0.4087            3rd Qu.:-0.4277           3rd Qu.:-0.5831               
 # Max.   : 0.3163              Max.   : 0.2040            Max.   : 0.2367           Max.   : 0.1466               
 # fBodyBodyGyroJerkMag_std_mean
 # Min.   :-0.9976              
 # 1st Qu.:-0.9802              
 # Median :-0.8941              
 # Mean   :-0.7715              
 # 3rd Qu.:-0.6081              
 # Max.   : 0.2878   
```


