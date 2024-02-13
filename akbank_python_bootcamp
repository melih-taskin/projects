class Library:
  # 1 - Constructor method to open
  def __init__(self, file_name):
    self.file_name = file_name
    ''' From the tip written in the project's pdf,
    used "a+" mode to read and append lines'''
    self.file = open(self.file_name, 'a+')

  # 1 - Destructor method to close the file
  def __del__(self):
    self.file.close()

  # 2.a - List Books
  def list_books(self):
    ''' I realized that the codeline below is a must.  '''
    self.file.seek(0)

    # 2.a.i - Read the contents of the file
    book_content = self.file.read()

    # 2.a.ii - Adding each line to a list using splitlines()
    book_lines = book_content.splitlines()

    # 2.a.iii - Print book names and authors
    for line in book_lines:
      ''' Since it is csv file that given in the introduction,
      the list "book_lines" should seperate with "," and I should create a
      new list for this to reach indexes of book names and authors'''
      book_info = line.split(',')
      book_name = book_info[0]
      author = book_info[1]
      print(f"Book Name: {book_name}, Author: {author}")

  # 2.b - Add Book
  def add_book(self):
    ''' I realized that the codeline below is a must.  '''
    self.file.seek(0)

    # 2.b.i - inputs of book information
    while True:
      book_title = input("Enter the title of the book: ")
      if book_title.isspace():
        print("Please enter something other than just whitespace.")
      else:
        book_title = str(book_title)
        break

    while True:
      book_author = input("Enter the author of the book: ")
      if book_author.isspace():
        print("Please enter something other than just whitespace.")
      else: 
        book_author = str(book_author)
        break

    while True:
      release_year = input("Enter the release year of the book: ")
      if release_year.isspace():
        print("Please enter something other than just whitespace.")
      else:
        release_year = str(release_year)
        break
    ''' Since, the number of pages must be a integer, I checked for if input is
    correct. I can do same things for other inputs of books' information, but
    the infos are respect to different kind of characteristics. Besides, we do
    not have to add this kind of utilities for our task, that is why I do it for
    only "number of pages of the book". String covers it all kind of things. '''
    while True:
      num_pages = input("Enter the number of pages of the book: ")
      if num_pages.isdigit():
        num_pages = int(num_pages)
        break
      else:
        print("Please enter a valid number.")

    # 2.b.ii - Create string with these infos
    ''' If we want to add 2 or many books' informations, we should add to
    the new line, so that we use "\n" at the end of string.'''
    book_info = f"{book_title},{book_author},{release_year},{num_pages}\n"

    # 2.b.iii - Appending book_info from above code to the file
    self.file.write(book_info)

  # 2.c - Remove Book
  
  def remove_book(self):

    # 2.c.i book title input
    book_title = input("Enter the title of the book to remove: ")

    # 2.c.ii Read the file contents and add book to a list
    self.file.seek(0) # We need it to start at the beginning
    book_content = self.file.read()
    book_lines = book_content.splitlines()

    # 2.c.iii Find the index of the book to be deleted in the list
    ''' I think creating a matrix to collect indexes would help us, if there 
    are many books with same name exist. There is no constraint for this 
    situation in the tasks. However, if we want to remove the certain book,
    we can add more if/elif/else statements. '''
    books_to_remove_indexes = []
    for index, line in enumerate(book_lines):
      book_info = line.strip().split(',')
      if book_info[0] == book_title:
        books_to_remove_indexes.append(int(index))

    # Additional code for input title of book doesn't exist
    if len(books_to_remove_indexes) == 0:
      print(f"Book title '{book_title}' does not exist!")

    # 2.c.iv Remove the book from the list
    ''' Using reverse sort helping us when we want to delete all of the books
    whose names' same as user's input. '''
    for index in sorted(books_to_remove_indexes, reverse=True):
      book_lines.pop(index)

    # 2.c.v Remove the contents of the books.txt
    self.file.seek(0) # We need it to start at the beginning
    ''' Without any argument of truncate will be delete all contents in file'''
    self.file.truncate()

    # 2.c.vi Add all elements of the list to the books.txt
    for line in book_lines:
      self.file.write(line + "\n")

# 3
lib = Library("books.txt")

# 4-Menu

while True:
  # 4.a
  print(""" ***MENU***
1) List Books
2) Add Books
3) Remove Book
q) Quit
       """)

  # 4.b
  choice = input("Enter your choice: ")

  # 4.c
  if choice == "1":
    lib.list_books()
  elif choice == "2":
    lib.add_book()
  elif choice == "3":
    lib.remove_book()
  elif choice == "q":
    break
  else:
    print("Invalid choice. Enter a valid option.")
