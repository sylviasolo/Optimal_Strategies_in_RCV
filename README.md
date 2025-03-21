# Optimal_Strategies_in_RCV
This repository contains codes that can be used to find optimal vote-addition strategies in ranked-choice voting (RCV). 

We develop a computational framework to find optimal vote-addition strategies for each candidate -- if we want a candidate to place in the top $k$ of the election, what is the optimal (requiring the minimum number of additional ranked ballots) vote addition strategy? Our algorithmic framework is as follows (and as detailed in our paper), given $n$ candidates and $m$ unique voter ballots.

(1) Each set of ballots induces a structure, referring to the outcome order (main-structure) and the round-specific elimination or winning order (sub-structure). Of course, given an initial set of votes, one can reach any alternative structure by adding enough votes.  Given a budget of $B$ additional votes, we first develop an algorithm to optimally (if possible) reach a given structure in $O(mn)$ time. Then, a binary search on the budget $B$ yields the optimal strategy to efficiently reach a given structure. 

However, with many candidates, there are a prohibitively large number of structures: there are $n!$ possible orders (main structures), of which the candidate would be in the top $k$ in $k \times (n - 1)!$ main structures. Each main structure has $2^{n-1}$ sub-structures. Naively, then, finding an optimal strategy requires finding the minimum vote additions over $k \times (n - 1)! \times 2^{n-1}$ structures.  

(2) Thus, we develop multiple approaches to reduce the election size, without affecting the optimality of the calculated strategies. (a) Given a budget of $B$ additional votes and status quo vote data, we next give an algorithm with $O(mn^4)$ complexity that removes a set of irrelevant candidates who will be eliminated first regardless of how the $B$ votes are added. (b) We show that for any set of $k$ winners, there are only $\sum_{j=1}^{k}$ $\mathcal{C}^n_k$ feasible substructures. Then, we show how to reduce the number of substructures further given status quo vote data. We give an algorithm with $O(mn^2)$ complexity that reduces the number of feasible sub-structures that can lead to an optimal win. 

This repository contains preliminary codes, functions to reach any desired structure of a set of winners, to find allocation to flip a social choice order, etc. As given above, it also contains codes that are used to trim down the election instance.

Finally, it contains codes that perform our case study analyses. This includes the strategies of leading candidates, both under perfect information and bootstrap data. 
