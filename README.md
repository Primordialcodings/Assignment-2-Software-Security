# Assignment-2-Software-Security
def display_menu():
    print("\n=== BOOK INVENTORY MANAGER ===")
    print("1. View available books")
    print("2. Add a new book")
    print("3. Exit")


def view_books(book_list):
    print("\n--- Available Books ---")
    if not book_list:
        print("No books available in the inventory.")
        return

    for index, book in enumerate(book_list, start=1):
        print(
            f"{index}. '{book['title']}' by {book['author']} | Genre: {book['genre']} | Year: {book['year']}"
        )


def add_book(book_list):
    print("\n--- Add a New Book ---")

    title = input("Enter book title: ").strip()
    while not title:
        print("Title cannot be empty.")
        title = input("Enter book title: ").strip()

    author = input("Enter author name: ").strip()
    while not author:
        print("Author cannot be empty.")
        author = input("Enter author name: ").strip()

    genre = input("Enter genre: ").strip()
    if not genre:
        genre = "Unknown"

    while True:
        year_input = input("Enter publication year: ").strip()
        if year_input.isdigit():
            year = int(year_input)
            break
        print("Please enter a valid numeric year.")

    new_book = {
        "title": title,
        "author": author,
        "genre": genre,
        "year": year,
    }

    book_list.append(new_book)
    print(f"\nSuccess: '{title}' has been added to the library!")


def main():
    # Initial list of available books
    available_books = [
        {
            "title": "The Great Gatsby",
            "author": "F. Scott Fitzgerald",
            "genre": "Classic",
            "year": 1925,
        },
        {
            "title": "1984",
            "author": "George Orwell",
            "genre": "Dystopian",
            "year": 1949,
        },
    ]

    while True:
        display_menu()
        choice = input("\nSelect an option (1-3): ").strip()

        if choice == "1":
            view_books(available_books)
        elif choice == "2":
            add_book(available_books)
        elif choice == "3":
            print("\nExiting program. Goodbye!")
            break
        else:
            print("Invalid selection. Please choose 1, 2, or 3.")


if __name__ == "__main__":
    main()