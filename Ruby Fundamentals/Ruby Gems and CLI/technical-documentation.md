# Adding Technical Documentation

- In software development it refers to instructions and explanations with code to help devs understand and use software

Why is it useful?

- Helps devs grasp the code and its structure

Two types of documentation:

*Internal Documentation*: For developers, focuses on understanding the code and its architecture

*External Documentation*: For end users, explains how to use the software

An example of internal documentation for our CLI is us putting this in our *readme.md* file:
```
# Countries of the World CLI

## Description

The Countries of the World CLI is a command line interface that allows you to get information about countries. It uses this [site](https://www.scrapethissite.com/pages/simple/) to get the information.

## Installation

1. Clone the repository
2. Run `bundle install`
3. Click `run`to run project.

## Gems

### Nokogiri

[Nokogiri](https://rubygems.org/gems/nokogiri) is a gem that allows you to parse HTML and XML documents.

### HTTParty

[HTTParty](https://rubygems.org/gems/httparty) is a gem that allows you to make HTTP requests.

### RSpec

[RSpec](https://rubygems.org/gems/rspec) is a gem that allows you to test your code.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
```
- Describes CLI and installation steps
- Lists used gems and mentions the license

- Now it is a helpful guide for developers using our CLI