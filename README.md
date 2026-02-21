# Real-Time Object Detection Using Hardware-Accelerated CNN on Xilinx Zynq FPGA with Arm Processor

## Overview
This project demonstrates real-time Convolutional Neural Network (CNN) inference acceleration on a Xilinx Zynq-7000 SoC. By heavily leveraging hardware/software co-design, compute-intensive layers of the CNN are offloaded to the FPGA programmable logic (PL), while the Arm Cortex-A9 processor (PS) handles system control, data movement, and image preprocessing.

Developed as part of the Bharat AI-SoC Student Challenge and ARM hackathon, this hardware-accelerated CNN IP was built using Vitis HLS, integrated via Vivado, and deployed on a PYNQ-Z2 board.

## Key Features
- FPGA-Accelerated Inference: Custom IP for spatial convolution and pooling.
- HW/SW Co-Design: Seamless partitioning using Vitis HLS and Vivado.
- Real-Time Processing: High-throughput object detection and image classification.
- Quantitative Benchmarking: Built-in scripts to compare latency, throughput, and power against a purely software-driven CPU baseline.

## System Stack
- Hardware: Xilinx Zynq-7000 SoC (PYNQ-Z2 Development Board)
- Software Design: Vitis HLS 2023.1, Vivado Design Suite 2023.1
- Embedded Environment: PYNQ Linux, Python 3.x, OpenCV

## Performance Highlights
| Metric | CPU Only | FPGA Accelerated |
|------|---------|-----------------|
| Latency (ms) | 3347.1 | 114.117 |
| FPS | 1.86 | 8.76 |
| Throughput | 0.056 | 0.108 |
| Power Efficiency | Baseline | Improved |

## GitHub Repository Structure
```
root/
├── Detection/
│   ├── hardware/
│   │   ├── hls/
│   │   │   └── dpu_core.cpp
│   │   └── software/
│   │       └── cpu_hw_inference.py
│   └── README.md
├── hardware/
│   ├── README.md
│   ├── hls/
│   │   ├── dpu_core.cpp
│   │   └── weights.h
│   └── vivado/
│       ├── bitstream/
│       │   ├── design_1_wrapper.bit
│       │   └── design_1_wrapper.hwh
│       ├── hdl/
│       │   └── design_1_wrapper.v
│       └── tcl/
│           ├── design_1.bd
│           └── design_1.tcl
├── model/
│   ├── README.md
│   ├── dataset.md
│   ├── training.py
│   └── weights.h
└── software/
    ├── README.md
    ├── cpu_inference.py
    └── hw_inference.py
```

## Demo
▶ Demo Video: [https://drive.google.com/file/d/1zEg1VLj9V9LxN7ka2FiaaFTp8HAQc8l4/view?usp=drive_link](https://drive.google.com/file/d/1zEg1VLj9V9LxN7ka2FiaaFTp8HAQc8l4/view?usp=drive_link)


## 🚀 How to Run

### Prerequisites
- PYNQ-Z2 (or compatible Zynq board)
- SD Card (≥16GB recommended)
- PYNQ Linux image
- Python 3.x
- OpenCV installed on board
- FPGA bitstream (`.bit`) and hardware handoff file (`.hwh`)
- CNN model weights

### Hardware Setup
1. Flash the PYNQ image to the SD card  
2. Insert the SD card into the board  
3. Connect power, Ethernet/USB, and camera (optional)  
4. Power ON the board  

### Deploy FPGA Bitstream
```bash
scp overlay.bit xilinx@<board_ip>:/home/xilinx/
scp overlay.hwh xilinx@<board_ip>:/home/xilinx/
python3 load_overlay.py
```



## Authors
- Royce Niran George A
- Kamalesh S
- Ranjith Ganesh B

