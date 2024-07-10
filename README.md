# TriQXNet: Forecasting Dst Index from Solar Wind Data 🌌🪐
---
![](https://scx2.b-cdn.net/gfx/news/hires/2016/whyweshouldw.jpg)
# Background Information
When solar winds from the sun interacts with the magnetic field of the Earth, a phenomenon known as a geomagnetic storm occurs. This phenomenon can be fatal to critical infrastructures such as power grids, satellites, GPS etc. Therefore, forecasting geomagnetic storms is an important task that can impact millions of people worldwide.

The strength of a geomagnetic storm is measured using the **DST** (**D**isturbance **S**torm-**T**ime) index
| | Quiet-Minor | Moderate storm | Intense Storm | Superintense storm |
| - | - | - | - | - |
| DST index | >-50 | -50 to -100 | <-100 | <-250 |

# Challenge
As part of [NASA SpaceApps Challenge 2023](https://www.spaceappschallenge.org/2023/find-a-team/team-aurora/?tab=project), our project uses Deep Learning to use solar wind data to predict the DST values for the current hour ($t0$) and forecast the DST value for the next hour ($t+1$)

# Dataset Description
The dataset used to predict the intensity of geomagnetic storms is taken from NOAA's website.  
(Click [here](https://www.ngdc.noaa.gov/geomag/data/geomag/magnet/) to download the dataset.)   
The dataset consists hourly values of solar wind data measured by instruments on two of NASA's satellites (ACE and DSCOVR) and an average of the DST values measured by 4 ground-based observatories near the equator.  
Description of Solar Wind features:
- `(bx/by/bz)_gse`: Interplanetary-magnetic-field (IMF) components (in X, Y & Z axes) in geocentric solar ecliptic (GSE) coordinate.
- `(bx/by/bz)_gsm`: IMF components (in X, Y & Z axes) in geocentric solar magnetospheric (GSM) coordinates.
- `theta_(gse/gsm)`: IMF latitude in GSE and GSM coordinates.
- `phi_(gse/gsm)`: IMF longitude in GSE and GSM coordinates.
- `bt`: IMF component magnitude.
- `density`: Solar wind proton density.
- `speed`: Solar wind bulk speed.
- `temperature`: Solar wind ion temperature.

# Evaluation metric
The evaluation metric used is [Root Mean Squared Error](https://en.wikipedia.org/wiki/Root-mean-square_deviation) (RMSE). The RMSE is calculated on DST value for $t0$ hour and $t+1$ hour simultaneously
$$\text{RMSE} = \sqrt{\frac{1}{N}\sum_{i=0}^{N} (y_i - \hat y_i)^2}$$
where,
  - $\hat y_i$ is the predicted DST value for $t0$ and $t+1$
  - $y_i$ is the actual DST value for $t0$ and $t+1$
  - $N$ is the number of samples

# XAI Implementation
In the pursuit of transparency and interpretability, we conducted ShapTime and [Permutation Feature Importance](https://christophm.github.io/interpretable-ml-book/feature-importance.html) analysis for the Conv1DTimeDistributedNet model.


[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.12694950.svg)](https://doi.org/10.5281/zenodo.12694950)




