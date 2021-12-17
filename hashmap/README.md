<!-- Code generated by gomarkdoc. DO NOT EDIT -->

# hashmap

```go
import "github.com/zyedidia/generic/hashmap"
```

Package hashmap provides an implementation of a hashmap\. The map uses linear probing and automatically resizes\. The map can also be efficiently copied\, and will perform copies lazily\, using copy\-on\-write\. However\, the copy\-on\-write will copy the entire map after the first write\. One can imagine a more efficient implementation that would split the map into chunks and use copy\-on\-write selectively for each chunk\.

<details><summary>Example</summary>
<p>

```go
{
	m := NewMap[g.String, g.Int](1)
	m.Put("foo", 42)
	m.Put("bar", 13)

	fmt.Println(m.GetZ("foo"))
	fmt.Println(m.GetZ("baz"))

	m.Remove("foo")

	fmt.Println(m.GetZ("foo"))

}
```

#### Output

```
42
0
0
```

</p>
</details>

## Index

- [type KV](<#type-kv>)
- [type Map](<#type-map>)
  - [func NewMap[K g.Hashable[K], V any](capacity uint64) *Map[K, V]](<#func-newmap>)
  - [func (m *Map[K, V]) Copy() *Map[K, V]](<#func-badrecv-copy>)
  - [func (m *Map[K, V]) Get(key K) (V, bool)](<#func-badrecv-get>)
  - [func (m *Map[K, V]) GetZ(key K) V](<#func-badrecv-getz>)
  - [func (m *Map[K, V]) Iter() iter.Iter[KV[K, V]]](<#func-badrecv-iter>)
  - [func (m *Map[K, V]) Put(key K, val V)](<#func-badrecv-put>)
  - [func (m *Map[K, V]) Remove(key K)](<#func-badrecv-remove>)
  - [func (m *Map[K, V]) Size() int](<#func-badrecv-size>)


## type KV

```go
type KV[K g.Hashable[K], V any] struct {
    Key K
    Val V
}
```

## type Map

A Map is a hashmap that supports copying via copy\-on\-write\.

```go
type Map[K g.Hashable[K], V any] struct {
    // contains filtered or unexported fields
}
```

### func NewMap

```go
func NewMap[K g.Hashable[K], V any](capacity uint64) *Map[K, V]
```

NewMap constructs a new map with the given capacity\.

### func \(\*BADRECV\) Copy

```go
func (m *Map[K, V]) Copy() *Map[K, V]
```

Copy returns a copy of this map\. The copy will not allocate any memory until the first write\, so any number of read\-only copies can be made without any additional allocations\.

### func \(\*BADRECV\) Get

```go
func (m *Map[K, V]) Get(key K) (V, bool)
```

Get returns the value stored for this key\, or false if there is no such value\.

### func \(\*BADRECV\) GetZ

```go
func (m *Map[K, V]) GetZ(key K) V
```

GetZ returns the value stored for this key\, or its zero value if there is no such value\.

### func \(\*BADRECV\) Iter

```go
func (m *Map[K, V]) Iter() iter.Iter[KV[K, V]]
```

Iter returns an iterator over all key\-value pairs in the map\.

### func \(\*BADRECV\) Put

```go
func (m *Map[K, V]) Put(key K, val V)
```

Put maps the given key to the given value\. If the key already exists its value will be overwritten with the new value\.

### func \(\*BADRECV\) Remove

```go
func (m *Map[K, V]) Remove(key K)
```

Remove removes the specified key\-value pair from the map\.

### func \(\*BADRECV\) Size

```go
func (m *Map[K, V]) Size() int
```

Size returns the number of items in the map\.



Generated by [gomarkdoc](<https://github.com/princjef/gomarkdoc>)