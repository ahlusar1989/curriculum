# Traffic simulation

## Description

Analyze the behavior of drivers on a new road to determine the optimal speed
limits.

## Objectives

### Learning Objectives

After completing this assignment, you should understand:

* The use of NumPy
* Complex stochastic simulations
* Basic statistical methods

### Performance Objectives

After completing this assignment, you should be able to:

* Create complex simulations
* Speak about your findings

## Details

### Deliverables

* A Git repo called traffic-simulation containing at least:
  * `README.md` file explaining how to run your project
  * a `requirements.txt` file
  * a suite of tests for your project

### Requirements  

* Passing unit tests
* No PEP8 or Pyflakes warnings or errors

## Normal Mode

We have a new section of road being built and do not know what the speed limit
should be. This section of road is 7 kilometers long.

* Kilometer 1: straight.
* Kilometer 2: slight curve. 40% higher slowing chance.
* Kilometer 3: straight.
* Kilometer 4: curve. 100% higher slowing chance.
* Kilometer 5: straight.
* Kilometer 6: slight curve. 20% higher slowing chance.
* Kilometer 7: straight.

![Road](road.png)

Your job will be to create a simulation and find the optimal speed limit. We
will start by simplifying the problem.

**Assumptions**

* Drivers want to go up to 120 km/hr.
* The average car is 5 meters long.
* Drivers want at least 4 car lengths between them and the next car.
* Drivers will accelerate 2 m/s up to their desired speed as long as they have
  room to do so.
* If another car is too close, drivers will match that car's speed until they
  have room again.
* If a driver would hit another car by continuing, they stop.
* Drivers will randomly (10% each second) slow by 2 m/s.
* This section of road will have a new car enter it every 2-6 seconds.
* This section of road is one lane going one way.

Given all this information, create a simulation of traffic on this road. Even
though the road is not circular in real life, you should treat it as such: cars
exiting the road start again at the beginning. This is to simulate a continuous
stream of traffic. When you start the simulation, add cars to the road every 2-6
seconds until the road is full. Then start collecting data after that point
now that you have a continuous stream.

The optimal speed limit is one standard deviation above the mean speed limit.
For ease of drivers, this should be rounded down to an integer.

Your final report should have a graph of traffic over time, showing traffic
jams, as well as your recommendation for the speed limit. Add any plots that
back up your analysis.

## Hard Mode

In addition to the requirements from **Normal Mode**:

The planning board has come back and given you a new requirement: this section
of road should not have more than an average of 10 fatalities per year.

We [know that a driver has a base fatality risk of 1 / 1463040 per km driven](http://journalistsresource.org/studies/environment/transportation/comparing-fatality-risks-united-states-transportation-across-modes-time).
This chance goes up by 3% for every 1 km/hr increase in speed. (To be clear,
this is an exponential increase. For ease of explanation, imagine that
the base risk is 1% at 1 km/hr. At 2 km/hr, the risk would be 1% * 1.03 =
1.03%. At 3 km/hr, the risk would be 1.03% * 1.03 = 1.0609%. At 4 km/hr,
1.0609% * 1.03 = 1.092727%.)

Come up with a new recommendation for the speed limit that will result in a
mean of 10 fatalities per year.

## Nightmare Mode

Calculate all of the above, but change your simulation to account for differing
types of drivers.

Driver type      | Normal   | Aggressive | Commercial
-----------------|----------|------------|------------
Acceleration     | 2 m/s/s  | 5 m/s/s    | 1.5 m/s/s
Desired speed    | 120 km/h | 140 km/h   | 100 km/h
Vehicle size     | 5 m      | 5 m        | 25 m
Minimum spacing  | 20 m     | 15 m       | 100 m
Slowing chance   | 10%/s    | 5%/s       | 10%/s
% of drivers     | 75%      | 10%        | 15%

* m = meters
* km = kilometers
* s = second
* h = hour

Alternately, use PyGame or Pyglet to show a live animation of your simulation.

## Notes

This is incredibly similar to real work that a highway planner would do. Using
these tools should highlight how randomness can be used to solve many
real-world problems.

Your simulations may take quite some time to run. You should create smaller
simulations and make sure they are giving you reasonable answers before scaling
up.

Remember that one simulation is meaningless: you need many simulations for the
law of large numbers to matter.

## Additional Resources

* Chapters 1 and 2 of [Monte Carlo Theory, Methods, and Examples](http://statweb.stanford.edu/~owen/mc/).
* [Traffic simulation on Wikipedia](https://en.wikipedia.org/wiki/Traffic_simulation).
