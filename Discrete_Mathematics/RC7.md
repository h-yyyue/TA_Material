# RC7

[TOC]



## Before start

hw5.5(ii)

![image-20230717012748739](C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717012748739.png)

Edge length of Hasse Diagram can vary.

To provide explicit coordinate, set the edge length as a converged series, like $\frac{1}{(2n+1)^2}$

## Graph Homomorphism

Definition:

* simple graphs G and H
* a map from V(G) to V(H) which takes edges to edges

=> **nonedge can be mapped to anything**

=> There is an injective homomorphism from *G* to *H* (i.e., one that never maps distinct vertices to one vertex) if and only if *G* is a subgraph of *H*. 

If a homomorphism *f* : *G* → *H* is a bijection whose inverse function is also a graph homomorphism, then *f* is a graph isomorphism

>  Definition in slides:
>
> Graphs G and H are isomorphic if there exists f : G → H and g : H → G such
> that $g ◦ f = id_G$ and $f ◦ g = id_H$,

Note: Two graphs *G* and *H* are **homomorphically equivalent** if *G* → *H* and *H* → *G*. The maps are not necessarily surjective nor injective. 

Can you give an example that is homomorphically equivalent but not surjective or injective?



### Graph Coloring

**Theorem**: A graph G is bipartite iff there exists a graph homomorphism $f: G \rightarrow K_2$ 

We can extend our theorem a little bit:

**Theorem**: A graph G is r-colorable ⇔ there exists a homomorphism from G to Kr

**Corollary**: A coloring of a graph G is precisely a homomorphism from G to some complete graph.

Firstly, let's defined r-colorable:

A proper coloring of a graph G is an assignment of colors to V (G) such that **no two adjacent vertices have the same color.**

A graph’s **chromatic number** is the minimum number of colors needed to properly color the graph. 

We say that a graph is n-colorable if it can be properly colored with n colors.

Now try to prove the theorem!



Example: 

![image-20230717023429829](C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717023429829.png)

Example: 

If we have 6 final periods with exams already scheduled such that no student must take consecutive exams, we can model this schedule as :

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717024909852.png" alt="image-20230717024909852" style="zoom: 33%;" />

where each vertex is a final exam period and there exists an edge between vertices if a student can be scheduled to to take an exam in both time slots.(we want to ensure that no student is scheduled to take 2 exams in consecutive periods)

Consider the following exams, is it possible to assign a suitable schedule for them? (edge means there exists student taking both of them)

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717025147724.png" alt="image-20230717025147724" style="zoom: 33%;" />



## Spanning Tree

T is a spanning tree of G

* subgraph
* tree = connected + without cycles
* V(T) =V(G) contain all vertices

**Theorem:** For connected graph with $|V(G)|\ge2$, subgraph H is a spanning tree

$\iff$ H is a minimal connected graph with V(T) =V(G)

$\iff$H is a maximal subgraph without cycles



## Kruskal’s Algorithm

Find a minimum-cost tree 

Greedy approach

* Maintain a “forest,” or a group of trees /disjoint sets
* Iteratively select cheapest edge in graph
  * If adding the edge forms a cycle, don’t add it
  * Otherwise, add it to the forest
* Continue until all vertices are part of the same set

Best for sparse graphs

Example:

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717005613919.png" alt="image-20230717005613919" style="zoom: 33%;" />

### Matroid

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717031100677.png" alt="image-20230717031100677" style="zoom: 25%;" />

Actually they are the same structure: Matroid

There are many way to define the matroid, let's see the version of independent set:

A matroid, M, defined by independent sets comes with two pieces. We call the first piece, E, the ground set of M. E is a collection of elements.

The second piece is $\mathcal{I}$, the collection of independent sets of M. We write M = (E, $\mathcal{I}$). Elements of $\mathcal{I}$ are subsets of E satisfying some properties, and we call the elements of $\mathcal{I}$ independent. 

1. ∅ ∈ $\mathcal{I}$
2. If A ∈ $\mathcal{I}$ and B ⊂ A, then B ∈ $\mathcal{I}$
3. If A ∈ $\mathcal{I}$, B ∈ $\mathcal{I}$ and |B| > |A|, then there is b ∈ B\A with A ∪ {b} ∈ $\mathcal{I}$

Example: Let E = {1, 2, 3, 4}. Let I = {∅, {1}, {2}, {3}, {4}, {12}, {13}, {14}, {23}, {24}, {34}}. In words, all the zero, one, and two element subsets of E are independent. 

Example: Graphic Matroids (also known as cycle matroids of a graph). Let G = (V, E) be an undirected graph. Matroid M = (E,  $\mathcal{I}$), where $\mathcal{I}$ = {F ⊆ E : F is acyclic}; i.e., forests in G.

click the links below if you want to learn more about Matroid

[lec8.pdf (mit.edu)](https://math.mit.edu/~goemans/18438F09/lec8.pdf)

## Dijkstra’s Algorithm

shortest path spanning tree for a certain vertex

Greedy Approach

* Separate vertices into two groups:
  * “Innies”: vertices that are present in your partial MST at any point in time
  * “Outies” : the other vertices
* Iteratively add nearest outie, converting to an innie

Best for dense graphs

Example: 

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717005313244.png" alt="image-20230717005313244" style="zoom: 25%;" />

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717005328924.png" alt="image-20230717005328924" style="zoom:25%;" />

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717005340718.png" alt="image-20230717005340718" style="zoom:25%;" />

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717005351830.png" alt="image-20230717005351830" style="zoom:25%;" />

Detailed approach: 

* Do the following until all vertices have been marked as “innies”:
  * Choose the “outie” vertex X that is the smallest distance from any
    “innie”
  * Add X to the innie tree; keep track of its “parent” (closest innie), so you
    know what edge connects it to the tree
  * Update vertices connected to the new “innie” with new weights and a
    new parent index if this weight is smaller than their previous weight

<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717005441283.png" alt="image-20230717005441283" style="zoom:50%;" />

## Basic Number Theory



<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717011238848.png" alt="image-20230717011238848" style="zoom:50%;" />

Another way to prove:

Well-Ordering Principle: every non-empty subset of integers which is bounded below has a minimal element. Like most axioms, this is formalized “common sense.”

How to use the Well-Ordering Principle to prove the Division Algorithm Theorem?





<img src="C:\Users\hyhy\AppData\Roaming\Typora\typora-user-images\image-20230717011444079.png" alt="image-20230717011444079" style="zoom:50%;" />

Exercise: $524a+148b=gcd(524, 148)$. Find a,b.





## Reference

* Umich EECS 281 Lab9 slides
* Umich MATH 412 worksheet 1
* [matroids](https://math.berkeley.edu/~charles/whatis/matroids.pdf)
* [davis-homomorphism-ups-434-2013](http://buzzard.ups.edu/courses/2013spring/projects/davis-homomorphism-ups-434-2013.pdf)
* [lec8(mit.edu)](https://math.mit.edu/~goemans/18438F09/lec8.pdf)