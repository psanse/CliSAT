This folder contains a linux binary release for the exact algorithm CliSAT for the maximum clique problem.

Article: CliSAT:A SAT-based exact algorithm for hard maximum clique problems by Pablo San Segundo, Fabio Furini, David Alvarez and Panos Pardalos (2022), (currently under review).

http://www.optimization-online.org/DB_HTML/2022/04/8874.html


Date of release@17/04/2022
Compiled with Ubuntu 16.04.7 LTS

%%%%%%%%%%%%
%%
%% INSTRUCTIONS
%%
%%%%%%%%%%%

Run the binary from the command line with the following parametes: name of the graph (in DIMACS format), time limit (in seconds), vertex ordering parameter (1 (DEG-SORT), 2 (COLOR-SORT):

./CliSAT <filename> <time limit> <ordering>

CliSAT considers two initial vertex orderings from the literature: DEG-SORT (based on vertex degree) and COLOR-SORT (based on determining an independent set partition). 

COLOR-SORT is expected to perform well in those instances where the size of the independent set partition is close to the clique number. Otherwise, DEG-SORT should be preferable (see article).

%%%%%%%%%%%%
%%
%% EXAMPLE
%%
%%%%%%%%%%%

Typing: 

./CliSAT keller5.clq 100 2  

selects the COLOR-SORT ordering of vertices and times out if the instance keller5.clq is not solved within 100s. 

The resulting output is: 
	
*****************************
DATA:../../../../CliSAT_inst/dimacs/brock200_1.clq       N:200   M:14834         D:0.745427
TIME_LIMIT:100
TIME_LIMIT_HEUR:0.05
SORTING:1
AMTS:1
*****************************

parsing....
preprocessing....
solving....
*****************************
102 31 103 174 143 3 198 121 137 25 131 47 179 82 106 99 190 45 119 136 40  [21]
omega:21        ts(s):0.164387  tp(s):0.051822  tr(s):1e-05     steps:6459

where:

omega: clique number
ts(s): search time (seconds)
tp(s): pre-processing time (seconds)
tr(s): parsing time (seconds)
steps: number of recursive calls to CliSAT
