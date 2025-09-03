This plugin demonstrates how a single markup can udisplay multiple sources of data with no code changes.

Instead of static values, parameters can describe mapings into the pollng result json.
The mapping syntax is defined by JSPath (https://github.com/dfilatov/jspath)

This mapping allows to select any value from the polling address response json, and a simple javascript function all
binds the mapping to values, then assigns thm to any graphcal copmonent.

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

3 parameters to describe access to polling response be used to update the HTML conent
<img width="1006" height="876" alt="image" src="https://github.com/user-attachments/assets/a3dc3e07-9373-48bc-8a10-443dc31b4faf" />


Simple Javascript then assigns values to graphical elements
```
const createPage = (data, mapping) => {
    const title = resolveMapping(data, mapping["title"]);
     setContents("title", title);
    const publisher = resolveMapping(data, mapping["title"]);
     setContents("title", title); 
```

<img width="815" height="487" alt="image" src="https://github.com/user-attachments/assets/dce56eb7-698e-49a2-9231-2a5201182b2e" />


mapping can be used to access different nodes in the polled address response,
or to adapt the markup to a different polling json structure.
