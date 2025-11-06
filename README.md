***Output after running make timestep.c***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ make

gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o main.o main.c
main.c:10:22: optimized: loop vectorized using 32 byte vectors
main.c:20:15: missed: statement clobbers memory: mymindt_6 = timestep (10000000, 9.800000000000000710542735760100185871124267578125e+0, 9.499999999999999555910790149937383830547332763671875e-1, &celltype, &H, &U, &V, &dx, &dy);
/usr/include/x86_64-linux-gnu/bits/stdio2.h:112:10: missed: statement clobbers memory: __printf_chk (1, "Minimum dt is %lf\n", mymindt_6);
gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o timestep.o timestep.c
timestep.c:9:22: missed: couldn't vectorize loop
timestep.c:9:22: missed: not vectorized: control flow in loop.
timestep.c:11:25: missed: statement clobbers memory: wavespeed_46 = sqrt (_9);
gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o timer.o timer.c
timer.c:5:5: missed: statement clobbers memory: clock_gettime (1, tstart_cpu_2(D));
timer.c:10:5: missed: statement clobbers memory: clock_gettime (1, &tstop_cpu);
gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed -o stream_triad main.o timestep.o timer.o -lm

(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ ./stream_triad 

Minimum dt is 0.016964

***Output after running make timestep_opt1.c***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ make

gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o timestep_opt1.o timestep_opt1.c
timestep_opt1.c:9:9: optimized: loop vectorized using 32 byte vectors
timestep_opt1.c:11:7: missed: couldn't vectorize loop
timestep_opt1.c:11:7: missed: not vectorized: control flow in loop.
timestep_opt1.c:9:9: optimized: loop vectorized using 32 byte vectors
timestep_opt1.c:12:22: missed: statement clobbers memory: wavespeed_58 = sqrt (_9);
gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed -o stream_triad main.o timestep_opt1.o timer.o -lm

***Output after running make timestep_opt2.c***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ make

gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o timestep_opt2.o timestep_opt2.c
timestep_opt2.c:9:9: optimized: loop vectorized using 32 byte vectors
timestep_opt2.c:11:7: missed: couldn't vectorize loop
timestep_opt2.c:11:7: missed: not vectorized: control flow in loop.
timestep_opt2.c:9:9: optimized: loop vectorized using 32 byte vectors
timestep_opt2.c:12:22: missed: statement clobbers memory: wavespeed_58 = sqrt (_9);
gcc -g -O3 -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed -o stream_triad main.o timestep_opt2.o timer.o -lm

***Output after running make timestep_opt3.c***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ make

gcc -g -O3 -fno-trapping-math -fno-math-errno -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o main.o main.c
main.c:10:22: optimized: loop vectorized using 32 byte vectors
main.c:20:15: missed: statement clobbers memory: mymindt_6 = timestep (10000000, 9.800000000000000710542735760100185871124267578125e+0, 9.499999999999999555910790149937383830547332763671875e-1, &celltype, &H, &U, &V, &dx, &dy);
/usr/include/x86_64-linux-gnu/bits/stdio2.h:112:10: missed: statement clobbers memory: __printf_chk (1, "Minimum dt is %lf\n", mymindt_6);
gcc -g -O3 -fno-trapping-math -fno-math-errno -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o timestep_opt3.o timestep_opt3.c
timestep_opt3.c:8:9: optimized: loop vectorized using 32 byte vectors
timestep_opt3.c:10:7: optimized: loop vectorized using 16 byte vectors
timestep_opt3.c:8:9: optimized: loop vectorized using 32 byte vectors
gcc -g -O3 -fno-trapping-math -fno-math-errno -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed   -c -o timer.o timer.c
timer.c:5:5: missed: statement clobbers memory: clock_gettime (1, tstart_cpu_2(D));
timer.c:10:5: missed: statement clobbers memory: clock_gettime (1, &tstop_cpu);
gcc -g -O3 -fno-trapping-math -fno-math-errno -fstrict-aliasing -ftree-vectorize -fopenmp-simd -march=native -mtune=native -mprefer-vector-width=256 -fopt-info-vec-optimized -fopt-info-vec-missed -o stream_triad main.o timestep_opt3.o timer.o -lm

***Output after running likwid-perfctr***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ likwid-perfctr -C 0 -f -g MEM_DP ./stream_triad
--------------------------------------------------------------------------------
CPU name:       Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz
CPU type:       Intel Core SandyBridge processor
CPU clock:      3.29 GHz
ERROR - [/home/student/likwid/src/perfgroup.c:perfgroup_readGroup:830] No such file or directory.
Cannot read group file MEM_DP.txt. Searched in /usr/local/share/likwid/perfgroups/sandybridge/MEM_DP.txt and /home/student/.likwid/groups/sandybridge/MEM_DP.txt
ERROR - [/home/student/likwid/src/perfmon.c:perfmon_addEventSet:2533] Permission denied.
Access to performance group MEM_DP not allowed

***Output after perf fot opt1***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ sudo perf stat -e branch-misses,bus-cycles,cache-misses,cache-references,cpu-cycles,instructions ./stream_triad 
Minimum dt is 0.016964

 Performance counter stats for './stream_triad':

            250665      branch-misses                                                         
          38764789      bus-cycles                                                            
           7129413      cache-misses                     #   74,58% of all cache refs         
           9559640      cache-references                                                      
        1279238064      cpu-cycles                                                            
         788502683      instructions                     #    0,62  insn per cycle            

       0,389861718 seconds time elapsed

       0,175835000 seconds user
       0,213800000 seconds sys

***Output after perf fot opt2***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ sudo perf stat -e branch-misses,bus-cycles,cache-misses,cache-references,cpu-cycles,instructions ./stream_triad 
Minimum dt is 0.016964

 Performance counter stats for './stream_triad':

            241152      branch-misses                                                         
          38681813      bus-cycles                                                            
           7050455      cache-misses                     #   74,08% of all cache refs         
           9516978      cache-references                                                      
        1276499816      cpu-cycles                                                            
         789379209      instructions                     #    0,62  insn per cycle            

       0,389736515 seconds time elapsed

       0,173896000 seconds user
       0,214871000 seconds sys

***Output after perf fot opt3***
(base) student@itcenter-lab128:~/Desktop/Parallel-Programming-Assignments$ sudo perf stat -e branch-misses,bus-cycles,cache-misses,cache-references,cpu-cycles,instructions ./stream_triad 
Minimum dt is 0.016964

 Performance counter stats for './stream_triad':

            248772      branch-misses                                                         
          39569490      bus-cycles                                                            
           7109890      cache-misses                     #   74,23% of all cache refs         
           9578530      cache-references                                                      
        1305793107      cpu-cycles                                                            
         795848805      instructions                     #    0,61  insn per cycle            

       0,413659901 seconds time elapsed

       0,176278000 seconds user
       0,221349000 seconds sys


***“Is it fully vectorized?”***
- Opt1: not fully vectorized, mostly scalar instructions
- Opt2: not fully vectorized, mostly scalar instructions
- Opt3: not fully vectorized, still scalar dominated.

***“What vector length instructions were used?”***
- Opt1: AVX/256-bit, high cache miss ratio 74.6%
- Opt2: AVX/256-bit 
- Opt3: AVX/256-bit

***“Which of the runs is the best?” ***
- Opt1: CPU cycles: 1.279.238.064; Elapsed time: 0.38986 s; Decent baseline, but slightly slower than opt2
- Opt2: PU cycles: 1.276.499.816; Elapsed time: 0.38974 s; Best performance of the three
- Opt3: CPU cycles: 1.305.793.107; Elapsed time: 0.41366 s; Slowest, worst performance
