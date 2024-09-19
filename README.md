# The SQL Murder Mystery Solution
Solution for https://mystery.knightlab.com/

**Problem Statement :** 

A crime has taken place and the detective needs your help. The detective gave you the crime scene report, but you somehow lost it. You vaguely remember that the crime was a ​murder​ that occurred sometime on ​Jan.15, 2018​ and that it took place in ​SQL City​. Start by retrieving the corresponding crime scene report from the police department’s database.

```
select * from crime_scene_report where city="SQL City" and type= "murder" and date = 20180115;
```


```
select * from person where address_street_name="Northwestern Dr" and address_number=4919;
```
```
select * from person where address_street_name like "%Franklin Ave%" and name like "%Annabel%";
```


```
select * from interview where person_id=16371 or person_id=14887;
```


```
select * from get_fit_now_member where membership_status="gold" and id like "48Z%";
```


```
select * from get_fit_now_check_in where  membership_id="48Z55" ;
```


```
select * from interview where person_id=67318;
```


```
select * from drivers_license where height =65 or height=67 and hair_color="red" and 
car_make="Tesla" and car_model="Model S" and gender="female";
```


```
select * from facebook_event_checkin where event_name like "%SQL Symphony Concert%"
and date like "201712__" group by person_id having count(person_id)=3;
```


```
select * from person where id =24556 or id =99716;
```


```
select * from drivers_license where id = 202298
```
