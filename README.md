# Real-Time Optical Heart Rate Monitor (Arduino + LabVIEW)

## Overview

This project implements a real-time optical heart rate monitoring system using a transmissive photoplethysmography (PPG) sensor integrated with an Arduino and a LabVIEW signal-processing pipeline.

The system acquires raw optical pulse signals from a finger-mounted sensor and processes them through a multi-stage signal-conditioning and validation architecture to reliably estimate heart rate in real time.

This project demonstrates experience with sensor-based data acquisition, real-time signal-processing pipelines, and algorithmic validation of physiological signals.


## System Architecture

Signal processing workflow:

Acquisition → Conditioning → Feature Extraction → Period Detection → HR Estimation → Validation → Output

Pipeline stages include:

- Analog signal acquisition from photoresistor sensor
- Waveform construction using Build Waveform VI
- Moving average smoothing
- Linear detrending
- Signal normalization
- Peak detection
- Autocorrelation-based periodicity validation
- Heart-rate estimation logic gating


## Hardware Setup

Components:

- Arduino UNO
- Green LED optical source
- Photoresistor (5528)
- 330Ω current-limiting resistor
- 10kΩ signal conditioning resistor
- Finger-mounted sensing fixture


## Signal Conditioning Pipeline

Raw optical signals are processed using a structured waveform pipeline:

1. Signal acquisition at 50 Hz sampling frequency
2. Moving-average smoothing
3. Linear detrending
4. Normalization to range [-1, 1]
5. Peak detection
6. Autocorrelation-based periodicity detection
7. Heart-rate validation gating logic


## Feature Extraction

Peak detection parameters:

- Peak width = 3
- Peak threshold = 0.2

Autocorrelation parameters:

- Minimum lag index = 20
- Maximum lag index = 70
- Peak width = 7
- Peak ratio threshold = 0.3

These parameters improve robustness against motion artifacts and ambient noise.


## Validation Logic

Heart-rate estimates are only accepted when:

- periodic signal detected
- valid peaks detected
- physiological HR range satisfied

This gating structure prevents incorrect HR output under noisy signal conditions.


## Real-Time Processing Features

System capabilities:

- continuous waveform acquisition
- signal smoothing and conditioning pipeline
- periodicity detection via autocorrelation
- peak marker visualization
- validated heart-rate estimation
- trend waveform visualization


## Skills Demonstrated

This project demonstrates experience with:

- sensor integration
- Arduino-based DAQ systems
- real-time waveform processing
- signal conditioning pipelines
- peak detection algorithms
- autocorrelation-based validation
- LabVIEW modular VI architecture


## Future Improvements

Possible extensions:

- motion artifact rejection filters
- adaptive threshold tuning
- Python-based signal-processing pipeline implementation
- machine-learning-based signal classification
