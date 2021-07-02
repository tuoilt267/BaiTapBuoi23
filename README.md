# BaiTapBuoi23
-- Hãy tìm tất cả những nam giới tuổi dưới 45

select p.* , DATE_FORMAT(FROM_DAYS(DATEDIFF(now(),birthdate)), '%Y')+0 AS Age 
FROM person p
where p.gender = "Male"
and  DATE_FORMAT(FROM_DAYS(DATEDIFF(now(),birthdate)), '%Y')+0 <45
order by Age
;
-- Hãy tìm tất cả những nữ giới làm nghề lái xe 'driver'

select * FROM person p
where p.gender = "Female"
and p.job = "driver"
;
-- Tính tỷ lệ nam/nữ lập trình viên trong tất cả tập dữ liệu

SELECT t.male/k.female tyle FROM 
(SELECT job, COUNT(*) as male
FROM person  
WHERE gender = "Male"
And job = "developer") as t
JOIN  
(SELECT job, COUNT(*) AS female
FROM person 
WHERE gender = "Female" 
AND job = "developer") as k on t.job  = k.job
;
-- Hãy tìm 5 thành phố có số lượng nữ lớn nhất
SELECT city, COUNT(*) as female
FROM person
WHERE gender= "Female"
GROUP BY city 
order by female DESC 
limit 5
