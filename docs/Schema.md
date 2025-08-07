## 🧬 Database Schema
This schema outlines the data structure for user accounts, posts, and follower relationships.

View the schema on [dbdiagram.io](https://dbdiagram.io/d/6893f982dd90d17865cdb5f5)


Table users {
  id integer [primary key]
  username varchar
  role varchar
  created_at timestamp
}

Table posts {
  id integer [primary key]
  title varchar
  body text [note: 'Content of the post']
  user_id integer [not null]
  status varchar
  created_at timestamp
}

Table follows {
  following_user_id integer
  followed_user_id integer
  created_at timestamp
}

Ref user_posts: posts.user_id > users.id
Ref: users.id < follows.following_user_id
Ref: users.id < follows.followed_user_id