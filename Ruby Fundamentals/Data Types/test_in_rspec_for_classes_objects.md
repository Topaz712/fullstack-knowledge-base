# Writing tests in RSpec for Classes and Objects

code from Book class to test:
```
class Book
  attr_accessor :title, :author, :pages

  def initialize(title, author, pages)
    @title = title
    @author = author
    @pages = pages
  end
end
```
Book class has three instance variables: @title, @author, and @pages

this is an example of a test for the Book class:
```
require_relative '../book'

describe Book do
  describe '#title' do
    it 'returns the title of the book' do
      book = Book.new("The Pragmatic Programmer", "Andy Hunt and Dave Thomas", 352)

      expect(book.title).to eq("The Pragmatic Programmer")
    end
  end
end
```

- Tests for the Book class are written using the *rspec* gem 
  - *The rspec gem is a testing framework for Ruby*

- The `describe` method outlines the Book class, and `require_relative` enables its use in tests 

- A specific test example checks if the title method correctly returns the book's title by creating an instance and verifying the expected outcome with `expect`