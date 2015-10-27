# Introduction #

The main usage is basically this.

Add this in html:
```

<div id="slider">

Unknown end tag for &lt;/div&gt;


<div id="slider-controller">
<select>
<option value="type1">Type 1

Unknown end tag for &lt;/option&gt;


<option value="type2">Type 2

Unknown end tag for &lt;/option&gt;


<option value="type3">Type 3

Unknown end tag for &lt;/option&gt;




Unknown end tag for &lt;/select&gt;


<button class="add">Add Range

Unknown end tag for &lt;/button&gt;


<button class="remove">Remove Range

Unknown end tag for &lt;/button&gt;




Unknown end tag for &lt;/div&gt;


```

This is the script for the slider:
```

$('#slider').slider({
min: 0,           // minimum
max: 24,          // maximum
values: [0, 24],  // values
handles: [
{
value : sliderMin,
type  : "minimum"
},
{
value : sliderMax,
type  : "saving"
}
],
step: 0.5, //
range: false,
tooltips: true,
// handleActivated callback
handleActivated: function(event, handle) {
// get select element
var select = $(this).parent().find('#slider-controller select');
// set selected option
select.val(handle.type);
}
});
```

And this makes the buttons work:

```

$('#slider-controller button.add').button({icons: {primary: 'ui-icon-plus'}, text: false})
.click(function(e) {
e.preventDefault();
// get slider
// trigger addHandle
$('#slider').slider('addHandle', {
value : 12,
type  : "minimum"
});

return false;
});
$('#slider-controller button.remove').button({icons: {primary: 'ui-icon-trash'}, text: false})
.click(function(e) {
e.preventDefault();
// trigger removeHandle
$('#slider').slider('removeHandle', $('#slider').find('a.ui-state-active').attr('data-id'));

return false;
});
```