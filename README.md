![header](https://sumalyo.github.io/benchmarkFASER/FASERImages/banner.png)
![C++ Badge](https://img.shields.io/badge/Built_with-C_%2B%2B-purple?logo=cplusplus)
![Python](https://img.shields.io/badge/python-3670A0?logo=python&logoColor=ffdd54)
![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?logo=plotly&logoColor=white)
![daqling Badge](https://img.shields.io/badge/Powered_By-daqling-green?link=https://gitlab.cern.ch/ep-dt-di/daq/daqling)
# Real-Time Lossless Data Compression for the FASER Experipent
__Author__ : Sumalyo Datta <br>
__Project__ : FASER <br>
__Mentors__ : Claire Antel and Brian Petersen <br>
__Date__ : 28.08.2023 <br>
__Project Proposal__ : [Link to Proposal](https://drive.google.com/file/d/1JiRfSXvvL208x196nnkluCsmFEGsbpOJ/view?usp=sharing)

## Introduction
The [FASER experiment](https://faser.web.cern.ch/index.php/) is an LHC experiment located in a tunnel parallel to the LHC ring. It is considerably smaller and low-budget compared to the titan LHC experiments such as ATLAS and CMS. The experiment seeks to detect new long-lived particles that have travelled half a kilometre from an LHC proton-proton collision site, escaping the major ATLAS experiment undetected. During proton collisions at the LHC, the FASER experiment records up to 1500 events per second using an open-source data acquisition (DAQ) software framework developed at CERN. The DAQ software receives dedicated data fragments from subcomponents on the detector, packs them into a single event and writes completed events to a file. This design leads to storage space limitations and increased data storage costs. The challenge was to develop a compression engine that would compress data in real time, __introducing minimal latency and performance overheads__. The compressed data files can be decompressed on the fly to reconstruct physics events. <p>

FASER has a trigger-based data acquisition model, and the DAQ software is developed using the DAQling framework.
>> DAQling is an open-source lightweight C++ software framework that can be used as the core of data acquisition systems of small and medium-sized experiments. It provides a modular system in which custom applications can be plugged-in. It also provides the communication layer based on the widespread ZeroMQ messaging library, error logging using ERS, configuration management based on the JSON format, control of distributed applications and extendable operational monitoring with web-based visualization.

You can read more about the strategy in the [paper published by the FASER collaboration](https://arxiv.org/abs/2110.15186).

The first part of the project involved __the exploration__ of various open-source lossless compression libraries and the development of a standalone compressor for raw files, which can be used to record performance metrics (such as compression ratio and compression speed) to help determine the best compressor that could be used in the engine. You can read more about the exploration of compression algorithms in this [medium blog](https://medium.com/gsoc-2023-data-compression-faser/real-time-lossless-data-compression-for-the-faser-experiment-part-1-274025eb4079) <p>

After exploration of various algorithms, the next task was to __develop a compression engine module__ that could be integrated into the full FASER DAQ system and can be configured to obtain a compressed file for physics events directly from the acquisition system. The challenge was to design a module that could handle high throughput working at high event rates (as high as 4kHz). The module would publish relevant metrics on the Monitoring dashboard reporting the compression ratio.
<p>

| ![DashBoard1](https://sumalyo.github.io/benchmarkFASER/FASERImages/Compression%20Dashboard%20High%20Rate.png) | 
|:--:| 
| *Fig 1: A Glimpse of The Metrics Dashboard* |

## The Community Bonding Period
Before the commencement of the coding period the plan for contributions was rougghly chalked out during the community bonding phase. The development setup was finalized during this phase. A Docker based setup was planned as it helped replicate the production environment and also made managing packagages and dependencies much easier and streamlined. I found some issues with the existing docker image and worked with the mentors to add necessary services like supervisord and reddis to the container configuration. To add support for data compression additional dev packages were added to aid in building the prototype implemnetation. 
Code for the new Dockerfile can be found here : [sumalyo_dev branch on faser-docker](https://gitlab.cern.ch/faser/docker/-/tree/sumalyo_dev?ref_type=heads)
<br>
Pull Request: [PR #2](https://gitlab.cern.ch/faser/docker/-/merge_requests/2)<br>
![PR_Merged](https://img.shields.io/badge/PR-In_Progress-yellow?style=for-the-badge&logo=appveyor)

## Raw File Compressor


### The Best Candidate

## The Compression Engine

### Decompression On-the-Fly

## Conclusion

![footer](https://sumalyo.github.io/benchmarkFASER/FASERImages/footerImage.png)









