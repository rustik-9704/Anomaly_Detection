The telemetry data in time series format comes from the two spacecrafts: the Soil Moisture Active Passive (SMAP) satellite and the Curiosity Rover on Mars (MSL). Since we are only interested in the sequential values of the signals, the data has been anonymized with respect to time, which doesn't affect the forecasting. The telemetry values are standardized such that they lie within the range from -1 to 1. The data for a given signal consists of m rows and n columns, where n corresponds to the number of timestamps and m rows represent the commands sent to different modules and the last m-th row contains the telemetry values themselves. The commands are not used as input features, so the dimensions from m x n go to 1 x n (or n x 1). 

The telemetry signals are divided into several channels. The name of the folders represent the channel category and the signal number: P stands for Power, R - Radiation, etc. So the signals of the same category are related. 

SMAP provides us with 55 signals and MSL with 27, where 54 of these signals are continuous and the rest is discrete. 
 
 |Anomalies|Normal|
 |---------|------|
 
