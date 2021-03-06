
DESCRIPTION
PROBLEM : Design a scheduler that can schedule the processes arriving system at periodical intervals. Every process is assigned with a fixed time slice t milliseconds. If it is not able to complete its execution within the assigned time quantum, then automated timer generates an interrupt. The scheduler will select the next process in the queue and dispatcher dispatches the process to processor for execution. Compute the total time for which processes were in the queue waiting for the processor. Take the input for CPU burst, arrival time and time quantum from the user.
We are using Round Robin Scheduling to solve this problem.
ECPLANATION:  Round Robin Scheduling is a scheduling algorithm used by the system to schedule CPU utilization. This is a preemptive algorithm. There exist a fixed time slice associated with each request called the quantum. The job scheduler saves the progress of the job that is being executed currently and moves to the next job present in the queue when a particular process is executed for a given time quantum.
No process will hold the CPU for a long time. The switching is called a context switch. It is probably one of the best scheduling algorithms. The efficiency of this algorithm depends on the quantum value.

ROUND ROBIN SCHEDULING ALGORITHM
We first have a queue where the processes are arranged in first come first serve order.
A quantum value is allocated to execute each process.
The first process is executed until the end of the quantum value. After this, an interrupt is generated and the state is saved.
The CPU then moves to the next process and the same method is followed.
Same steps are repeated till all the processes are over.

ALGORITHM
1. Take array arrival[] (keep track of the arrival time of the processes) , burst[] (keep track of burst time of processes), temp[] (to store wating time of the processes temporarily).
2. Take total (to add total time ) and flag . Initialize them 0.
3.Take total no of processes and there arrival time and burst time from the user.
4. Take quantumtime from user.
5.Keep in a loop  all  the processes while all processes are not done. Do following for i'th process if it is not done yet. 
 	1. . If temp[i] <= tquantum && temp[i] > 0 
		(i) total = total + temp[i];
		(ii) temp[i] = 0; 
		(iii) flag = 1; 
	2. Else if temp[i] > 0
		 (i) temp[i] = temp[i] - quantum;
		 (ii) total = total + quantum; 
	3. If temp[i] == 0 && flag == 1 
		(i) print burst[i], total, arrival [i], total - arrival[i] - burst[i]);
		(ii) counter = 0;
		(iii) x--; 
		(iv)save the i into a variable a;
 	4. If i == total_processes – 1 
		(i) i = 0; 
	5. Else if arrival[i + 1] <= total
		(i) i++; 
	6. Else (i) i = 0;
	7. print the total time taken as total_time-arrival[a];

TEST CASES
1.   Quantum = 3
 PROCESS	ARRIVAL TIME	BURST TIME
P1		0			4
P2		1			7
P3		2			5
P4		 3			6
gang chart 
0 	(P1 Arrv) , P1 (4-1)          1
 1 	 (P2 Arrv) , P1(3-1)          2
 2 	 (P3 Arrv)  | P2(7-1)        3
 3	  (P4 Arrv) , P2(6-1)         4
 4 	, P3(5-1)                     5
 5 	  P3(4-1)                      6
6 	 P4(6-1)                      7
7 	P4(5-1)                     8
8 	P1(2-1)                     9
9 	 P1(1-1) P1 Competed    10 
10	 P2(5-1)                 	11
11	 P2(4-1)                  12
12	 P3(3-1)13
13	  P3(2-1) 14
14	 P4(4-1) 15
15	  P4(3-1) 16
16	  P2(3-1) 17
17	 P3(1-1) P3 COMPLETED 18   
18	 P4(2-1)  19
19	 P4(1-1) P4 COMPLETED    20
20	 P2(1-1) P2 COMPLETED    21 

SO  it took 21 sec to complete all processes
and waiting time 
P1	9
P2	14
P3	11
P4	12
Test case passed sucessfully
