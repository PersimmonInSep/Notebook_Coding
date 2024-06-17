# 常见的日期和时间函数

1. **CURRENT_DATE() 或 CURDATE()**
   - 返回当前日期。
   ```sql
   SELECT CURRENT_DATE();
   ```

2. **CURRENT_TIME() 或 CURTIME()**
   - 返回当前时间。
   ```sql
   SELECT CURRENT_TIME();
   ```

3. **CURRENT_TIMESTAMP() 或 NOW()**
   - 返回当前日期和时间。
   ```sql
   SELECT CURRENT_TIMESTAMP();
   ```

4. **DATE()**
   - 从日期时间值提取日期部分。
   ```sql
   SELECT DATE('2023-06-16 10:30:45');
   ```

5. **TIME()**
   - 从日期时间值提取时间部分。
   ```sql
   SELECT TIME('2023-06-16 10:30:45');
   ```

6. **YEAR()**
   - 提取年份。
   ```sql
   SELECT YEAR('2023-06-16');
   ```

7. **MONTH()**
   - 提取月份。
   ```sql
   SELECT MONTH('2023-06-16');
   ```

8. **DAY()**
   - 提取天数。
   ```sql
   SELECT DAY('2023-06-16');
   ```

9. **HOUR()**
   - 提取小时。
   ```sql
   SELECT HOUR('2023-06-16 10:30:45');
   ```

10. **MINUTE()**
    - 提取分钟。
    ```sql
    SELECT MINUTE('2023-06-16 10:30:45');
    ```

11. **SECOND()**
    - 提取秒。
    ```sql
    SELECT SECOND('2023-06-16 10:30:45');
    ```

12. **DATE_ADD() 或 ADDDATE()**
    - 增加日期间隔。
    ```sql
    SELECT DATE_ADD('2023-06-16', INTERVAL 10 DAY);
    ```

13. **DATE_SUB() 或 SUBDATE()**
    - 减少日期间隔。
    ```sql
    SELECT DATE_SUB('2023-06-16', INTERVAL 10 DAY);
    ```

14. **DATEDIFF()**
    - 返回两个日期之间的天数差。
    ```sql
    SELECT DATEDIFF('2023-06-16', '2023-06-01');
    ```

15. **TIMEDIFF()**
    - 返回两个时间值之间的时间差。
    ```sql
    SELECT TIMEDIFF('10:30:45', '08:30:00');
    ```

16. **TIMESTAMPDIFF()**
    - 返回两个日期时间值之间的指定单位的差异。
    ```sql
    SELECT TIMESTAMPDIFF(DAY, '2023-06-01', '2023-06-16');
    ```

17. **STR_TO_DATE()**
    - 将字符串转换为日期。
    ```sql
    SELECT STR_TO_DATE('16-06-2023', '%d-%m-%Y');
    ```

18. **DATE_FORMAT()**
    - 格式化日期。
    ```sql
    SELECT DATE_FORMAT('2023-06-16', '%Y/%m/%d');
    ```

19. **UNIX_TIMESTAMP()**
    - 返回 Unix 时间戳。
    ```sql
    SELECT UNIX_TIMESTAMP('2023-06-16 10:30:45');
    ```

20. **FROM_UNIXTIME()**
    - 将 Unix 时间戳转换为日期。
    ```sql
    SELECT FROM_UNIXTIME(1623831045);
    ```

# 窗口函数