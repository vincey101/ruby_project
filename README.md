# Rails CRUD API

A RESTful API built with Rails 8.1 for managing posts. This is an API-only backend designed to work with a React frontend.

## 🚀 Features

- Full CRUD operations for Posts
- MySQL database integration
- JSON API responses
- CORS enabled for frontend integration
- Input validation
- RESTful routing

## 📋 Prerequisites

- Ruby 3.3.5 or higher
- MySQL 5.6.4 or higher
- Bundler gem

## 🛠️ Setup

### 1. Install Dependencies

```bash
bundle install
```

### 2. Database Configuration

The database is configured to use MySQL with the following defaults:

- **Username:** `root`
- **Password:** `breitling`
- **Host:** `localhost`
- **Port:** `3306`
- **Database:** `rails_crud_development`

You can override these in `config/database.yml` or set environment variables:

- `DB_USERNAME`
- `DB_PASSWORD`
- `DB_HOST`
- `DB_PORT`

### 3. Create and Setup Database

```bash
# Create the database
bin/rails db:create

# Run migrations
bin/rails db:migrate
```

### 4. Start the Server

```bash
bin/rails server
```

The server will start on **http://localhost:3001** (port changed from default 3000 to avoid conflict with React).

To use a different port:

```bash
PORT=3002 bin/rails server
# or
bin/rails server -p 3002
```

## 📡 API Endpoints

### Base URL

```
http://localhost:3001
```

### Posts Endpoints

| Method   | Endpoint     | Description       |
| -------- | ------------ | ----------------- |
| `GET`    | `/posts`     | Get all posts     |
| `GET`    | `/posts/:id` | Get a single post |
| `POST`   | `/posts`     | Create a new post |
| `PATCH`  | `/posts/:id` | Update a post     |
| `PUT`    | `/posts/:id` | Update a post     |
| `DELETE` | `/posts/:id` | Delete a post     |

### Example Requests

#### Create a Post

```bash
POST /posts
Content-Type: application/json

{
  "post": {
    "title": "My Post Title",
    "body": "This is the post content. Must be at least 10 characters."
  }
}
```

#### Get All Posts

```bash
GET /posts
```

#### Get Single Post

```bash
GET /posts/1
```

#### Update a Post

```bash
PATCH /posts/1
Content-Type: application/json

{
  "post": {
    "title": "Updated Title",
    "body": "Updated content here"
  }
}
```

#### Delete a Post

```bash
DELETE /posts/1
```

## 📝 Post Model

### Fields

- `id` (integer, auto-increment)
- `title` (string, required, 3-100 characters)
- `body` (text, required, minimum 10 characters)
- `created_at` (datetime)
- `updated_at` (datetime)

### Validations

- Title must be present and between 3-100 characters
- Body must be present and at least 10 characters

## 🧪 Testing with Postman

See `POSTMAN_GUIDE.md` for detailed Postman testing instructions.

Quick test:

```bash
# Create a post
curl -X POST http://localhost:3001/posts \
  -H "Content-Type: application/json" \
  -d '{"post":{"title":"Test Post","body":"This is a test post with enough content"}}'

# Get all posts
curl http://localhost:3001/posts
```

## 📂 Project Structure

```
rails-crud/
├── app/
│   ├── controllers/
│   │   └── posts_controller.rb    # Handles HTTP requests
│   └── models/
│       └── post.rb                 # Post model with validations
├── config/
│   ├── routes.rb                   # API routes
│   ├── database.yml                # Database configuration
│   └── puma.rb                     # Server configuration
├── db/
│   └── migrate/                    # Database migrations
└── README.md
```

## 🔧 Configuration

### Port Configuration

Default port is **3001** (configured in `config/puma.rb`).

### CORS

CORS is enabled for all origins in development. Configure in `config/initializers/cors.rb`.

### Database

MySQL database configuration in `config/database.yml`.

## 📚 Documentation

- `POSTMAN_GUIDE.md` - Complete Postman testing guide
- `RAILS_ARCHITECTURE.md` - Detailed Rails architecture explanation
- `QUICK_START_GUIDE.md` - Quick start guide with visual flows

## 🛠️ Development

### Rails Console

```bash
bin/rails console
```

Example:

```ruby
# Create a post
Post.create(title: "Test", body: "Testing from console")

# Get all posts
Post.all

# Find a post
Post.find(1)
```

### View Routes

```bash
bin/rails routes
```

### Database Commands

```bash
# Create database
bin/rails db:create

# Run migrations
bin/rails db:migrate

# Rollback last migration
bin/rails db:rollback

# Reset database (⚠️ deletes all data)
bin/rails db:reset
```

## 🐛 Troubleshooting

### Server Already Running

If you see "A server is already running", remove the PID file:

```bash
rm -f tmp/pids/server.pid
```

### Database Connection Issues

- Verify MySQL is running
- Check database credentials in `config/database.yml`
- Ensure database exists: `bin/rails db:create`

### Port Already in Use

Change the port:

```bash
PORT=3002 bin/rails server
```

## 📦 Tech Stack

- **Ruby:** 3.3.5
- **Rails:** 8.1.1
- **Database:** MySQL
- **Server:** Puma
- **API Format:** JSON

## 📄 License

This project is for educational purposes.

---

**Built with ❤️ using Rails**
