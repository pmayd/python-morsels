
# PermaDict
Assigned from Intermediate Level on 11/18/2019

Hi there!

This week you're going to create a dictionary-like class that disallows keys to be updated (they can only be added or removed).

The PermaDict class should allow keys to be added and deleted, just like any other dictionary:

```python
>>> locations = PermaDict({'Trey': "San Diego", 'Al': "San Francisco"})
>>> locations['Harry'] = "London"
>>> locations.update({'Russell': "Perth", 'Katie': "Sydney"})
>>> locations['Trey']
'San Diego'
````

And your PermaDict class should have keys, values, and items methods and should be iterable just like a dictionary:

```
>>> locations = PermaDict([('Kojo', "Houston"), ('Tracy', "Toronto")])
>>> list(locations)
['Kojo', 'Tracy']
>>> list(locations.keys())
['Kojo', 'Tracy']
>>> list(locations.values())
['Houston', 'Toronto']
>>> for name, place in locations.items():
...     print(f"{name} in {place}")
...
Kojo in Houston
Tracy in Toronto
```

But unlike a dictionary when a value is set and for a key that already exists, a KeyError exception should be raised:

```python
>>> locations = PermaDict({'David': "Boston"})
>>> locations['David'] = "Amsterdam"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 5, in __setitem__
KeyError: "'David' already in dictionary."
>>> locations['Asheesh'] = "Boston"
>>> locations.update({'Asheesh': "San Francisco"})
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 5, in update
KeyError: "'Asheesh' already in dictionary."
>>> locations
{'David': 'Boston', 'Asheesh': 'Boston'}
````

## Bonus 1

For the first bonus, I'd like you to add a force_set method to your PermaDict class which allows keys to be updated without error. ✔️

```python
>>> locations = PermaDict({'David': "Boston"})
>>> locations.force_set('David', "Amsterdam")
>>> locations.force_set('Asheesh', "Boston")
>>> locations.force_set('Asheesh', "San Francisco")
>>> locations
{'David': 'Amsterdam', 'Asheesh': 'San Francisco'}
```

## Bonus 2

For the second bonus, I'd like you to handle an optional silent keyword argument passed to the initializer of your dictionary to allow your dictionary to silently ignore updates to existing keys. ✔️

```python
>>> locations = PermaDict({'David': "Boston"}, silent=True)
>>> locations['David'] = "Amsterdam"
>>> locations['Asheesh'] = "Boston"
{'David': 'Boston', 'Asheesh': 'Boston'}
````

## Bonus 3

For the third bonus, I'd like your PermaDict class's update method to handle an optional force keyword argument to allow your dictionary's update method to force update the values for existing keys. ✔️

```python
>>> locations = PermaDict({'David': "Boston"})
>>> locations.update([('David', 'Amsterdam'), ('Asheesh', 'SF')], force=True)
>>> locations
{'David': 'Amsterdam', 'Asheesh': 'SF'}
````

## Hints

A hint for this week: you'll want to use inheritance. You don't want to implement all these methods from scratch.

- [Making a custom dictionary class](https://treyhunner.com/2019/04/why-you-shouldnt-inherit-from-list-and-dict-in-python/#Making_a_custom_dictionary)
- [Making x[key] = value work](https://gist.github.com/turicas/1510860)
- [Checking if a key already exists](https://stackoverflow.com/a/1602964/2633215)
- [You may want to inherit from this class](https://stackoverflow.com/a/19775773/2633215)
- [Another helper to make a dictionary-like class](https://docs.python.org/3/library/collections.html#collections.UserDict)
- [Bonus 1: Updating existing keys](https://blog.anvetsu.com/posts/custom-dictionary-type-python/)
- [Bonus 2 and 3: making silent argument a keyword-only argument](https://treyhunner.com/2018/04/keyword-arguments-in-python/#Requiring_your_arguments_be_named)

## Tests

Automated tests for this week's exercise can be found here. You'll need to write your code in a module named permadict.py next to the test file. To run the tests you'll run "python test_permadict.py" and check the output for "OK". You'll see that there are some "expected failures" (or "unexpected successes" maybe). If you'd like to do the bonus, you'll want to comment out the noted lines of code in the tests file to test them properly.
