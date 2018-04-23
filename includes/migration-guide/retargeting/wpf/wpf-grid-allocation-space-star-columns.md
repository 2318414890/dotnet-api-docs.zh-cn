### <a name="wpf-grid-allocation-of-space-to-star-columns"></a><span data-ttu-id="db6b2-101">WPF 网格分配到星型列的空间</span><span class="sxs-lookup"><span data-stu-id="db6b2-101">WPF Grid allocation of space to star-columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="db6b2-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="db6b2-102">Details</span></span>|<span data-ttu-id="db6b2-103">从.NET Framework 4.7 开始，WPF 将替代该算法的<xref:System.Windows.Controls.Grid>使用分配到的空间 \* 的列。</span><span class="sxs-lookup"><span data-stu-id="db6b2-103">Starting with the .NET Framework 4.7, WPF replaces the algorithm that <xref:System.Windows.Controls.Grid> uses to allocate space to \*-columns.</span></span> <span data-ttu-id="db6b2-104">这将更改分配给的实际宽度 \* 的事例数中的列：</span><span class="sxs-lookup"><span data-stu-id="db6b2-104">This will change the actual width assigned to \*-columns in a number of cases:</span></span><ul><li><span data-ttu-id="db6b2-105">当一个或多个 \* 的列还具有一个重写该列的比例分配的最小值或最大宽度。</span><span class="sxs-lookup"><span data-stu-id="db6b2-105">When one or more \*-columns also have a minimum or maximum width that overrides the proportional allocation for that colum.</span></span> <span data-ttu-id="db6b2-106">（最小宽度可以源自的显式 MinWidth 声明，或者从列的内容中获取的隐式的最小值。</span><span class="sxs-lookup"><span data-stu-id="db6b2-106">(The minimum width can derive from an explicit MinWidth declaration, or from an implicit minimum obtained from the column's content.</span></span> <span data-ttu-id="db6b2-107">最大宽度可以仅定义显式，从 MaxWidth 声明。）</span><span class="sxs-lookup"><span data-stu-id="db6b2-107">The maximum width can only be defined explicitly, from a MaxWidth declaration.)</span></span></li><li><span data-ttu-id="db6b2-108">当一个或多个 *-列声明极大 *-权重，大于 10 ^298。</span><span class="sxs-lookup"><span data-stu-id="db6b2-108">When one or more *-columns declare an extremely large *-weight, greater than 10^298.</span></span></li><li><span data-ttu-id="db6b2-109">当 \*-权重是充分不同，会遇到浮点不稳定 （溢出、 下溢、 精度损失）。</span><span class="sxs-lookup"><span data-stu-id="db6b2-109">When the \*-weights are sufficiently different to encounter floating-point instability (overflow, underflow, loss of precision).</span></span></li><li><span data-ttu-id="db6b2-110">当布局圆化处理已启用且有效显示 DPI 足够高时。</span><span class="sxs-lookup"><span data-stu-id="db6b2-110">When layout rounding is enabled, and the effective display DPI is sufficiently high.</span></span></li></ul><span data-ttu-id="db6b2-111">在前两个情况下，在新的算法生成的宽度可以是明显不同于旧算法; 生成的那些在最后一种情况，差异将最多一个或两个像素。将新算法修复旧算法中存在的几个 bug:</span><span class="sxs-lookup"><span data-stu-id="db6b2-111">In the first two cases, the widths produced by the new algorithm can be significantly different from those produced by the old algorithm; in the last case, the difference will be at most one or two pixels.The new algorithm fixes several bugs present in the old algorithm:</span></span><ol><li><span data-ttu-id="db6b2-112">向列分配的总空间可能会超过网格宽度。</span><span class="sxs-lookup"><span data-stu-id="db6b2-112">Total allocation to columns can exceed the Grid's width.</span></span> <span data-ttu-id="db6b2-113">当向比例份额小于其大小下限的列分配空间时，可能会出现这种问题。</span><span class="sxs-lookup"><span data-stu-id="db6b2-113">This can occur when allocating space to a column whose proportional share is less than its minimum size.</span></span> <span data-ttu-id="db6b2-114">算法会分配大小下限对应的空间，这将减少其他列的可用空间。</span><span class="sxs-lookup"><span data-stu-id="db6b2-114">The algorithm allocates the minimum size, which decreases the space available to other columns.</span></span> <span data-ttu-id="db6b2-115">如果有任何 \* 的列向左以分配的总分配将太大。</span><span class="sxs-lookup"><span data-stu-id="db6b2-115">If there are no \*-columns left to allocate, the total allocation will be too large.</span></span></li><li><span data-ttu-id="db6b2-116">向列分配的总空间可能会占不满网格宽度。</span><span class="sxs-lookup"><span data-stu-id="db6b2-116">Total allocation can fall short of the Grid's width.</span></span> <span data-ttu-id="db6b2-117">这是 #1，因大于其最大大小，没有将其成比例共享分配给某一列时的双重问题 \*-有待占用 slack 的列。</span><span class="sxs-lookup"><span data-stu-id="db6b2-117">This is the dual problem to #1, arising when allocating to a column whose proportional share is greater than its maximum size, with no \*-columns left to take up the slack.</span></span></li><li><span data-ttu-id="db6b2-118">两个 * 的列可以接收不成正比的分配其 * 的权重。</span><span class="sxs-lookup"><span data-stu-id="db6b2-118">Two *-columns can receive allocations not proportional to their *-weights.</span></span> <span data-ttu-id="db6b2-119">这是第 1 个/第 2 个问题造成的较为温和的影响，当依序向 \*-列 A、B 和 C 分配空间，但 B 列的比例份额与约束下限（或上限）冲突时，可能会出现这种问题。</span><span class="sxs-lookup"><span data-stu-id="db6b2-119">This is a milder version of #1/#2, arising when allocating to \*-columns A, B, and C (in that order), where B's proportional share violates its min (or max) constraint.</span></span> <span data-ttu-id="db6b2-120">同样，这会更改 C 列的可用空间，它将比 A 列获得更少（或更多）的按比例分配空间。</span><span class="sxs-lookup"><span data-stu-id="db6b2-120">As above, this changes the space available to column C, who gets less (or more) proportional allocation than A did,</span></span></li><li><span data-ttu-id="db6b2-121">使用极大的权重列 (&gt; 10 ^298) 所有看做就好像它们具有权重 10 ^298。</span><span class="sxs-lookup"><span data-stu-id="db6b2-121">Columns with extremely large weights (&gt; 10^298) are all treated as if they had weight 10^298.</span></span> <span data-ttu-id="db6b2-122">这些列（以及权重略小的列）之间的比例差异将不会生效。</span><span class="sxs-lookup"><span data-stu-id="db6b2-122">Proportional differences between them (and between columns with slightly smaller weights) are not honored.</span></span></li><li><span data-ttu-id="db6b2-123">未正确处理使用 inifinte 权重列。</span><span class="sxs-lookup"><span data-stu-id="db6b2-123">Columns with inifinte weights are not handled correctly.</span></span> <span data-ttu-id="db6b2-124">[实际上，不能设置无穷大的权重，但这是一项人为限制。</span><span class="sxs-lookup"><span data-stu-id="db6b2-124">[Actually you can't set a weight to Infinity, but this is an artificial restriction.</span></span> <span data-ttu-id="db6b2-125">空间分配代码是在努力处理这样的列，但处理得并不好。]</span><span class="sxs-lookup"><span data-stu-id="db6b2-125">The allocation code was trying to handle it, but doing a bad job.]</span></span></li><li><span data-ttu-id="db6b2-126">在避免溢出、下溢、精度损失和类似浮点问题时，存在一些小问题。</span><span class="sxs-lookup"><span data-stu-id="db6b2-126">Several minor problems while avoiding overflow, underflow, loss of precision and similar floating-point issues.</span></span></li><li><span data-ttu-id="db6b2-127">在 DPI 足够高的情况下，无法正确调整布局的圆化处理。</span><span class="sxs-lookup"><span data-stu-id="db6b2-127">Adjustments for layout rounding are incorrect at sufficiently high DPI.</span></span></li></ol><span data-ttu-id="db6b2-128">新的算法将生成满足以下条件： A 的结果。</span><span class="sxs-lookup"><span data-stu-id="db6b2-128">The new algorithm produces results that meet the following criteria:A.</span></span> <span data-ttu-id="db6b2-129">分配给的实际宽度 \* 的列不小于其最小宽度也不大于其最大宽度。B。</span><span class="sxs-lookup"><span data-stu-id="db6b2-129">The actual width assigned to a \*-column is never less than its minimum width nor greater than its maximum width.B.</span></span> <span data-ttu-id="db6b2-130">每个<em>-不是列分配其最小或最大宽度分配宽度成正比其<em>的权重。要精确，如果两个列声明宽度 x</em>和 y</em>分别，并且如果既不该列未接收到其最小值或最大宽度，实际宽度 v 和 w 分配给列位于相同的比例： v / w = = x / y.C.</span><span class="sxs-lookup"><span data-stu-id="db6b2-130">Each <em>-column that is not assigned its minimum or maximum width is assigned a width proportional to its <em>-weight. To be precise, if two columns are declared with width x</em> and y</em> respectively, and if neither column receives its minimum or maximum width, the actual widths v and w assigned to the columns are in the same proportion: v / w == x / y.C.</span></span> <span data-ttu-id="db6b2-131">总宽度分配给&quot;成比例&quot;*-列后的可用空间等于分配给受约束的列 (固定的自动和 *-分配其最小值或最大宽度的列)。</span><span class="sxs-lookup"><span data-stu-id="db6b2-131">The total width allocated to &quot;proportional&quot; *-columns is equal to the space available after allocating to the constrained columns (fixed, auto, and *-columns that are allocated their min or max width).</span></span> <span data-ttu-id="db6b2-132">例如，这可能是零，如果最小宽度的总和超过了网格的 availbable 宽度。D。</span><span class="sxs-lookup"><span data-stu-id="db6b2-132">This might be zero, for instance if the sum of the minimum widths exceeds the Grid's availbable width.D.</span></span> <span data-ttu-id="db6b2-133">所有这些语句是相对于解释&quot;理想&quot;布局。</span><span class="sxs-lookup"><span data-stu-id="db6b2-133">All these statements are to be interpreted with respect to the &quot;ideal&quot; layout.</span></span> <span data-ttu-id="db6b2-134">布局舍入在生效时，实际的宽度可能与不同的理想宽度多达一个像素。旧算法遵循 (A)，但无法接受在上述情况下的其他条件。有关列和宽度这篇文章中的所说的一切也适用于行和高度。</span><span class="sxs-lookup"><span data-stu-id="db6b2-134">When layout rounding is in effect, the actual widths can differ from the ideal widths by as much as one pixel.The old algorithm honored (A) but failed to honor the other criteria in the cases outlined above.Everything said about columns and widths in this article applies as well to rows and heights.</span></span>|
|<span data-ttu-id="db6b2-135">建议</span><span class="sxs-lookup"><span data-stu-id="db6b2-135">Suggestion</span></span>|<span data-ttu-id="db6b2-136">默认情况下，应用从.NET Framework 4.7 的.NET framework 目标版本，将看到新算法，应用面向.NET Framework 4.6.2 或更早版本，将看到旧算法时。若要重写默认值，请使用以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="db6b2-136">By default, apps that target versions of the .NET Framework starting with the .NET Framework 4.7 will see the new algorithm, while apps that target the .NET Framework 4.6.2 or earlier versions will see the old algorithm.To override the default, use the following configuration setting:</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><span data-ttu-id="db6b2-137">值 'true' 选择旧算法，'false' 选择新的算法。</span><span class="sxs-lookup"><span data-stu-id="db6b2-137">The value 'true' selects the old algorithm, 'false' selects the new algorithm.</span></span>|
|<span data-ttu-id="db6b2-138">范围</span><span class="sxs-lookup"><span data-stu-id="db6b2-138">Scope</span></span>|<span data-ttu-id="db6b2-139">次要</span><span class="sxs-lookup"><span data-stu-id="db6b2-139">Minor</span></span>|
|<span data-ttu-id="db6b2-140">版本</span><span class="sxs-lookup"><span data-stu-id="db6b2-140">Version</span></span>|<span data-ttu-id="db6b2-141">4.7</span><span class="sxs-lookup"><span data-stu-id="db6b2-141">4.7</span></span>|
|<span data-ttu-id="db6b2-142">类型</span><span class="sxs-lookup"><span data-stu-id="db6b2-142">Type</span></span>|<span data-ttu-id="db6b2-143">重定目标</span><span class="sxs-lookup"><span data-stu-id="db6b2-143">Retargeting</span></span>|
