#Event-Assisted RGB Fusion for Motion-Blur Robust Object Detection

This project demonstrates a lightweight RGB–Event fusion pipeline for improving object detection performance under motion blur. The system integrates event camera data with conventional RGB frames using a deterministic overlay-based fusion strategy, without modifying the detection network.

⚡ Optimized for real-time deployment on AMD Xilinx Kria KV260 with Prophesee IMX636 Event Camera

#📷 Features

✅ RGB + Event data fusion without model modification

✅ Synthetic event generation using V2E

✅ Polarity-based event overlay (ON/OFF events)

✅ YOLOv8-compatible inference pipeline

✅ Motion-blur robust object detection

✅ Real-time event camera deployment on Kria KV260

✅ PetaLinux BSP bring-up and media pipeline debugging

✅ Embedded latency and system-level evaluation

#🧠 Methodology

RGB videos are converted into synthetic event streams using V2E

Events are accumulated over short temporal windows to form 2D event frames

Event frames are temporally and spatially aligned with RGB images

Polarity-encoded events are overlaid onto RGB frames

Fused images are directly used for YOLOv8 training and inference

#📊 Dataset

1,470 car images collected from public YouTube videos

Motion blur simulated using directional blur kernels

Synthetic event data generated using DAVIS-style sensor configuration

Dataset variants:

RGB-only (blurred)

Event-only

Fused RGB–Event

#🖥️ Hardware Platform

Event Camera: Prophesee IMX636 (DVS)

Embedded Board: AMD Xilinx Kria KV260

OS: PetaLinux BSP

Bring-Up Highlights

Device tree configuration for event camera

media-ctl pipeline debugging

Kernel driver validation

Custom WIC image flashing

Stable real-time event data streaming

#🧪 Training & Inference

Model: YOLOv8-M

Image Size: 640 × 640

Optimizer: AdamW (Cosine LR)

Epochs: 100

Batch Size: 8

Embedded inference includes RGB + Event fusion, YOLOv8 deployment, and latency evaluation on KV260.

#📈 Results
