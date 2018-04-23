### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="ad154-101">XmlSchemaException 现在正确设置行的位置</span><span class="sxs-lookup"><span data-stu-id="ad154-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ad154-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ad154-102">Details</span></span>|<span data-ttu-id="ad154-103">如果<xref:System.Xml.Linq.LoadOptions.SetLineInfo>值传递给 Load 方法并发生验证错误，<xref:System.Xml.Schema.XmlSchemaException.LineNumber>和<xref:System.Xml.Schema.XmlSchemaException.LinePosition>属性现在包含行信息。</span><span class="sxs-lookup"><span data-stu-id="ad154-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="ad154-104">建议</span><span class="sxs-lookup"><span data-stu-id="ad154-104">Suggestion</span></span>|<span data-ttu-id="ad154-105">假定的异常处理代码<xref:System.Xml.Schema.XmlSchemaException.LineNumber>和<xref:System.Xml.Schema.XmlSchemaException.LinePosition>将不会因为加载 XML 时使用 SetLineInfo 时，这些属性将立即正确设置应更新集。</span><span class="sxs-lookup"><span data-stu-id="ad154-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="ad154-106">范围</span><span class="sxs-lookup"><span data-stu-id="ad154-106">Scope</span></span>|<span data-ttu-id="ad154-107">边缘</span><span class="sxs-lookup"><span data-stu-id="ad154-107">Edge</span></span>|
|<span data-ttu-id="ad154-108">版本</span><span class="sxs-lookup"><span data-stu-id="ad154-108">Version</span></span>|<span data-ttu-id="ad154-109">4.5</span><span class="sxs-lookup"><span data-stu-id="ad154-109">4.5</span></span>|
|<span data-ttu-id="ad154-110">类型</span><span class="sxs-lookup"><span data-stu-id="ad154-110">Type</span></span>|<span data-ttu-id="ad154-111">运行时</span><span class="sxs-lookup"><span data-stu-id="ad154-111">Runtime</span></span>|
|<span data-ttu-id="ad154-112">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ad154-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
