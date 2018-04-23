### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>IMessageFilter.PreFilterMessage 的可重入实现不会再引发 Application.FilterMessage

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.6.1 之前，使用名为 <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> 或 <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> 的 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 调用 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)>（同时调用 <xref:System.Windows.Forms.Application.DoEvents>）会导致 <xref:System.IndexOutOfRangeException?displayProperty=name>。从面向 .NET Framework 4.6.1 的应用程序开始，不再引发此异常，并且可能使用上述的可重入筛选器。|
|建议|请注意，上述的可重入 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 行为将不再引发 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)>。 此更改仅影响面向 .NET Framework 4.6.1 的应用程序。面向 .NET Framework 4.6.1 的应用可使用 [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) 兼容性开关，选择退出此更改（或者面向较早的 Framework 的应用可选择使用此更改）。|
|范围|边缘|
|版本|4.6.1|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

