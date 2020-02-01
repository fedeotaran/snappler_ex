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
iex> put_elem(tuple, 0, 'uno')
{'uno', :two, "three"}
iex> tuple_size(tuple)
3
```


Tuple module 
------------

```ruby
Tuple.append(tuple, value)
# Inserts an element at the end of a tuple.
Tuple.delete_at(tuple, index)
# Removes an element from a tuple.
Tuple.duplicate(data, size)
# Creates a new tuple.
Tuple.insert_at(tuple, index, value)
# Inserts an element into a tuple.
Tuple.to_list(tuple)
# Converts a tuple to a list.
```

Doc: [Tuple](https://hexdocs.pm/elixir/Tuple.html)


List
----

```elixir
iex> [1, "two", 3, :four]
[1, "two", 3, :four]
iex> [1, 2, 3] ++ [4, 5, 6]
[1, 2, 3, 4, 5, 6]
iex> [1, true, 2, false, 3, true] -- [true, false]
[1, 2, 3, true]
iex> [1, "two", :three, 4] ++ ["more numbers"]
[1, "two", :three, 4, "more numbers"]
iex> hd([1, 2, 3])
1
iex> tl([1, 2, 3])
[2,3]
iex> 2 in [1,2,3]
true
```


```elixir
iex> [0 | [1, "two", 3, :four]]
[0, 1, "two", 3, :four]
iex> [1 | [2 | [3 | []]]]
[1, 2, 3]

iex> list = [1, 2, 3]
iex> [0 | list] # fast
[0, 1, 2, 3]
iex> list ++ [4] # slow
[1, 2, 3, 4]
```


List module
-----------

```elixir
List.delete(list, element)
# Deletes the given element from the list.
# Returns a new list without the element.
List.delete_at(list, index)
# Produces a new list by removing the value at the specified index.
List.first(list)
# Returns the first element in list or nil if list is empty.
List.flatten(list)
# Flattens the given list of nested lists.
```

Doc: [`List`](https://hexdocs.pm/elixir/List.html)


Keyword
-------

```elixir
iex> [{:first_number, 1}, {:second_number, 2}]
[first_number: 1, second_number: 2]

iex> [first_number: 1, second_number: 2]
[first_number: 1, second_number: 2]
```


Keyword module
--------------

```elixir
Keyword.fetch(keywords, key)
# Fetches the value for a specific key and returns it in a tuple.
Keyword.fetch!(keywords, key)
# Fetches the value for specific key.
Keyword.keys(keywords)
# Returns all keys from the keyword list.
Keyword.values(keywords)
# Returns all values from the keyword list.
Keyword.split(keywords, keys)
# Takes all entries corresponding to the given keys and
# extracts them into a separate keyword list.
Keyword.take(keywords, keys)
# Takes all entries corresponding to the given keys and
# returns them in a new keyword list.
```

Doc: [`Keyword`](https://hexdocs.pm/elixir/Keyword.html)


Map
---

```elixir
iex> %{"one" => :two, 3 => "four"}
%{3 => "four", "one" => :two}
iex> map = %{a: 1, b: 2}
iex> map[:b]
2
iex> map["non_existing_key"]
nil
iex> map.a
1
iex> map.non_existing_key
** (KeyError) key :non_existing_key not found in: %{a: 1, b: 2}
```


Map module
----------

```elixir
Map.drop(map, keys)
# Drops the given keys from map.
Map.equal?(map1, map2)
# Checks if two maps are equal.
Map.from_struct(struct)
# Converts a struct to map.
Map.fet(map, key, default \\ nil)
# Gets the value for a specific key in map.
Map.has_key?(map, key)
# Returns whether the given key exists in the given map.
```

Doc: [`Map`](https://hexdocs.pm/elixir/Map.html)


MapSet module
-------------

```elixir
iex> my_set = MapSet.new([1, 2, 3, 4, 5])
iex> MapSet.put(my_set, 6)
MapSet<[1, 2, 3, 4, 5, 6]>
iex> MapSet.delete(my_set, 6)
MapSet<[1, 2, 3, 4, 5]>
```

```elixir
MapSet.difference(map_set1, map_set2)
# Returns a set that is map_set1 without the members of map_set2.
MapSet.disjoint?(map_set1, map_set2)
# Checks if map_set1 and map_set2 have no members in common.
MapSet.intersection(map_set, map_set)
# Returns a set containing only members that map_set1 and 
# map_set2 have in common.
MapSet.subset?(map_set1, map_set2)
# Checks if map_set1's members are all contained in map_set2.
MapSet.union(map_set1, map_set2)
# Returns a set containing all members of map_set1 and map_set2.
```

Doc: [`MapSet`](https://hexdocs.pm/elixir/MapSet.html)


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


Enumerable and Enum
-------------------

The protocol [`Enumerable`](https://hexdocs.pm/elixir/Enumerable.html) is
implemented by `Range`, `List` and `Map`. So many function to work with these
are found in the [`Enum`](https://hexdocs.pm/elixir/Enum.html) module.
