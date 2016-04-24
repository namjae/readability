# Readability

[![Build Status](https://travis-ci.org/keepcosmos/readability.svg?branch=master)](https://travis-ci.org/keepcosmos/readability)
[![Readability version](https://img.shields.io/hexpm/v/readability.svg)](https://hex.pm/packages/readability)

Readability is Elixir library for extracting and curating articles.  
Check out The [Documentation](https://hexdocs.pm/readability/Readability.html) for full and detailed guides

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed as:

  1. Add readability to your list of dependencies in `mix.exs`:

    ```elixir
    def deps do
      [{:readability, "~> 0.3"}]
    end
    ```

  2. Ensure readability is started before your application:

    ```elixir
    def application do
      [applications: [:readability]]
    end
    ```

## Usage

To parse document, you must prepare html string.
The example below, `html` variable is the html source from [Elixir Design Goals](http://elixir-lang.org/blog/2013/08/08/elixir-design-goals/)

### Examples
```elixir

### Extract the title
Readability.title(html)
#=> Elixir Design Goals

### Extract the content with transformed html.
html
|> Readability.article
|> Readability.raw_html
#=>
# <div><div class=\"entry-content\"><p>During the last year,
# ...
# ... out our sidebar for other learning resources.</p></div></div>

### Extract the text only content.
html
|> Readability.article
|> Readability.readable_text

#=>
# During the last year, we have spoken at many conferences spreading the word about Elixir. We usually s.....
# ...
# ... started guide, or check out our sidebar for other learning resources.
```

### Options

You may provide options(Keyword type) to `Readability.article`, including:

* retry_length \\\\ 250
* min_text_length \\\\ 25
* remove_unlikely_candidates \\\\ true,
* weight_classes \\\\ true,
* clean_conditionally \\\\ true,
* remove_empty_nodes \\\\ true,

## Test

To run the test suite:

    $ mix test

## Todo
* [ ] Extract authors
* [ ] Extract Images
* [ ] Extract Videos
* [ ] Convert relative paths into absolute paths of `img#src` and `a#href`
* [ ] More configurable
* [ ] Command line interface

## Related and Inpired Projects

* [readability.js](https://github.com/mozilla/readability) is a standalone version of the readability library used for Firefox Reader View.
* [newspaper](https://github.com/codelucas/newspaper) is an advanced news extraction, article extraction, and content curation library for Python.
* [ruby-readability](https://github.com/cantino/ruby-readability) is a tool for extracting the primary readable content of a webpage.

## LICENSE

This code is under the Apache License 2.0. See <http://www.apache.org/licenses/LICENSE-2.0>.
