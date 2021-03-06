
# 数据库设计方案

## 数据库
    1. 管理软件采用 PostgreSQL
    2. 名称为 Hospital


## 表的设计


### 帐号 accounts

#### 患者帐号 paccounts

列 | 列名 | 类型 | 约束
---| --- | --- | ---
代码 | id          | integer|  not null 外键约束 patients (id)
用户名 | username  | text   | not null Primary key
密码 | password | text(hash) | not null


#### 医生帐号 daccounts

列 | 列名 | 类型 | 约束
---| --- | --- | ---
代码 | id         | integer  |not null  外键约束 doctors (id)
用户名 | username  | text    | not null Primary key
密码 | password | text(hash) | not null



### 医生 doctors
医生表

列 | 列名 | 类型 | 约束
---| ---| --- | ---
医生代码 | id | serial | 主键 null
姓名 | name | text | not null
科室  | office |  text |  not null

### 患者 patients
患者表

列 | 列名 | 类型 | 约束
---| --- | --- | ---
患者代码| id | serial | 主键
姓名 | name | text | not null
性别 | gender | boolean | not null
出生日期 | birthday | date | not null

### 病历 records
病历表


列   | 列名 | 类型 | 约束
-----|-----|-----| ----
预约号| id  | serial | 外键 reservation(id)
药物使用| medicine | text
病例描述| description | text | not null



### 预约 reservations
预约表

列 | 列名 | 类型 | 约束
--- | --- | --- | ---
预约号 | id | serial | 主键 not null
日期   | commitdate | date | not null
医生代码 | did | integer | not null 外键约束
患者代码 | pid | integer | not null 外键约束
预约时间 | section | integer | not null Unique 约束


## 视图的设计

### 今日预约
### 空闲医生



