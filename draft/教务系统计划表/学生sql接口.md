# 学生sql接口

## 插入学生必修记录
```sql

-- 插入学生必修记录
DELIMITER $$
CREATE PROCEDURE IF NOT EXISTS insert_major_into_selec(IN new_cid INT, IN new_majid INT, IN new_phase INT, IN new_uid INT)
BEGIN
    DECLARE m INT;
    DECLARE selectcid_to_assign INT DEFAULT 0;
    DECLARE record_count INT;
    
    -- 计算 m
    SET m = (((new_cid * 1000) + new_majid) * 10 + new_phase);
    
    -- 降序查询 selec 中 selectcid 大于 m*100 且小于 (m+1)*100 的记录
    -- 并将第一条记录的 selectcid 赋值给 selectcid_to_assign
    SELECT selec.selectcid INTO selectcid_to_assign
    FROM selec
    WHERE selec.selectcid > m*100 AND selec.selectcid < (m+1)*100
    ORDER BY selec.selectcid DESC
    LIMIT 1;
    
    -- 如果存在记录，则赋值给 m
    IF selectcid_to_assign > 0 THEN
        SET m = selectcid_to_assign;
    ELSE 
        SET m = m*100 + 1;
    END IF;
    
    -- 统计 selec 表中 selectcid=m 的记录条数
    SELECT COUNT(*) INTO record_count FROM selec WHERE selectcid = m;
    
    -- 根据条数判断插入 m 或者 m+1
    IF record_count < 90 THEN
        INSERT INTO selec (selectcid, cid, majid, phase, uid, tid) 
        SELECT t1.selectcid, t1.cid, t1.majid, t1.phase, t1.uid, t2.tid 
        FROM (SELECT m AS selectcid, new_cid AS cid, new_majid AS majid, new_phase AS phase, new_uid AS uid) t1 
        LEFT JOIN (SELECT tid, selectcid FROM tclass) t2 ON t2.selectcid = t1.selectcid
        ON DUPLICATE KEY UPDATE selectcid = VALUES(selectcid), cid = VALUES(cid), majid = VALUES(majid), phase = VALUES(phase), uid = VALUES(uid), tid = VALUES(tid);
    ELSE
        INSERT INTO selec (selectcid, cid, majid, phase, uid, tid) 
        SELECT t1.selectcid, t1.cid, t1.majid, t1.phase, t1.uid, t2.tid 
        FROM (SELECT m + 1 AS selectcid, new_cid AS cid, new_majid AS majid, new_phase AS phase, new_uid AS uid) t1 
        LEFT JOIN (SELECT tid, selectcid FROM tclass) t2 ON t2.selectcid = t1.selectcid
        ON DUPLICATE KEY UPDATE selectcid = VALUES(selectcid), cid = VALUES(cid), majid = VALUES(majid), phase = VALUES(phase), uid = VALUES(uid), tid = VALUES(tid);
    END IF;
END$$
DELIMITER $$
call insert_major_into_selec(2,1,4,21001006);
DROP PROCEDURE insert_major_into_selec


```
## 插入学生选课记录
```sql

-- 插入学生选课记录
DELIMITER //
CREATE PROCEDURE IF NOT EXISTS insert_select_into_selec(IN new_selectcid INT, IN new_uid VARCHAR(255))
BEGIN
    -- 存储过程的逻辑
			DECLARE num INT;
			select COUNT(*) into num from selec where selectcid = new_selectcid;
			IF(num < 90) THEN
				insert into selec (cid, majid, phase,selectcid, tid, uid) select cid, majid, phase, selectcid, tid, new_uid from tclass where tclass.selectcid = new_selectcid;
				SET num = 1;
				ELSE SET num = 0;
			END IF;
			select num as result;
			
END //
DELIMITER ;
call insert_select_into_selec(101501, 21001004);
call insert_major_into_selec(2,1,4,21001006);
drop PROCEDURE insert_select_into_selec;
-- call insert_select_into_selec(101501, 2100104);
```

## 课程性质  全部课程

```sql
-- 设置课程性质字段
UPDATE a
SET nature = IF(subj IS NULL OR subj = '', 0, 3 * subj) +
IF(majid IS NULL, 0, 2 * majid) +
IF(required IS NULL, 0, required);


select DISTINCT phase ,t1.majid cmajid, required, t1.subj, selectcid, cname,  tname from course t1 join major t2 join (select tc.selectcid, tc.cid, tc.tid, tc.majid, tc.phase from tclass tc join selec sel on tc.selectcid = sel.selectcid where uid = 21001002) t3 on t3.cid = t1.cid join tea t4 on t4.id = t3.tid where phase = 4 and ((t2.majid = 1 and t2.subj = t1.subj ) or t1.subj is NULL) ORDER BY selectcid;  -- 分班后的大三上 全部课程

select  DISTINCT  cname,cid, t1.majid, required, t1.subj from course t1 JOIN major t2  where (t2.majid = 1 and t2.subj = t1.subj ) or t1.subj is NULL; -- 全部课程



```

## 课程班级编号

```sql
UPDATE `school`.`selec`
SET selectcid = (((cid * 1000) + majid) * 10 + phase) * 100 + {num};

```


## 分配学生id  （导入学生时，需要有姓名、入学年份、专业）
根据专业、入学按名字排序、设置学生id
新版
```sql
UPDATE `school`.`stu` t1
JOIN (
SELECT
`id`,
`uname`,
`enrol`,
`majid`,
`pid`,
ROW_NUMBER() OVER (ORDER BY `uname`) AS row_num
FROM
`school`.`stu` 
WHERE
`majid` = 1 -- AND `enrol` = {grade}
) t2 ON t1.`pid` = t2.`pid`
SET t1.`id` = t2.`row_num` + t2.`enrol` * 1000000 + t2.`majid` * 1000;
```
旧版
```sql
UPDATE `school`.`stu` t1
JOIN (
SELECT
`id`,
`uname`,
`enrol`,
`majid`,
ROW_NUMBER() OVER (ORDER BY `uname`) AS row_num
FROM
`school`.`stu`
WHERE
`majid` = {num} --AND `enrol` = {grade}
) t2 ON t1.`majid` = t2.`majid` AND t1.`uname` = t2.`uname`
SET t1.`id` = t2.`row_num` + t2.`enrol` * 1000000 + t2.`majid` * 1000;
```

## 分专业班
```sql
UPDATE `school`.`stu` Set sclass = enrol * 10000 + majid * 100 + FLOOR(id % 100 / 9 + 1);
```

## 大学分学期：
```c
switch phase:
case 0: 大一上;
case 1: 大一下;
break;

phase = 0;
phase += (time.year - enrol)*2;
phase += time.month > 8 ? 1 : 0;
```

## 选修、必修


必修课程：
```sql
select  * , ROW_NUMBER() OVER (ORDER BY t5.cname) as num from (select DISTINCT t1.cid, cname, required, t3.majid, tname, selectcid, phase from course t1 join major t2 join tclass t3 on t3.cid = t1.cid join tea t4 on t4.id = t3.tid where (t1.majid = 1 and required = 1) or (t1.majid is null and t1.subj is null and required = 1) or (required = 1 and t2.subj = t1.subj and t1.majid is NULL and t2.majid = 1) ORDER BY cid) t5;
```

选修课程
```sql
select  * , ROW_NUMBER() OVER (ORDER BY t5.cid) as num from (select DISTINCT t1.cid, cname, required, t3.majid, tname, selectcid, phase from course t1 join major t2 join tclass t3 on t3.cid = t1.cid join tea t4 on t4.id = t3.tid where (required is NULL and t2.subj = t1.subj and t1.majid is NULL and t2.majid = 1) or (t1.majid = 1 and required is NULL) or (t1.majid is null and required is null and t1.subj is NULL)) t5;
```


