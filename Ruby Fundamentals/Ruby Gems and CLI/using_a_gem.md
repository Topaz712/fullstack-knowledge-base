# Using a Gem

To use the Nokogiri gem in our project:

1. Create a repl/project and name it
2. Add the following code to our Gemfile:

```
# frozen_string_literal: true

source "https://rubygems.org"
ruby '3.1.2'
gem "nokogiri"
```

In the Gemfile, 
- Use the source method to specify the source:
  - `source "https://rubygems.org"`

- Use the gem method to add the Nokogiri gem:
  - `gem "nokogiri"`

- To add more gems, list them using the gem method:
    ```
    gem 'gem-1'
    gem 'gem-2'
    ```
- Specify the gem versions if needed. For example:
    ```
    # frozen_string_literal: true

    source "https://rubygems.org"

    ruby '3.1.2'
    gem "nokogiri", "1.15.4"
    ```
- The version consists of the "major. minor. and patch" numbers, indicating major changes, minor changes, and bug fixes

- If not specified, the latest versions of the gem and Ruby will be used in our project


## Nokigiri Gem

To use the Nokogiri gem and extract text from an HTML document we will:

- Run `bundle install` to install the Nokogiri gem and its dependencies specified in the Gemfile

- Gems are installed locally for our project, not globally

- The difference between the `Gemfile` and the `Gemfile.lock` is:
  - The *Gemfile* is used to specify the gems we want to use in our project
  - The *Gemfile.lock* file keeps track of the gems we are actually using in our project and their versions/dependencies

So if we have an *index.html* file:
```
<!DOCTYPE html>

<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<title>Nokogiri Example</title>
	</head>
	<body>
		<h1>Hello World</h1>
	</body>
</html>
```

Then in our *main.rb* file: 
```
require "nokogiri"

doc = Nokogiri::HTML(File.open("index.html"))

puts doc.css("h1").text
```

So the breakdown of main.rb:

`require "nokogiri"`: Imports the nokogiri gem

`Nokogiri::HTML`: Module to parse HTML documents

`doc = Nokogiri::HTML(File.open("index.html"))`: The **File.open("index.html")** method opens and parses the *"index.html"* file
When this file is passed to the **Nokogiri::HTML** module, it parses the HTML content and stores it in the **doc** variable 
  - Parsing means transforming the HTML into a usable format, like a Nokogiri instance 
With the **doc** variable, we can easily access and retrieve the desired data from the HTML document

`puts doc.css("h1").text`: Uses the *css method* and a *nokogiri method* to select the h1 element and extract its text content using the *text method*

so then we run **ruby main.rb** to print "Hello World" to the terminal