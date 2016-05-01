From [Wikipedia](https://en.wikipedia.org/wiki/Hash_table):

A hash table (hash map) is a data structure used to implement an associative array, a structure that can map keys to values. A hash table uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.


```

function HashTable(obj) {
    this.length = 0;
    this.items = {};
    for (var p in obj) {
        if (obj.hasOwnProperty(p)) {
            this.items[p] = obj[p];
            this.length++;
        }
    }

    this.setItem = function(key, value) {
        var previous = undefined;
        if (this.hasItem(key)) {
            previous = this.items[key];
        }
        else {
            this.length++;
        }
        this.items[key] = value;
        return previous;
    }

    this.getItem = function(key) {
        return this.hasItem(key) ? this.items[key] : undefined;
    }

    this.hasItem = function(key) {
        return this.items.hasOwnProperty(key);
    }
   
    this.removeItem = function(key) {
        if (this.hasItem(key)) {
            var previous = this.items[key];
            this.length--;
            delete this.items[key];
            return previous;
        }
        else {
            return undefined;
        }
    }

    this.keys = function() {
        var keys = [];
        for (var k in this.items) {
            if (this.hasItem(k)) {
                keys.push(k);
            }
        }
        return keys;
    }

    this.values = function() {
        var values = [];
        for (var k in this.items) {
            if (this.hasItem(k)) {
                values.push(this.items[k]);
            }
        }
        return values;
    }

    this.each = function(fn) {
        for (var k in this.items) {
            if (this.hasItem(k)) {
                fn(k, this.items[k]);
            }
        }
    }

    this.clear = function() {
        this.items = {}
        this.length = 0;
    }
}

```
To Use: 

```
var h = new HashTable({one: 1, two: 2, three: 3, "i'm no 4": 4});

console.log('h', h)

console.log('length: ' + h.length);

console.log('value of key "one": ', h.getItem('one'));
console.log('has key "foo"? ', h.hasItem('foo'));
h.setItem('foo', 'bar')
h.setItem('loggedIn', false)
console.log('h after setting new keys', h)
console.log('length after setItem: ', h.length);
console.log('value of key "foo": ', h.getItem('foo'));
console.log('has key "foo"? ', h.hasItem('foo'));
console.log('value of key 4: ',  h.getItem("i'm no 4"));
console.log('length before remove item: ', h.length);
h.removeItem("three")
console.log('h after remove item', h)
console.log('length after remove item: ', h.length);
h.clear();
console.log('length: ', h.length);

```