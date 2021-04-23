
# about\_Admin\_Filtering.txt

## Topic
XenDesktop - Advanced Dataset Filtering


## Short Description
Describes the common filtering options for XenDesktop cmdlets.


## Long Description
Some cmdlets operate on large quantities of data and, to reduce the overhead of sending all of that data over the network, many of the Get- cmdlets support server-side filtering of the results.

The conventional way of filtering results in PowerShell is to pipeline them into Where-Object, Select-Object, and Sort-Object, for example:

Get-&lt;Noun&gt; | Where { \$\_.Size = 'Small' } | Sort 'Date' | Select -First 10

However, for most XenDesktop cmdlets the data is stored remotely and it would be slow and inefficient to retrieve large amounts of data over the network and then discard most of it. Instead, many of the Get- cmdlets provide filtering parameters that allow results to be processed on the server, returning only the required results.

You can filter results by most object properties using parameters derived from the property name. You can also sort results or limit them to a specified number of records:

Get-&lt;Noun&gt; -Size 'Small' -SortBy 'Date' -MaxRecordCount 10

You can express more complex filter conditions using a syntax and set of operators very similar to those used by PowerShell expressions.

Those cmdlets that support filtering have the following common parameters:

-MaxRecordCount &lt;int&gt; Specifies the maximum number of results to return. For example, to return only the first nine results use:

Get-&lt;Noun&gt; -MaxRecordCount 9

If not specified, only the first 250 records are returned, and if more are available, a warning is produced:

WARNING: Only first 250 records returned. Use -MaxRecordCount to retrieve more.

You can suppress this warning by using -WarningAction or by specifying a value for -MaxRecordCount.

To retrieve all records, specify a large number for -MaxRecordCount. As the value is an integer, you can use the following:

Get-&lt;Noun&gt; -MaxRecordCount \[int\]::MaxValue

-ReturnTotalRecordCount \[&lt;SwitchParameter&gt;\] When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. For example:

Get-&lt;Noun&gt; -MaxRecordCount 9 -ReturnTotalRecordCount ....

Get-&lt;Noun&gt; : Returned 9 of 10 items At line:1 char:18 + Get-&lt;Noun&gt; &lt;&lt;&lt;&lt;  -MaxRecordCount 9 -ReturnTotalRecordCount + CategoryInfo          : OperationStopped: (:) \[Get-&lt;Noun&gt;\], PartialDataException + FullyQualifiedErrorId : PartialData,Citrix.&lt;SDKName&gt;.SDK.Get&lt;Noun&gt;

The count can be accessed using the TotalAvailableResultCount property:

\$count = \$error\[0\].TotalAvailableResultCount

-Skip &lt;int&gt; Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount.

-SortBy &lt;string&gt; Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order, respectively. Ascending order is assumed if no prefix is present.

Sorting occurs before -MaxRecordCount and -Skip parameters are applied. For example, to sort by Name and then by Count (largest first) use:

-SortBy 'Name,-Count'

By default, sorting by an enumeration property uses the numeric value of the elements. You can specify a different sort order by qualifying the name with an ordered list of elements or their numeric values, or &lt;null&gt; to indicate the placement of null values. Elements not mentioned are placed at the end in their numeric order. For example, to sort by two different enums and then by the object id:

-SortBy 'MyState(StateC,&lt;null&gt;,StateA,StateB),Another(0,3,2,1),Id'

-Filter &lt;String&gt; This parameter lets you specify advanced filter expressions, and supports combination of conditions with -and and -or, and grouping with braces. For example:

Get-&lt;Noun&gt; -Filter 'Name -like "High\*" -or (Priority -eq 1 -and Severity -ge 2)'

The syntax is close enough to PowerShell syntax that you can use script blocks in most cases. This can be easier to read as it reduces quoting:

Get-&lt;Noun&gt; -Filter { Count -ne \$null }

The full -Filter syntax is provided below.


## Examples
Filtering by strings performs a case-insensitive wildcard match. Separate parameters are combined with an implicit -and operator. Normal PowerShell quoting rules apply, so you can use single or double quotes, and omit the quotes altogether for many strings. The order of parameters does not make any difference. The following are equivalent:

Get-&lt;Noun&gt; -Company Citrix -Product Xen\* Get-&lt;Noun&gt; -Company "citrix" -Product '\[X\]EN\*' Get-&lt;Noun&gt; -Product "Xen\*" -Company "CITRIX" Get-&lt;Noun&gt; -Filter { Company -eq 'Citrix' -and Product -like 'Xen\*' }

See about\_Quoting\_Rules and about\_Wildcards for details about PowerShell handling of quotes and wildcards.

To avoid wildcard matching or include quote characters, you can escape the wildcards using the normal PowerShell escape mechanisms (see about\_Escape\_Characters), or switch to a filter expression and the -eq operator:

Get-&lt;Noun&gt; -Company "Abc\[\*\]"                 # Matches Abc\* Get-&lt;Noun&gt; -Company "Abc\`\*"                  # Matches Abc\* Get-&lt;Noun&gt; -Filter { Company -eq "Abc\*" }    # Matches Abc\* Get-&lt;Noun&gt; -Filter { Company -eq "A\`"B\`'C" } # Matches A"B'C

Simple filtering by numbers, booleans, and TimeSpans perform direct equality comparisons, although if the value is nullable you can also search for null values. Here are some examples:

Get-&lt;Noun&gt; -Uid 123 Get-&lt;Noun&gt; -Enabled \$true Get-&lt;Noun&gt; -Duration 1:30:40 Get-&lt;Noun&gt; -NullableProperty \$null

More comparisons are possible using advanced filtering with -Filter:

Get-&lt;Noun&gt; -Filter 'Capacity -ge 10gb' Get-&lt;Noun&gt; -Filter 'Age -ge 20 -and Age -lt 40' Get-&lt;Noun&gt; -Filter 'VolumeLevel -like "\[123\]"' Get-&lt;Noun&gt; -Filter 'Enabled -ne \$false' Get-&lt;Noun&gt; -Filter 'NullableProperty -ne \$null'

You can check boolean values without an explicit comparison operator, and you can also combine them with -not:

Get-&lt;Noun&gt; -Filter 'Enabled'      # Equivalent to 'Enabled -eq \$true' Get-&lt;Noun&gt; -Filter '-not Enabled' # Equivalent to 'Enabled -eq \$false'

See about\_Comparison\_Operators for an explanation of the operators, but note that only a subset of PowerShell operators are supported (-eq, -ne, -gt, -ge, -lt, -le, -like, -notlike, -in, -notin, -contains, -notcontains).

Enumeration values can either be specified using typed values or the string name of the enumeration value:

Get-&lt;Noun&gt; -Shape \[Shapes\]::Square Get-&lt;Noun&gt; -Shape Circle

With filter expressions, typed values can be specified with simple variables or quoted strings. They also support enumerations with wildcards:

\$s = \[Shapes\]::Square Get-&lt;Noun&gt; -Filter { Shape -eq \$s -or Shape -eq "Circle" } Get-&lt;Noun&gt; -Filter { Shape -like 'C\*' }

By their nature, floating point values, DateTime values, and TimeSpan values are best suited to relative comparisons rather than just equality. DateTime strings are converted using the locale and time zone of the user device, but you can use ISO8601 format strings (YYYY-MM-DDThh:mm:ss.sTZD) to avoid ambiguity. You can also use standard PowerShell syntax to create these values:

Get-&lt;Noun&gt; -Filter { StartTime -ge "2010-08-23T12:30:00.0Z" } \$d = \[DateTime\]"2010-08-23T12:30:00.0Z" Get-&lt;Noun&gt; -Filter { StartTime -ge \$d } \$d = (Get-Date).AddDays(-1) Get-&lt;Noun&gt; -Filter { StartTime -ge \$d }

Relative times are quite common and, when using filter expressions, you can also specify DateTime values using a relative format:

Get-&lt;Noun&gt; -Filter { StartTime -ge '-2' }         # Two days ago Get-&lt;Noun&gt; -Filter { StartTime -ge '-1:30' }      # Hour and a half ago Get-&lt;Noun&gt; -Filter { StartTime -ge '-0:0:30' }    # 30 seconds ago


### Array Properties
When filtering against list or array properties, simple parameters perform a case-insensitive wildcard match against each of the members. With filter expressions, you can use the -contains and -notcontains operators. Unlike PowerShell, these perform wildcard matching on strings. Note that for array properties the naming convention is for the returned property to be plural, but the parameter used to search for any match is singular. The following are equivalent (assuming Users is an array property):

Get-&lt;Noun&gt; -User Fred\* Get-&lt;Noun&gt; -Filter { User -like "Fred\*" } Get-&lt;Noun&gt; -Filter { Users -contains "Fred\*" }

You can also use the singular form with -Filter to search using other operators:


```
      # Match if any user in the list is called "Frederick" 
      Get-<Noun> -Filter { User -eq "Frederick" } 
      # Match if any user in the list has a name alphabetically below 'F' 
      Get-<Noun> -Filter { User -lt 'F' } 

```

### Complex Expressions
When matching against multiple values, you can use a sequence of comparisons joined with -or operators, or you can use -in and -notin:

Get-&lt;Noun&gt; -Filter { Shape -eq 'Circle' -or Shape -eq 'Square' } \$shapes = 'Circle','Square' Get-&lt;Noun&gt; -Filter { Shape -in \$shapes } \$sides = 1..4 Get-&lt;Noun&gt; -Filter { Sides -notin \$sides }

Braces can be used to group complex expressions, and override the default left-to-right evaluation of -and and -or. You can also use -not to invert the sense of any sub-expression:

Get-&lt;Noun&gt; -Filter { Size -gt 4 -or (Color -eq 'Blue' -and Shape -eq 'Circle') } Get-&lt;Noun&gt; -Filter { Sides -lt 5 -and -not (Color -eq 'Blue' -and Shape -eq 'Circle') }


### Paging
The simplest way to page through data is to use the -Skip and -MaxRecordCount parameters. So, to read the first three pages of data with 10 records per page, use:

Get-&lt;Noun&gt; -Skip 0  -MaxRecordCount 10 &lt;other filtering criteria&gt; Get-&lt;Noun&gt; -Skip 10 -MaxRecordCount 10 &lt;other filtering criteria&gt; Get-&lt;Noun&gt; -Skip 20 -MaxRecordCount 10 &lt;other filtering criteria&gt;

You must include the same filtering criteria on each call, and ensure that the data is sorted consistently.

The above approach is often acceptable, but as each call performs an independent query, data changes can result in records being skipped or appearing twice. One approach to improve this is to sort by a unique id field and then start the search for the next page at the unique id after the last unique id of the previous page. For example:


```
      # Get the first page 
      Get-<Noun> -MaxRecordCount 10 -SortBy SerialNumber 
      SerialNumber  ... 
      ------------  --- 
      A120004 
      A120007 
      ... 7 other records ... 
      A120900 

```

```
      # Get the next page 
      Get-<Noun> -MaxRecordCount 10 -Filter { FirstName -gt 'A120900' } 
      SerialNumber  ... 
      ------------  --- 
      A120901 
      B220000 
      ... 

```

## Filter Syntax Definition

&lt;Filter&gt;        ::= &lt;ScriptBlock&gt; | &lt;ComponentList&gt;

&lt;ScriptBlock&gt;   ::= "{" &lt;ComponentList&gt; "}"

&lt;ComponentList&gt; ::= &lt;Component&gt; &lt;AndOrOperator&gt; &lt;ComponentList&gt; | &lt;Component&gt;

&lt;Component&gt;     ::= &lt;NotOperator&gt; &lt;Factor&gt; | &lt;Factor&gt;

&lt;Factor&gt;        ::= "(" &lt;ComponentList&gt; ")" | &lt;PropertyName&gt; &lt;ComparisonOperator&gt; &lt;Value&gt; | &lt;PropertyName&gt;

&lt;AndOrOperator&gt; ::= "-and" | "-or"

&lt;NotOperator&gt;   ::= "-not" | "!"

&lt;ComparisonOperator&gt; ::= "-eq" | "-ne" | "-le" | "-ge" | "-lt" | "-gt" | "-like" | "-notlike" | "-contains" | "-notcontains" | "-in" | "-notin"

&lt;PropertyName&gt;  ::= &lt;simple name of property&gt;

&lt;Value&gt;         ::= &lt;string literal&gt;  | &lt;numeric literal&gt; | &lt;scalar variable&gt; | &lt;array variable&gt;  | "\$null" | "\$true" | "\$false"

Numeric literals support decimal and hexadecimal literals, with optional multiplier suffixes (kb, mb, gb, tb, pb).

Dates and times can be specified as string literals. The current culture determines what formats are accepted. To avoid any ambiguity, use strings formatted to the ISO8601 standard. If not specified, the current time zone is used.

Relative date-time string literals are also supported, using a minus sign followed by a TimeSpan. For example, "-1:30" means 1 hour and 30 minutes ago.


