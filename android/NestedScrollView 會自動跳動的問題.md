# Description:

當有 ScrollView 放在 NestedScrollView 的時候會發生這樣的問題

這時候只要在 NestedScrollView 底下的主元素加上屬性 android:descendantFocusability="blocksDescendants" 就可以解掉這問題

# 參考

* http://stackoverflow.com/a/35723694
