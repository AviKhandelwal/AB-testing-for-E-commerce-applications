# AB-testing-for-E-commerce-applications

## Introduction

The project uses a dataset which tries to mimic an online e-commerce site. A dummy relational database has been used which consists of tables related to user information, product details, item viewing activity and order details. It is called as dsv1069 which is available at Mode, a free public data warehouse.

1. The first part of the project will deal with data exploration that would include understanding the data, getting a clear understanding of various tables, how they are related to one another and answering important data questions that arise at any e-commerce company by writing queries using SQL.

2. The second part will end the proejct with AB testing where running some tests would help us decide if the change we are trying to introduce at our dummy company could yeild any statistically significant results.

Below is a simple wireframe drawing of a website owned by a fictitious e-commerce company. We have some items which can be viewed and purchased via the users, in order to purchase an item a visitor must first create an account and be logged in and then add the item to their cart and then check out.

![image](https://user-images.githubusercontent.com/71550473/126879795-0057cefa-7183-44f3-b1ac-6c12a2009cc7.png)

## Dataset

### Users Table
![image](https://user-images.githubusercontent.com/71550473/126879849-77dfc4a5-cf0d-4a98-bcfa-f9be7dbf282b.png)

The first table is the users table, to keep a tab of users in our database-

1.	ID keeps track of the user ID which is unique to every user
2.	Name of the user
3.	Email address of the user,
4.	When user created the account
5.	When/If account was deleted
6.	When/If  the account has been merged (might be used to group customers with similar purchasing habits which could be important while sending a bulk email to targeted audience)
7.	Parent user ID of the user account (ID corresponding to the group in which user has been put in)

### Items Table
![image](https://user-images.githubusercontent.com/71550473/126879947-50b5e07d-933b-479e-ba96-e0ab7598110f.png)

To keep track of the items that company is selling on the imaginary website, we have
 
1.	ID for the corresponding item 
2.	name for the item
3.	the adjective describing the item
4.	category of item
5.	modifier, this helps to sell the same item with different options, such as buying a dominos regular pizza with add on extra cheese and coke
6.	when the item was put on website
7.	the current price for the item. 

### Invoice Table
![image](https://user-images.githubusercontent.com/71550473/126880101-bf6efb7f-1ff8-43be-825f-8006b5951919.png)

When a user completes the purchase, we would create an invoice indicating

1.	The invoice_id (unique to every purchase made)
2.	Item_id (Id corresponding to order placed)
3.	Line_item_id (if the order contained 4 items, all the 4 items would have distinct line_item_id but same item_id indicating they are part of the same order placed)
4.	Name of item
5.	ID of user who purchased
6.	Time of payment
7.	Price paid for the item

### Events Table
![image](https://user-images.githubusercontent.com/71550473/126880151-a1859bab-eefa-40f5-99d6-5fc7d766b08f.png)

Events table stimulates a copy of a live production table. It is more like a stream of receipts for activity information and we'll be using it to keep track of more ephemeral things like page views. 

1.	Event_id shows the unique Id corresponding to the event 
2.	Event time shows the time at which the event happened
3.	Event name indicates the type of event which could be an item view event where a user has gone to specific item page. 
4.	Platform through which event took place (mobile/computer etc.)
5.	Parameter name and value giving further details about the event (this is discussed further in data exploration)

### View_items Table
![image](https://user-images.githubusercontent.com/71550473/126880188-9892ab6e-0c4c-4db1-a59b-bc00dc1bf772.png)

View item table will be giving information about the viewing details of the item like –

1.	Event ID 
2.	Event time
3.	Event name
4.	User Id who viewed
5.	Platform used for viewing
6.	Parameter name and value
