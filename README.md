# Lesson 10 Final Project: Posts 200 points

# Directions

This course has exposed you to many parts that make up back-end JavaScript development with Node. In this final project, you will create a full, Back-End application that reviews many of the topics discussed in this course. Where applicable, use Handlebars for your views. Follow the below requirements closely, and good luck!

# Caution!

Do not submit your project until you have completed all requirements! You will not be able to resubmit.

# Setup

Open up your terminal/command prompt.

Navigate to your desktop in your terminal:

cd Desktop
Then, navigate to the Express-Course directory in your terminal:

cd Express-Course
# Requirements

# Step 1

Create an Express application with the Express generator

This application should be named L10HandsOn and should live within your Express-Course directory
Install all needed dependencies
This application should use Sequelize as its ORM
# Step 2

Create a new MySQL database called bulletinboard

# Step 3

Run migrations to create two new tables: users and posts

These tables should have the following structure:
users:
UserId: integer, autoincrement, primary key, not null
FirstName: string
LastName: string
Username: string, unique
Password: string
Email: string, unique
Admin: boolean, default value is false, not null
createdAt: date, not null
updatedAt: date, not null
posts:
PostId: integer, autoincrement, primary key, not null
PostTitle: string
PostBody: string
UserId: integer, foreign key to UserId in users table
createdAt: date, not null
updatedAt: date, not null

# Step 4

Update models to reflect the create table migrations

Don't forget the associations
# Step 5

Users should be able to Signup/Login/Logout

Use JWT for secure login (hashing and salting passwords)

# Step 6

Users should be able to create, edit, and delete

Be able to click on a post to update or delete it
Run a migration to add a Deleted column
After the post has been deleted, redirect the user to their profile page

# Step 7

Users should be able to view their profile page. Their profile page should render the following:

Their full name
Their username
The posts they have written

# Step 8

Admin users should be able to see a list of all users that have not been deleted by the user's first and last name

Run another migration to add a Deleted column
Render a different hbs file for the Admin profile page, which should list all users
Every Admin should see the same page. Use the route /users/admin

# Step 9

Admin users should be able to click on a user and view their information, but not edit their information

Use the route /users/admin/editUser/:id

# Step 10

Admin users should be able to Delete users and their posts, but not edit them

# Step 11

Add some styling to your application so it is unique to your taste

# Additional Info!

To gain a better understanding of this assignment, watch this workshop: Final Review.
Making route files requires those route files be included in the app.js file
You do this by app.get and app.use


const { Router } = require("express");

//Router for admin users - authenticated 
Router.get("/route", function(req, res, next){
     let token = req.cookies.jwt;
     if (token) {
          authService.verifyUser(token)
          .then(founderUser => {
               if (founderUser) {
                    if (founderUser.Admin) {
                    //Our statements for the route goes here
               } else {
                    res.send("Not an admin");
               }
          } else {
               res.send("Token was invalid")
          }
          })
     } else {
          res.send("token doesn´t exist")
     }
})

//Get all
router.get('/', function(req, res, next) {
});
//Get one
router.get('/:id', function(req, res, next) {
});
//Create one
router.post('/create', function(req, res, next) {
});
//Delete one
router.delete('/:id', function(req, res, next) {
});
//Update one
router.put('/:id', function(req, res, next) {
});

