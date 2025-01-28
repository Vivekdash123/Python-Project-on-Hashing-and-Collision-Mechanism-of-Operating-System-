Project: Simple Hash Map with Collision Handling in Python
We’ll create a class HashMap that:

Implements a hash function for converting keys into an index.
Handles collisions using chaining (i.e., storing multiple key-value pairs in a list when they hash to the same index).
Allows inserting, retrieving, and deleting key-value pairs

Line-by-Line Explanation:
class HashMap:
We define a HashMap class that will implement our custom hash map.

def __init__(self, size=10):
This is the constructor of the class. It initializes the hash map with a fixed size (default is 10).

self.size = size sets the size of the hash map.
self.map = [[] for _ in range(size)] creates a list of empty lists (buckets) to hold key-value pairs, which will handle collisions using chaining.
def _hash(self, key):
This method is responsible for generating an index from the key using a hash function.

return hash(key) % self.size uses Python’s built-in hash() function to compute a hash value for the key, and then takes the modulus with the map size to ensure the index is within bounds (i.e., it will fit in one of the available buckets).
def insert(self, key, value):
This method is used to insert a key-value pair into the hash map.

index = self._hash(key) calls the _hash method to get the index where the key-value pair should be stored.
We then check if the key already exists in that index (bucket) by iterating over the list (for pair in self.map[index]).
If the key exists, we update its value.
If the key doesn't exist, we append a new key-value pair to the list at that index.
def get(self, key):
This method retrieves the value associated with a given key.

index = self._hash(key) computes the index for the key.
It then checks if the key exists at that index by iterating over the bucket (for pair in self.map[index]).
If the key is found, the corresponding value is returned. If not, None is returned.
def delete(self, key):
This method deletes a key-value pair from the hash map.

index = self._hash(key) computes the index for the key.
We loop through the list at that index (for i, pair in enumerate(self.map[index])).
If the key is found, we delete the key-value pair and return True.
If the key is not found, we return False.
def display(self):
This method displays the contents of the hash map. It prints the index of each bucket and the key-value pairs stored in it.

Main Program (if __name__ == "__main__":)
We create a HashMap instance (hashmap = HashMap()).
Insert a few key-value pairs into the hash map using insert().
We attempt to insert a key that may collide ("applf") with another key ("apple"), demonstrating collision handling.
We display the hash map using display().
We retrieve values for some keys using get().
We delete a key-value pair ("banana") using delete() and display the hash map again.
