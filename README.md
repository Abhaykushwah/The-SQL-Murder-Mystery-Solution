# The SQL Murder Mystery Solution
Solution for https://mystery.knightlab.com/


![Sql muder mystry](https://github.com/user-attachments/assets/de88de45-a7b6-4d0b-a064-de86961e20d5)

**Problem Statement :** 

A crime has taken place and the detective needs your help. The detective gave you the crime scene report, but you somehow lost it. You vaguely remember that the crime was a ​murder​ that occurred sometime on ​Jan.15, 2018​ and that it took place in ​SQL City​. Start by retrieving the corresponding crime scene report from the police department’s database.

```
select * from crime_scene_report where city="SQL City" and type= "murder" and date = 20180115;
```
Decription says "Security footage shows that there were 2 witnesses. The first witness lives at the last house on "Northwestern Dr". The second witness, named Annabel, lives somewhere on "Franklin Ave"."


```
select * from person where address_street_name="Northwestern Dr" and address_number=4919;
```
<pre>
id     name             license_id  address_number  address_street_name  ssn
14887  Morty Schapiro	118009      4919            Northwestern Dr      111564949
16371  Annabel Miller	490173      103              Franklin Ave        318771143

</pre>

  ```
 select * from person where (address_street_name="Northwestern Dr" and address_number=4919)
 or (address_street_name like "%Franklin Ave%" and name like "%Annabel%");
```
Got the person_id

```
select * from interview where person_id=16371 or person_id=14887;
```

**person_id :** 14887   **transcript :**      	I heard a gunshot and then saw a man run out. He had a "Get Fit Now Gym" bag. The membership number on the bag started with "48Z". Only gold members have those bags. The man got into a car with a plate that included "H42W".

**person_id :** 16371   **transcript :**      	I saw the murder happen, and I recognized the killer from my gym when I was working out last week on January the 9th.

```
select * from get_fit_now_member where membership_status="gold" and id like "48Z%";
```
According to statement we got two guys let's filter out who is the muderer.

```
select * from get_fit_now_check_in where  membership_id="48Z55" ;
```
The guy with membership id 48Z55 is muderer as by our 2nd witness : recognized the killer from my gym when I was working out last week on January the 9th.

Submit the answer with this ```INSERT INTO solution VALUES (1, 'Jeremy Bowers'); SELECT value FROM solution;```

**And it says :** Congrats, you found the murderer! But wait, there's more... If you think you're up for a challenge, try querying the interview transcript of the murderer to find the real villain behind this crime. If you feel especially confident in your SQL skills, try to complete this final step with no more than 2 queries. Use this same INSERT statement with your new suspect to check your answer.


```
select * from interview where person_id=67318;
```
I was hired by a woman with a lot of money. I don't know her name but I know she's around 5'5" (65") or 5'7" (67"). She has red hair and she drives a Tesla Model S. I know that she attended the SQL Symphony Concert 3 times in December 2017.

```
select * from drivers_license where height =65 or height=67 and hair_color="red" and 
car_make="Tesla" and car_model="Model S" and gender="female";
```
There are lot of results with this let's filter out with Facebook Event CheckIn

```
select * from facebook_event_checkin where event_name like "%SQL Symphony Concert%"
and date like "201712__" group by person_id having count(person_id)=3;
```
We got two person_id's 99716 and 24556

```
select * from drivers_license where id = 202298
```
Got the Master mind 

```
select * from person where id =99716;
```
Miranda Priestly is the Master Mind

Submit the solution by ```INSERT INTO solution VALUES (1, 'Miranda Priestly');SELECT value FROM solution;```
