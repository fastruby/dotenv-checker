# Dotenv Validator

This gem validates `.env` variables. You can configure validation rules by adding the
appropriate comments to the `.env.sample` file.

# Installation

Add the gem to your gemfile:

```
gem "dotenv_validator", github: "fastruby/dotenv_validator", branch: :main
```

Call `DotenvValidator.check!` in an initializer:

```
echo "DotenvValidator.check!" > "config/initializers/1_dotenv_validator.rb"
```

> Note the `1-` in the name so it's executed before any other initializer, since initializers are run in alphabetical order.

> You can use `DotenvValidator.check` without the `!` to show warnings instead of raising an exception.

## Updating

At the moment it is only available on Github, so you would need to run:

```
bundle update --source dotenv_validator
```

# Configuring env variable

In your `.env.sample` file, you can add comments to tell DotenvValidator how to validate the variable:

```
MY_REQUIRED_VAR=value #required
THIS_IS_AN_OPTIONAL_INT=123 #format=int
THIS_IS_A_REQUIRED_EMAIL=123 #required,format=email
```

## Formats

- `int` or `integer`
- `float` (note that all integers are floats too)
- `str` or `string` (accepts anything)
- `email` (checks value against `/[\w@]+@[\w@]+\.[\w@]+/`)
- `url` (checks value against `/https?:\/\/.+/`)
- any other value acts as a regexp!

### Regexp format

If you have a complex format, you can use a regexp for validation:

```
MY_WEIRD_ENV_VAR=123_ABC #required,format=\d{3}_\w{3}
```

In the above example, `\d{3}_\w{3}` is converted to a regexp and the value is checked against it.

## Contributing

Bug reports and pull requests are welcome on GitHub at [https://github.com/fastruby/dotenv_validator](https://github.com/fastruby/dotenv_validator). This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

When Submitting a Pull Request:

* If your PR closes any open GitHub issues, please include `Closes #XXXX` in your comment

* Please include a summary of the change and which issue is fixed or which feature is introduced.

* If changes to the behavior are made, clearly describe what changes.

* If changes to the UI are made, please include screenshots of the before and after.
