# Tag Helpers

* For Razor pages, NOT Razor components (and therefore not Blazor currently)
* Class inherits from TagHelper (theres a Add new item template for item)
	* public properties for tag attributes
	* [HtmlTargetElement(Attributes="xxx") to define mandatory attrs
* Pascal cased C# classnames are mapped by default to kebab-cased tag names, i.e. MyCustomer = my-customer
* `_ViewIMports.cshtml` to import new tag helper namespaces
* Uses a "matching" approach to determine whether a helper is activated


## Built-ins

### Anchor `<A>`

* asp-controller & asp-action
* asp-route-{value}
  * `.../asp-controller/asp-action/asp-route-value`
* asp-route
  * Maps to a named route, see standard routing attributes
* asp-all-route-data
  * Supply all route data via a dictionary
* asp-fragmen
  * defines the "fragment" (big after a '#') of the resulting URL
* asp-area
  * see [RazorPagesOptions.AllowAreas](https://docs.microsoft.com/en-gb/dotnet/api/microsoft.aspnetcore.mvc.razorpages.razorpagesoptions.allowareas?view=aspnetcore-2.2)
* asp-protocol
  * http/https etc.
* asp-hos
  * specify the url host (i.e. google.com)
* asp-pages
  * for Razor pages, mutually exclusive with asp-route/controller & action
* asp-page-handler
  * Used to link to specific page handlers (i.e. `OnGet{pageHandler}`

### `<cache>/<distributed-cache>`

* Properties
  * enabled, expires-after, expires-sliding, vary-by-/query/route/cookie/user/by, priority

### `<environment names|include|exclude="env1, env2..." ...`

* Triggers rendering on an environment basis
  * compares env to [IHostingEnvironment.EnvironmentName]( https://docs.microsoft.com/en-gb/dotnet/api/microsoft.aspnetcore.hosting.ihostingenvironment.environmentname?view=aspnetcore-2.2)
  * See Project properties/debug tab which has the default env vars on

### Form `<form>`

* asp-controller/action/route
* asp-route-returnurl
* See Anchor above for other link-generating related attributes

### Image `<img>`

* src
* asp-append-version - appends a hash to the image for caching

### Input `<input>`

* asp-for={expression name} - generates id, name, derives input type from data type of expression and(or?) data annotations

### Label `<label>`

* asp-for={expression name}

### Validation

* asp-validation-for/asp-validation-summary

### Select `<select>`

* asp-for/asp-items
* auto generate `<optgroup>` auto generated if more than one SelectListItem.Group
* auto generate multiple attribute if the asp-for is IEnumerable

### Script

* asp-append-version 
* asp-src-include/exclude - globbing file patterns
* asp-fallback-test - tests if library loaded or uses fallback src
* asp-fallback-src
* asp-fallback-src-include/exclude

### Link

* Similar to Script, but...
  * asp-fallback-test-class/test-property/test-value
  * asp-fallback-href
