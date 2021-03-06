# Immigrant
[<img src="https://secure.travis-ci.org/jenseng/immigrant.png?rvm=1.9.3" />](http://travis-ci.org/jenseng/immigrant)

Immigrant gives [Foreigner](https://github.com/matthuhiggins/foreigner) a
migration generator so you can effortlessly add missing foreign keys. This is
particularly helpful when you decide to add keys to an established Rails app.

Like Foreigner, Immigrant requires Rails 3.0 or greater.

## Installation

Add the following to your Gemfile:

```ruby
gem 'immigrant'
```

## Usage

```bash
rails generate immigration AddKeys
```

This will create a migration named AddKeys which will have `add_foreign_key`
statements for any missing foreign keys. Immigrant infers missing ones by
evaluating the associations in your models (e.g. `belongs_to`, `has_many`, etc.).
Only missing keys will be added; existing ones will never be altered or
removed.

## Considerations

If the data in your tables is bad, then the migration will fail to run
(obviously). IOW, ensure you don't have orphaned records **before** you try to
add foreign keys.

## Known Issues

Immigrant currently only looks for foreign keys in `ActiveRecord::Base`'s
database. So if a model is using a different database connection and it has
foreign keys, Immigrant will incorrectly include them again in the generated
migration.

## [Changelog](CHANGELOG.md)

## License

Copyright (c) 2012-2014 Jon Jensen, released under the MIT license
