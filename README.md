This plugin demonstrates how a single markup can udisplay multiple sources of data with no code changes.

Instead of static values, parameters can describe mapings into the pollng result json.
The mapping syntax is defined by JSPath (https://github.com/dfilatov/jspath)

This mapping allows to select any value from the polling address response json, and simple javascript functions binds mappings to values, then assigns them to graphical components.

Given this polling response:
```
{
  "provider": "awazleon.space",
  "timestamp": "2025-09-03",
  "name": "Worldwide",
  "imagepath": "none",
  "ref": "none",
  "cities": {
    "number": 88,
    "invaders": "4333",
    "pts": "119950"
  },
  "invadersState": {
    "alive": 2406,
    "ptsAlive": 68910,
    "dead": 1457,
    "ptsDead": 37970,
    "damaged": 424,
    "ptsDamaged": 10530,
    "hidden": 21,
    "ptsHidden": 530,
    "unknown": 25,
    "ptsUnknown": 360
  }
}
```

we can create a simple markup to display a text and a banner:

```
<div class="layout layout--row" id="content">
  <span id="text" class="value value--large" data-value-fit="true"></span>
</div>
<div class="title_bar">
    <span id="title" class="title"></span>
  <span id="subtitle" class="instance"></span>
</div>
```

3 parameters to describe access to polling response to be used to update the HTML content

<img width="500" height="413" alt="image" src="https://github.com/user-attachments/assets/9503f200-a4b7-4e30-bcb6-21e6e799bc1f" />


Simple Javascript then assigns values to graphical elements
```
const createPage = (data, mapping) => {
    const title = resolveMapping(data, mapping["title"]);
    setContents("title", title);
    const publisher = resolveMapping(data, mapping["title"]);
    setContents("title", title);
    const text = resolveMapping(data, mapping.text)
    setContents("text", text);
  }
```

the result is

<img width="605" height="355" alt="image" src="https://github.com/user-attachments/assets/9c671339-e6dc-4201-89c7-05e2e4c7e8fc" />

