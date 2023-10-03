# Basic Steps
1. Initialization: generate initial population at random
2. Fitness Eval; every individual in the population
3. Repeat the following generations(stopping cond not met)
	1. Selection: select two parents based on their fitness
	2. Crossover: produce offspring viw selected parents
	3. Mutation: random changes
	4. Eval: eval the fitness of the offspring
	5. Replacement: use the new offspring to replace the current population
4. Stoping condition:
	1. Run given generation
	2. Satisfactory solution is found

## Selection
### Roulette Wheel Selection
- We end up selecting the population with the lower fitness due to the subtraction (review)
### Tournament Selection
### Rank Selection

## Crossover Techniques
- One point
	- A crossover point is selected and genes from the parents are combined based on this point
- Two Point
	- Two crossover points are selected and parent genes are crossed between those two points
- Uniform
	- Genes from both parents are mixed uniformly

## Mutation Techniques
- Bit Flip Mutation
	- A random bit in the individual’s encoding is flipped.  
- Swap Mutation
	- Two random genes in the individual’s encoding are   swapped.  
- Inversion Mutation
	- A random subset of genes in the individual’s

## Selection Techniques
- Elitism
	- The best individuals from the old generation are carried over to the new generation.  
- Generational Replacement
	- The entire old generation is replaced by the new generation.  
- Steady-State Replacement
	- Only a portion of the old generation is replaced by the new generation. The rest of the individuals are carried over.

## Parameter Setting
Should be Balanced  
- multiple experiments with different parameter settings to understand how each influences the GA’s performance for a specific problem.  
- In general  
- High crossover rate  
- Low mutation rate
## Steps
- Initialize population with random permutations  
- Repeat until termination criteria met:  
- Evaluate fitness for each permutation in the population  
- Select parents for crossover based on fitness  
- Apply crossover operators to create child permutations  
- Apply mutation operators to introduce small changes in child permutations  
- Replacement  
- Optionally apply elitism  
- Check for termination criteria