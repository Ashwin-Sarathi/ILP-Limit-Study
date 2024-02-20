# ILP-Limit-Study
Used the executable of an out of order processor, 721sim, to study ILP  bottlenecks in a subset of the SPEC benchmarks. This project was done as a part of ECE 721: Advanced Microarchitecture, under Proff Eric Rotenberg at NC State University.

Explored the effect that the following features have on the IPC measured for a 16-wide superscalar processor:
1. Sizes of ILP-extracting structures: Active List (AL), Load Queue/Store Queue (LQ/SQ), and Issue Queue (IQ). Note: by not explicitly specifying the size of the Physical Register File (PRF), 721sim defaults to auto-sizing the PRF conservatively (upper bound) with respect to the AL size: PRF size = AL size + # architectural registers.
2. Data cache: perfect (always hit in L1 data cache) vs. real memory hierarchy (L1, L2, L3).
3. Branch prediction: perfect vs. real.
4. Trace cache: perfect trace cache vs. no trace cache.
5. Memory dependence prediction: oracle vs. real (three different variants)

The following parameters are fixed for Project 1, by virtue of specifying the -L (limit study) command-line argument.
1. The fetch, dispatch, issue, and retire widths are all 16. Thus, the upper bound on IPC for this limit study is 16 instr./cycle.
2. Each of the 16 execution lanes can execute any instruction type (universal execution lanes) with 1-cycle EX latency.
3. The IQ uses ideal age-based scheduling.
4. There are 64 branch checkpoints (the maximum supported by 721sim). 
5. Fetch Queue (FQ) size is 64.

After running the simulator, you can see all parameters of the modeled superscalar processor in the stats.* output file from 721sim. Run “./721sim -h” to get a complete list of command-line arguments.

Go through the project specification to understand the various run conditions used and to understand the commands used.
