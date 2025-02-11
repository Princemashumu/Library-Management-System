# 📚 Library Management System

## 📖 Project Overview
The **Library Management System** is designed to manage a collection of books, authors, and patrons. This system allows users to perform various **CRUD (Create, Read, Update, Delete) operations** on the collections, as well as advanced queries using **MongoDB**.

---

## 🔧 Prerequisites
- Install **MongoDB** on your local machine if you haven't already.
- Ensure the **MongoDB server** is running.
- Open a terminal or command prompt.
- Start the **MongoDB shell (mongosh)** by running:
  
  ```sh
  mongosh
  ```

You should now be in the **MongoDB shell**, ready to execute commands.

---

## 🚀 Instructions

### 🏗 Step 1: Create Database **LibraryDB**
```sh
use LibraryDB
```

### 📚 Step 2: Create Collections and Insert Documents

#### 📕 Books Collection
```sh
db.books.insertMany([
  { _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true },
  { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true },
  { _id: 3, title: "The Great Gatsby", author_id: 3, genres: ["Tragedy"], published_year: 1925, available: true },
  { _id: 4, title: "Brave New World", author_id: 4, genres: ["Dystopian", "Science Fiction"], published_year: 1932, available: true },
  { _id: 5, title: "The Catcher in the Rye", author_id: 5, genres: ["Realist Novel", "Bildungsroman"], published_year: 1951, available: true }
])
```

#### ✍️ Authors Collection
```sh
db.authors.insertMany([
  { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 },
  { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 },
  { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 },
  { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 },
  { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 }
])
```

#### 👤 Patrons Collection
```sh
db.patrons.insertMany([
  { _id: 1, name: "Alice Johnson", email: "alice@example.com", borrowed_books: [] },
  { _id: 2, name: "Bob Smith", email: "bob@example.com", borrowed_books: [1, 2] },
  { _id: 3, name: "Carol White", email: "carol@example.com", borrowed_books: [] }
])
```

---

## 🔍 Step 3: CRUD Operations

### 📂 Retrieve Data
#### Find All Books
```sh
db.books.find()
```
#### Find a Specific Book by Title
```sh
db.books.find({ title: "To Kill a Mockingbird" })
```
#### Find All Books by a Specific Author
```sh
db.books.find({ author_id: 5 })
```
#### Find All Available Books
```sh
db.books.find({ available: true })
```

### 📝 Update Operations
#### Update Book Availability
```sh
db.books.updateOne({ _id: 3 }, { $set: { available: false } })
```
#### Add a Genre to a Book
```sh
db.books.updateOne({ _id: 8 }, { $addToSet: { genres: "Classic" } })
```
#### Add a Borrowed Book to a Patron's Record
```sh
db.patrons.updateOne({ _id: 5 }, { $addToSet: { borrowed_books: 9 } })
```

### 🗑 Delete Operations
#### Delete a Book by Title
```sh
db.books.deleteOne({ title: "Brave New World" })
```
#### Delete an Author
```sh
db.authors.deleteOne({ _id: 3 })
```

---

## 🔍 Step 4: Advanced Queries with Operators

### 📅 Find Books Published After 1950
```sh
db.books.find({ published_year: { $gt: 1950 } })
```
### 🌎 Find All American Authors
```sh
db.authors.find({ nationality: "American" })
```
### ✅ Set All Books to Available
```sh
db.books.updateMany({}, { $set: { available: true } })
```
### 📚 Find Books That Are Available and Published After 1950
```sh
db.books.find({ available: true, published_year: { $gt: 1950 } })
```
### 🔎 Find Authors Whose Names Contain "George"
```sh
db.authors.find({ name: { $regex: "George", $options: "i" } })
```
### 📅 Increment the Published Year by 1
```sh
db.books.updateOne({ published_year: 1869 }, { $inc: { published_year: 1 } })
```

---

## 🎯 Conclusion
This **Library Management System** provides a structured way to manage books, authors, and patrons in a MongoDB database. Using the provided commands, you can efficiently create, retrieve, update, and delete records while performing advanced queries to retrieve specific data insights.

Happy Coding! 🚀

