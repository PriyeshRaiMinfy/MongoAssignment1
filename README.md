# MongoAssignment1
Simple mongodb assignment

### 1 Create collection and inser initial data
```
db.books.insertMany([
    { title: "Learn EC2 Basics", author: "John Doe", due_date: new Date("2025-05-01"), is_read: true },
    { title: "Master IAM", author: "Jane Smith", due_date: new Date("2025-05-05"), is_read: true }
])
```
![1](/Assignment1/images/1.png)
### 2 View All Books
```
db.books.find().pretty()
```
![Screenshot](/Assignment1/images/2.png)
### 3 Change is_read Data Type from String to Boolean
```
db.books.updateMany(
    { is_read: "true" },
    { $set: { is_read: true } }
)
```
![Screenshot](/Assignment1/images/3.png)
### 4 Insert More Books
```
db.books.insertMany([
    { title: "AWS Lambda Guide", author: "Sam Wilson", due_date: new Date("2025-06-01"), is_read: false },
    { title: "CloudWatch Deep Dive", author: "Bruce Wayne", due_date: new Date("2025-06-10"), is_read: false }
])
```
![Screenshot](/Assignment1/images/4.png)
### 5 Set Default is_read to false (When inserting new docs)
```
db.books.insertOne({
    title: "Introduction to CloudTrail",
    author: "Clark Kent",
    due_date: new Date("2025-06-20")
})
// --------------update------------
db.books.updateOne(
    { title: "Introduction to CloudTrail" },
    { $set: { is_read: false } }
)
```
![Screenshot](/Assignment1/images/5.png)
### 6 Change is_read Status Using ObjectId
```
db.books.updateOne(
  { _id: ObjectId("6837f3121713d3061af8a0c3") },
  { $set: { is_read: true } }
)
```
![Screenshot](/Assignment1/images/6.png)
### 7 Add priority Field Using Enum (Low, Medium, High)
b.books.updateMany(
  {},
  { $set: { priority: "Medium" } }
)
![Screenshot](/Assignment1/images/7.png)
### 8 Insert a Book with Priority
db.books.insertOne({
  title: "Set up CloudFront",
  author: "Natasha Romanoff",
  due_date: new Date("2025-06-30"),
  is_read: false,
  priority: "Low"
})
![Screenshot](/Assignment1/images/8.png)
### 9 Sort Books by Due Date
```
db.books.find().sort({ due_date: 1 })
```
![Screenshot](/Assignment1/images/9.png)
### 10 Find Pending Books for Specific Date
```
db.books.find({
  due_date: new Date("2025-06-30"),
  is_read: false
})
```
![Screenshot](/Assignment1/images/10.png)
### 11 Count Total Books
```
db.books.countDocuments()
```
![Screenshot](/Assignment1/images/11.png)