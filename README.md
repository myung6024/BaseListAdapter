# Sample

```
sealed class SampleListItem(override val viewType: ViewType) : ListItem {
    data class Sample(
        val id: String
    ) : SampleListItem(ViewType.SAMPLE1)

    data class Sample2(
        val name: String
    ) : SampleListItem(ViewType.SAMPLE2)

    enum class ViewType {
        SAMPLE1,
        SAMPLE2
    }
}

class SampleAdapter : MultiTypeListAdapter<SampleListItem, SampleListItem.ViewType>({
    when (it) {
        is SampleListItem.Sample -> it.id
        is SampleListItem.Sample2 -> it.name
    }
}) {
    override fun onCreateViewHolder(viewType: SampleListItem.ViewType, parent: ViewGroup): CommonViewHolder<SampleListItem> {
        when (viewType) {
            SampleListItem.ViewType.SAMPLE1 -> TODO()
            SampleListItem.ViewType.SAMPLE2 -> TODO()
        }
    }

    private class SampleViewHolder(binding: ViewBinding) : CommonViewHolder<SampleListItem.Sample>(binding) {
        override fun onBindView(item: SampleListItem.Sample) {
            TODO()
        }
    }

    private class Sample2ViewHolder(binding: ViewBinding) : ViewOnlyViewHolder(binding)
}
```
