Data Structures
===============


Tuple
-----

```elixir
iex> tuple = {1, :two, "three"}  
iex> elem(tuple, 0)
1
iex> elem(tuple, 2) 
"three"
```


List
----

```elixir
iex> list = [1, "two", 3, :four] 
iex> list 
[1, "two", 3, :four]

iex> numbers = [1, 2, 3, 4]
iex> List.first(numbers) 
1
iex> List.last(numbers)  
4

iex> [1, "two", :three, 4] ++ ["more numbers"]
[1, "two", :three, 4, "more numbers"]
```


Keyword
-------

```elixir
iex> [{:first_number, 1}, {:second_number, 2}]
[first_number: 1, second_number: 2]

iex> [first_number: 1, second_number: 2]
[first_number: 1, second_number: 2]
```


Map
---

```elixir
iex> %{"one" => :two, 3 => "four"}
%{3 => "four", "one" => :two}

iex> map = %{a: 1, b: 2}
iex> Map.fetch(map, :a)
{:ok, 1}
iex> map[:b]
2
iex> map["non_existing_key"]
nil
```


MapSet
------

```elixir
iex> my_set = MapSet.new([1, 2, 3, 4, 5])
iex> MapSet.put(my_set, 6)
MapSet<[1, 2, 3, 4, 5, 6]>
iex> MapSet.delete(my_set, 6)
MapSet<[1, 2, 3, 4, 5]>
```


Struct
------

```elixir
iex> defmodule User do
...>   defstruct name: "John", age: 27
...> end

iex> %User{}
%User{age: 27, name: "John"}
iex> %User{name: "Jane"}
%User{age: 27, name: "Jane"}

iex> %User{oops: :field}
** (KeyError) key :oops not found in: %User{age: 27, name: "John"}
```

