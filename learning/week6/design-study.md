# Design Pattern Change Study


Overview
We proposed to study the design of automobiles. Using the methods
(200 words summary of the design study your team proposed)

#Overview

Our team proposed to study the design of automobiles. Using the methods described in the paper, "Collect, Decompile, Extract, Stats, and Diff: Mining Design Pattern Changes in Android Apps", by Khalid Alharbi and Tom Yeh, we considered design features of automobiles and how these impacted new car sales over time.

The following sections outline the phases of our proposed analysis:

#Collect Phase

The first step in our analysis involves collection of automobile data from websites such as Edmunds.com, Kelley Blue Book and the National Highway Traffic Safety Administration.
#Decompile Phase

The decompile phase involves translating the data collected into a format from which the features can be easily extracted.
**Depending on the data format we can get from, we may able to skip this phase, assuming the data format enable to extract it right away.


#Extract Phase

the following features are extracted from the decompiled data.

    Manufacturer
    Model
    Make
    Year
    Color
    Fuel (gas, electric, hybrid, diesel or alternative)
    Horse Power
    Engine Type
    Body Style
    Miles per gallon
    Drive Train (FWD, AWD, 4WD)
    Safety
    Reliability
    Number of passengers
    Size
    Transmission type (automatic, manual)
    Car Type (SUV, Minivan, Wagon, Crossover, etc.)

#Statistics Phase

During the statistics phase, we will:
1.select features of interest
2.calculate the number of units sold 
3.average sales price for various values of these features.

#Diff Phase

In the last step or our analysis, we consider 
1.how the number of units sold 
2.average sales price change over time for the features of interest.




