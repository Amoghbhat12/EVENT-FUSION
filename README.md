Event-Assisted Fusion for Improved Object Detection in Motion-Blurred Scenarios

This repository implements a lightweight RGB–Event fusion pipeline for robust object detection under motion blur. The system integrates synthetic and real event data with RGB imagery and supports both offline training and embedded deployment on the AMD Xilinx Kria KV260 platform.

System Overview

The proposed pipeline combines event-based vision with conventional RGB sensing to improve detection robustness without modifying the detector architecture. The framework supports:

Synthetic event generation using V2E for large-scale training

Real-time event camera deployment on embedded hardware

Architecture-agnostic fusion compatible with YOLOv8

Edge-friendly inference with low latency and minimal overhead

Hardware Platform
Event Camera Deployment on AMD Kria KV260

Event camera: Prophesee IMX636 (DVS)

Embedded platform: AMD Xilinx Kria KV260

OS: PetaLinux BSP

Bring-Up and Integration

Integrated the IMX636 event camera using PetaLinux BSP customization

Configured device tree overlays for camera and peripheral support

Debugged and validated media-ctl pipelines for correct sensor-to-userspace routing

Verified kernel driver functionality and event stream stability

Built and flashed custom WIC images to enable persistent deployment

Achieved stable, real-time event data streaming on KV260

Methodology

RGB videos are converted into synthetic event streams using the V2E simulator, configured to emulate a DAVIS346 sensor.

Event streams are accumulated over short temporal windows to form 2D event frames.

Event frames are temporally synchronized and spatially scaled to match RGB resolution.

Polarity-based event information is overlaid onto RGB frames using a deterministic pixel-level fusion scheme.

The fused RGB–Event images are directly used by YOLOv8, requiring no architectural changes.

Dataset

1,470 car-centric images collected from publicly available YouTube videos

Motion blur simulated using directional convolution kernels

Synthetic event data generated using V2E with realistic sensor noise modeling

Three dataset variants created:

RGB-only (motion blurred)

Event-only

Fused RGB–Event

Training and Inference Setup
Training (Offline)

Model: YOLOv8-M (Ultralytics)

Platform: Google Colab (NVIDIA T4, 16 GB VRAM)

Image size: 640 × 640

Epochs: 100

Optimizer: AdamW

Learning rate: Cosine decay

Embedded Inference (KV260)

Deployed YOLOv8-based inference pipeline on Kria KV260

Integrated real-time RGB + event fusion

Evaluated:

End-to-end inference latency

Event-to-frame synchronization stability

System-level performance under motion blur
