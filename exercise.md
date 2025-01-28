# Exercise

Let's apply what we've learned and create an ERD.

## Using dbdiagram

Take a look at the previous [ERD](https://dbdiagram.io/d/ERD-Course-678e2dc76b7fa355c36da566) built using the [dbdiagram tool](dbdiagram.io)

Notice the left-hand pane.

This contains a markup language DBML. This is how we specify what to draw.

Notice how each element is defined:

- Table
- Column name and datatype
- Primary key
- Relation (_ref:_ tag)

You can read the complete [DBML documentation](https://dbml.dbdiagram.io/home) for more details.

# Exercise 1

Create a free account with [dbdiagram.io](dbdiagram.io)

Draw the ERD for an inventory system in a warehouse.

In the warehouse, each product has an SKU, a price and a two-digit warehouse Aisle location.

Customers are known by their name and email address.

Customers may place an order to the warehouse. An order needs to record the date the order was placed, which customer it was for and the Products they wish to buy.

_hint: think of a paper order form with many line items listed, one per line. Having an order line item table simplifies this problem_

# Exercise 2

Customers are to get a chat board! They can barely contain their excitement.

Each customer can enter a short message of up to 200 characters length. The message will contain a link to the Profile details for the customer who wrote it.

A customer profile shows their uploaded image and bio text.

Messages are part of a group chat, which any customer can enter or leave at any time. Upon joining, the full group chat history of messages will be available to them.

Each group chat is closed to new comments after 14 days. The data stored needs enough information for an application to do this.

Update the ERD diagram.

# Next

[Back to Contents](/contents.md)
