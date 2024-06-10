               			CUDA Parallel Programming Course
   						 	  	Learn_CUDA_by_Joamon

- Tutorial: By Hamdy Abdelkhalik
- Link: https://www.youtube.com/watch?v=ZZveGGevzk8&list=PLBQlPZZ80yqRVrt99CsmYY77MLaenKVa8

- Course includes: Examining, explaining, and studying graphic processing unit known as GPU.

                        GPU
                         |
                How Nvidia Established
                         |
                  GPU Architecture

- Video 1:

- Nvidia was founded by Jensen Huang in 1993.
- Nvidia launched its first Hardware Product NV1 in 1995.
  Structure of NV1:

  1.  GPU: 2MB
  2.  64-bit of BUS Width
      A. A BUS Width refers to the number of bits that can be transfer across the bus, its a crucial specification that determines the speed and efficiency of the data transfer between the components such as CPU and RAM.
      B. For example you must have seen 32 bit or 64 bit operating system in you This PC Properties, which means that your operating system is capable of transfering the data upto the bits between CPU, RAM, and other peripherals.
      C. A wider bus allows for faster data transfer rates, as more data can be transmitted in parallel.

  3.  TMU:1 (Texture Mapping Units)
      A. A TMU is a component found in GPU which is responsible for applying texture(images) to 3D objects in computer graphics.
      B. For Example, Imagine you have a coloring book with lot of pictures, and you want to paint them. the TMUs are like your painting brushes. which helps your computer's graphics card to texture(like colors or patterns)to the surfaces of 3D object in the game or 3D application

      4. ROP:1 (Raster Operation Pipline or Raster Output Pipline)
         A. ROP helps in blending the colors, drawing lines and shapes,and making sure everything is in the right place. the more ROPs you have, the faster your graphic card can create the final image, leading to smoother and more detailed graphics.
      5. Pixel Shaders:1 ( Core )
      6. Graphics Processor:NV1
      7. EDO Memory Type( Extended Data Out)
         A. An EDO memory is a type of computer memory that was used in older systems, during 1990s. It was an improvement over the previous FPM ( Fast Page Mode ) memory technology and was commonly used in system like Pentium-based computers.
         B. The key feature of the EDO was its ability to allow the CPU to access memory more quickly than FPM memory.
         C. EDO memory was eventually replaced by SDRAM (Synchronous Dynamic Random Access Memory) due to its even faster access times and improved efficiency.

  4.  Vertex Shaders N/A
      A. Vertex shaders are a type of shader program used in computer graphics to manipulate the attributes of vertices (points) of 3D objects.
      B. Vertex shaders work by taking inputs such as the position, color, and texture coordinates of a vertex, and using these inputs to transform the vertex's position in 3D space, change its color, or apply textures to it.

- In 1997 Nvidia introduce RIVA 128 also known as NV3.
  A. This was the first GPU to bring the 3D acceleration to the market.

- In 1998 Nvidia unveil what would become there iconic GPU generation(The Geforce Generation), The Nvidia Geforce 256 SDR.
  Structure of Geforce 256 SDR:

  1.  Graphic processor NV10
  2.  Pixel Shaders 4
  3.  Vertex Shaders N/A
  4.  TMUs 4
  5.  ROPs 4
  6.  Memory Size 32MB
  7.  Memory type SDR
  8.  Bus Width 64 bit

          																*ABOVE IS HISTORY OF NVIDIA *

- Video 2:

      																*The difference between CPUs & GPUs*

- Introduction to GPU Architecture
- Basic knowledge of GPU hardware architecture with Nvidia designs.

Q1. Can we simply write a Code and run it on GPU? yes or no, and Why?
ANS: 1. Yes, we can write code and run it on a GPU, but its not as staghtforward as writing code on CPU. As we know GPU are designed to handle parallel processing tasks. 2. To run code on a GPU, we need to use languages or libraries such as CUDA (for NVIDIA GPUs) or OpenCL (for Various GPU architectures). 3. This language allows you to write code that can be executed in parallel on the GPU, taking advantages of its parallel processing capabilities.

Q2. Comparison table of CPUs and GPUs with its components with respect to hardware.
ANS: Table 1:
Component CPU GPU
Purpose General-purpose Graphics rendering
Computing parallel tasks

    Cores(ALU)					Fewer(usully upto																		Many(from hundreds
    							32 Cores)																				to thousands of core)

    Architecture				Designed for sequential																	Designed gor parallel
    							processing																				processing

    Clock Speed					Typically higher																		Lower the CPU, but
    							(GHz range)																				many more cores compensate

    Cache						L1, L2, L3 caches for																	Typically has smaller
    							fast data access																		caches per core

    Memory						Supports system RAM																		Has dedicated VRAM
    							and caches																				(Video RAM)

    Floting point				Supports both single																	Often optimizeed for single
    							and bouble precision																	precision calculation

    Power Consumption			Generally higher																		can be higher, but more efficient
    																													for parallel tasks

    Special Features			Instruction set optimized																Specialized instruction set for
    							for general computing																	graphics rendering

Q3. One on one comparison between 1 ALU(Arithmetic Logic Unit) from the CPU and 1 Core from the GPU.
ANS:
In one-one camparison the ALU in CPUs are more powerful and more complex then the Cores in the GPUs.
For example, the term powerful in this case referring to a powerfull ALU we are speaking of attributes such as speed, as we know modern CPUs can operate at frequencies upto 3-4 GHz.
On other hand the newly released GPU in 2020 the A100 GPU from the Nvidia company has a frequency ranging from 765-1200 MHz,

    To be clear 1200MHz means 1.2GHz, which is roughly a quarter of the avarage speed of CPU speed.

    The ALU in CPUs are designed for general purpose computing tasks and often focus on executing a single thread quickly, on the other hand the GPU core are designed for parallel processing(Performing specific 	types of tasks very efficiently).

    The GPUs core are optimized to process many threads simultaneously making them ideal for tasks like rendering graphics

    The ALU typically accesses the data from the CPU's cache or main memory, where the core in a GPU has its own cache and memory (VRAM) and is optimized for high-speed accessto this memory for parallel processing tasks.

Q4. How does the differences between CPUs ALU and GPUs Core impact the application performance?
ANS:
The difference between a CPU's ALU and a GPU's core can significantly impact application performance depending on the nature of the application and it requirements.

    Let's compare it with respect to the number of core in the GPU and the number of ALU in the CPU.

    Let's take two cases for example

    					Case1																						Case2
    			Dependent instructions																		Independent instructions
    			*Sequential execution*

    				ADD R1, R2, R3																	There is a twist in the independent instruction,
     				Let R2= 3, R3= 5, R1=?															each instruction is independent of the other
    				R1=R2+R3
    				R1=3+5																			Lets take a exapmle: (5+3)*2-4
    				R1=8

The initial instruction takes the value from register ADD R1, R2, R3
R2 and R3 adds them together and stores result in R1. MUL R4, R5, R6
SUB R7, R8, R9
MUL R4, R1, R5
Let R4=?, R1=8, R5=4 Now as we add values from register R2 and R3 and
R4=R1*R5 store the result in R1, our multiplication doen't  
 R4=8*4 depend on the outcome of the addition, instead it
R4=32 multiplies the values from R5 and R6 and stores the
Next we Multiply, the Value stored in R1 with R5 to store result in R4. same with division it doesn't depend
the outcome value in R4, the crucial point to note here is on the outcome of the multiplicaton.with such
the interdependency of these instructions, as the second Independence between the instruction if we have
instruction uses R1 the same register that was used multiple core available we can assign each
in the first instruction(or in the preceding addition). instruction to a seperate core and execute them
simultaneously.
DIV R6, R4, R7
Let R6=?, R4=32, R7=2 parallel addition(5+3): core 1 calculates 5+3=8
R6=R4/R7 parallel multiplication: core2 calculates 8\*2=16
R6=32/2 parallel subtraction: core3 calculates 16-4=12
R6=16 combining Results: core4 combines the result from
Next we Division, core1, core2, core3, the final result is 12l.

This means before we complete the Division the Example imagine that we have n number of instructions
Multiplicaton need to be complete, similarly before with each requiring just one cycle for the execution
completing the Multiplicationthe Addition need in the parallel,In this independent scenario all the
to be Completed. That means each instructions instruction would be executed in parallel at once on
depends on the result of its previous instructions. n number of core, finishing collectively in just one
This method of processing is termed or called cycle.
as Sequential execution
However in a dependent situation it would take n
Q1. Why don't we utilize multiple-core for these number of cycles to execute because each instruction
instruction to execute them parallelly in one step? must wait for its predecessor to finish the execution
ANS: The above operation is simple and can be which means in sequential each instruction depends
executed quickly bysinglr core in a sequenctial manner. on the result of previous one.
However if you are dealing with more complex tasks
or datasets, utilizing multiple-core for parallel However when dealing with tasks filed with numerous
execution can be benificial. independent instructions GPUs take the lead dure to
their abiloty to run multiple instructions parallel
For example: The arithmatic expression(5+3)\*2-4, across various cores.
it's not practical to split the operationacross
multiple cores for parallel execution because each
operation depends on the result of the previous one.
you can't calculate 5+3 in parallel with 2-4 because
the multiplication operation depends on the result of
the addition.

    														*Let's explore how CPU and GPU coexist in most of the system*

- The CPU and GPU can coexist on a single board called as motherboard or a system board, etc.

- But first let's understand

![MOTHERBOARD_PNG_IMAGE_ANIMATION](/home/popocon/Learn_CUDA_by_Joamon.md/Screenshot (165).png)

Q5. What is a motherboard?
ANS: A motherboard (also known as mainboard, system board, or logic board) is a primary printed circuit board(PCB) in a computer or other electronic devices. It serves as the central hub that connects and communicate with various components, allowing them to work together as a cohesive system.

    Here is the list of components found on motherboard of a CPU:

    1. CPU Socket: The socket where the CPU (Central processing unit) is installed.

    2. Chipset: A set of chips that manage data flow between the CPU, memory, storage deviced, and peripherals.
    	    Peripherals(Are devices that are connected to a computer but are not part of the core computer architecture. Ex. Input/ Output Devices, Storage devices, networking devices and othet external devices)

    3. RAM Slots: Slots for installing RAM(Random Access Memory) modules.

    4. PCIs Slots: Slots for installing expansion cards such as graphics cards, sound cards, and network cards into the motherboard.

    5. SATA Connectors: Connectors for SATA (serial ATA(Advanced Technology Attachment)) devices such as HDD(Hard Disk Drive) and SSDs (Solid State Drive).

    6. USB Headers: Headers for connecting USB ports on the front or back of the case.

    7. CMOS Battery: A battry that powers the CMOS (Complementary Metal-Oxide-Semiconductor)memory, which stores BIOS (Basic Input/Output System) or UEFI (Unified Extensible Firmware Interface) settings. CMOS(A samll coin-shaped battery found on cumputer's motherboard. )

    8. BIOS Chip: A chip that stores the BIOS(Basic input/output system) firmware.

    9. Power Connectors: Connectord for the power supply unit, including ATX( Advanced Technology eXtended) power connectors and CPU power connector.

    10. Front Panel Connectors: Connectors for buttons, LEDs, and audio ports on the front of the case.

    11. Cooling System Connectors: Connectore for CPU fans, case fans, and something liquid cooling system.

    12. M.2 Slots: Slots for installing M.2 SSDs. M.2 Slots are Physical connectors on a computer motherboard that allow for high-speed storage abd other expansion devices.

    	    	   M.2 is a form factor and interface standard desigined to accommodate small, high-performance components, such as SSDs, Wi-Fi and Bluetooth modules.

    13. Ethernet Port: A port for connecting to a wired network.

    14. Audio Port: Ports for connecting speakers, headphones, and microphones.

    15. VRM(Voltage Regulator Module): Modules that regulate the voltage supplied to the CPU.

    16. Debug LEDs/Display: LEDs or a display that shows error codes or system status.

    17. Thunderbolt Header: A Thunderbolt header is a connector on a computer motherboard designed to support Thunderbolt technology, typically to enable high-speed connections with external devices.

    			Thunderbolt is an interface standard developed by intel, offering fast data transfer rate and a variety of connectivity option, often used for connecting external storage devices, monitors, docking stations and more.

    18. Wi-Fi/Bluetooth Module: A module for wireless connection.

    19. Internal Headers: Headers for connecting various internal components such as case fans, front panel audio, and USB ports.

now, Lets dive into the compoents that exist in GPUs.

![NVIDIA_GPU_IMAGE_PNG](/home/popocon/Learn_CUDA_by_Joamon.md/Nvidia GPU.png)

Q6. What are the components that exists in GPUs?(Particulraly focusing on Nvidia GPU)
ANS: NVIDIA GPUs (Graphics Processing Units) contains several key components that work together to process graphics and perform other parallel computing tasks efficiently.

The green box shown in the photo above is a GPU care.

Here are some of the main components found in NVIDIA GPUs:

    1. SM(streaming Multi-processor):

    	A. Streaming Multiprocessor (SMs) are key components in NVIDIA GPU that handels parallel tasks. Each SM consist of multiple CUDA cores and other specialized units, allowing it to execute multiple threads simultaneously.

    	Example: Imagine a classroom full of students(threads) working on different assignments. The teacher (SM) can manage and help these students work independently on their tasks at the same time, making the whole process more efficent.

    2. L2 Cache Memory:

    	A. L2 Cache Memory is a small, high speed memory unit located on the GPU that stores recently accessed data.It helps improve performance by reducing the time it takes to access the frequently used data.

    	Example: Think of L2 cache memory as a student desk where they keep their most important books and notes. when they need tese resorces they can quickly acess thm without having to go to the library(System Memory), saving time.

    3. Device Global Memory:

    	A. Device Global Memory is the main memory on the GPU where data is stored for processing. It is large but slower than the L2 cache Memory, and it can be accessed by all the Cores and SMs on the GPU.

    	Example: Device Global Memory is like a large library where all the books(Data) needed for assignment are kept. Student(Threads) can access books when they need them, but it may take a bit longer than accessing books from their desks(L2 Cache Memory).

    4. Scheduler:

    	A. The scheduler in a GPU is like a traffic controller, deciding which tasks(Kernels) should be executed next on the GPUs streaming multiprocessor(SMs). It manages the flow of tasks to ensure the GPU's resources are used efficiently.

    	Example: Imagine you're in charge of a busy intersection with many lanes(SMs) and cars(Kernels) coming form different directions. you need to decide which car goes where and when to keep traffic flowing smoothly. That's what the scheduler does for the GPU, ensuring that tasks are executed efficiently.

    5. Dispatcher:

    	A. The dispatcher is responsible to send tasks(Kernels) to the streaming multiprocessors(SMs) for execution. It takes the tasks from the scheduler and asign them to the SMs, manging the distribution of work.

    	Example: Think of the dispatcher as a messenger who takes the tasks(Kernels) from the scheduler and delivers them to the SMs. Just like the messenger ensures that messages reach their destination, the dispatcher ensures that tasks are executed by the SMs.

Q7. A step-by-step explanation of how Streaming Multi-porcessor(SM) works in a GPU.
ANS: SM(Streaming Multiprocessor) consist of:

    1. L0 Instruction cache.
    2. Warp Scheduler (32 threads/clk)
    3. Dispatch Unit (32 threads/clk)
    4. Register File (16,384 x 32-bit)
    5. INT32 (is a data format used for integer arithmatic operations)
    6. FP32 (is data format used for floting-point arithmatic operations)
    7. Tensor Core (is a specialized processing unit designed to accelerate matrix-matrix multiplication operations, which are common in deep learning and neural    	network computations.)
    8. LD/ST (Load/store Units)
    9. SFU (Special Function)
    10.Tex (Texture Units)

Alright, let's dive into the inner working of a Streaming Multi-processor(SM) in GPU!

    1. Instruction Fetch: The SM recives instructions from the dispatcher, which include the kernel to be executed and the data needed for the computation.

    2. Thread Assignment: The SM organizes the incoming threads into groups called warps. A warp consists of 32 threads that are executed together.(warp, refers to the process of texture coordinate warpping or addresing modes, which determines how textures are applied to 3D models. When a texture is mapped onto 3D surface, the texture coordinates might exceed the standard range(0 to 1). The warp controls how these out-of-range texture coordinates are handled. common warp modes include: Repeat(warp), Clamp to Edge, Mirror Repeat, Clamp to Border).

    3. Thread Scheduling: The SM scheduler decides which warp to execute next based on the availablity of resources an the priority of the warp.

    4. Instruction Decode and Issue: The SM decodes the instructions from the warp and issues them to the CUDA cores for execution.

    5. Parallel Execution: The CUDA cores within the SM execute the instruction in parallel. Each core executes a different thread from the warp, allowing multiple threads to be processed simultaneously.

    6. Data Access: The threads access from thr GPU's memory(VRAM) or cache. If the data is not in the cache, it is fetched from memory.

    7. Execution Completion: Once all threads in the warp have completed their instructions, the SM updates the warp's status and checks for any dependencies with other warps.

    8. Warps Synchronization(if needed): In some cases, threads within a warp may need to synchronize their execution to ensure that certain operations are complete in a specific order. This is done using synchronization primitives such as barries.

    9. Result Accumulation: The results of the computation are accumulated and stored in registers or shared memory within the SM.

    10. Completion and Result Return: Once all the warps in the kernel have completed their execution, the result are retured to the GPU's memory(VRAM) or back to the CPU if required.

    Example: Let's say we have a smiple kernel that calculates the square of a number. If we luanch this kernel on the GPU, the SM would execute it as fellows:

    	1. The SM recives the krenel and oerganizes the imcoming threads into warps.
    	2. Each warp is assigned a group of the threads to calculate the square of a number.
    	3. The SM scheduler decides which warpto execute next, and the CUDA cores within the SM execute the instructions in parallel.
    	4. Each thread within a wrap calculates the square of its assigned number.
    	5. The result are accumulated and stored in registers or shared memory within the SM.
    	6. Once all threads in the warp have completed their calculations, the results are returned to GPU's memory.

- Video 3:
  _Understanding NVIDIA's GPU Architectures and Generations_

Q8. What is the Architecture in the context of NVIDIA GPUs?
ANS:
