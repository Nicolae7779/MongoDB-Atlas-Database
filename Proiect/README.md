# Proiect

## Prerequisites:
- Download the latest US Zips dataset from https://simplemaps.com/data/us-zips (choose the free tier). The dataset has approximately 33k entries.
- Create a MongoDB instance. You may use your own MongoDB Atlas instance in cloud or use a local instance. For local instances Docker is preferred, but you may also choose to install MongoDB as a standalone server on your OS.
- Import the dataset into the MongoDB instance.


## Requirements:
 a) Get the states with a total population of over 10 million.
  
 b) Get the average city population by state.

 c) Get the largest and the smallest city in each state.

 d) Get the largest and the smallest counties in each state.

 e) Get the nearest 10 zips from one of Chicago's landmarks, the Willis Tower situated at coordinates 41.878876, -87.635918.

 f) Get the total population situated between 50 and 200 kms around New York's landmark, the Statue of Liberty at coordinates 40.689247, -74.044502.



## a) Get the states with a total population of over 10 million.

db.People.aggregate() - pentru operații de agregare($group, $match, $sort) într-un singur pipeline
 
$group - am grupat documentele astfel încât să-mi afișeze doar state_name și state_population

$sum - se calculează suma populației "$populaion" din toate documentele care au același "$state_name"

$match - filtrează documentele pe baza unui criteriu

$gt - mai mare decât

$sort - sorteză ca documentele să fie în ordine crescătoare (1) sau descrescătoare (-1)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/a/population%20over%2010%20million.png)


$limit: 10 - limitează ca numărul de documente returnate să fie 10

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/a/population%20over%2010%20million%20%20%202.png)


toArray().slice(0, 10) sau toArray().slice(10) - toArray() convertește rezultatul într-un array de documente, slice(10) sau slice(0, 10) returnează primele 10 elemente din array

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/a/population%20over%2010%20million%20%20%20%203.png)


## b) Get the average city population by state.

afișeză numărul total de documente care conțin numele statului "Delaware"

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/b/How%20many%20cities%20are%20in%20a%20specific%20state.png)


Fiind 68 de documente care conțin numele de "Delaware", se adună populația din fiecare document 

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/b/Total%20population%20in%20a%20specific%20state.png)


afișează toate orașele și populația din statul "Delaware"

city: 1, _id: 0, population: 1 - toate documentele afișate vor conține doar city și population

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/b/all%20the%20cities%20in%20a%20specific%20State.png)


afișează populația totală din toate statele

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/b/total%20population%20by%20states.png)


afișează populația totală și numărul total de orașe din fiecare stat

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/b/all%20the%20population%20and%20all%20the%20cities%20in%20the%20states.png)


afișează populația medie a orașelor din fiecare stat

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/b/Average%20State%20population.png)

## c) Get the largest and the smallest city in each state.

Afișează toate orașele din statul "American Samoa"

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/c/all%20the%20cities%20in%20a%20specific%20state.png)


Afișează toate orașele din fiecare stat care au populația 0

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/c/all%20the%20cities%20with%200%20population%20in%20every%20state.png)


Afișează toate orașele din fiecare stat în ordine crescătoare după populație

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/c/All%20the%20cities%20in%20each%20state%20in%20ascending%20order%20by%20population.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/c/All%20the%20cities%20in%20each%20state%20in%20ascending%20order%20by%20population%20%20%20%202.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/c/All%20the%20cities%20in%20each%20state%20in%20ascending%20order%20by%20population%20%20%20%20%203.png)


Se sorteză în ordine descrescătoare a populației

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/c/The%20smallest%20and%20largest%20cities%20by%20population%20in%20every%20state.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/c/The%20smallest%20and%20largest%20cities%20by%20population%20in%20every%20state%20%20%20%202.png)

## d) Get the largest and the smallest counties in each state.


Afișează toate orașele și populația lor din comitatul Laramie care, la rândul său, se află în statul Wyoming

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/all%20cities%20in%20a%20specific%20county.png)


Afișează toate orașele și populația lor din comitatul Larimer care, la rândul său, se află în statul Wyoming

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/all%20cities%20in%20a%20specific%20county%20%20%20%202.png)


Afișează toate comitatele și populația lor în ordine descrescătoare din statul Wyoming

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/the%20population%20of%20counties%20in%20descending%20order%20in%20the%20state%20of%20Wyoming.png)


Afișează toate comitatele și populația lor în ordine descrescătoare din statul Wyoming 

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/the%20entire%20population%20of%20counties%20in%20descending%20order%20in%20the%20state%20of%20Wyoming.png)


Afișează toate comitatele și populația lor în ordine crescătoare din statul Wyoming 

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/the%20entire%20population%20of%20counties%20in%20ascending%20order%20in%20the%20state%20of%20Wyoming.png)


Afișează toate comitatele și populația lor din toate statele

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/the%20entire%20population%20of%20the%20counties%20in%20each%20state.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/the%20entire%20population%20of%20the%20counties%20in%20each%20state%20%20%20%202.png)


Afișează cel mai mic și larg comitat din fiecare stat

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/The%20smallest%20and%20biggest%20county%20in%20each%20state.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/d/The%20smallest%20and%20biggest%20county%20in%20each%20state%20%202.png)


## e) Get the nearest 10 zips from one of Chicago's landmarks, the Willis Tower situated at coordinates 41.878876, -87.635918.

Document de tip json

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/a%20Document%20that%20has%20lat%20and%20lng.png)


Din toate documentele lat si lng au fost înlocuite cu un array de coordonate 

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/Change%20all%20documents%20containing%20lat%20and%20lng%20in%20coordinates%20of%20type%20array.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/coordinates.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/coordinates%20of%20type%20array.png)


location - numele câmpului unde sunt stocate coordonatele geografice al documentelor

$geoWithin - este folosit pentru a verifica dacă un punct se află într-o anumită zonă

$centerSphere - este folosit pentru a defini un cerc într-un sistem de coordonate sferic

[[-87.635918, 41.878876], 2.5 / 6378.1] - acest array reprezintă centrul cercului și raza acestuia

Coordonatele [-87.635918, 41.878876] - reprezintă longitudinea și latitudinea centrului cercului

2.5 / 6378.1 - reprezintă raza cercului în kilometri, exprimată în raport cu raza Pământului

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/geoWithin.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/geoWithin%20%20%20%202.png)


$near - este folosit pentru a găsi documentele care sunt în apropierea unui anumite locații greografice

$geometry - este folosit pentru a specifica o formă geometrică (de exemplu: un punct)

$maxDistance - specifică distanța maximă în radiani, metri, kilometri, sau mile

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/near%2C%20geometry%2C%20maxDistance.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/near%2C%20geometry.png)


maxDistance fiind 10000, limit(10), afișează doar primele 10 documente

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/near%2C%20geometry%2C%20maxDistance%2C%20limit.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/e/near%2C%20geometry%20%20%20%202.png)

## f) Get the total population situated between 50 and 200 kms around New York's landmark, the Statue of Liberty at coordinates 40.689247, -74.044502.


![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/f/geoWithin%2C%20centerSphere.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/f/geoWithin%2C%20centerSphere%20%202.png)

![imagine](https://github.com/Nicolae7779/MongoDB-Atlas-Database/blob/main/Proiect/imagini/f/geoWithin%2C%20centerSphere%20%203.png)














