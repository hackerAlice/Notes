# Postgresql Notes

Linux系统切换到**posgres**用户来开启命令行工具，命令如下：

```shell
sudo -i -u postgres
```

进入命令行后，输入`psql`打开postgresql。可以使用`\help`来查看各个命令的语法：

```shell
postgres-# \help <command_name>
```

## PostgreSQL 数据类型

### 1. 数值类型

| 名字 | 存储长度 | 描述 | 范围 |
| :--- | :------ | :--- | :---- |
| smallint | 2字节 | 小范围整数 | -32768到+32767 |
| integer | 4字节 | 常用的整数 | -2147483648到+2147483647 |
| bigint | 8字节 | 大范围整数 | -92233720368547755808到92233720368547755807 |
| decimal | 可变长 | 用户指定的精度，精确 | 小数点前131072位，小数点后16383位 |
| numeric | 可变长 | 用户指定的精度，精确 | 小数点前131072位，小数点后16383位 |
| real | 4字节 | 可变精度，不精确 | 6位十进制数字精度 |
| double precision | 8字节 | 可变精度，不精确 | 15位十进制数字精度 |
| smallserial | 2字节 | 自增的小范围整数 | 1到32767 |
| serial | 4字节 | 自增整数 | 1到2147483647 |
| bigserial | 8字节 | 自增的大范围整数 | 1到92233720368547755807 |

### 2. 字符类型

| 序号 | 名字 | 描述 |
| :--- | :--- | :--- |
| 1 | character varying(n), varchar(n) | 变长，有长度限制 |
| 2 | character(n), char(n) | 定长，不足补空白 |
| 3 | text | 变长，无长度限制 |

### 3. 布尔类型

| 名称 | 存储格式 | 描述 |
| :--- | :------ | :--- |
| boolean | 1字节 | true/false |

### 4. 枚举类型

Posgresql中枚举类型类似于C语言中enum类型，枚举类型使用`CREATE TYPE`命令创建。

创建一周中的几天，如下所示：

```
CREATE TYPE week AS ENUM ('Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun');
```

