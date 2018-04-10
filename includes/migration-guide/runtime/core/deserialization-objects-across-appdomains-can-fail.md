### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="7f853-101">跨应用程序域的对象的反序列化可能会失败</span><span class="sxs-lookup"><span data-stu-id="7f853-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7f853-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="7f853-102">Details</span></span>|<span data-ttu-id="7f853-103">在某些情况下，当应用使用两个或更多带有不同应用程序基的应用域时，尝试跨应用域在逻辑调用上下文中为对象反序列化将引发异常。</span><span class="sxs-lookup"><span data-stu-id="7f853-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="7f853-104">建议</span><span class="sxs-lookup"><span data-stu-id="7f853-104">Suggestion</span></span>|<span data-ttu-id="7f853-105">请参阅[缓解： 跨应用程序域的对象的反序列化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="7f853-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="7f853-106">范围</span><span class="sxs-lookup"><span data-stu-id="7f853-106">Scope</span></span>|<span data-ttu-id="7f853-107">边缘</span><span class="sxs-lookup"><span data-stu-id="7f853-107">Edge</span></span>|
|<span data-ttu-id="7f853-108">版本</span><span class="sxs-lookup"><span data-stu-id="7f853-108">Version</span></span>|<span data-ttu-id="7f853-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7f853-109">4.5.1</span></span>|
|<span data-ttu-id="7f853-110">类型</span><span class="sxs-lookup"><span data-stu-id="7f853-110">Type</span></span>|<span data-ttu-id="7f853-111">运行时</span><span class="sxs-lookup"><span data-stu-id="7f853-111">Runtime</span></span>|

