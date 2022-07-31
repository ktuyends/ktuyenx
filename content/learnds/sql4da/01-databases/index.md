---
title: "Databases và DBMS"
weight: 1
subtitle: ""
excerpt: "Bài viết đầu tiên trong Series giới thiệu về các câu lệnh truy vấn SQL. Trong bài này, chúng ta sẽ đi làm quen với các khái niệm cơ bản về dữ liệu và cơ sở dữ liệu."
slug: databases-and-dbms
date: 2022-02-26
lastmod: 2022-02-26
draft: false
tags:
  - SQL
  - SQL for Data Analysis
---

## 1. Dữ liệu là gì?

Dữ liệu là một tập hợp các thông tin về một sự vật, hiện tượng nào đó. Ví dụ như giá sản phẩm, tên sản phẩm...

### 1.1. Phân loại dữ liệu

Có ba loại dữ liệu cơ bản: 

- Dữ liệu có cấu trúc _(structured)_
- Dữ liệu bán cấu trúc _(semi-structured)_
- Dữ liệu phi cấu trúc _(unstructured)_

<p style="text-align:justify">Dữ liệu có cấu trúc là dữ liệu thường được lưu trữ ở trong các cơ sở dữ liệu. Mà CSDL chúng ta thường gặp nhất là cơ sở dữ liệu quan hệ, trong đó các bảng mang thông tin về một thực thể nào đó và giữa các bảng được liên kết với nhau dựa vào các mối quan hệ. Ngoài ra, mối quan hệ giữa các bảng còn được thể hiện bằng mô hình quan hệ thực thể ER <i>(Entity relationship)</i>.</p>

<p style="text-align:justify">Dữ liệu phi cấu trúc là dữ liệu không có cấu trúc cụ thể, ví dụ như email, video, hình ảnh, mạng xã hội...</p>

### 1.2. Data Lake và Data Warehouse

<img src="./img/data.webp" width=85% class="center-fig">

<p style="text-align:justify">Data Lake, ta hiểu đơn giản nó là một kho lưu trữ trung tâm chứa dữ liệu thô chưa qua xử lý <i>Raw data</i>. Nghĩ theo một cách khác thì Data Lake sẽ tập hợp dữ liệu từ tất cả các nguồn bao gồm dữ liệu có cấu trúc, bán cấu trúc và phi cấu trúc về một nguồn duy nhất.</p>  

<p style="text-align:justify">Sau khi dữ liệu đã được tập hợp vào trong Data Lake, Data Engineer sẽ thực hiện các thao tác ETL <i>(Trích xuất, biến đổi và xử lý)</i> trước khi chuyển vào trong Data Warehouse. Như vậy, Data Warehouse cũng là một kho lưu trữ dữ liệu nhưng các dữ liệu này đã được phân loại và xử lý cho mục đích báo cáo và phân tích dữ liệu.</p>  

<p style="text-align:justify">Data Warehouse còn có một phiên bản thu nhỏ gọi là Data Mart. Về cơ bản thì nó được thiết kế để sử dụng bởi một bộ phận, đơn vị hoặc nhóm người dùng cụ thể trong tổ chức. Ví dụ như cho các phòng ban Marketing, HR, Sales...</p>


## 2. Mô hình CSDL quan hệ

### 2.1. Mô hình ERD

<p style="text-align:justify">ERD là tên viết tắt của Entity Relationship Diagram. Mô hình này bao gồm E <i>(Entity – Thực thể)</i> và R <i>(Relationship – Mối quan hệ)</i>. Từ đó ta có khái niệm ERD: <b>Mô hình ERD</b> là một sơ đồ, thể hiện các thực thể có trong database và mối quan hệ giữa chúng với nhau.</p>

ERD gồm ba thành phần chính:

- **Entity**: thực thể (hoặc đối tượng) mà hệ thống quản lý.
- **Attribute**: thuộc tính của các đối tượng.
- **Relationship**: mối quan hệ giữa các đối tượng.

### 2.2. Thực thể

<p style="text-align:justify">Thực thể là những đối tượng như: người, sự vật, sự việc,...mà chúng ta muốn lưu trữ trên hệ thống. Thông thường, các thực thế rất dễ hình dung trong thực tế bên ngoài, nhưng cũng có những thực thể hơi khó hình dung khi chúng nằm giữa hai thực thể khác để thể hiện mối quan hệ <code>nhiều - nhiều</code> giữa hai thực thể này.</p>

### 2.3. Thuộc tính

<p style="text-align:justify">Thuộc tính, hiểu đơn giản là các đặc điểm, tính chất mô tả các thông tin về một thực thể, đối tượng nào đó.</p>

### 2.4. Mối quan hệ

Về cơ bản thì trong mô hình ERD có ba loại quan hệ chính:

- **One-to-One**: quan hệ `1 - 1` 
- **One-to-Many**: quan hệ `1 - nhiều`
- **Many-to-Many**: quan hệ `nhiều - nhiều`

Ký hiệu thể hiện mối quan hệ trong sơ đồ:

<img src="./img/erd.png" width=45% class="center-fig">

Cách đọc các mối quan hệ (ví dụ từ blog của anh [thinhnotes](https://thinhnotes.com/chuyen-nghe-ba/erd-la-gi/)).

<figure><img src="./img/erd_1.webp" width=80% class="center-fig"><figcaption class="img-cap">Quan hệ một - một</figcaption></figure>

<figure><img src="./img/erd_2.webp" width=80% class="center-fig"><figcaption class="img-cap">Quan hệ một - một và chỉ một</figcaption></figure>

<figure><img src="./img/erd_3.webp" width=80% class="center-fig"><figcaption class="img-cap">Quan hệ một - không hoặc một</figcaption></figure>

<figure><img src="./img/erd_4.webp" width=80% class="center-fig"><figcaption class="img-cap">Quan hệ một - nhiều</figcaption></figure>

<figure><img src="./img/erd_5.webp" width=80% class="center-fig"><figcaption class="img-cap">Quan hệ một - một hoặc nhiều</figcaption></figure>

<figure><img src="./img/erd_6.webp" width=80% class="center-fig"><figcaption class="img-cap">Quan hệ một - không hoặc nhiều</figcaption></figure>

<figure><img src="./img/erd_7.webp" width=80% class="center-fig"><figcaption class="img-cap">Quan hệ nhiều nhiều</figcaption></figure>

<p style="text-align:justify">Tổng kết lại ta có thể hiểu: Các thực thể, đối tượng ám chỉ danh từ. Các thuộc tính ám chỉ tính từ mô tả thông tin về thực thể. Mối quan hệ là các động từ thể hiện tác động qua lại giữa các thực thể.</p>

<p style="text-align:justify">Trong thực tế, quan hệ <code>nhiều - nhiều</code> sẽ không được thể hiện trực tiếp mà phải thông qua một quan hệ trung gian. Ví dụ ta có bảng A và bảng B là quan hệ <code>nhiều - nhiều</code>, khi vẽ sơ đồ ta cần một bảng M và A với M là quan hệ <code>một - nhiều</code>, B với M cũng là quan hệ <code>một - nhiều</code>. Khi đó A với B sẽ có quan hệ <code>nhiều - nhiều</code>.</p>  

### 2.5. Cơ sở dữ liệu quan hệ

<p style="text-align:justify">Cơ sở dữ liệu quan hệ hiểu đơn giản là các CSDL được tổ chức thành nhiều bảng, và giữa các bảng có quan hệ với nhau dựa vào các khóa. Liên kết với khái niệm ERD, thì một bảng sẽ đại diện cho một thực thể, các cột trong bảng sẽ đại diện cho thuộc tính của thực thể đó. Các dòng là các bản ghi <i>(record)</i>, là số lượng dữ liệu mà bảng đó lưu trữ trong CSDL.</p>

### 2.6. Khóa chính (PK)

<p style="text-align:justify">Khóa chính là một cột hoặc một tập hợp kết hợp giữa các cột, trong đó mỗi hàng sẽ có một giá trị xác định và không trùng lặp với các hàng khác. Nếu khóa chính là kết hợp của nhiều cột, thì tập hợp các giá trị trong mỗi hàng phải khác nhau.</p>

### 2.7. Khóa ngoại (FK)

<p style="text-align:justify">Khóa ngoại là một cột hoặc một tập hợp các cột tham chiếu đến khóa chính trong một bảng khác. Khóa ngoại thường có cùng tên và kiểu dữ liệu với khóa chính được tham chiếu.</p> 

<p style="text-align:justify">Khóa ngoại có thể có giá trị NULL, ngược lại khóa chính thì không. Một bảng có thể có nhiều khóa ngoại nhưng chỉ có duy nhất một khóa chính. Một điểm khác biệt cuối cùng, các giá trị trong cột khóa chính là duy nhất, còn khóa ngoại thì có thể lặp lại.</p>

### 2.8. Null 

<p style="text-align:justify">Giá trị Null là giá trị bị thiếu trong một hàng, ta có thể hiểu đó là một giá trị không xác định.</p>

## 3. Tạo bảng với SQL Server

<p style="text-align:justify">Việc cần làm đầu tiên trước khi tạo bảng, bạn cần phải xác định xem hệ quản trị CSDL mình đang dùng là gì, vì mỗi DBMS <i>(Database Management System)</i> sẽ có một số khác biệt nhỏ về cú pháp khi tạo bảng. Trong phần này, ta sẽ đi tìm hiểu về cách tạo bảng với SQL Server.</p>

### 3.1. Tạo database

Cú pháp tổng quát:

```sql
-- Nếu chưa có Database
-- Tạo Database LearnDS
CREATE DATABASE LearnDS;
GO

-- Sử dụng Database LearnDS
USE LearnDS;
GO
```

### 3.2. Schema

<p style="text-align:justify">Schema hiểu nôm na là một Namespace dùng để gom nhóm các table có chung một đặc điểm nào đó để dễ dàng quản lý. Nếu không sử dụng Schema trong CSDL thì SQL Server mặc định nó là <code>dbo</code>. Trong CSDL, tên của Schema là duy nhất.</p>

```sql
-- Tạo schema
CREATE SCHEMA schema_name;

-- Trình tự
server.database.schema.object
```

### 3.3. Tạo bảng

```sql
-- Tạo bảng
-- database_name: Tên database chứa table
-- schema_name: Tên schema
-- table_name: Tên bảng
-- pk_column: Khóa chính
-- data_type: Kiểu dữ liệu
-- constraints: Ràng buộc

-- option: PRIMARY KEY, NULL/NOT NULL, UNIQUE
-- DEFAULT "value", IDENTITY(start, step)

CREATE TABLE [database_name.][schema_name.]table_name (
    pk_column data_type PRIMARY KEY,
    column_1 data_type [option],
    column_2 data_type [option],
    ...,
    table_constraints
);
```

### 3.4. Kiểu dữ liệu

| Kiểu dữ liệu | Ý Nghĩa |
|:-:|-|
| CHAR(10) | Chuỗi ký tự với độ dài cố định là 10 |
| NCHAR(10) | Tương tự char, nhưng có thể bao gồm các ký tự Unicode |
| VARCHAR(50) | Chuôi ký tự với độ dài tùy biến, tối đa là 50|
| NVARCHAR(50) | Tương tự nvarchar, nhưng có thể bao gồm các ký tự Unicode|
| TEXT | Chuỗi có chứa độ dài tùy biến, không bao gồm các ký tự Unicode |
| NTEXT | Chuỗi có độ dài tùy biến, có thể bao gồm các ký tự Unicode |
| TINYINT/SMALLINT/INT/BIGINT | Số nguyên với các phạm vi khác nhau|
| DECIMAL | Lưu trữ số thực có giá trị chính xác |
| FLOAT | Lưu trữ số thực có giá trị xấp xỉ |
| DATE/TIME/DATETIME| Kiểu dữ liệu ngày tháng - thời gian|

### 3.5. Các ràng buộc

```sql
-- Khóa chính, trong trường hợp có nhiều cột làm khóa chính
PRIMARY KEY (pk_column_1, pk_column_2)

-- Khóa ngoại
CONSTRAINT fk_constraint_name 
FOREIGN KEY (fk_column_1, fk_column2,...)
REFERENCES tb_name(pk_column1, pk_column2,..)

-- Check điều kiện
CHECK(conditional)
```

### 3.6. Nhập dữ liệu vào bảng

```sql
-- Nhập dữ liệu cơ bản
INSERT INTO table_name (column_list)
VALUES
    (value_list_1),
    (value_list_2),
    ...
    (value_list_n);

-- Nhập dữ liệu từ câu lệnh Select
INSERT INTO table_name (column1, column2, … )
SELECT expression_1, expression_2, …
FROM source_tables
WHERE conditions;
```

## 4. Làm quen với PostgreSQL

### 4.1. Cài đặt

Trước khi làm việc với PostgreSQL, ta cần cài đặt một số phần mềm:

- [PostgreSQL](https://www.postgresql.org/download/)
- PgAdmin (Cài đặt được lựa chọn trong quá trình cài PostgreSQL)

Sau khi cài đặt, ta bật PgAdmin để tương tác với database:

<img src="./img/postgresql.png" width=80% class="center-fig">

### 4.2. Tạo database

Để tạo database, ta click chuột phải vào `Databases -> Create -> Database` và nhập tên database:

<img src="./img/postgre-database.png" width=60% class="center-fig">

### 4.3. Tạo table

Để tạo bảng, ta click chuột phải vào `database_name -> Schemas -> Schema_name -> Tables` và chọn `Create Table`.

<img src="./img/postgresql-create-table.png" width=80% class="center-fig">

### 4.4. Query Tool

<p style="text-align:justify">Để viết các truy vấn trong CSDL, click chuột phải vào database muốn thực hiện truy vấn và chọn <code>Query Tool</code></p>

<img src="./img/query-tool.png" width=80% class="center-fig">

### 4.5. PostgreSQL và Pandas

<p style="text-align:justify">Có nhiều cách để sử dụng PostgreSQL trong môi trường Python. Với những người làm Data Analytics, bạn có thể sử dụng Pandas để đọc các lệnh truy vấn và kết quả được lưu trữ dưới dạng <code>DataFrame</code>, hoặc các bạn có thể sử dụng <code>Jupyter Magic</code> để chạy trực tiếp các truy vấn.</p>

<p style="text-align:justify">Trong phần này, chúng ta sẽ đi tìm hiểu cách để kết nối đến PostgreSQL database từ Python, và thực hiện một số thao tác truy vấn bằng Pandas. Trước tiên ta cần cài đặt một số module:</p>

```python
conda install pandas       # Đọc truy vấn
conda install ipython-sql  # Hỗ trợ sql trên jupyter
conda install sqlalchemy   # Để làm việc với SQL
conda install psycopg2     # Kết nối với PostgreSQL
```

Tiếp theo, ta cần phải xác định một số thông tin của database (click chuột phải vào _PostgreSQL 14 -> Properties -> Connection_ để lấy các thông tin như bên dưới).

```python
hostname = 'localhost'
database = 'parch'
username = 'postgres'
pwd = 'admin' # password
port_id = '5432'
```

**Kết nối Python với PostgreSQL**



```python
# import module
from sqlalchemy import create_engine

# Connection: dialect+driver://username:password@host:port/database
conn = create_engine('postgresql://postgres:admin@localhost:5432/parch')

```

**Thực hiện truy vấn với _Pandas_**


```python
# import module
import pandas as pd

# pd.read_sql(query, conn)
data = pd.read_sql('SELECT * FROM public.region', conn)
data
```

```
       id       name
    0   1  Northeast
    1   2    Midwest
    2   3  Southeast
    3   4       West
```

### 4.6. PostgreSQL và Jupyter

Về cơ bản cú pháp cũng tương tự như khi sử dụng Pandas:


```python
# load_ext để sử dụng jupyter magic
%load_ext sql

# Connect
%sql postgresql://postgres:admin@localhost:5432/parch
```




    'Connected: postgres@parch'



Một số cách sử dụng _Jupyter Magic_ để thực hiện truy vấn:

- Sử dụng `%sql` nếu các câu lệnh truy vấn nằm trên cùng 1 dòng.
- Sử dụng `%%sql` nếu các câu lệnh truy vấn nằm trên nhiều dòng.
- Sử dụng `%sql $query_var` với `query_var` là biến string gồm nhiều câu lệnh truy vấn.

Ví dụ:


```sql
%%sql

SELECT *
FROM public.region
```

     * postgresql://postgres:***@localhost:5432/parch
    4 rows affected.
    

<table>
    <thead>
        <tr>
            <th>id</th>
            <th>name</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Northeast</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Midwest</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Southeast</td>
        </tr>
        <tr>
            <td>4</td>
            <td>West</td>
        </tr>
    </tbody>
</table>

---