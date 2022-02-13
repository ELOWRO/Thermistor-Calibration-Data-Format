🌡Thermistor Calibration Data Format
====================================

## Compact v1.0

This format is dedicated for QR Codes and URLs but can be used for any purpose.

File extension: `.thermistor`

### Formats:

#### Steinhart-Hart: 

##### Without calibration points:

```
thermistor://<CoefficientA>_<CoefficientB>_<CoefficientC>
```

Example:

```
thermistor://1.12924E-03_2.34108E-04_0.87755E-07
```

##### With calibration points:


```
thermistor://[CoefficientA]_[CoefficientB]_[CoefficientC]/[Temperature(Kelvin)~Uncertainty(Kelvin)]K[Resistance(Ohms)~Uncertainty(Ohms)]_Temperature(Kelvin)~Uncertainty(Kelvin)]K[Resistance(Ohms)~Uncertainty(Ohms)_Temperature(Kelvin)~Uncertainty(Kelvin)]K[Resistance(Ohms)~Uncertainty(Ohms)
```

Uncertainty can be ommited for resistances.

Example:

```
thermistor://1.12924E-03_2.34108E-04_0.87755E-07/273.16~0.009K10000.017~0.006_273.16~0.009K10000.017~0.006_273.16~0.009K10000.017~0.006
```

#### Beta: 

```
thermistor://B[Beta]_[ResistanceAt25(Ohms)]
```

Example:

```
thermistor://B3799.41_10000.1
```

## Full v1.0

This `json` based format is dedicated for machine-to-machine communication. 

File extension: `.thermistor`

### Formats:

#### Steinhart-Hart: 

##### Without calibration points:

```
{
	"a": <CoefficientA>, 
	"b": <CoefficientB>, 
	"c": <CoefficientC>
}
```

Example:

```json
{
	"a": 1.12924E-03, 
	"b": 2.34108E-04, 
	"c": 0.87755E-07
}
```

##### With calibration points:


```
{
	"a": <CoefficientA>, 
	"b": <CoefficientB>, 
	"c": <CoefficientC>,
	"calibration": [ 
		{
			"T": <T-Kelvin>, "dT": <T-Kelvin>, "R": <R-Ohms>, "dR": <R-Ohms>
		},
		{
			"T": <T-Kelvin>, "dT": <T-Kelvin>, "R": <R-Ohms>, "dR": <R-Ohms>
		},
		{
			"T": <T-Kelvin>, "dT": <T-Kelvin>, "R": <R-Ohms>, "dR": <R-Ohms>
		}
	]
}
```

Example:

```json
{
	"a": 1.12924E-03, 
	"b": 2.34108E-04, 
	"c": 0.87755E-07,
	"calibration": [
		{
			"T": 215.0, "dT": 0.01, "R": 10000.0, "dR": 0.2
		},
		{
			"T": 225.0, "dT": 0.02, "R": 9000.0, "dR": 0.18
		},
		{
			"T": 235.0, "dT": 0.06, "R": 8000.0, "dR": 0.14
		}
	]
}
```

#### Beta: 

##### Without calibration points:

```
{
	"beta": <BETA Coefficient>, 
	"R25": <Resistance at 25C in Ohms>
}
```

Example:

```json
{
	"beta": 3799.41, 
	"R25": 10000
}
```

##### With calibration points:

```
{
	"beta": <BETA Coefficient>, 
	"R25": <Resistance at 25C in Ohms>,
	"calibration": [
		{
			"T": <T-Kelvin>, "dT": <T-Kelvin>, "R": <R-Ohms>, "dR": <R-Ohms>
		},
		{
			"T": <T-Kelvin>, "dT": <T-Kelvin>, "R": <R-Ohms>, "dR": <R-Ohms>
		}
	]
}
```

Example:

```json
{
	"beta": 3799.41, 
	"R25": 10000, 
	"calibration": [
		{
			"T": 215.0, "dT": 0.01, "R": 10000.0, "dR": 0.2
		},
		{
			"T": 225.0, "dT": 0.02, "R": 9000.0, "dR": 0.18
		}
	]
}
```
