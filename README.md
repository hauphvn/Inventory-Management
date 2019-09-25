# Inventory-Management
Jack' Blog
==

This is a second my project with Hibernate, Spring MVC, Postgresql

## Requirement

- Maven  
    - Hibernate
    - Spring-core: define beans
    - Spring-context: call beans, xml config
- Postgresql
- Tomcat

### Notes:
- After run app, web.xml file is run firstly.
- 

## Let's start
On Ubuntu:  
- Start service postgres:  
``$ sudo service postgresql start``  
- Stop service postgres:  
``$ sudo service postgresql stop``  
- Switch over to the postgres account:  
``$ sudo -u postgres psql``  
or prompt immediately:  
``$ psql``  
- Set the password:  
``postgres=# \password postgres``
- Exit out of the Postgres:  
``postgres=# \q``  
- Creating a new Database:  
``postgres=# create database [your name database] ;``  
- Deleting a Database:                          
``postgres=# drop database [your name database] ;``   
- Listing Databases: 
``postgres=# \l ;`` or ``postgres=# \list ;``  
- Switching Databases:  
``postgres=# \c [nameDatabase] ;``   
- Listing Tables:  
``postgres=# \dt ;`` 
---
## Step 02: Phân tích nghiệp vụ
Project này làm về quản lí kho:
1. Phân tích bài toán:

a. Phân tích nghiệp vụ:  
- Đối tượng: Chuỗi siêu thị, hệ thống bán hàng điện thoại.  
-  Giải quyết vấn đề: nhập xuất hàng hóa, báo cáo dữ liệu.  
- Đối tượng sử dụng:  Nhân viên quản lí kho, người quản lí cấp cao  

b. Các chức năng hệ thống:  
- Phân quyền 
- Thêm sửa xóa dữ liệu 
- Upload file, xuất báo cáo 
- Phân trang 
- Tìm kiếm  

## Step 03:Sơ đồ Usecase:  
![Usecase diagram](https://raw.github.com/hauphvn/Inventory-Management/master/images/UsecaseDiagram.png)

## Step 04: Thiết kế Database:
- Phân quyền gồm các bảng: USERS, ROLE, USER_ROLE, AUTH, MENU.  
- Chức năng gồm các bảng: CATEGORY, PRODUCT_INFO, INVOICE, HISTORY, PRODUCT_IN_STOCK.  

![Class diagram](https://raw.github.com/hauphvn/Inventory-Management/master/images/ClassDiagram.png)  

- Một user có nhiều role , một role có nhiều users : nên xuất hiện bảng users_role   
- Vì ta cần show ra những tuỳ chọn menu theo quyền nên ta cần dữ liệu động để thay đồi tùy theo user nên ta tạo bảng menu để load data động.  
- Để biết quyền nào thì có những menu nào ta dựa vào bảng auth.  

