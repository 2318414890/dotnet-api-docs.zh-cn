### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System.Uri 转义现在支持 RFC 3986

|   |   |
|---|---|
|详细信息|URI 转义在 .NET 4.5 中做了更改，以支持 [RFC 3986](http://tools.ietf.org/html/rfc3986)。 具体更改包括：<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> 根据 RFC 3986 转义保留字符。</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> 未转义保留字符。</li><li>如果 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> 遇到无效的转义序列，则它不会引发异常。</li><li>未保留的转义字符已取消转义。</li></ul>|
|建议|<ul><li>更新应用程序以不依赖于<xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name>在无效的转义序列的情况下引发。 此类序列现在必须直接进行检测。</li><li>同样，预计转义和非转义 URI 和数据字符串在 .NET 4.0 和 .NET 4.5 中可能会有所不同，并且这些字符串不应直接在各种 .NET 版本中进行比较。 而在对这些字符串进行任何比较前，应在单个 .NET 版本中对其进行分析和规范化。</li></ul>|
|范围|次要|
|版本|4.5|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|

