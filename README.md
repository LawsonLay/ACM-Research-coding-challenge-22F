**For the ACM Coding Challenge,**

> Accident-prone Cars by Lawson Lay

The goal of this program is to sort data from the given CarsForSale's cars_raw.csv based on certain conditions that are deemed to contribute to a car's likelihood to be in an accident.
The conditions to which a car is determined to be more accident prone will be based on the following articles:
* https://insurify.com/insights/car-models-with-the-most-accidents-2021/
* https://www.855mikewins.com/michigan-car-accident-lawyer/is-your-car-one-of-the-10-most-accident-prone-vehicles/
* https://www.cglawoffices.com/blog/2022/06/the-most-accident-prone-types-of-vehicles/
* https://www.collisionrepairmag.com/eye-catching-crashes-sports-cars-found-to-be-particularly-accident-prone-study-finds/

According to the following articles, the common attributes of cars that are more accident-prone tend to have are:
* Sport, SUV, or Luxury Type
* High-selling (ex. Ford F150)
* Large Size
* Imported
* Old Age (Discontinued)

While a proper research into this topic might go something like:
*To what extent does a car's attributes affect a driver's likelihood to be in a accident?*

Which could have a theoretical counter-argument stating that it is mostly the driver's own fault for most vehicular accidents.

However, that's not the goal today, so one quick Google search of "Accident-prone cars", and here we are now.

Looking at the CarsForSale spreadsheet, the columns which meet or are related to our aforementioned accident-prone attributes are as follows:
* Reliability Rating
* Mileage
* -Transmission-
* -Engine-
* Performance Rating
* Price
* Year
* Make
* Used/New
* Deal Type

*NOTE: Transmission and Engine omitted due to added parsing complexity.*

Now with our interesting columns defined, the next step is to determine how being more accident-prone will be visualized.
For time-crunch sake, a simple "accident-prone" score calculated by some makeshift algorithm will be used. A list of the top 10 accident prone cars will be printed out along with their "accident-prone" score.

To create a accident-prone score, the different attributes of a car must be weighted against each other in their "accident-prone"-ness.
According to the four article's ratings on most accident prone cars, what the most accident-prone cars have in common are their type. Specifically, them being of sport or luxury type. Second is affordability therefore availability. If more people can buy a car, the car will be more common on the streets, therefore more common to be in an accident. Then the third factor this program will look at is age, since another common factor is old age of the vehicle.

The columns can then be split into three main score factors divided into subfactors:
> Type
* Make
* Performance Rating

> Accessibility
* Price
* Deal Type

> Age
* Reliability Rating
* Year
* Used/New
* Mileage

Note that accessibility is referring to the ability of many people to access or buy the car.

The main three factors don't contradict each other, so a high level look at the score algorithm could look like the following with weights:

**ACCIDENT PRONE SCORE = (0.60)TYPE + (0.40)ACCESS + (0.20)AGE**
 
Then define the subfactors:

**TYPE = MAKE + PERFORMANCE_RATING**

**ACCESS = DEAL TYPE - PRICE**

**AGE = YEAR + USED_NEW + MILEAGE - RELIABILITY_RATING**

*NOTE: Subfactor scales in the code*

For type, the make and performance rating can add to the accident prone score from being luxury and performing too well (Sport car like).
For access, the greater the deal and the lower the price, the accessible the car will be.
For age, how old a car is from manufacture date, if it is used, and the mileage are all additive to the accident prone score. 
The only exception is reliability rating, where a lower reliability rating will equate to a greater accident prone score.

**RESULTS**
From this algorithm, the conclusion is that the most accident prone cars from the dataset are:

1. 2005 Used Lexus ES 330 Base (A5)
2. 2003 Used Mercedes-Benz SL-Class SL500 Roadster
3. 2010 Used BMW 535 i
4. 2005 Used Porsche Cayenne S
5. 2008 Used Lexus RX 350 Base
6. 2008 Used Mercedes Benz S-Class S 550 4MATIC
7. 2011 Used BMW 328 i xDrive

*Omitted duplicates*

Overall, the results are satisfactory. A Accident-prone score was produced. However, due to time constraints, some other factors were not considered which could make these results inaccurate.
A new algorithm with these factors considered will provide more accurate results.