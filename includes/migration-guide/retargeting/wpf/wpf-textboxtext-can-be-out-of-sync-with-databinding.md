### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text 可以是扩展的同步因数据绑定

|   |   |
|---|---|
|详细信息|在某些情况下，如果在数据绑定的写入操作期间修改属性，则 <xref:System.Windows.Controls.TextBox.Text> 属性会反映数据绑定属性值的以前的值。|
|建议|这不应有负面影响。 不过，你可以通过将 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> 属性设置为 <code>false</code> 来还原以前的行为。|
|范围|边缘|
|版本|4.5|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

