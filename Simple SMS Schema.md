# How to Design Database for Simple FB-like Social Media Service Platform
Are you interested in designing a database for a social network, like Facebook?

Facebook is a popular website and designing a database for a site like Facebook is a common exercise, 
whether you're in a database course at college or want to practice your skills.

In this exercise, you'll start with a series of basic features of the system, and one-by-one we'll create a 
database design, adding to the design at each step.

The final design will meet the requirements of the features we have identified.

You can then expand on the design, and of course modify it if you want different requirements.

# Social Media Service Platform Features

* Sign up and create a profile
* Add other profile as friends
* Add posts that contain text, photos, or videos
* See posts that friends have added
* Like and add comments to posts others have added

![image](https://github.com/alexntwu/mssql-sns/assets/1982325/734f5150-10a1-4474-aa57-4347799269d2)

# Entities and Attributes for the Social Media Services Platform
Entities serve as the building blocks of our database, representing the fundamental objects or concepts that need to be stored and managed. Attributes define the characteristics or properties of each entity. Let’s explore each entity and attribute in detail

## user_profile: Represents individual users registered on the platform.
* id (Primary Key): Unique identifier for each user.
* email_address: Email address of the user used for authentication.
* password: Securely hashed password for user authentication.
* given_name First name of the user.
* surname: Surname of the user.

## Post: Represents individual posts shared by users on the platform.
* id (Primary Key): Unique identifier for each post.
* profile_id (Foreign Key): Reference to the profile who created the post.
* written_text: Text content of the post.
* media_location: URL or reference to the media file attached to the post.
* created_datetime: Date and time when the post was created.

## Comment: Represents comments made by users on posts.
* id (Primary Key): Unique identifier for each comment.
* post_id (Foreign Key): Reference to the post being commented on.
* profile_id (Foreign Key): Reference to the profile who made the comment.
* comment_text: Text content of the comment.
* created_datetime: Date and time when the comment was posted.

## Like: Represents likes given by users to posts or comments.
* id (Primary Key): Unique identifier for each like.
* post_id (Foreign Key): Reference to the post being liked.
* profie_id (Foreign Key): Reference to the profile who liked the post.
* created_datetime: Date and time when the like was given.

## Friendship: Represents mutual friendships between users.
* profile_requst (Foreign Keys): References to the users who are friends.
* profile_accept (Foreign Keys): References to the users who are friends.

