# lucide-rails

[heyvito/lucide-rails](https://github.com/heyvito/lucide-rails) with a current
[Lucide](https://lucide.dev) icon snapshot.

`lucide_icon` is the same helper. This fork vendors Lucide **1.33.0** (gem
**0.7.6**) so icons added after the 0.7.4 snapshot — including `user-round-key` —
resolve. It also uses `File.binread` for `stripped.bin.gz` so the snapshot
loads on Windows ([upstream #39](https://github.com/heyvito/lucide-rails/pull/39)).

Icon refresh is offered upstream as
[heyvito/lucide-rails#43](https://github.com/heyvito/lucide-rails/pull/43).

## Installation

```ruby
gem "lucide-rails", github: "firedev/lucide-rails", tag: "v0.7.6"
```

## Usage

### Quickstart

The gem default options should be enough for most applications. Simply add it to
your `Gemfile`, and, in any view:

```erb
<%= lucide_icon('accessibility') %>
```

Which renders:

```html
<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="16" cy="4" r="1"></circle><path d="m18 19 1-7-5.87.94"></path><path d="m5 8 3-3 5.5 3-2.21 3.1"></path><path d="M4.24 14.48c-.19.58-.27 1.2-.23 1.84a5 5 0 0 0 5.31 4.67c.65-.04 1.25-.2 1.8-.46"></path><path d="M13.76 17.52c.19-.58.27-1.2.23-1.84a5 5 0 0 0-5.31-4.67c-.65.04-1.25.2-1.8.46"></path></svg>
```

### Providing Extra Attributes to a Single Icon

To provide extra attributes to a single SVG, pass them through the helper:

```erb
<%= lucide_icon('accessibility', 'extra-attr' => 'test') %>
```

Which yields the following HTML:

```html
<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" extra-attr="test"><circle cx="16" cy="4" r="1"></circle><path d="m18 19 1-7-5.87.94"></path><path d="m5 8 3-3 5.5 3-2.21 3.1"></path><path d="M4.24 14.48c-.19.58-.27 1.2-.23 1.84a5 5 0 0 0 5.31 4.67c.65-.04 1.25-.2 1.8-.46"></path><path d="M13.76 17.52c.19-.58.27-1.2.23-1.84a5 5 0 0 0-5.31-4.67c-.65.04-1.25.2-1.8.46"></path></svg>
```

### Providing Extra Attributes to All Icons

In case an application needs to add an extra attribute on every icon output by
this library, create a new initializer, and use `LucideRails.default_options=`:

```ruby
# config/initializers/lucide_rails.rb
LucideRails.default_options = LucideRails.default_options.merge(
  'class' => 'lucide-icon',
  'some-extra-attr' => 'some-other-value',
)
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run
`bundle exec rspec` to run the tests. You can also run `bundle exec bin/console`
for an interactive prompt that will allow you to experiment.

Tag a new version after an icon refresh: bump `lib/lucide-rails/version.rb`,
commit, `git tag vX.Y.Z`, push the tag. Houseviser pins that tag in the Gemfile.

### Updating Bundled Icons

```
bundle exec bin/fetch-icons
```

That clones the latest Lucide release, regenerates `icons/`, and updates
`LUCIDE_VERSION`. Then bump the gem version and tag.

## Contributing

This fork lives at https://github.com/firedev/lucide-rails. Upstream is
https://github.com/heyvito/lucide-rails.

## Code of Conduct

Everyone interacting in the Lucide::Rails project's codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/heyvito/lucide-rails/blob/master/CODE_OF_CONDUCT.md).

## License

```
The MIT License (MIT)

Copyright (c) 2022-2024 Vito Sartori

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

```
