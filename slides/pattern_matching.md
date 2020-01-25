Pattern Matching
================


Match Operator
--------------

Símbolo "="

```elixir 
iex(1)> x = 2
2
iex(2)> 2 = x
2
iex(3)> 1 = x
** (MatchError) no match of right hand side value: 2
    (stdlib) erl_eval.erl:453: :erl_eval.expr/5
    (iex) lib/iex/evaluator.ex:257: IEx.Evaluator.handle_eval/5
    (iex) lib/iex/evaluator.ex:237: IEx.Evaluator.do_eval/3
    (iex) lib/iex/evaluator.ex:215: IEx.Evaluator.eval/3
    (iex) lib/iex/evaluator.ex:103: IEx.Evaluator.loop/1
    (iex) lib/iex/evaluator.ex:27: IEx.Evaluator.init/4
```


With tuples
-----------

```elixir
iex> {a, b, c} = {:hello, "world", 42}
{:hello, "world", 42}
iex> a
:hello
iex> b
"world"

iex> {:ok, result} = {:ok, 13}
{:ok, 13}
iex> result
13
```


With Lists
----------

```elixir
iex(1)> [head | tail] = [1,2,3,4]
[1, 2, 3, 4]
iex(2)> head
1
iex(3)> tail
[2, 3, 4]
```


With Structs
------------

```elixir
iex> %User{name: "Fede", age: age} = %User{name: "Fede", age: 30}
%User{age: 30, name: "Fede"}

iex> %{name: "Fede", age: age} = %User{name: "Fede", age: 30}
%User{age: 30, name: "Fede"}

iex> %User{name: "Fede", age: age} = %{name: "Fede", age: 30}
** (MatchError) no match of right hand side value: %{age: 30, name: "Fede"}
    (stdlib) erl_eval.erl:453: :erl_eval.expr/5
    (iex) lib/iex/evaluator.ex:257: IEx.Evaluator.handle_eval/5
    (iex) lib/iex/evaluator.ex:237: IEx.Evaluator.do_eval/3
    (iex) lib/iex/evaluator.ex:215: IEx.Evaluator.eval/3
    (iex) lib/iex/evaluator.ex:103: IEx.Evaluator.loop/1
    (iex) lib/iex/evaluator.ex:27: IEx.Evaluator.init/4
```


Pin Operator
------------

```elixir
iex> x = 1
1
iex> ^x = 2
** (MatchError) no match of right hand side value: 2
iex> {y, ^x} = {2, 1}
{2, 1}
iex> y
2
iex> {y, ^x} = {2, 2}
** (MatchError) no match of right hand side value: {2, 2}
```


Underscore
----------

```elixir
iex> [head | _] = [1, 2, 3]
[1, 2, 3]
iex> head
1

iex> _
** (CompileError) iex:1: invalid use of _. "_" represents a
  value to be ignored in a pattern and cannot be used in expressions
```


Real Example
------------

```elixir
response = HTTP.patch(url, body, headers, [])
case response do
  {:ok, %{status_code: 200, body: body}} ->
    body
  {:ok, %{status_code: 404} = resp} ->
    "Error: #{resp.status_code} Not found!"
  {:error, %{reason: reason}} ->
    "Error: #{reason}"
end
```
