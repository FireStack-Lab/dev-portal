| id       | title |
| -------- | ----- |
| arch-faq | FAQ   |

本文档包含来自以太坊区块链的开发人员遇到的常见问题。请认真阅读本文档，以免以后提出本文中提及的问题。



## 我必须等待多少次确认？

您无需等待任何确认。Zilliqa的[共识协议](https://github.com/Zilliqa/dev-portal/blob/master/docs/arch-overview.md#structure-and-consensus)具有极大的好处：与工作证明不同，它不依赖于哈希/经济博弈的数量来产生区块链的标准状态。一旦您的交易被包含在一个区块中，它就不会被回滚。



## 我想运行一个节点，但我不想打开入站端口。

Zilliqa节点的p2p网络层要求节点操作者（无论是分片还是种子节点）至少为p2p通信打开一个入站端口。这是因为节点之间的底层TCP连接不是持久的。

因此，为了使您的节点能够从网络的其他节点接收消息，他必须能够启动与您的节点的TCP连接。如果不能，这将导致您的节点在整个到时时期会被其他节点列入黑名单。



## Zilliqa节点可以管理我的钱包吗？

不可以。与某些比特币或以太坊客户端不同，Zilliqa节点永远不会管理你的钱包，永远不会签署交易。出于安全考虑，签名必须始终由用户通过SDK或其他方式执行。



## 什么是Tx Block时间？

通常持续2分钟。请注意，您的交易可能不会包含在下一个Tx区块中。交易广播通常包含在Tx区块`n+(1|2)`中。例如，如果下一个Tx区块为100，则您可能发现您的交易只包含在TxBlock 101或102中。



## 是否有WS API？

没有WebSocket API。请使用长轮询来监听新的交易。本文档详细介绍了执行此操作的一般技术。



## *什么是电汇格式？*

Zilliqa电汇格式是Protobuf。它仅用于p2p通信和签名生成或验证。大多数开发人员永远不应该处理它，因为RPC API完全是JSON编码的。
