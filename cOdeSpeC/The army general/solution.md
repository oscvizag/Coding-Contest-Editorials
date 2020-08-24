# Question

![Question](https://raw.githubusercontent.com/oscvizag/Coding-Contest-Editorials/master/cOdeSpeC/The%20army%20general/The%20army%20general.png)


# Explanation
## Special case of M = 1
A good start is to see what happens if M = 1. Suppose selected position by the captain is pos. Then,
```
numbering[i] = 0 if i = pos
numbering[i] = numbering[i – 1] + 1 if i > pos
numbering[i] = numbering[i + 1] + 1 if i < pos
```
where numbering is the resulting array. We can see that if i > pos, numbering[i] = i – pos and if i < pos, numbering[i] = pos – i. But this is the definition of absolute value. So numbering[i] = |i – pos| (where by |x| I denote absolute value of x).

## Take general case
For general case, suppose pos[1], pos[2], …, pos[M] are positions asked by the captain during the M rounds. For each i (0 <= i < N) you need to output max(|i – pos[1]|, |i – pos[2]|, …, |i – pos[M]|).
So now let’s calculate for a particular i (let’s forget for a moment we need to iterate each i, we’re interested only in a single value of i). Let’s maximize |i – a|, where a can be pos[1], pos[2], …, pos[M]. A property of absolute value says that |i – a| = max(a – i, i – a). So if we maximize the expressions (a – i) and (i – a), then take their maximum value, we’re done for the given i.

In both expressions i is a constant (since we’ve decided to calculate only for a particular value of i). Since i is constant, it can’t influence maximization. So we need to maximize (a) and (–a). Now it’s obvious we need to take maximum and minimum between pos[1], pos[2], …, pos[M]. Let max_value be the maximum and min_value be the minimum. The answer for a fixed i is max(max_value – i, i – min_value).

The only remained thing is to iterate over all possible i. We calculate at the beginning max_value and min_value, then we iterate i and print max(max_value – i, i – min_value).

## Time Complexity
The algorithm solves each test in O(N + M) time complexity.

## solution
```
#include <bits/stdc++.h>
using namespace std;

#define T_LIMIT 10000
#define N_LIMIT 100000

int main() {
	int t;
	scanf("%d", &t);

	while(t--) {
		int n, m;
		scanf("%d%d", &n, &m);

		int minm = 1111111, maxm = -minm;
		// Find the minimum and maximum.
		while(m--) {
			int x;
			scanf("%d", &x);
			minm = min(x, minm);
			maxm = max(x, maxm);
		}
		// print the answers
		for(int i=0; i<n; i++) {
			printf("%d ", max( abs(i-minm), abs(i-maxm)));
		}
		printf("\n");
	}

}
```
