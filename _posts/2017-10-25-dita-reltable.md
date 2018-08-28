---
layout: post
category: dita
---

# DITA Relationship Table

DITA结构化写作中，不同主题之间的链接除了层级链接和内嵌链接外，还有另一种链接选择：相关链接（related links）。通常，使用关系表（对应DITA元素为<reltable>
）创建相关主题间、DITA topic文件和非DITA文件之间的相互链接。

## 关系表的类型

关系表常用于生成Related links的列表，一般分为三种：

- **主题类型连接表：** 根据Concept、Task、Reference主题类型，使用主题类型表来创建相关链接。
- **单向链接表：** 创建从一个主题到另一主题的相关链接，仅在从来源主题到目标主题时有效，反向则无效。
- **双向链接表：** 创建两个主题之间的双向链接，与主题类型无关。

## 关系表 VS `cross reference`

cross reference要求源文件和目标文件均需要在DITA map中，并可用，同时二者之间的依存关系不能发生变化.

因此，使用关系表创建相关链接还有以下优势：

- **集中的链接管理：** 关系表使得主题之间的链接更容易定位，因为链接关系不是在每个主题而是在同一个位置定义。
- **简化的维护：** 一旦相关主题文件位置发生变化，从集中的位置修复和更新链接比遍历每个主题会更加容易。
- **更好的重用性：** 在DITA map文件中创建链接，主题对其他文档的依存性会减少，即改进了主题的潜在的重用性。

## 关系表使用注意事项

在创建关系表时，请注意以下方面：

- 只能在DITA map中创建关系表
- 关系表不出现在发布物中，只用于生成Related links的列表。
- 关系表可以出现在DITA map和DITA bookmap文件中，任意数量。
  - 理论上，<reltable>元素可出现在map的任意位置，但通常的做法是将其放在最后一个topicref之后。
  - 在DITA bookmap中，<reltable>元素必须是最后一个元素。
- 关系表中各列的顺序和相对位置没有任何意义。
- 同一个topicref可出现在关系表的不同行。
- 关系表中的单元格中可包含一个或多个 topicref，也可以没有。

## 高级关系表

- collection-type 属性

关系表中某个单元格中包含多个topicref时，设置collection-type属性能让多个topicref之间相互链接。

在以下示例中，A主题和B主题会相互链接。

```
<relcell collection-type="family">
      <topicref href="a.dita">
      <topicref href="b.dita">
</relcell>
```

## 建立关系表的最佳实践

- 列数不宜过多。

