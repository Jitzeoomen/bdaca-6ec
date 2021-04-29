
#### question regarding using `re.sub` on a particular sub-part of a string

You can exclude parts from replacing by capturing a group `()` around the part of the str you want to preserve. In the example below, the non-capturing groups are indicated as follows `(?<=..)` and `(?:..)`

```python
import re
t = r'wekogegkp RT egowgiwegj : @AnneKroon92042' # we want to remove 'egowgiwegj'
re.sub(r'(?<=RT )[a-z]*?(?=:?) ', '',  t)
```

output: `wekogegkp RT : @AnneKroon92042`

----

#### example using `re.findall` and `re.sub` to remove errors in your corpus

This example may help you to clean up your data/ deal with spelling variations.

```python
import re
testo = "this is an example with twitter and also one with twittter and one with faaaacebooook"
re.findall("[Tt]witt+er|[Ff]a+ceboo+k", testo)
testo_recoded = re.sub(r"[Tt]wittter| [Ff]a+ceboo+k", "**a social medium**", testo)
```
