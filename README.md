# reporter-ruby

This is a Ruby library for reading and analyzing data from the [Reporter iOS app](http://reporter-app.com). Currently under heavy development.

## Installation

Add this line to your application's Gemfile:

    gem 'reporter-ruby', github: 'eturk/reporter-ruby'

And then execute:

    $ bundle

## Usage

```ruby
reporter = Reporter::Client.from_export(Dir.glob('/Users/ethan/Dropbox/Apps/Reporter-App/*.json'))

reporter.snapshots # => [ Reporter::Snapshot, Reporter::Snapshot, ... ]
reporter.questions #= > [ Reporter::Question, Reporter::Question, ... ]

whom = reporter.questions.where(questionPrompt: 'Who are you with?').first # => Reporter::Question

freq_table = reporter.analyze.frequency_table(whom, :tokens) # => Reporter::Analyze::FrequencyTable

freq_table.to_arr # => [ [ "Neil deGrasse Tyson", 10 ], [ "Carl Sagan", 5 ] ]
freq_table.mean # => 7.5
```

## Contributing

1. Fork it ( https://github.com/eturk/reporter-ruby/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
