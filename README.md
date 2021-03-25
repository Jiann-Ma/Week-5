# Week-5
本週作業目的是讓大家學會架設 MySQL 資料庫伺服器，並且使用 SQL 語句對資料庫進行新增、讀取、修改、刪除等動作。


![要求一、MySQL創建以及連線成功](https://user-images.githubusercontent.com/72090089/112459376-b966ce80-8d98-11eb-8841-e685dfbd39fc.PNG)
![要求一：安裝 MySQL 伺服器](https://user-images.githubusercontent.com/72090089/112459381-ba97fb80-8d98-11eb-9ee5-a96e7982d2c1.PNG)
![要求二：建立資料庫和資料表](https://user-images.githubusercontent.com/72090089/112459382-bb309200-8d98-11eb-9385-e89c45afb1d8.PNG)


使用 INSERT 指令新增一筆資料到 user 資料表中，這筆資料的 username 和 password 欄位必須是 ply。接著繼續新增至少 4 筆隨意的資料。 

SELECT * FROM website.user;
INSERT INTO user
VALUES (1, 'Peng-Peng', 'ply', 'ply', '2021/03/24'),
(2, 'Jiann', 'JiannAccount', 'JiannPassword', '2021/03/25'),
(3, 'Alisa', 'AlisaAccount', 'AlisaPassword', '2021/03/26'),
(4, 'Amanda', 'AmandaAccount', 'AmandaPassword', '2021/03/27'),
(5, 'Betty', 'BettyAccount', 'BettyPassword', '2021/03/28');

![image](https://user-images.githubusercontent.com/72090089/112458744-1615b980-8d98-11eb-82a4-8f7e7dc1fb24.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 SELECT 指令取得所有在 user 資料表中的使用者資料。 

SELECT * FROM website.user;

![image](https://user-images.githubusercontent.com/72090089/112458799-29c12000-8d98-11eb-88e9-ac9b7433513c.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 SELECT 指令取得 user 資料表中總共有幾筆資料。 

SELECT COUNT(name) FROM website.user;

![image](https://user-images.githubusercontent.com/72090089/112458860-39406900-8d98-11eb-8355-0f79ff7edbb6.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 SELECT 指令取得所有在 user 資料表中的使用者資料，並按照 time 欄位，由近 到遠排序。 

SELECT * FROM website.user ORDER BY time ASC;

![image](https://user-images.githubusercontent.com/72090089/112458941-478e8500-8d98-11eb-9ad8-2839c9dbb587.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 SELECT 指令取得 user 資料表中第 2 ~ 4 共三筆資料，並按照 time 欄位，由近 到遠排序。 

SELECT *
	FROM
    (SELECT ROW_NUMBER() OVER (ORDER BY time ASC) AS RowNumber,
		id,
		name,
		username,
		password,
		time
    FROM website.user) AS RowTable
WHERE RowTable.RowNumber BETWEEN 2 AND 4;

![image](https://user-images.githubusercontent.com/72090089/112459021-59702800-8d98-11eb-8c6f-f4fd2d75cedb.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 SELECT 指令取得欄位 username 是 ply 的使用者資料。 

SELECT * FROM website.user WHERE user.username = 'ply';

![image](https://user-images.githubusercontent.com/72090089/112459091-69880780-8d98-11eb-8f5e-07fcada3d003.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 SELECT 指令取得欄位 username 是 ply、且欄位 password 也是 ply 的資料。 

SELECT * FROM website.user WHERE user.username = 'ply' AND user.password = 'ply';

![image](https://user-images.githubusercontent.com/72090089/112459142-77d62380-8d98-11eb-85bf-38abd596a192.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 UPDATE 指令更新欄位 username 是 ply 的使用者資料，將資料中的 name 欄位 改成【丁滿】。 

UPDATE website.user SET name = '丁滿' WHERE username = 'ply';
SELECT * FROM website.user;

![image](https://user-images.githubusercontent.com/72090089/112459182-86243f80-8d98-11eb-96c5-6ad2bb02761a.png)

------------------------------------------------------------------------------------------------------------------------------------------------

使用 DELETE 指令刪除所有在 user 資料表中的資料。 
DELETE FROM website.user;

![image](https://user-images.githubusercontent.com/72090089/112459240-9805e280-8d98-11eb-8219-b03f8f3977b5.png)





