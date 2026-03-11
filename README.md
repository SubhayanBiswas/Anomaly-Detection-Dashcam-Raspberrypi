# Real-Time Road Anomaly Detection (Edge AI)

## Overview
This project is an Edge AI pothole detection system deployed entirely on a Raspberry Pi without any cloud dependency. The system performs real-time pothole detection on live or recorded road video streams using TensorFlow Lite (TFLite) optimized YOLOv8 models. It features event-triggered buffered recording and a lightweight Flask dashboard for remote monitoring and downloading event clips.



## Hardware Platform
The system was deployed and validated using the following hardware configuration[cite: 86]:
* **Board**: Raspberry Pi 4 Model B 
* **CPU**: Quad-core Cortex-A72 @ 1.5 GHz 
* **RAM**: 4GB LPDDR4 
* **Storage**: 32GB microSD
* **OS**: Raspberry Pi OS (64-bit) 
* **Camera Input**: Pi Camera or USB Camera

## Model Details & Inference
The detection backbone utilizes a YOLOv8 Nano model converted to TensorFlow Lite format for optimized edge inference.
* **Input Resolution**: 320x320
* **Confidence Threshold**: 0.20
* **IoU Threshold**: 0.45
* **Quantization Tested**: Float16 and INT8

## Key Features & Optimizations
* **Optimized Performance**: The Float16 quantized model achieves an inference speed of 4-6 FPS, making it feasible for near real-time edge deployment. This semi-quantization provides an approximate 25-35% speed improvement over the INT8 model while preserving detection capability.
* **Thermal Stability**: The system is designed for continuous roadside monitoring, running stably for over 2 hours without triggering thermal throttling. Peak recorded CPU temperatures remained around 72°C.
* **Efficient Pipeline**: To manage hardware limitations, the architecture utilizes multi-threaded TFLite inference, non-blocking background clip saving, and a cooldown-based event trigger system.
* **Local Dashboard**: A Flask-based web interface provides a real-time MJPEG/MP4 stream alongside JSON-based event logs and downloadable clips.

## Future Scope
Future enhancements planned for the system include:
* Integration of Coral TPU acceleration to boost inference speeds.
* CAN bus integration for comprehensive vehicle metrics.
* Upgrading to an 8GB Raspberry Pi 4 to expand the 'latest-frame' buffer and handle background processes entirely in volatile memory (tmpfs), reducing SD card wear.
* City-scale deployment architecture and edge-to-cloud hybrid analytics.

## Authors
* Mr. Rounak Sengupta 
* Mr. Saurabh Mishra 
* Mr. Subhayan Biswas

**Institution**: St. Xavier's College (Autonomous), Kolkata
