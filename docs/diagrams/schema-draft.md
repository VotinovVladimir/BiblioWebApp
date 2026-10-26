genres
  id INTEGER PK
  name VARCHAR(100) NOT NULL UNIQUE

books
  id INTEGER PK
  title VARCHAR(255) NOT NULL
  author VARCHAR(255) NOT NULL
  year SMALLINT NULL
  inventory_no VARCHAR(50) NOT NULL UNIQUE
  genre_id INTEGER FK → genres.id
  is_available BOOLEAN NOT NULL DEFAULT 1

readers
  id INTEGER PK
  full_name VARCHAR(255) NOT NULL
  card_no VARCHAR(50) NOT NULL UNIQUE
  phone VARCHAR(30) NULL
  email VARCHAR(100) NULL

loans
  id INTEGER PK
  book_id INTEGER FK → books.id NOT NULL
  reader_id INTEGER FK → readers.id NOT NULL
  loan_date DATE NOT NULL
  due_date DATE NOT NULL
  return_date DATE NULL
  status VARCHAR(20) NOT NULL  -- 'on_hand' | 'returned' | 'overdue'