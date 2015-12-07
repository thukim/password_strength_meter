# PasswordStrengthMeter

Welcome to your new gem! In this directory, you'll find the files you need to be able to package up your Ruby library into a gem. Put your Ruby code in the file `lib/password_strength_meter`. To experiment with that code, run `bin/console` for an interactive prompt.

TODO: Delete this and the text above, and describe your gem

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'password_strength_meter'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install password_strength_meter

## Usage

The password score is calculated based on the following algorithm:
  * If the password matches the username then BadPassword
  * If the password is less than 4 characters then TooShortPassword
  * Score += password length * 4
  * Score -= repeated characters in the password ( 1 char repetition )
  * Score -= repeated characters in the password ( 2 char repetition )
  * Score -= repeated characters in the password ( 3 char repetition )
  * Score -= repeated characters in the password ( 4 char repetition )
  * If the password has 3 numbers then score += 5
  * If the password has 2 special characters then score += 5
  * If the password has upper and lower character then score += 10
  * If the password has numbers and characters then score += 15
  * If the password has numbers and special characters then score += 15
  * If the password has special characters and characters then score += 15
  * If the password is only characters then score -= 10
  * If the password is only numbers then score -= 10
  * If score > 100 then score = 100

Then according to the score, we can determine the password strength:
  * If 0 < score < 34 then BadPassword
  * If 34 < score < 68 then GoodPassword
  * If 68 < score < 100 then StrongPassword

Reference: https://phiras.wordpress.com/2007/04/08/password-strength-meter-a-jquery-plugin/
## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake rspec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/thukim/password_strength_meter. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

