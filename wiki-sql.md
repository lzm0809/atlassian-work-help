## 查询所有空间及管理员列表
```mysql
SELECT s.SPACEKEY, s.SPACENAME, c.user_name, c.display_name,c.active FROM SPACES s 
 JOIN SPACEPERMISSIONS p ON s.SPACEID = p.SPACEID
 JOIN user_mapping u ON p.PERMUSERNAME = u.user_key 
 JOIN cwd_user c ON u.username = c.user_name
  WHERE p.PERMTYPE = 'SETSPACEPERMISSIONS'
group by s.SPACEID,c.user_name
  order by s.SPACEKEY;
```
