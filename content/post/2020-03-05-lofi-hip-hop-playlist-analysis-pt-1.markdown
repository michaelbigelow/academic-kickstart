---
title: Lofi Hip Hop Playlist Analysis pt.1
author: Michael Bigelow
date: '2020-03-05'
slug: lofi-hip-hop-playlist-analysis-pt-1
categories:
  - Data Mining
tags:
  - principal component analysis
  - data mining
  - EDA
subtitle: ''
summary: ''
authors: [admin]
lastmod: '2020-03-05T04:21:38-07:00'
featured: yes
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---



# Introduction and Motivation
In the coming weeks, I will analyze four Lofi Hip Hop Spotify playlists to gain an understanding of how the features of Spotify's music recommendation system relate to the characteristics of a particular genre.  I seek to apply the data science techniques I am learning to a subject that will be interesting to lovers of music. In addition, I seek to understand all I can about these music recommendation systems in particular, and about such recommender systems in general.

Of course, one must start somewhere, and due to my keen interest in the recent sounds of lofi hip hop, this first post quantitatively examines the differences between track features of four Spotify playlists containing lofi hip hop. Two playlists are user-created; two Spotify-curated.

In particular, I surmise that the procedures generating these playlists differ between the user-created and the Spotify-created playlists, and likely between the two user-created playlists.  I hope to examine the effects of these differences on the respective track feature profiles of these playlists.  

The ultimate goal in the coming series to use this knowledge to train a machine learning classifier that designates newly-heard tracks as a good fit for a certain playlist, given their Spotify track features. 

Suggestively, the two user-created playlists have roughly the same name; one is curated by independent record label [Strange Fruits](https://strangefruits.net/), and the other by [ChilledCow](https://open.spotify.com/user/chilledcow?si=1X7-feB4TWSaxMBmp-vqGA), the moniker used by a so-called YouTube ["pirate radio"](https://en.wikipedia.org/wiki/Pirate_radiohttps://en.wikipedia.org/wiki/Pirate_radio) account that has streamed lofi hip-hop 24/7 for 548 days.

## Playlists
The playlists in question are:

1. [lofi hip hop music - beats to relax/study to](https://open.spotify.com/playlist/0vvXsWCC9xrXsKd4FyS8kM?si=n6cUXA64St2O_y6CA0hA5A) created by [ChilledCow](https://open.spotify.com/user/chilledcow?si=1X7-feB4TWSaxMBmp-vqGA). At the end of last month, YouTube mistakenly terminated ChilledCow's account, immortalizing the 548-day stream as a 13,000+ hour video. 

2. [lofi hip hop music to study and relax to](https://open.spotify.com/playlist/3LFIBdP7eZXJKqf3guepZ1?si=6APSrudcTQWPA1HxNog_8w) created by [Strange Fruits](https://open.spotify.com/user/a902190?si=oq-GoNIzRSqo6ZCykUWqhw), who on their [website](https://strangefruits.net/) claims to be "one of the fastest growing independent record labels around the world."  All the tracks in this playlist appear to be the label's own releases.

3. [Lo-Fi Beats](https://open.spotify.com/playlist/37i9dQZF1DWWQRwui0ExPn?si=5EDe-ipXRMSXbAfUo0xRRg) created by [Spotify](https://open.spotify.com/user/spotify?si=rcowuSBSQd2weQw2mpylaA)

4. [Lush Lofi](https://open.spotify.com/playlist/37i9dQZF1DXc8kgYqQLMfH?si=4qSavvG3S7-sgOS3LlbHxA) created by [Spotify](https://open.spotify.com/user/spotify?si=rcowuSBSQd2weQw2mpylaA)
  


# Data
## Overview
The Python code for gathering track features for each playlist utilizes the SpotiPy library, and will soon be available on my [GitHub](https://github.com/michaelbigelow) for those interested.  

After processing the data into one tibble, we can see that it contains 997 individual tracks of 12 features each (excluding "id" and "playlist").  An explanation of the features can be found [here](https://developer.spotify.com/documentation/web-api/reference/tracks/get-several-audio-features/).


```
## # A tibble: 997 x 14
##    danceability energy   key loudness  mode speechiness acousticness
##           <dbl>  <dbl> <dbl>    <dbl> <dbl>       <dbl>        <dbl>
##  1        0.717  0.193     9   -16.1      0      0.0459       0.802 
##  2        0.698  0.239     4   -11.1      1      0.103        0.928 
##  3        0.665  0.403     9   -10.1      1      0.214        0.322 
##  4        0.665  0.183     9   -12.0      1      0.135        0.808 
##  5        0.856  0.288     0   -11.7      1      0.0764       0.0691
##  6        0.683  0.424     8    -9.16     0      0.0867       0.787 
##  7        0.769  0.32      5   -13.3      0      0.111        0.535 
##  8        0.725  0.28      1   -15.0      1      0.142        0.818 
##  9        0.831  0.341     6    -9.62     0      0.12         0.929 
## 10        0.684  0.463     0    -8.52     0      0.0843       0.417 
## # … with 987 more rows, and 7 more variables: instrumentalness <dbl>,
## #   liveness <dbl>, valence <dbl>, tempo <dbl>, playlist <chr>,
## #   duration_s <dbl>, id <chr>
```

Out of interest, let us examine how many tracks belong to each playlist:

```r
tracks %>%
  group_by(playlist) %>%
  summarize(track_count = n())
```

```
## # A tibble: 4 x 2
##   playlist      track_count
##   <chr>               <int>
## 1 ChilledCow            209
## 2 Sp_LoFiBeats          450
## 3 Sp_LushLoFi           121
## 4 StrangeFruits         217
```

## Exploratory Data Analysis
First we examine how the playlists differ with respect to the distributions of a few track features.  Since these playlists are all from a specific subgenre of music rather than four very distinct genres, the tracks will (we presume) be more similar-- the data points will be far from linearly separable, making the ultimate task of classification more difficult.  We need to get a good sense of the data.

### Principal Component Analysis
We perform principal component analysis on the data, reducing the dimensionality of the data from 10 to 2 in the optimal way to visually get a sense of which combinations of features contribute most to the variance in the cloud of data points. 

We use the very handy FactoMineR package to perform the PCA.


We can examine the eigenvalues:

```
##         eigenvalue percentage of variance cumulative percentage of variance
## comp 1   1.9740392              19.740392                          19.74039
## comp 2   1.6759104              16.759104                          36.49950
## comp 3   1.2136679              12.136679                          48.63618
## comp 4   1.0490515              10.490515                          59.12669
## comp 5   0.9123840               9.123840                          68.25053
## comp 6   0.8547382               8.547382                          76.79791
## comp 7   0.7479275               7.479275                          84.27719
## comp 8   0.6425137               6.425137                          90.70232
## comp 9   0.5413248               5.413248                          96.11557
## comp 10  0.3884429               3.884429                         100.00000
```

...and look at a screeplot (using the helpful factoextra package):
<img src="/post/2020-03-05-lofi-hip-hop-playlist-analysis-pt-1_files/figure-html/unnamed-chunk-6-1.png" width="672" />

We will lose a lot of variance in reducing the dimensionality from 10 to 2, but hopefully the resulting plot will still be at least partially informative.  We now examine a biplot:
<img src="/post/2020-03-05-lofi-hip-hop-playlist-analysis-pt-1_files/figure-html/unnamed-chunk-7-1.png" width="672" />

The biplot does still manage to provide some idea of the relative importance of the different features.  Principal component 1 preserves nearly 20% of the original variance, and principal component 2 just shy of 17%; the directions of the loadings appear correlated for certain combinations of features, such as "valence," "danceability," and "speechiness."

### Comparison of Track Feature Distributions
We shall examine a few representative features and compare their distributions, playlist-to-playlist.  The distribution of values for each feature is visualized for reference at the [Spotify track features info page](https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-feat).

#### Track Energies
From Spotify: *"Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy."*

<img src="/post/2020-03-05-lofi-hip-hop-playlist-analysis-pt-1_files/figure-html/unnamed-chunk-8-1.png" width="672" />

Interestingly, it appears that the ChilledCow playlist shares a similar median track energy with Spotify's Lush Lofi, while Strange Fruits' playlist shares a similar median with Spotify's Lo-Fi Beats.

We shall test the null hypothesis that the mean energies are the same for all playlists.  We shall actually use Tukey's method to test this hypothesis between each pair of playlists. 

```r
anova1 <- aov(energy ~ playlist, data = tracks)
TukeyHSD(anova1, conf.level = .99)
```

```
##   Tukey multiple comparisons of means
##     99% family-wise confidence level
## 
## Fit: aov(formula = energy ~ playlist, data = tracks)
## 
## $playlist
##                                    diff         lwr         upr     p adj
## Sp_LoFiBeats-ChilledCow     0.093603115  0.05552168  0.13168455 0.0000000
## Sp_LushLoFi-ChilledCow     -0.013710043 -0.06567865  0.03825857 0.8433985
## StrangeFruits-ChilledCow    0.095551753  0.05146057  0.13964294 0.0000000
## Sp_LushLoFi-Sp_LoFiBeats   -0.107313159 -0.15390062 -0.06072569 0.0000000
## StrangeFruits-Sp_LoFiBeats  0.001948638 -0.03565040  0.03954768 0.9984934
## StrangeFruits-Sp_LushLoFi   0.109261797  0.05764563  0.16087796 0.0000000
```

The adjusted p-values tell us what we expected by looking at the boxplot: for the two pairs of playlists noted (whose adjusted p-value is greater than 0.01), we fail to reject the null hypothesis at the 99% confidence level, concluding they have the same mean Energy.  For all others, we reject the null hypothesis of equal means; this evidence that, for instance, Strange Fruits' playlist, while sharing a very similar name with ChilledCow's, is not algorithmically copying its tracks' energy profiles. 

#### Track Valences
From Spotify: *"[Valence is] a measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry)."*

<img src="/post/2020-03-05-lofi-hip-hop-playlist-analysis-pt-1_files/figure-html/unnamed-chunk-10-1.png" width="672" />

This time the Spotify playlists appear most similar; to investigate more quantitatively, we again test the null hypothesis of equal means pairwise, using Tukey's method:

```r
anova2 <- aov(valence ~ playlist, data = tracks)
TukeyHSD(anova2, conf.level = .99)
```

```
##   Tukey multiple comparisons of means
##     99% family-wise confidence level
## 
## Fit: aov(formula = valence ~ playlist, data = tracks)
## 
## $playlist
##                                    diff          lwr         upr     p adj
## Sp_LoFiBeats-ChilledCow     0.051104293 -0.007588564  0.10979715 0.0337731
## Sp_LushLoFi-ChilledCow      0.060151544 -0.019944872  0.14024796 0.0889727
## StrangeFruits-ChilledCow   -0.033206299 -0.101161662  0.03474906 0.4227332
## Sp_LushLoFi-Sp_LoFiBeats    0.009047251 -0.062755496  0.08085000 0.9793646
## StrangeFruits-Sp_LoFiBeats -0.084310593 -0.142259965 -0.02636122 0.0000372
## StrangeFruits-Sp_LushLoFi  -0.093357844 -0.172911060 -0.01380463 0.0014960
```

In this case, we reject the null hypothesis of equal mean valences between Strange Fruits' playlist and either of the Spotify playlists, since the resulting adjusted p-values are <0.01.  For all other pairs of playlists, at the 99% confidence level we fail to reject the null hypothesis and conclude that they have the same average valence.  

#### Acousticness
From Spotify: *"[Acousticness is] a confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic."*

<img src="/post/2020-03-05-lofi-hip-hop-playlist-analysis-pt-1_files/figure-html/unnamed-chunk-12-1.png" width="672" />

Again, the Strange Fruits and Lofi Beats playlists visually appear more similar, with ChilledCow and Lush Lofi appearing likewise.  Let us perform ANOVA once more.  

```r
anova3 <- aov(acousticness ~ playlist, data = tracks)
TukeyHSD(anova2, conf.level = .99)
```

```
##   Tukey multiple comparisons of means
##     99% family-wise confidence level
## 
## Fit: aov(formula = valence ~ playlist, data = tracks)
## 
## $playlist
##                                    diff          lwr         upr     p adj
## Sp_LoFiBeats-ChilledCow     0.051104293 -0.007588564  0.10979715 0.0337731
## Sp_LushLoFi-ChilledCow      0.060151544 -0.019944872  0.14024796 0.0889727
## StrangeFruits-ChilledCow   -0.033206299 -0.101161662  0.03474906 0.4227332
## Sp_LushLoFi-Sp_LoFiBeats    0.009047251 -0.062755496  0.08085000 0.9793646
## StrangeFruits-Sp_LoFiBeats -0.084310593 -0.142259965 -0.02636122 0.0000372
## StrangeFruits-Sp_LushLoFi  -0.093357844 -0.172911060 -0.01380463 0.0014960
```

At the 99% confidence level we see no evidence to reject the null hypothesis of equal mean acousticness pair-wise between the pairs listed in row 1, 4, or 6.

#### Duration
The duration, while not a very descriptive feature sound-wise, could nevertheless prove valuable in training a classifier.  Its appearance as a prominent loading in the biplot leads us to investigate.
<img src="/post/2020-03-05-lofi-hip-hop-playlist-analysis-pt-1_files/figure-html/unnamed-chunk-14-1.png" width="672" />

Lush Lofi appears to have a shorter average track duration; we will carry out analysis of variance as before to confirm.

```r
anova4 <- aov(duration_s ~ playlist, data = tracks)
TukeyHSD(anova2, conf.level = .99)
```

```
##   Tukey multiple comparisons of means
##     99% family-wise confidence level
## 
## Fit: aov(formula = valence ~ playlist, data = tracks)
## 
## $playlist
##                                    diff          lwr         upr     p adj
## Sp_LoFiBeats-ChilledCow     0.051104293 -0.007588564  0.10979715 0.0337731
## Sp_LushLoFi-ChilledCow      0.060151544 -0.019944872  0.14024796 0.0889727
## StrangeFruits-ChilledCow   -0.033206299 -0.101161662  0.03474906 0.4227332
## Sp_LushLoFi-Sp_LoFiBeats    0.009047251 -0.062755496  0.08085000 0.9793646
## StrangeFruits-Sp_LoFiBeats -0.084310593 -0.142259965 -0.02636122 0.0000372
## StrangeFruits-Sp_LushLoFi  -0.093357844 -0.172911060 -0.01380463 0.0014960
```

Looking at the p-values given for each pair, the p-values <0.01 for the pairings between Lush Lofi and any other track indicate at the 99% confidence level that its duration differs.  Looking at the column labeled "diff", we see that the tracks are generally around 15 to 20 seconds shorter.

#### Track Tempos
For reference, let us examine a feature whose loading in the PCA biplot above appeared near the origin:
<img src="/post/2020-03-05-lofi-hip-hop-playlist-analysis-pt-1_files/figure-html/unnamed-chunk-16-1.png" width="672" />

The median tempos appear to be strongly concentrated around ~88 beats per minute for all playlists.  Performing an analysis of variance is probably unneccessary. The author has heard tempos in this neighborhood referred to as "Tempo di Hip Hop" and we may infer that this will likely be a shared feature amongst all Lo-Fi Hip Hop playlists.  

# Moving Forward
We have seen that while this data certainly isn't linearly separable--there is considerable overlap between the features of the tracks--there do exist differences in the tendencies of different playlists.  Moving forward in part two we may wish to continue with some clustering or factor analysis but what we have already seen so far leads us to believe a suitable machine learning classifier could potentially be found.  In future posts we shall examine that aspect of the problem more, perhaps processing the data using kernel methods to improve separability.  We shall try different models and compare their results.  If you are reading this and would care to weigh in, please message me-- I am always learning and would love to hear your thoughts!
