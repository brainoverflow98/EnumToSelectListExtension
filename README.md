# EnumToSelectListExtension
This is a an extension method ,intended for using with AspNetCore-MVC, which makes it easy to create SelectList with Enum types.

-----EXAMPLE USAGE-----

Define your Enum as below:
```C#
enum Color
{		
	Blue,
	[Category("Light")]
	[DisplayName("Light Blue")]
	LBlue,
	[Category("Dark")]
	[DisplayName("Dark Blue")]
	DBlue,
	Red,
	[Category("Dark")]
	[DisplayName("Dark Red")]
	DRed,
	[Category("Light")]
	[DisplayName("Light Red")]
	LRed,
	Green,
	[Category("Dark")]
	[DisplayName("Dark Green")]
	DGreen,
	[Category("Light")]
	[DisplayName("Light Green")]
	LGreen	
}
```

Include the extension namespace and simply call the ToSelectList() extension method on a Enum type:
```C#
var list = typeof(Color).ToSelectList();
```

You can provide custom options with the options paramete which is a SelectListOptions object.
Usage of SelectListOptions object is like below:

```C#
public string Placeholder { get; set; }  //Add a placeholder to SelectList with given name which has a real value of empty string.
var list = typeof(Color).ToSelectList(new SelectListOptions { Placeholder = "Please Select A Color"});
```

```C#
public bool IsStringValue { get; set; }  //If set the true, values of the SelectList Items will be populated with the Enum.ToString()
var list = typeof(Color).ToSelectList(new SelectListOptions { IsStringValue = true});
```

```C#
public object[] SelectedValues { get; set; }  //Provide selected values for the SelectList
var list = typeof(Color).ToSelectList(new SelectListOptions { SelectedValues = new object[]{Color.Red}});
```

```C#
public object[] DisabledValues { get; set; }  //Provide disabled values for the SelectList
var list = typeof(Color).ToSelectList(new SelectListOptions { DisabledValues = new object[]{Color.Green}});
```

```C#
public string[] DisabledGroups { get; set; }  //Provide disabled group names for the SelectList
var list = typeof(Color).ToSelectList(new SelectListOptions { DisabledGroups = new string[]{"Dark"}});
```
