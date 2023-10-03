---
tags:
  - project
  - dsa
Course: Data Structures and Algorithms 2
---
# Pseudocode
```txt

function: selectTopNChromosomes(n):
	elites[]
	sort population by fitness
	for i from 0 to n
		if(chromosome not in elites)
			add chromosome to elites	
	return elites

function: getDistance(currentCity, nextCity):
	return cityGraph[currentCity][nextcity]

function: evaluateFitness(individual):
	fitness = 0
	for city in in individual:
		fitness += getDistance(currentCity, nextCity)
	fitness += getDistance(lastCity, firstCity)
	return fitness
	
function: evaluatePopFitness():
	bestFitness = 0
	bestTour[]
	for each individual in population:
		currentTour = individual
		newFitness = evaluateFitness(individual)
		if(currentFitness < bestFitness)
			bestFitness = newFitness
			bestTour = currentTour
			
	return [bestFitness, bestTour]

function: selection(tournamentSize):
	tournamentPopulation
	for i from 1 to tournamentSize
		tournamentPopulaiton.push(randomChromosome)
	return best chromosome in tournamentPopulation
	
function: crossover(parents):
	point1 = randint from 0 to parentLength
	do 
		point2 = randint from 0 to parentLength 
	while point2 == point1
	for i from point1 to point2
		child1 at i = parent1 at i
		child2 at i = parent2 at i
	return [child1, child2]

function: mutate(chromosome):
	swapped[]
	foreach city in chromosome:
		if randomDouble <= mutationRate and city not in swapped
			do getRandomCity while randCity not in swapped or = city
			swap(city, randCity)
			swapped.push(city)

function: geneticAlgorithm(populationSize, maxGenerations):
	initializePopulation(populationSize)
	for generation from 1 to maxGenerations:
		currentBestFitness, currentBestTour = evaluatePopFitness()
		if(currentBestFitness betterThan bestFitness):
			bestFitness = currentBestFitness
			bestTour = currentBestTour
			
		newPopulation[]
		numElites = populationSize * elitismRatio
		for i from 1 to populationSize/2 - numElites:
			parent1 = tournamentSelection(tournamentSize)
			parent2 = tournamentSelection(tournamentSize)
			children = crossover(parents)
			mutate(children[0])
			mutate(children[1])
			newPopulation.pushBack(child1)
			newPopulation.pushBack(child2)
		elites[] = SelectTopNIndividuals(numElites)
		for each elite in elites
			newPopulation.pushBack(elite)
	
		population = newPopulation
	
```