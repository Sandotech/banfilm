# Banfilm - Movie and Actor Library

Banfilm is a Ruby on Rails application that serves as a library for movies and actors. In this application, movies and actors are modeled as separate entities, and there is a many-to-many relationship established between them using a through table called "part."

![Banfilm_Screenshot_1](https://i.ibb.co/sHJ5tFZ/Firefox-Screenshot-2023-10-22-T15-09-43-015-Z.png)

## Prerequisites

Before getting started with Banfilm, make sure you have the following prerequisites installed on your system:

- ruby (version 3.1.2)
- rails (version 7.0.8)
- sqlite3 (version 1.4)

## Getting Started

To set up the Banfilm application on your local machine, follow these steps:

1. Clone the Banfilm repository from GitHub:

   ```bash
   git clone https://github.com/Sandotech/banfilm
   ```

2. Navigate to the project directory:

   ````bash
   cd banfilm
   ```

3. Install the required dependencies:

   ````bash
   bundle install
   ```

4. Create the PostgreSQL database and run the migrations:

   ````bash
   rails db:create
   rails db:migrate
   ```

5. Start the Rails server:

   ````bash
   rails server
   ```

6. Open your web browser and access the application at `http://localhost:3000`.

![Banfilm_Screenshot_2](https://i.ibb.co/Yh7vNQX/Firefox-Screenshot-2023-11-05-T20-14-26-843-Z.png)

## Models and Associations

Banfilm has two main models: `Movie` and `Actor`.

### Movie Model

The `Movie` model represents a movie in the library. It has the following attributes:

- `title` (string): The title of the movie.
- `release_year` (date): The release date of the movie.
- `plot` (string): short description about the movie.
- `image` (string): URL to a image of the movie.

The `Movie` model has the following associations:

```ruby
class Movie < ApplicationRecord
  has_many :parts
  has_many :actors, through: :parts
end
```

- `has_many :parts`: Specifies that a movie can have multiple parts (actor-movie relationships).
- `has_many :actors, through: :parts`: Establishes a many-to-many relationship between movies and actors through the `parts` table.

### Actor Model

The `Actor` model represents an actor in the library. It has the following attributes:

- `first_name` (string): The first name of the actor.
- `last_name` (string): The last name of the actor.
- `image` (string): URL image of the actor.
- `bio` (string): short description about the actor.

The `Actor` model has the following associations:

```ruby
class Actor < ApplicationRecord
  has_many :parts
  has_many :movies, through: :parts
end
```

- `has_many :parts`: Specifies that an actor can have multiple parts (actor-movie relationships).
- `has_many :movies, through: :parts`: Establishes a many-to-many relationship between actors and movies through the `parts` table.

### Part Model

The `Part` model represents the through table for the many-to-many relationship between movies and actors. It has the following attributes:

- `actor_id` (integer): The ID of the actor.
- `movie_id` (integer): The ID of the movie.

The `Part` model has the following associations:

```ruby
class Part < ApplicationRecord
  belongs_to :actor
  belongs_to :movie
end
```

- `belongs_to :actor`: Specifies that a part belongs to an actor.
- `belongs_to :movie`: Specifies that a part belongs to a movie.

![Banfilm_Screenshot_3](https://i.ibb.co/9bn8MK8/Firefox-Screenshot-2023-11-05-T20-15-28-241-Z.png)

## Author

By Diego Santos, fullstack developer with ruby on Rails.
@Sandotech.

## Conclusion

Congratulations! You now have a basic understanding of Banfilm, a movie and actor library built with Ruby on Rails. The application allows you to create movies and actors, associate actors with movies, and view detailed information about movies and actors. The many-to-many relationship between movies and actors is facilitated through the `parts` table. Feel free to explore and enhance the application further according to your requirements. Happy film browsing!
