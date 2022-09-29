# murder-mystery
SQL Murder Mystery (https://mystery.knightlab.com/)
Here are the queries I used to find the murderer in SQL City.

```
SELECT * FROM crime_scene_report 
WHERE type = "murder" AND city = "SQL City"

SELECT * FROM person 
WHERE address_street_name = "Northwestern Dr"
ORDER BY address_number DESC

SELECT * FROM person 
WHERE name LIKE "%Annabel%"
AND address_street_name = "Franklin Ave"

SELECT name, transcript
FROM interview
JOIN person
ON interview.person_id = person.id
WHERE name = "Morty Schapiro" OR name = "Annabel Miller"        

SELECT * FROM get_fit_now_member member
JOIN get_fit_now_check_in gymcheck
ON member.id = gymcheck.membership_id
JOIN person
ON person.id = member.person_id
JOIN drivers_license license
ON license.id = person.license_id
WHERE membership_id LIKE "48Z%" AND check_in_date = "20180109" AND license.plate_number LIKE "%H42W%"
              
SELECT transcript FROM interview
JOIN person
ON person.id = interview.person_id
WHERE person.name = "Jeremy Bowers"

SELECT name FROM facebook_event_checkin fbcheck
JOIN person
ON person.id = fbcheck.person_id
JOIN drivers_license license
ON license.id = person.license_id
WHERE LOWER(license.car_make) = "tesla"
AND fbcheck.event_name LIKE "SQL%"
```
