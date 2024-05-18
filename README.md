# Learn CUDA by Joamon

Welcome to the **CUDA Parallel Programming Course**! This repository contains notes and resources for learning CUDA, based on a tutorial series by Hamdy Abdelkhalik.

## Course Overview

**Tutorial by:** Hamdy Abdelkhalik  
**YouTube Link:** [CUDA Tutorial Series](https://www.youtube.com/watch?v=ZZveGGevzk8&list=PLBQlPZZ80yqRVrt99CsmYY77MLaenKVa8)

### Contents
- Introduction to GPUs
- History of NVIDIA
- Difference between CPUs and GPUs
- GPU Architecture and Components
- Step-by-step SM Functionality

## NVIDIA History

### Video 1: The Founding and Early Products

- **1993:** NVIDIA was founded by Jensen Huang.
- **1995:** Launch of first hardware product, NV1.
  - **Specifications of NV1:**
    - **GPU:** 2MB
    - **Bus Width:** 64-bit
      - *Explanation:* Determines speed and efficiency of data transfer between components.
    - **TMU:** 1 (Texture Mapping Unit)
      - *Explanation:* Applies textures to 3D objects.
    - **ROP:** 1 (Raster Operation Pipeline)
      - *Explanation:* Blends colors, draws lines and shapes, ensuring correct image placement.
    - **Pixel Shaders:** 1
    - **Graphics Processor:** NV1
    - **Memory Type:** EDO (Extended Data Out)
      - *Explanation:* Faster than previous FPM memory, used in the 1990s.
    - **Vertex Shaders:** N/A
      - *Explanation:* Manipulates vertex attributes in 3D objects.

- **1997:** Introduction of RIVA 128 (NV3).
  - *Significance:* First GPU with 3D acceleration.

- **1998:** Launch of NVIDIA GeForce 256 SDR.
  - **Specifications of GeForce 256 SDR:**
    - **Graphics Processor:** NV10
    - **Pixel Shaders:** 4
    - **Vertex Shaders:** N/A
    - **TMUs:** 4
    - **ROPs:** 4
    - **Memory Size:** 32MB
    - **Memory Type:** SDR
    - **Bus Width:** 64-bit

## Video 2: CPU vs GPU

### Introduction to GPU Architecture

#### Can we simply write code and run it on GPU?
- **Answer:** Yes, but not straightforward. Requires CUDA (NVIDIA GPUs) or OpenCL.

#### Comparison of CPUs and GPUs

| Component                | CPU                                       | GPU                                         |
|--------------------------|-------------------------------------------|---------------------------------------------|
| Purpose                  | General-purpose computing                 | Graphics rendering, parallel tasks          |
| Cores (ALU)              | Fewer (up to 32 cores)                    | Many (hundreds to thousands)                |
| Architecture             | Sequential processing                     | Parallel processing                         |
| Clock Speed              | Typically higher (GHz range)              | Lower than CPU, but many more cores         |
| Cache                    | L1, L2, L3 caches                         | Smaller caches per core                     |
| Memory                   | System RAM and caches                     | Dedicated VRAM (Video RAM)                  |
| Floating Point           | Supports single and double precision      | Optimized for single precision calculations |
| Power Consumption        | Generally higher                          | Higher, but efficient for parallel tasks    |
| Special Features         | Optimized for general computing           | Specialized for graphics rendering          |

#### One-on-One Comparison: CPU ALU vs GPU Core

- **CPU ALU:** More powerful, operates at higher frequencies (3-4 GHz).
- **GPU Core:** Optimized for parallel processing, lower frequencies (765-1200 MHz).

#### Application Performance Impact

- **Sequential Execution:** Dependent instructions processed step-by-step.
- **Parallel Execution:** Independent instructions executed simultaneously across multiple cores.

### Coexistence of CPU and GPU

- **Motherboard:** Central hub connecting CPU, GPU, and other components.

![Motherboard Image](path/to/motherboard_image.png)

#### Motherboard Components

1. **CPU Socket**
2. **Chipset**
3. **RAM Slots**
4. **PCI Slots**
5. **SATA Connectors**
6. **USB Headers**
7. **CMOS Battery**
8. **BIOS Chip**
9. **Power Connectors**
10. **Front Panel Connectors**
11. **Cooling System Connectors**
12. **M.2 Slots**
13. **Ethernet Port**
14. **Audio Ports**
15. **VRM (Voltage Regulator Module)**
16. **Debug LEDs/Display**
17. **Thunderbolt Header**
18. **Wi-Fi/Bluetooth Module**
19. **Internal Headers**

### NVIDIA GPU Components

![NVIDIA GPU Image](path/to/nvidia_gpu_image.png)

1. **SM (Streaming Multiprocessor)**
   - Manages parallel tasks, contains multiple CUDA cores.
2. **L2 Cache Memory**
   - Stores recently accessed data for faster retrieval.
3. **Device Global Memory**
   - Main memory for data storage, accessible by all cores and SMs.
4. **Scheduler**
   - Decides which tasks (kernels) to execute next.
5. **Dispatcher**
   - Sends tasks to SMs for execution.

### SM (Streaming Multiprocessor) Functionality

1. **Instruction Fetch**
2. **Thread Assignment**
3. **Thread Scheduling**
4. **Instruction Decode and Issue**
5. **Parallel Execution**
6. **Data Access**
7. **Execution Completion**
8. **Warp Synchronization (if needed)**
9. **Result Accumulation**
10. **Completion and Result Return**

#### Example Kernel Execution

- Calculates the square of a number.
  1. Organize threads into warps.
  2. Assign tasks to CUDA cores.
  3. Execute instructions in parallel.
  4. Store results in shared memory.
  5. Return results to GPU memory.

## Video 3: NVIDIA GPU Architectures and Generations

### GPU Architecture

- **Definition:** The design and organization of the GPU's components and functionality.

## Further Learning

Stay tuned for more updates and detailed explanations as we progress through the course. Happy learning!

## Contributing

Feel free to contribute to this repository by submitting pull requests, opening issues, or providing feedback.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
