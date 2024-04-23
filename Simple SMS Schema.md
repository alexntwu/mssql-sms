# How to Design Database for Simple FB-like Social Media Service Platform
Are you interested in designing a database for a social network, like Facebook?

Facebook is a popular website and designing a database for a site like Facebook is a common exercise, whether you're in a database course at college or want to practice your skills.

In this exercise, you'll start with a series of basic features of the system, and one-by-one we'll create a database design, adding to the design at each step.

The final design will meet the requirements of the features we have identified.

You can then expand on the design, and of course modify it if you want different requirements.

# Social Media Service Platform Features

* Sign up and create a profile
* Add other profile as friends
* Add posts that contain text, photos, or videos
* See posts that friends have added
* Like and add comments to posts others have added

  ![image](https://github.com/alexntwu/mssql-sns/assets/1982325/8cc6a3a2-c01e-4c53-9970-3d5652ad0037)



* User Management: Efficiently manage user profiles, including personal information, authentication credentials, and privacy settings.
* Content Management: Store and organize various types of content shared by users, such as posts, photos, videos, and links.
* Social Graph: Represent relationships between users, including friendships, followers, and following relationships.
* Interaction Tracking: Record user interactions with content, such as likes, comments, shares, and views.
* Messaging System: Enable users to send private messages to each other, supporting real-time communication.
* Analytics and Recommendations: Analyze user behavior and preferences to provide personalized content recommendations and insights.


# Entities and Attributes for the Social Media Services Platform
Entities serve as the building blocks of our database, representing the fundamental objects or concepts that need to be stored and managed. Attributes define the characteristics or properties of each entity. Let’s explore each entity and attribute in detail

## user_profile: Represents individual users registered on the platform.
* UserID (Primary Key): Unique identifier for each user.
* Username: Unique username chosen by the user.
* Email: Email address of the user used for authentication.
* Password: Securely hashed password for user authentication.
* Name: Full name of the user.
* Bio: Optional bio or description provided by the user.
* ProfilePicture: URL or reference to the user’s profile picture.

## Post: Represents individual posts shared by users on the platform.
* PostID (Primary Key): Unique identifier for each post.
* UserID (Foreign Key): Reference to the user who created the post.
* Content: Text content of the post.
* MediaType: Type of media included in the post (e.g., text, image, video).
* MediaURL: URL or reference to the media file attached to the post.
* Timestamp: Date and time when the post was created.

## Comment: Represents comments made by users on posts.
* CommentID (Primary Key): Unique identifier for each comment.
* PostID (Foreign Key): Reference to the post being commented on.
* UserID (Foreign Key): Reference to the user who made the comment.
* Content: Text content of the comment.
* Timestamp: Date and time when the comment was posted.

## Like: Represents likes given by users to posts or comments.
* LikeID (Primary Key): Unique identifier for each like.
* PostID (Foreign Key): Reference to the post being liked.
* CommentID (Foreign Key): Reference to the comment being liked (nullable).
* UserID (Foreign Key): Reference to the user who liked the post or comment.
* Timestamp: Date and time when the like was given.

## Friendship: Represents mutual friendships between users.
* FriendshipID (Primary Key): Unique identifier for each friendship.
* UserID1, UserID2 (Foreign Keys): References to the users who are friends.
* Timestamp: Date and time when the friendship was established.
* Message: Represents private messages sent between users.
* MessageID (Primary Key): Unique identifier for each message.
* SenderID, ReceiverID (Foreign Keys): References to the users involved in the conversation.
* Content: Text content of the message.
* Timestamp: Date and time when the message was sent.

## Relationships Between these Entities
* User – Post Relationship
Each post is associated with one user (UserID in the Post table references UserID in the User table).
This is a one-to-many relationship, as one user can create multiple posts, but each post belongs to only one user.

* User – Comment Relationship
Each comment is associated with one user (UserID in the Comment table references UserID in the User table).
This is a one-to-many relationship, as one user can make multiple comments, but each comment belongs to only one user.

* User – Like Relationship
Each like is associated with one user (UserID in the Like table references UserID in the User table).
This is a one-to-many relationship, as one user can give multiple likes, but each like belongs to only one user.

* Post – Comment Relationship
Each comment is associated with one post (PostID in the Comment table references PostID in the Post table).
This is a one-to-many relationship, as one post can have multiple comments, but each comment belongs to only one post.

* Friendship Relationship
Each friendship involves two users (UserID1 and UserID2 in the Friendship table reference UserID in the User table).
This is a many-to-many relationship, as multiple users can be friends with each other.

* User – Message Relationship
User – Message Relationship
Each message involves two users (SenderID and ReceiverID in the Message table reference UserID in the User table).
This is a one-to-one relationship, as each message is sent between two users.


REF: https://www.geeksforgeeks.org/how-to-design-database-for-social-media-platform/
