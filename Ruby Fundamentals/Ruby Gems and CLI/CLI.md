# CLI : Countries of The World 

- CLI stands for Command Line Interface
  - It allows interaction with the computer using commands
  - A comparable example is Angular CLI for Angular projects

In this lesson we will be creating a CLI to scrape country information

We start by creating a new repl in replit named *countries_of_the_world_cli*

the following files we will be utilizing: 
  - *readme.md* for documentation 
  - *Gemfile* for gem specification
  - *main.rb* to run the project and start the CLI
  - *lib* directory for code files


1. We create a file called *lib/cli.rb*
```
class CLI
  def start
    puts "Welcome to the Countries of the World CLI!"
    puts "What is your name?"
    name = gets.strip
    puts "Hello #{name}!"
  end

  def get_input
    gets.strip
  end
end
```
- Method `start` displays a welcome message, asks for the user's name, and greets them

- `get_input` method retrieves and strips user's input of whitespace

2. In *main.rb*, a CLI instance is created, and `start` method is called
```
require_relative './lib/cli.rb'
CLI.new.start
```
once we run this in console or shell it should say
```
Welcome to the Countries of the World CLI!
What is your name?
Topaz
Hello Topaz!
```

## Adding Tests

3. 
- RSpec is added/installed for testing
- Run `bundle add rspec` , it installs RSpec
- The run `bundle exec rspec --init` , it initializes RSpec in the project folder
- Make sure to run `gem install rspec` to use the rspec gem in shell provided by commands like rspec

Now we create a test file, `spec/lib/cli_spec.rb`to test the CLI class
```
require_relative "../../lib/cli.rb"

RSpec.describe CLI do
  describe "#start" do
    it "prints a welcome message and asks the user for their name" do
      cli = CLI.new

      # Stubbing user input to simulate interaction
      allow(cli).to receive(:gets).and_return("Topaz\n")

      # Expecting specific output to standard output
      expect { cli.start }.to output(
        "Welcome to the Countries of the World CLI!\nWhat is your name?\nHello Topaz!\n"
      ).to_stdout
    end
  end
end
```
- Now run tests with `bundle exec rspec`

There are two ways to run tests: 
  - rspec : will use the globally installed version of rspec
  - bundle exec rspec : will use the locally installed version of rspec

- We should use `bundle exec rspec` because it ensures the use of the locally installed version of RSpec, preventing version conflicts

Here we use `RSpec.describe` to talk about what we're testing , which is the CLI class
  - `describe "#start"` specifies that we're focusing on the start method
  - The `it` method explains the expected behavior of `start` which is printing a welcome message and asking for the user's name
  - We create a new CLI object named cli `cli = CLI.new`
  - Stubbing: We pretend that what user input `gets` is "Topaz" using the `allow` method
  - Then use `expect` method to output the `cli.start` method to output the welcome message and user input

## Web Scraping with Nokogiri and httparty

In this section we will learn about scraping data about countries like capitals, populations, and area from (www.scrapethissite.com)[www.scrapethissite.com] using Nokogiri and HTTParty gems
  - This website allows scraping for education purposes but we need to watch out for sites that don't allow it or else we'll be banned from the site

Gemfile:
```
source "https://rubygems.org"

git_source(:github) {|repo_name| "https://github.com/#{repo_name}" }

ruby '3.1.2'
gem "rspec"
gem "nokogiri"
gem "httparty"
```
- Include "nokogiri" and "httparty" gems
- Run `bundle install` to install them

Then we create a file called *scraper.rb*:
```
require "nokogiri"
require "httparty"

module Scraper
  INDEX_URL = 'https://www.scrapethissite.com/pages/simple/'
  def self.scrape_countries
    unparsed_page = HTTParty.get(INDEX_URL)
    parsed_page = Nokogiri::HTML(unparsed_page.body)
    countries = parsed_page.css("div.country")

    countries.each do |country|
      name = country.css("country-name").text
      capital = country.css("country-capital").text
      population = country.css("country-population").text
      area = country.css("country-area").text

      puts "#{name} #{capital} #{population} #{area}"
    end
  end
end
```
- It makes a GET request to www.scrapethissite.com
- Parses HTML using Nokogiri
- Prints out the HTML to the terminal when we click run
- Initially selected all div elements with the class "country"
- Later we refined the selection to get country specific details like name, capital, population, and area

Then we also have our created file *cli.rb*:
```
require_relative "scraper.rb"

class CLI
  def start
    Scraper.scrape_countries
    puts "Welcome to the Countries of the World CLI!"
    puts "What is your name?"
    name = gets.strip
    puts "Hello #{name}!"
  end

  def get_input
    gets.strip
  end
end
```
- It calls `Scraper.scrape_countries` from the `start` method
- Asks for the user's name after scraping

So with extracting information from a website about countries, we initially grabbed too much information and needed to fine tune our approach to get the specific details we wanted to see, but now we have a bug because it only prints alot of blanks so we'll have to debug

## Byebug gem

While scraping country data from (www.scrapethissite.com)[www.scrapethissite.com] using Nokogiri and HTTParty we encountered a bug where it would only print blank spaces
so now we will be incorporating the `Byebug gem for debugging`

1. In Gemfile:
```
# frozen_string_literal: true

source "https://rubygems.org"

git_source(:github) {|repo_name| "https://github.com/#{repo_name}" }

ruby '3.1.2'
gem "rspec"
gem "nokogiri"
gem "httparty"
gem "byebug"
```
- We included the "byebug" gem
- Then we run `bundle install` to install that gem

2. In lib/scraper.rb:
```
require "nokogiri"
require "httparty"
require "byebug"
.
.
.
  def self.scrape_countries
    unparsed_page = HTTParty.get(INDEX_URL)
    parsed_page = Nokogiri::HTML(unparsed_page.body)
    countries = parsed_page.css("div.country")

    countries.each do |country|
      name = country.css("country-name").text
      capital = country.css("country-capital").text
      population = country.css("country-population").text
      area = country.css("country-area").text
      debugger; # <---- Add this line
      puts "#{name} #{capital} #{population} #{area}"
    end
end
```
To debug we:
- Add `require "byebug"`
- Insert `debugger;` to pause the code for inspection
- Run the project and use terminal commands to inspect variables in our code

After doing this, we saw that the initial debug revealed empty strings for scraped data
  - Identified missing periods in CSS selectors to be *".country-name"* and not *"country-name"* since they're classes and shouldn't be selected as elements
  - We used Byebug to inspect nokogiri instances, correct CSS selectors, and strip unwanted characters/white-space

3. Then we created a file called country.rb:
```
class Country
  attr_accessor :name, :capital, :population, :area

  @@all = []

  def initialize(name, capital, population, area)
    @name = name
    @capital = capital
    @population = population
    @area = area
    @@all << self
  end

  def self.all
    @@all
  end
end
```
- We created a class to store country data with attributes: name, capital, population, and area

- Utilized `attr_accessor` for **getter and setter** methods

- Implemented `@@all` class variable *to store instances*

- `initialize` method to initialize new Country object with name, capital, population, and area

*Using objects to store data makes things easier, we create a Country object, store data in it, and then access the information we need through that object*

4. In scraper.rb:
```
require "nokogiri"
require "httparty"
require "byebug"
require_relative "./country.rb"

module Scraper
  INDEX_URL = 'https://www.scrapethissite.com/pages/simple/'
  def self.scrape_countries
    unparsed_page = HTTParty.get(INDEX_URL)
    parsed_page = Nokogiri::HTML(unparsed_page.body)
    countries = parsed_page.css("div.country")

    countries.each do |country|
      name = country.css(".country-name").text.strip
      capital = country.css(".country-capital").text.strip
      population = country.css(".country-population").text.strip
      area = country.css(".country-area").text.strip
      Country.new(name, capital, population, area)
    end
  end
end
```
- We now update scraper to use the Country class so now the modified *scraper.rb* file can create Country objects and store scraped data in them

5. In cli.rb:
```
require_relative "./scraper.rb"

class CLI
  def start
    Scraper.scrape_countries
    puts "Welcome to the Countries of the World CLI!"
    puts "What is your name?"
    name = gets.strip
    puts "Hello #{name}!"
    puts "Please enter a country name to get more information about it."
    input = gets.strip
    country = Country.all.find { |country| country.name.downcase == input.downcase }
    if country === nil
      puts "Sorry, that country is not in our database. Please try again."
    else
      puts "Name: #{country.name}"
      puts "Capital: #{country.capital}"
      puts "Population: #{country.population}"
      puts "Area: #{country.area}"
    end
  end

  def get_input
    gets.strip
  end
end
```
- Like this we made it so: 
- User is welcomed, asked for their name, and prompted to enter a country name
- Incorporated user interaction to enter a country name
- It Implements a search function to retrieve information about a specific country
- Displays information about the entered country or an error message if not found

*In this lesson about the CLI the process involves web scraping, debugging, and structuring data in classes to create a functional CLI for country information*
