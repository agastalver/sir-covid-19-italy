# COVID-19 SIR mathematical model for Italy

SIR mathematical model for infectious diseases optimized for COVID-19 using italian public available data.

-----

![sir-cases](https://github.com/agastalver/sir-covid-19-italy/raw/master/images/generated-sir-cases.png "SIR Model Cases")

![sir](https://github.com/agastalver/sir-covid-19-italy/raw/master/images/generated-sir.png "SIR Model")

**Note**: 

* `susceptible`, `infected`, and `recovered`, stand for the observable population; thus, the ones that can be detected. The actual values could be higher.
* `susceptible` is an estimated value calculated from `N` with respect to the `infected` and `recovered`, the actual value is not provided by the government.
* `recovered` stands for people who has recovered from the virus or has died; as considered in the SIR model.

-----

## Last optimization

### Case forecasting table

| Date           | Infected  | Cases      |
|:--------------:|:---------:|:----------:|
| 2020-04-20     | 100561    | 174713     |
| 2020-04-21     | 99588     | 176342     |
| 2020-04-22     | 98509     | 177839     |
| 2020-04-23     | 97338     | 179214     |
| 2020-04-24     | 96085     | 180477     |
| 2020-04-25     | 94764     | 181637     |
| 2020-04-26     | 93383     | 182702     |
| 2020-04-27     | 91951     | 183680     |
| 2020-04-28     | 90479     | 184580     |
| 2020-04-29     | 88973     | 185407     |
| 2020-04-30     | 87440     | 186167     |
| 2020-05-01     | 85886     | 186867     |

### Optimized SIR parameters

```
N = 197342.6038798863
beta = 0.31343409735458366
gamma = 0.02577856381684178
delta = 0.4659804562950558
delay = 0
```

* `delta` stands for a factor of reduction of `beta` during the lockdown.
* All results are available in the folders `images` and `data`.

-----

## Last data information

### Italyn total cases

![total](https://github.com/agastalver/sir-covid-19-italy/raw/master/images/generated-total.png "Total cases")

-----

## Methodology

### Data sources

Main data source:

* Github: https://github.com/pcm-dpc/COVID-19
  * https://raw.githubusercontent.com/pcm-dpc/COVID-19/master/dati-andamento-nazionale/dpc-covid19-ita-andamento-nazionale.csv

### Epidemiology model

This is based on the SIR epidemiology model proposed by W. O. Kermack and A. G. McKendrick in:

```
Kermack, W. O.; McKendrick, A. G. (1927). "A Contribution to the Mathematical Theory of Epidemics". Proceedings of the Royal Society A: Mathematical, Physical and Engineering Sciences. 115 (772): 700. Bibcode:1927RSPSA.115..700K. doi:10.1098/rspa.1927.0118. JSTOR 94815.
```

You can find the description on wikipedia: https://en.wikipedia.org/wiki/Mathematical_modelling_of_infectious_disease#The_SIR_model

### Optimization

The parameters `N`, `beta`, and `gamma`, are unknown. Additionally, a `delay` parameter is considered; defined as a time synchronization parameter in case the available data is not adjusted to day 0.

The optimization method is Nendel-Mead, adjusting mean squares on `I(t)` and `R(t)` to the available data. `S(t)` and `N` are calculated backwards.

```
Nelder, John A.; R. Mead (1965). "A simplex method for function minimization". Computer Journal. 7 (4): 308–313. doi:10.1093/comjnl/7.4.308.
```

## Usage

Execute:

```
$ python main.py
```

## Important note

The mathematical model could not adjust to the real behaviour of the virus. Furthermore, the data can have errors, delays, or be incomplete, so the adjustment can vary in the future.
