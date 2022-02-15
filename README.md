# Renpy Character Alternative
## Code fully object oriented in ren'py!


### First example

Paste this in screens.rpy:
```py
init python:
    class Person():
        def __init__(self, name, color="#fff", what_color="#fff", what_prefix='', what_suffix='', points = None, path = True):
            self.s = Character(name, color=color, what_color=what_color, what_prefix=what_prefix, what_suffix=what_suffix) # Normal text
            self.t = Character(name, color=color, what_color=what_color, what_prefix="(", what_suffix=")") # (Thinking)
            self.d = Character(name, color=color, what_color=what_color, what_prefix="*", what_suffix="*") # *Doing*
            self.pts = points
            self.path = path

```
Tutorials will always tell you to write:
```py
default horn = Character("Horn nii-san", color="#fff")
default horn_thinking = Character("Horn nii-san", color="#fff", what_prefix="(", what_suffix=")")
default horn_doing = Character("Horn nii-san", color="#fff", what_prefix="*", what_suffix="*")

$ horn_lovepoints = 0
$ horn_path = True
```

With my module you can just write:
```py
default horn = Person("Horn nii-san", color="#fff")
# Lovepoints will automatically be 0 and path will automatically be True
```

Example:
```py
label start:
  horn.s "Hey [mc.s]"
  mc.s "Hey Horn, you're looking rather handsome today. (no homo.)"
  $ horn.pts += 1
  horn.t "That's really sweet!"
  horn.d "Blushes"
```

Instead of:
```py
label start:
  horn "Hey [mc]"
  mc "Hey Horn, you're looking rather handsome today. (no homo.)"
  $ horn_points += 1
  horn_thinking "That's really sweet!"
  horn_doing "Blushes"
```



### Second example (lust, love, anger)

Paste this in screens.rpy:
```py
init python:
    class Person():
        def __init__(self, name, color="#fff", what_color="#fff", what_prefix='', what_suffix='', points = None, path = True):
            self.s = Character(name, color=color, what_color=what_color, what_prefix=what_prefix, what_suffix=what_suffix) # Normal text
            self.t = Character(name, color=color, what_color=what_color, what_prefix="(", what_suffix=")") # (Thinking)
            self.d = Character(name, color=color, what_color=what_color, what_prefix="*", what_suffix="*") # *Doing*
            if points is None:
                self.pts = points
            else:
                self.pts = 0
            self.path = path
    class Points():
        def __init__(self, love=0, lust=0, anger=0): # Follow this template to add or remove type of points
            self.love = love
            self.lust = lust
            self.anger = anger
```

Tutorials will always tell you to write:
```py
default horn = Character("Horn nii-san", color="#fff")
default horn_thinking = Character("Horn nii-san", color="#fff", what_prefix="(", what_suffix=")")
default horn_doing = Character("Horn nii-san", color="#fff", what_prefix="*", what_suffix="*")

$ horn_lovepoints = 0
$ horn_lustpoints = 0
$ horn_angerpoints = 0
$ horn_path = True
```

With my module you can just write:
```py
default horn = Person("Horn nii-san", color="#fff", points=Points())
# There will be love-, lust- and angerpoints now.
```

Example:
```py
label start:
  horn.s "Hey [mc.s]"
  mc.s "Hey Horn, you're looking rather handsome today. (no homo.)"
  $ horn.pts.love += 1
  horn.t "That's really sweet!"
  horn.d "Blushes"
  mc.s "I was kidding, you're ugly."
  $ horn.pts.anger += 1
  horn.s "Showing you the [horn.pts.lust] would be pretty sus..."
```

Instead of:
```py
label start:
  horn "Hey [mc]"
  mc "Hey Horn, you're looking rather handsome today. (no homo.)"
  $ horn_lovepoints += 1
  horn_thinking "That's really sweet!"
  horn_doing "Blushes"
  mc "I was kidding, you're ugly."
  $ horn_angerpoints += 1
  horn "Showing you the [horn_lustpoints] would be pretty sus..."
```
