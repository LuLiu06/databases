Exercise 2: Single Table Query

Question 1:

select * from goal;

<img width="795" alt="Screenshot 2024-09-09 at 1 55 42 PM" src="https://github.com/user-attachments/assets/5f573cb5-c72c-4e2c-aaa0-384933267028">


Question 2:

select name,type from airport where iso_country='FI';

<img width="528" alt="Screenshot 2024-09-09 at 9 34 44 PM" src="https://github.com/user-attachments/assets/038f7ae2-77b5-4494-869f-5cc69f3a547c">


Question 3:

select name from airport where iso_country="FI"order by name;

<img width="326" alt="Screenshot 2024-09-09 at 9 40 41 PM" src="https://github.com/user-attachments/assets/f2bf028e-6f3e-4359-9e12-959e717dd1a7">


Question 4:

select name,type from airport where iso_country="FI"order by type,name;

<img width="681" alt="Screenshot 2024-09-09 at 9 45 59 PM" src="https://github.com/user-attachments/assets/7a235e6c-812c-4305-8a28-cc7341fc5c33">


Question 5:

select name from country where name like "F%";

<img width="514" alt="Screenshot 2024-09-09 at 9 49 36 PM" src="https://github.com/user-attachments/assets/86fc9535-f368-4984-a11b-b032edf892eb">


Question 6:

select name from country where name like "%F%";

<img width="485" alt="Screenshot 2024-09-09 at 9 52 04 PM" src="https://github.com/user-attachments/assets/9b3ddd6e-e024-4d41-af60-5b159ec5713f">


Question 7:

select location from game where screen_name="Vesa";

<img width="534" alt="Screenshot 2024-09-09 at 9 56 02 PM" src="https://github.com/user-attachments/assets/7281abba-ad4c-480c-95c8-e552c1e00e9a">


Question 8:

select co2_consumed from game where screen_name="Ilkka";

<img width="580" alt="Screenshot 2024-09-10 at 10 34 38 AM" src="https://github.com/user-attachments/assets/48eda9cc-0074-46aa-9994-1453997a5443">


Question 9:

select distinct co2_budget from game;

<img width="442" alt="Screenshot 2024-09-09 at 10 12 10 PM" src="https://github.com/user-attachments/assets/9299eb68-19cf-4540-b9d3-cd96dd669722">


Question 10:

select screen_name,co2_budget,co2_consumed,@co2_left:=co2_budget-co2_consumed as co2_left from game where screen_name="Ilkka";

<img width="822" alt="Screenshot 2024-09-10 at 10 28 54 AM" src="https://github.com/user-attachments/assets/13cea131-d207-46c3-b199-c65ac4bc6af9">


Exercise 3: Multiple Table Queries


Question 1:

select country.name as "country name",airport.name as "airport name"
from country,airport
where airport.iso_country=country.iso_country and country.name="Iceland";

<img width="833" alt="Screenshot 2024-09-10 at 2 12 08 PM" src="https://github.com/user-attachments/assets/63ea2166-b85e-4a62-8415-81d1ef2f4f1c">


Question 2:

select airport.name as "airport name" from airport,country where airport.type like '%larg%'and airport.iso_country=country.iso_country;

<img width="833" alt="Screenshot 2024-09-10 at 2 17 52 PM" src="https://github.com/user-attachments/assets/064581d9-63cc-4029-b178-34f4288f8022">


Question 3:

select country.name as "country_name",airport.name as "airport_name"
from airport,country
where country.continent="AN" and airport.iso_country=country.iso_country;

<img width="698" alt="Screenshot 2024-09-10 at 2 25 50 PM" src="https://github.com/user-attachments/assets/9d410d21-60ed-4b19-8430-4f313a84531e">


Question 4:

select airport.elevation_ft
from airport,game
where airport.ident=game.location and game.screen_name="Heini";

<img width="503" alt="Screenshot 2024-09-10 at 2 33 54 PM" src="https://github.com/user-attachments/assets/56a49aa6-95fe-4f0c-9b36-a543d15bede7">


Question 5:

select airport.elevation_ft *0.3048 as "elevation_m"
from airport,game
where airport.ident=game.location and screen_name="Heini";

<img width="530" alt="Screenshot 2024-09-10 at 5 00 32 PM" src="https://github.com/user-attachments/assets/75c91cfe-f7ae-47aa-b3c7-1387a8199bc3">


Question 6:

select airport.name
from airport, game
where airport.ident=game.location and screen_name="Ilkka";

<img width="459" alt="Screenshot 2024-09-10 at 5 05 29 PM" src="https://github.com/user-attachments/assets/7ab51d98-7953-4ef1-b3d3-c7214ca7398c">


Question 7:

select country.name
from country,game,airport
where country.iso_country=airport.iso_country
      and airport.ident=game.location
      and screen_name="Ilkka";

<img width="386" alt="Screenshot 2024-09-10 at 5 08 58 PM" src="https://github.com/user-attachments/assets/53e35c2b-e0c4-48ad-8c49-dee79d7e56dc">


Question 8:

select goal.name
from goal,goal_reached,game
where goal.id=goal_reached.goal_id
   and goal_reached.game_id=game.id
   and game.screen_name="Heini";

<img width="308" alt="Screenshot 2024-09-10 at 5 13 17 PM" src="https://github.com/user-attachments/assets/22f9e561-b082-44c9-b95c-24e0bc6e1bd4">


Question 9:

select airport.name
from airport,game,goal_reached,goal
where goal.id=goal_reached.goal_id
   and goal_reached.game_id=game.id
   and game.location=airport.ident
   and game.screen_name="Ilkka"
   and goal.name="CLOUDS";

<img width="329" alt="Screenshot 2024-09-10 at 5 17 06 PM" src="https://github.com/user-attachments/assets/33a06bb0-f0b4-4e47-bce4-787370a6c831">


Question 10:

select country.name
from country,airport,game,goal_reached,goal
where goal.id=goal_reached.goal_id
   and goal_reached.game_id=game.id
   and game.location=airport.ident
   and airport.iso_country=country.iso_country
   and game.screen_name="Ilkka"
   and goal.name="CLOUDS";

<img width="391" alt="Screenshot 2024-09-10 at 5 21 50 PM" src="https://github.com/user-attachments/assets/0a3acbcb-8de8-40f6-b94c-3289aba5bb09">



Exercise 4: Join


Question 1:

select country.name as "country name",airport.name as "airport name"
from country
inner join airport on airport.iso_country=country.iso_country
where airport.scheduled_service="yes" and country.name="Finland";

<img width="657" alt="Screenshot 2024-09-11 at 9 40 04 PM" src="https://github.com/user-attachments/assets/5fb2fc6a-7708-4a0f-b90d-8b065e13cccd">


Question 2:

select game.screen_name,airport.name
from game
inner join airport on airport.ident=game.location;

<img width="453" alt="Screenshot 2024-09-11 at 9 34 55 PM" src="https://github.com/user-attachments/assets/7d8ee86a-e4b3-4315-92e6-5498fa6ecf1c">


Question 3:

select game.screen_name,country.name
from game
inner join airport on game.location=airport.ident
inner join country on airport.iso_country=country.iso_country;

<img width="516" alt="Screenshot 2024-09-11 at 9 33 06 PM" src="https://github.com/user-attachments/assets/baea9a6a-57a8-4fa8-acd1-7cc05368dd63">


Question 4:

select airport.name,game.screen_name
from airport
left join game on game.location=airport.ident
where airport.name like "%Hels%";

<img width="449" alt="Screenshot 2024-09-11 at 9 26 46 PM" src="https://github.com/user-attachments/assets/3f8ecc58-8e79-47a6-baa1-b6da4f884de0">


Question 5:

select goal.name,game.screen_name
from goal
left join goal_reached on goal.id=goal_reached.goal_id
left join game on game.id=goal_reached.game_id;

<img width="459" alt="Screenshot 2024-09-11 at 9 20 37 PM" src="https://github.com/user-attachments/assets/cfa5774d-bb1b-4d01-a20a-8c460efbbd2c">



Exercise 5: Subqueries

Question 1:


select name 
from country
where iso_country in
(select iso_country from airport
where name like"%Satsuma%");

<img width="831" alt="Screenshot 2024-09-25 at 11 09 57 PM" src="https://github.com/user-attachments/assets/bae0090f-b09c-42d0-9350-57cce7b8d6b4">


Question 2:

select name
from airport
where iso_country in
(select iso_country from country
where name="Monaco");

<img width="833" alt="Screenshot 2024-09-25 at 11 11 59 PM" src="https://github.com/user-attachments/assets/6f8e3541-0adb-48be-b0f8-190ff8155d2d">


Question 3:




