## Usage[](#usage)

This section will show you how to use the field type via API and in the view layer.


### Setting Values[](#usage/setting-values)

You can set the field type value with a string.

    $entry->example = $html;


### Basic Output[](#usage/basic-output)

The field type always returns the storage file content by default.

    $entry->example; // Raw contents of storage::example/input/file.html


### Presenter Output[](#usage/presenter-output)

This section will show you how to use the decorated value provided by the `\Anomaly\WysiwygFieldType\WysiwygFieldTypePresenter` class.


#### WysiwygFieldTypePresenter::path()[](#usage/presenter-output/wysiwygfieldtypepresenter-path)

The `path` method returns the prefix hinted path to the storage file.

###### Returns: `string`

###### Example

    $decorated->example->path(); // storage::the/path/example.html

###### Twig

    {{ decorated.example.path() }} // storage::the/path/example.html


#### WysiwygFieldTypePresenter::render()[](#usage/presenter-output/wysiwygfieldtypepresenter-render)

The `render` method returns the rendered view using the storage file.

###### Returns: `string`

###### Arguments

<table class="table table-bordered table-striped">

<thead>

<tr>

<th>Key</th>

<th>Required</th>

<th>Type</th>

<th>Default</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>

$payload

</td>

<td>

false

</td>

<td>

array

</td>

<td>

null

</td>

<td>

Additional payload data for the view.

</td>

</tr>

</tbody>

</table>

###### Example

    $decorated->example->render(['name' => 'Ryan']);

###### Twig

    {{ decorated.example.render({'name': 'Ryan'})|raw }}


#### WysiwygFieldTypePresenter::content()[](#usage/presenter-output/wysiwygfieldtypepresenter-content)

The `content` method returns the raw value.

###### Returns: `string`

###### Example

    $decorated->example->content();

###### Twig

    {{ decorated.example.content() }}


#### WysiwygFieldTypePresenter::excerpt()[](#usage/presenter-output/wysiwygfieldtypepresenter-excerpt)

The `excerpt` method returns a limited snippet from the `text` method while preserving whole words.

###### Returns: `string`

###### Arguments

<table class="table table-bordered table-striped">

<thead>

<tr>

<th>Key</th>

<th>Required</th>

<th>Type</th>

<th>Default</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>

$length

</td>

<td>

false

</td>

<td>

integer

</td>

<td>

100

</td>

<td>

The length to limit the value by.

</td>

</tr>

<tr>

<td>

$end

</td>

<td>

false

</td>

<td>

string

</td>

<td>

...

</td>

<td>

The ending for the string only if truncated.

</td>

</tr>

</tbody>

</table>

###### Example

    $decorated->example->excerpt();

###### Twig

    {{ decorated.example.excerpt() }}


#### WysiwygFieldTypePresenter::text()[](#usage/presenter-output/wysiwygfieldtypepresenter-text)

The `text` method returns the text-only content from the storage file.

###### Returns: `string`

###### Arguments

<table class="table table-bordered table-striped">

<thead>

<tr>

<th>Key</th>

<th>Required</th>

<th>Type</th>

<th>Default</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>

$allowed

</td>

<td>

false

</td>

<td>

string

</td>

<td>

none

</td>

<td>

The string of tags to allow.

</td>

</tr>

</tbody>

</table>

###### Example

    $decorated->example->text();

###### Twig

    {{ decorated.example.text() }}


#### WysiwygFieldTypePresenter::__toString()[](#usage/presenter-output/wysiwygfieldtypepresenter-tostring)

The `__toString` method is mapped to the `render` method.

###### Returns: `string`

###### Example

    $decorated->example;

###### Twig

    {{ decorated.example|raw }}

<div class="alert alert-danger">**Heads Up:** The **__toString** will not properly display exceptions spurring from value content.</div>
