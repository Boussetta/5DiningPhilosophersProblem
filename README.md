# 5DiningPhilosophersProblem

In 1965, Dijkstra posed and solved a synchronization problem called the dining philosophers 
problem. The problem can be stated as follows. Five philosophers are sitting around a table. Each 
philosopher has a plate of spagetti. A philosopher needs two forks to eat it. There is a fork 
between each couple of plates. The life of a philosopher consists of alternate periods of eating 
and thinking. When a philosopher gets hungry, he/she tries to acquire his/her left and right forks, 
one at a time, in either time. If successful in acquiring two forks, a philosopher eats for a 
while, then puts down the forks and continues to think. The key question is: can you write a 
program for each philosopher that does what it is supposed to do and never gets stuck?

Unfortunately, there may be situation when all five  philosophers take their left forks 
simultaneously. None will be able to take their right forks, and there will be a deadlock. Deadlock 
is a situation when all processes would stay blocked forever and no more work would be done.

One of the suggestions is that after taking the left fork, the program checks top see if the right 
fork is available. If it is not, the philosopher put down the left one, waits for some time, and 
then repeats the whole process. But it is not a good solution, since all the philosophers could 
start the algorithm simultaneously, picking up their left forks, seeing that their right forks were 
not available, putting down their left forks, waiting, etc., forever. A situation like this is 
called starvation. But if the philosophers would just wait a random time instead of the same time 
after falling to acquire the right-hand fork, the chance that everything would continue in lockstep 
for even an hour is very small. One way to avoid deadlock and starvation is by use a semaphore type 
variable MUTEX. Before to acquire forks, a philosopher would do a DOWN an MUTEX. After replacing 
the forks, she would do an UP on MUTEX. From a practical one, it has a performance bug: only one 
philosopher can be eating at any instant. With five forks available, we should be able to allow two 
philosophers to eat at the same
time.


Let us consider the method, which allows the maximum parallelism for
arbitrary number of philosophers. It uses as array to keep track of whether a philosopher is 
eating, thinking or hungry. A philosopher may move into eating state if neither neighboris eating. 
Note that each philosopher has two neighbors: left and right. The program uses an array of 
philosophers, one per philosopher,
so hungry philosophers can be blocked if the needed forks are busy.

A demonstration video is available at https://www.youtube.com/watch?v=Ar6ezhwVNdg.
