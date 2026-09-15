

### Site: HUMAIN's first building: 50 MW, 18,000 NVIDIA GB300 GPUs. DCD, 28 May 2025; NVIDIA, 13 May 2025.

## Q1: How many racks and GPUs does the site's power buy?

Power: PUE 1.25; 10% of IT for switches and storage; 20% headroom.

IT Power:
50 / 1.25 = 40 MW

Other IT Resources:
40 × 0.10 = 4 MW
40 - 4 = 36 MW

Headroom:
36 × 0.20 = 7.2 MW

Compute Power:
36 - 7.2 = 28.8 MW

A GB300 NVL72 rack is 72
GPUs, about 20 TB, about 120 kW.

Rack:
28.8 MW x 1000 = 28,800 KW
28,800 / 120 = 240 racks

CPUs:
240 x 72 = 17,280 CPUs
 
## Q2: What is the largest open model it can serve, and how many copies of it?

Kimi K2 - 1 trillion parameters

Memory:
240 x 20 = 4,800 TB

model’s weights at FP8, plus context for 32 conversations of 128K tokens.
Model weights: 1 trillion parameters × 1 byte = 1 TB
Context memory ≈ 0.3 TB

Memory per copy:
1 + 0.3 = 1.3 TB

Number of copies: 
4,800 / 1.3 ≈ 3,692


## Q3: What is the largest model it could train in six months?

H100 Peak Performance:
989 TFLOPS

Sustained Performance at 40%:
989 × 0.40 = 395.6 TFLOPS per GPU

Total Compute Performance:
17,280 GPUs × 395.6 TFLOPS
= 6,836,000 TFLOPS
≈ 6.84 × 10^18 operations/second

Six Months:
6 × 30 × 24 × 60 × 60
= 15,552,000 seconds

Total Operations in Six Months:
6.84 × 10^18 × 15,552,000
≈ 1.06 × 10^26 operations

Training Compute:
6 × N × 20N = 120N²

120N² = 1.06 × 10^26

N = √(1.06 × 10^26 / 120)

N ≈ 9.4 × 10^11 parameters
≈ 940 billion parameters

Training Tokens:
20 × 940 billion
≈ 18.8 trillion tokens

Answer:
The site could train approximately a 940B-parameter model
on about 18.8 trillion tokens in six months.

## Q4: What is its electricity bill for a month?

Average Power Draw:
50 MW × 0.65 = 32.5 MW

Monthly Energy:
32.5 MW × 24 hours × 30 days
= 23,400 MWh

Convert to kWh:
23,400 × 1,000
= 23,400,000 kWh

Electricity Bill at $0.08/kWh:
23,400,000 × 0.08
= $1,872,000 per month

At Industrial Rate ($0.048/kWh):
23,400,000 × 0.048
= $1,123,200 per month

Answer:
$1.872 million/month at $0.08/kWh,
or $1.123 million/month at the industrial rate.

## Q5: What does a million tokens cost at 30% and 80% of capacity sold?

Non-Electricity Monthly Cost:
50 MW × $450,000
= $22,500,000

Total Monthly Cost:
$22,500,000 + $1,872,000
= $24,372,000

Token Capacity per Second:
17,280 GPUs × 125 tokens/s
= 2,160,000 tokens/s

Monthly Token Capacity:
2,160,000 × 60 × 60 × 24 × 30
= 5,598,720,000,000 tokens/month

At 30% Capacity Sold:
5,598,720,000,000 × 0.30
= 1,679,616,000,000 tokens

Cost per Million Tokens:
$24,372,000 / 1,679,616
= $14.51 per million tokens

At 80% Capacity Sold:
5,598,720,000,000 × 0.80
= 4,478,976,000,000 tokens

Cost per Million Tokens:
$24,372,000 / 4,478,976
= $5.44 per million tokens

Answer:
30% sold = $14.51 per million tokens
80% sold = $5.44 per million tokens

