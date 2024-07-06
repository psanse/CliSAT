This folder contains a linux binary release for the exact algorithm CliSAT for the maximum clique problem (a second binary CliSAT_2024_07_06_ub16.04 has been added for compatibility with older linux sytems).

Article: CliSAT:A SAT-based exact algorithm for hard maximum clique problems by Pablo San Segundo, Fabio Furini, David Alvarez and Panos Pardalos, European Journal of Operational Research, 307:3, (2023), pp. 1008-1025. 

http://www.optimization-online.org/DB_HTML/2022/04/8874.html


Date of release@06/07/2024
Compiled with Ubuntu 22.04.3 LTS

%%%%%%%%%%%%
%%
%% INSTRUCTIONS
%%
%%%%%%%%%%%

Run the binary from the command line with the following parameters: name of the graph (in DIMACS format), time limit (in seconds), vertex ordering parameter (1 (DEG-SORT), 2 (COLOR-SORT), heuristic parameter (0 - no heuristic, 1 - AMTS heuristic 0.05s):

./CliSAT_2024_07_06 <filename> <time limit> <ordering> <heuristic>

CliSAT considers two initial vertex orderings from the literature: DEG-SORT (based on vertex degree) and COLOR-SORT (based on determining an independent set partition). 

COLOR-SORT is expected to perform well in those instances where the size of the independent set partition is close to the clique number. Otherwise, DEG-SORT should be preferable (see article).

CliSAT also employs the AMTS hueuristic to determine a large initial clique (see article). 

%%%%%%%%%%%%
%%
%% EXAMPLE
%%
%%%%%%%%%%%

Typing: 

./CliSAT_2024_07_06 keller5.clq 100 2 1 

selects the COLOR-SORT ordering of vertices and times out if the instance keller5.clq is not solved within 100s. 

The resulting output is: 
	
*****************************
DATA:../../../../CliSAT_inst/dimacs/keller5.clq  N:776   M:225990        D:0.751546
TIME_LIMIT:100
TIME_LIMIT_HEUR:0.05
SORTING:2
AMTS:1
*****************************

parsing....
preprocessing....
solving....
*****************************
716 760 685 663 343 586 481 540 634 668 606 285 326 271 490 457 428 149 134 203 239 183 8 41 366 74 48  [27]
omega:27        ts(s):23.212    tp(s):0.131353  tr(s):5e-06     steps:222737


where:

omega: clique number
ts(s): search time (seconds)
tp(s): pre-processing time (seconds)
tr(s): parsing time (seconds)
steps: number of recursive calls to CliSAT

