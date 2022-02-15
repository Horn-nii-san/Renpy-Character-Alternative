# Renpy Character Alternative
## Code fully object oriented in ren'py!


Paste this in screens.rpy:
```py
init python:
    class Person():
        def __init__(self, name, color="#fff", what_color="#fff", what_prefix='', what_suffix='', points = 0, path = True):
            self.s = Character(name, color=color, what_color=what_color, what_prefix=what_prefix, what_suffix=what_suffix) # Normal text
            self.t = Character(name, color=color, what_color=what_color, what_prefix="(", what_suffix=")") # (Thinking)
            self.d = Character(name, color=color, what_color=what_color, what_prefix="*", what_suffix="*") # *Doing*
            self.f = Character(name, color=color, what_color=what_color, what_prefix=what_prefix, what_suffix=what_suffix) # Flashback
            self.pts = points
            self.path = path

```
Tutorials will always tell you to write:
```py
define horn = Character("Horn nii-san", color="#fff")
define horn_thinking = Character("Horn nii-san", color="#fff", what_prefix="(", what_suffix=")")
$ horn_lovepoints = 0
$ horn_path = True
```

With my module you can just write:
```py
define horn = Person("Horn nii-san", color="#fff")
# Lovepoints will automatically be 0 and path will automatically be True
```
Example:
```py
label start:
  horn.s "Hey MC"
  mc.s "Hey Horn, you're looking rather handsome today. (no homo)"
  horn.pts += 1
  horn.t "That's really sweet"
```

Instead of:
```py
label start:
  horn "Hey MC"
  mc "Hey Horn, you're looking rather handsome today. (no homo)"
  horn_points += 1
  horn_thinking "That's really sweet"
```
