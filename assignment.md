# Assignment

## Brief

Create an ERD for each of the following case study question.

## Instructions

Paste the answer as DBML in the answer code section below each question.

### Question 1

Construct an ERD for a social media company whose database includes information about users, their followers, and the posts that they make. Users can follow multiple users and create multiple posts.

Each entity has the following attributes:

- User: id, username, email, created_at
- Post: id, title, body, user_id, status, created_at
- Follows: following_user_id, followed_user_id, created_at

Answer: https://dbdiagram.io/d/1-2-Q1-6789c9126b7fa355c328c9d9

```dbml

Table User {
    id int [primary key] // Unique identifier for the user
    username varchar [not null, unique] // Unique username for the user
    email varchar [not null, unique] // Email address of the user
    created_at timestamp [not null] // Timestamp of when the user account was created
}

Table Post {
    id int [primary key] // Unique identifier for the post
    title varchar [not null] // Title of the post
    body text [not null] // Body content of the post
    user_id int [not null] // Reference to the user who created the post
    status varchar [not null] // Status of the post (e.g., 'draft', 'published')
    created_at timestamp [not null] // Timestamp of when the post was created
}

Table Follows {
    following_user_id int [not null] // Reference to the user who is following
    followed_user_id int [not null] // Reference to the user being followed
    created_at timestamp [not null] // Timestamp of when the follow relationship was created
}

Ref: User.id < Post.user_id //One to Many
Ref: User.id < Follows.following_user_id //One to Many
Ref: User.id < Follows.followed_user_id //One to Many

```

### Question 2

Construct an ERD for a company that sells books online. The company has a website where customers can browse available books and add them to their shopping carts. Each cart can contain multiple books.

There are 4 entities, think of what attributes each entity should have.

- Customer
- Book
- Cart
- CartItem

Answer: https://dbdiagram.io/d/1-2-Q2-6789cd446b7fa355c3291c81

```dbml

Table Customer {
    id int [primary key] // Unique identifier for the customer
    name varchar [not null] // Full name of the customer
    email varchar [not null, unique] // Email address of the customer
    password varchar [not null] // Encrypted password for account login
    created_at timestamp [not null] // Timestamp of when the account was created
}

Table Book {
    id int [primary key] // Unique identifier for the book
    title varchar [not null] // Title of the book
    author varchar [not null] // Author of the book
    price decimal [not null] // Price of the book
    stock int [not null] // Number of books available in stock
    created_at timestamp [not null] // Timestamp of when the book was added
}

Table Cart {
    id int [primary key] // Unique identifier for the cart
    customer_id int [not null] // Reference to the customer who owns the cart
    created_at timestamp [not null] // Timestamp of when the cart was created
}

Table CartItem {
    id int [primary key] // Unique identifier for the cart item
    cart_id int [not null] // Reference to the cart containing this item
    book_id int [not null] // Reference to the book in this cart item
    quantity int [not null] // Quantity of the book added to the cart
    created_at timestamp [not null] // Timestamp of when the cart item was created
}

Ref: Customer.id < Cart.customer_id // A customer can have multiple carts, but each cart belongs to one customer
Ref: Cart.id < CartItem.cart_id // A cart can have multiple cart items, but each cart item belongs to one cart
Ref: Book.id < CartItem.book_id // A book can appear in multiple cart items, but each cart item references one book


```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
