### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>列表&lt;T&gt;。ForEach 可修改列表项时引发异常

|   |   |
|---|---|
|详细信息|从.NET 4.5 开始<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})>枚举器将引发<xref:System.InvalidOperationException?displayProperty=name>异常如果修改调用的集合中的元素。 该操作在以前不会引发异常，但可能会导致争用条件。|
|建议|理想情况下，应修复代码以便在枚举列表元素时不会修改列表，因为这始终不是安全操作。 但是，若要还原到以前行为，应用可以面向 .NET 4.0。|
|范围|边缘|
|版本|4.5|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

