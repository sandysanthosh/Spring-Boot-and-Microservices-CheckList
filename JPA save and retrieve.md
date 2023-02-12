

```


import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import javax.persistence.*;
import java.util.List;

@RestController
@RequestMapping("/api/books")
public class BookController {

  @Autowired
  private BookRepository repository;

  @GetMapping
  public List<Book> getAllBooks() {
    return repository.findAll();
  }

  @PostMapping
  public Book addBook(@RequestBody Book book) {
    return repository.save(book);
  }

  @PutMapping("/{id}")
  public Book updateBook(@PathVariable long id, @RequestBody Book book) {
    book.setId(id);
    return repository.save(book);
  }

  @DeleteMapping("/{id}")
  public void deleteBook(@PathVariable long id) {
    repository.deleteById(id);
  }
}

@Entity
class Book {

  @Id
  @GeneratedValue(strategy=GenerationType.AUTO)
  private long id;

  private String title;
  private String author;

  public long getId() {
    return id;
  }

  public void setId(long id) {
    this.id = id;
  }

  public String getTitle() {
    return title;
  }

  public void setTitle(String title) {
    this.title = title;
  }

  public String getAuthor() {
    return author;
  }

  public void setAuthor(String author) {
    this.author = author;
  }
}

interface BookRepository extends JpaRepository<Book, Long> {

}


```


In this example, we have a BookController that defines the REST endpoints for creating, reading, updating, and deleting books.

The Book entity represents a book and has properties for the id, title, and author.

The BookRepository is an interface that extends JpaRepository and provides basic CRUD operations for the Book entity.

The @Autowired annotation is used to inject an instance of BookRepository into the BookController. 

The @RestController annotation indicates that this class is a REST controller, and the @RequestMapping annotation maps the endpoint to /api/books.

The getAllBooks method maps to the GET /api/books endpoint and returns a list of all books. 

The addBook method maps to the POST /api/books endpoint and adds a new book to the repository.

The updateBook method maps to the PUT /api/books/{id} endpoint and updates an existing book. 

The deleteBook method maps to the DELETE /api/books/{id} endpoint and deletes a book from the repository.

This is just a simple example of how to use Spring Boot and JPA to create a REST API for saving and retrieving data. 

You can customize this code to fit your specific needs.


