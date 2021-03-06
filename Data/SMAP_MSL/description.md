The telemetry data in time series format comes from the two spacecrafts: the Soil Moisture Active Passive (SMAP) satellite and the Curiosity Rover on Mars (MSL). Since the main concern is in the sequential values of the signals, the data has been anonymized with respect to time as well as the channel IDs, which doesn't affect the forecasting. The telemetry values are standardized such that they lie within the range from -1 to 1. The data for a given signal consists of m rows and n columns, where n corresponds to the number of timestamps and m rows represent the commands sent to different modules and the last m-th row contains the telemetry values themselves. The commands are not used as input features, so the dimensions go from m x n to 1 x n (or n x 1). 

The telemetry signals are divided into several channels. The name of the folders represent the channel category and the signal number: P stands for Power, R - Radiation, etc. So the signals of the same category are related. 

SMAP provides us with 55 signals and MSL with 27, where 54 of these signals are continuous and the rest is discrete. 

The anomalies are classified into 2 categories: point anomalies (identified by properly-set alarms or distance-based methods that ignore temporal information) and contextual anomalies (detected by more complex methodologies such as LSTMs or Hierarchical Temporal Memory). The anomalous regions were manually extracted so we have regions of normal and anomalous data separately for each signal.

 ||SMAP|MSL|Total|
 |-----------------------|----|---|-----|
 |Total anomaly sequences|69|36|105|
 |Point anomalies (% tot.)|43 (62%)|19 (53%)|62 (59%)|
 |Contextual anomalies (% tot.)|26 (38%)|17 (47%)|43 (41%)|
 


__Telemetry streams generated by SMAP:__

Channel category A
|   |A-1|A-2|A-3|A-4|A-5|A-6|A-7|A-8|A-9|
|---|---|---|---|---|---|---|---|---|---|
|Anomaly sequences|[4690, 4774]|[4450, 4560]|[4575, 4760]|[4550, 4660]|[2750, 2800]|[1890, 1930]|[6200, 8600]|[4569, 8374]|[4569, 8433]|
|Anomaly type|point|contextual|contextual|contextual|point|point|contextual|contextual|contextual|
|No of val|8640|7914|8205|8080|4693|4453|8631|8375|8434|

Channel category B
|   |B-1|
|---|---|
|Anomaly sequences|[5060, 5130]|
|Anomaly type|point|
|No of val|8044|

Channel category D
|   |D-1|D-2|D-3|D-4|D-5|D-6|D-7|D-8|D-9|D-11|D-12|D-13|
|---|---|---|---|---|---|---|---|---|---|----|----|----|
|Anomaly sequences|[5250, 8508]|[4319, 8536]|[5225, 8500]|[5225, 8472]|[4800, 4850]|[4870, 4950]|[4940, 7641]|[4370, 4420]|[6250, 7405]|[4270, 4330]|[5178, 7917]|[5070, 5230]|
|Anomaly type|point|point|point|point|point|point|point|point|point|point|point|point|
|No of val|8509|8595|8640|8473|7628|7884|7642|7874|7406|7431|7918|7633|

Channel category E
|   |E-1|E-2|E-3|E-4|E-5|E-6|E-7|E-8|E-9|E-10|E-11|E-12|E-13|
|---|---|---|---|---|---|---|---|---|---|----|----|----|----|
|Anomaly sequences|[5000, 5030], [5610, 6086]|[5598, 6995]|[5094, 8306]|[5450, 8261]|[5600, 5920]|[5610, 5675]|[5394, 5674]|[5400, 6022]|[5550, 5900]|[5000, 5050], [5601, 5871]|[5000, 5050], [5614, 5857]|[5610, 6141], [5000, 5050]|[5309, 5410], [5600, 5640], [6449, 6569]|
|Anomaly type|contextual, contextual|point|point|point|point|point|point|point|point|contextual, contextual|contextual, contextual|contextual, contextual|contextual, contextual, contextual|
|No of val|8516|8532|8307|8354|8294|8300|8310|8532|8302|8505|8514|8512|8640|

Channel category F
|   |F-1|F-2|F-3|
|---|---|---|---|
|Anomaly sequences|[5392, 5492]|[5669, 8625]|[5600, 5640]|
|Anomaly type|point|point|contextual|
|No of val|8584|8626|8376|

Channel category G
|   |G-1|G-2|G-3|G-4|G-6|G-7|
|---|---|---|---|---|---|---|
|Anomaly sequences|[4770, 4890]|[4030, 4070]|[4200, 4250]|[4690, 4720]|[5600, 5700]|[3650, 3750], [5050, 5100], [7560, 7675]|
|Anomaly type|contextual|point|point|point|point|contextual, point, contextual|
|No of val|8469|7361|7907|7632|8640|8029|

Channel category P
|   |P-1|P-2|P-3|P-4|P-7|
|---|---|---|---|---|---|
|Anomaly sequences|[2146,2349],[4536,4844],[3539,3779]|?????|[5401, 6736]|[950, 1080], [2150, 2350], [4770, 4880]|[4950, 6600]|
|Anomaly type|contextual, contextual, contextual|?????|point|point, point, point|contextual|
|No of val|8505|?????|8493|7783|8071|

Channel category R
|   |R-1|
|---|---|
|Anomaly sequences|[4510, 4590]|
|Anomaly type|point|
|No of val|7244|

Channel category S
|   |S-1|
|---|---|
|Anomaly sequences|[5300, 5747]|
|Anomaly type|point|
|No of val|7331|

Channel category T
|   |T-1|T-2|T-3|
|---|---|---|---|
|Anomaly sequences|[2399, 3898], [6550, 6585]|[6840, 8624]|[2098, 2180], [5200, 5300]|
|Anomaly type|point, contextual|point|point, point|
|No of val|8612|8625|8579|



__Telemetry streams generated by MSL:__

Channel category C
|   |C-1|C-2|
|---|---|---|
|Anomaly sequences|[550, 750], [2100, 2210]|[290, 390], [1540, 1575]|
|Anomaly type|point, contextual|point, contextual|
|No of val|2264|2051|

Channel category D
|   |D-14|D-15|D-16|
|---|----|----|----|
|Anomaly sequences|[1630, 1650], [1800, 2000]|[1500, 2140]|[600, 1250]|
|Anomaly type|point, point|point|contextual|
|No of val|2625|2158|2191|

Channel category F
|   |F-4|F-5|F-7|F-8|
|---|---|---|---|---|
|Anomaly sequences|[2700, 2770]|[3550, 3700]|[1250, 1450], [2670, 2790], [3325, 3425]|[1950, 2486]|
|Anomaly type|point|point|contextual, contextual, contextual|contextual|
|No of val|3422|3922|5054|2487|

Channel category M
|   |M-1|M-2|M-3|M-4|M-5|M-6|M-7|
|---|---|---|---|---|---|---|---|
|Anomaly sequences|[1110, 2250]|[1110, 2250]|[1250, 1500]|[1250, 1500]|[1250, 1550]|[1850, 2030]|[940, 1040]|
|Anomaly type|contextual|contextual|contextual|contextual|contextual|point|point|
|No of val|2277|2277|2127|2038|2303|2049|2156|

Channel category P
|   |P-10|P-11|P-14|P-15|
|---|----|----|----|----|
|Anomaly sequences|[4590, 4720]|[1778, 1898], [1238, 1344]|[4575, 4755]|[1390, 1410]|
|Anomaly type|point|point, point|point|point|
|No of val|6100|3535|6100|2856|

Channel category S
|   |S-2|
|---|---|
|Anomaly sequences|[900, 910]|
|Anomaly type|point|
|No of val|1827|

Channel category P
|   |T-4|T-5|T-8|T-9|T-12|T-13|
|---|---|---|---|---|----|----|
|Anomaly sequences|[1172, 1240]|[1200, 1225]|[870, 930], [1330, 1370]|[780, 810], [890, 970]|[630, 750]|[690, 790], [1900, 2050]|
|Anomaly type|point|point|contextual, contextual|point, point|contextual|contextual, contextual|
|No of val|2217|2218|1519|1096|2430|2430|
 
References:
1) https://arxiv.org/pdf/1802.04431.pdf
2) Machine Learning for Time Series Anomaly Detection by Ihssan Tinawi
3) https://github.com/khundman/telemanom 
