# Asciidoctor::IndirExt

An Asciidoctor extension that adds a variable `indir`, which always points to the directory of the currently included asciidoc file.

This extension solves the problem that standard asciidoctor allows [no relative paths in subdocuments](https://github.com/asciidoctor/asciidoctor/issues/650), see  [asciidoctor issue #650](https://github.com/asciidoctor/asciidoctor/issues/650).


## Status and Maintenance

This is a fork of https://github.com/johannesjh/asciidoctor-indir_ext. I just updated some dependencies to make it work with the latest asciidoc version.


## Installation

If using bundler, add this line to your application's Gemfile:

```ruby
gem 'asciidoctor-indir-extension'
```

And then execute:

    $ bundle install


If you do not wish to use bundler, install as:

    $ gem install asciidoctor-indir-extension


## Usage

1. In the beginning of a subdocument, add this line:
`ifndef::indir[:indir: .]`

2. Include images like this:
`image::{indir}/images/example.svg[]`

3. When compiling a master document (that includes other subdocuments), require this extension.

For example:

```bash
bundle exec asciidoctor -r asciidoctor-indir-extension master.adoc
```


...or without bundler:

```bash
asciidoctor -r asciidoctor-indir-extension master.adoc
```

As a result, the extension provides an `indir` variable, which always points at the directory of the included asciidoc file. This allows image paths like `{indir}/images/example.svg` to be resolved relative to the included subdocument.



## Development

It is possible to start a docker container using `docker-compose run --rm dev bash`.
This allows to run the following commands inside the docker container
and thus avoids messing with the local system setup.

* Run `bundle install` to install dependencies
* To list all available rake tasks, run `bundle exec rake -T`
* To build a gem package on your local machine, run `bundle exec rake build`
* To install this gem onto your local machine, run `bundle exec rake install`
* To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org)


## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/pustekuchen91/asciidoctor-indir-extension.


## Credits

This extension is based on another asciidoctor extension called [jirutka/asciidoctor-include-ext](https://github.com/jirutka/asciidoctor-include-ext), which provides a cleaner implementation of asciidoctor's include processing, and thus makes it easier to overwrite according behavior through an extension.

Special thanks goes to [@mojavelinux](https://github.com/mojavelinux) for pointing out this solution in [asciidoctor issue #650](https://github.com/asciidoctor/asciidoctor/issues/650) and for providing valuable feedback.


## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
