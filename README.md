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
| 2020-04-06     | 88286     | 129760     |
| 2020-04-07     | 88798     | 132910     |
| **2020-04-08** | **89010** | **135770** |
| 2020-04-09     | 88947     | 138358     |
| 2020-04-10     | 88636     | 140692     |
| 2020-04-11     | 88105     | 142793     |
| 2020-04-12     | 87379     | 144681     |
| 2020-04-13     | 86483     | 146375     |
| 2020-04-14     | 85937     | 148396     |
| 2020-04-15     | 85147     | 150155     |

### Optimized SIR parameters

```
N = 162710.41931344185
beta = 0.24691725125805608
gamma = 0.02949789196784256
delta = 0.7405691955902629
delay = 3
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
