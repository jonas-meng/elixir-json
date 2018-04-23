# Elixir JSON v2 

[![Build Status](https://travis-ci.org/cblage/elixir-json.svg?branch=develop)](https://travis-ci.org/cblage/elixir-json) [![Hex.pm](https://img.shields.io/hexpm/dt/json.svg?style=flat-square)](https://hex.pm/packages/json) [![Test Coverage](https://api.codeclimate.com/v1/badges/43b6e8c25e036558ccb6/test_coverage)](https://codeclimate.com/github/cblage/elixir-json/test_coverage) [![Hex.pm](https://img.shields.io/hexpm/v/json.svg?style=flat-square)](https://hex.pm/packages/json) [![Inline docs](http://inch-ci.org/github/cblage/elixir-json.svg)](http://inch-ci.org/github/cblage/elixir-json)
                                                                                                                                     
This library provides a blazing fast (link to benchmarks) 100% Elixir natively implemented JSON encoder and decoder for Elixir.
It also provides a Streaming API so you can stream the parsing of JSON payloads (for example processing a json array you coudl stream the individual elements of that array, etc). It also uses custom-made heuristic to allow parallel processing of the json payload (again for example when processing lists or deeply nested objects. You can fine tune the parallelization parameters in the config file. 

All contributions are welcome.

# Installing

Simply add ```{:json, "~> 2.5}``` to your project's ```mix.exs``` file, in the dependencies list and run ```mix deps.get json```.

## Example for a project that already uses [Plug](https://github.com/elixir-plug/plug):

```elixir
[
  {:cowboy, "~> 1.0.0"},
  {:plug, "~> 1.0"},
  {:json, "~> 2.5"},
]
```

# Simple Usaage

Encoding an Elixir type
```elixir
  @doc "
	JSON encode an Elixir list
  "	
  list = [key: "this will be a value"]
  is_list(list)
  # true
  list[:key]
  # "this will be a value"
  {status, result} = JSON.encode(list)
  # {:ok, "{\"key\":\"this will be a value\"}"}
  String.length(result)
  # 41
```

Decoding a list from a string that contains JSON
```elixir
  @doc "
	JSON decode a string into an Elixir list
  "
  json_input = "{\"key\":\"this will be a value\"}"
  {status, list} = JSON.decode(json_input)
	{:ok, %{"key" => "this will be a value"}}
  list[:key]
  # nil
  list["key"]
  # "this will be a value"
```

# Using `JSON.Stream`

## TODO: write me

# License
The Elixir JSON library is available under the [BSD 3-Clause aka "BSD New" license](http://www.tldrlegal.com/l/BSD3)
