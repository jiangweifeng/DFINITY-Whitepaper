给极客的互联网计算机白皮书


(v1.0)

DFINITY团队[^1]

一月21日, 2022

**摘要**

智能合约是一种新的软件形式，它将彻底改变现有的软件编写方式，IT系统的维护方式，以及改变各种应用程序的构建方式甚至是整个商业的革命。智能合约是在去中心化区块链上运行的可组合的、独立自主的软件，这使得它们不可篡改且无法停止。在本文中，我们描述了互联网计算机 (IC)，它是一种全新的区块链设计，可以释放智能合约的全部潜力，克服传统区块链上智能合约在速度、存储成本和计算能力方面的限制. 这样子智能合约第一次可以实现完全去中心化的应用程序，这些应用程序端到端的托管在区块链上。 IC 由一组加密协议组成，这些协议将各个独立运营的节点连接到一个区块链集合中。这些区块链托管并执行“canister”，即 IC 的智能合约形式。Canisters可以存储数据，对该数据执行非常通用的计算，并提供完整的技术堆栈，直接为终端用户提供网页服务。计算和存储费用通过“反向GAS模型”，由canister开发人员通过cycles预付这些费用，这些cycles是由IC的原生代币 ICP 兑换获得的。 ICP代币也用于治理：IC由去中心化自治组织（DAO）管理，决定网络拓扑结构的变化、协议的升级以及其他事情。

1 介绍

1.  释放智能合约的潜力

由于其独有的特性，智能合约是 Web3 的关键推动者，Web3 是一种新的互联网方法，应用程序完全由用户控制并在去中心化的区块链平台上运行。这种去中心化应用程序（dapps）通常是代币化的，这意味着代币被分发给用户作为参与 dapps 的奖励。参与可以有多种不同的形式，从审核和提供内容到管理 dapp 以及创建和维护 dapp。通常，代币也可以在交易所购买；事实上，出售代币是给 dapp 开发提供资金的一种常见方式。最后，代币还被用作 dapp 提供的服务或内容的一种支付方式。在当今的区块链平台上运行的智能合约，包括所有流行的平台（如以太坊），都受到许多限制，例如交易和存储成本高、计算速度慢以及无法为用户提供前端服务。因此，许多流行的区块链应用程序并不是完全去中心化的，而是混合体，其中大部分应用程序托管在传统云平台上，并调用区块链上的智能合约以实现其整体功能的一小部分。不幸的是，这使得此类应用程序变得非去中心化，并让它们面临传统云托管应用程序的许多缺点，例如受云服务提供商的控制，以及容易受到许多单点故障的影响。

**互联网计算机（IC）** 是执行智能合约的新平台。在这里，我们在非常广泛的意义上使用 **智能合约** 一词：一种*通用目的、不可变、防篡改的*计算机程序，在*去中心化的公共网络*上面*自主*执行。

-   *通用目的*，我们是指智能合约程序是图灵完备的那类（即任何可计算的东西都可以由智能合约计算）。

-   *不可变*，是指一旦部署，智能合约的代码不能由一方单方面更改。

-   *防篡改*，是指程序的指令得到如实执行，中间和最终结果被准确存储和/或传输。

-   *独立自主*，是指智能合约由网络自动执行，无需任何个人采取任何行动。

-   *去中心化公共网络*，是指可公开访问、地理位置分散，且不受少数个人或组织控制的计算机网络。

此外，智能合约

-   *可组合*，意味着它们可以相互交互，并且

-   支持*代币化*，意味着它们可以使用和交易数字代币。

与现有的智能合约平台相比，IC 旨在：

-   *更具成本效益*，特别是允许应用程序以先前平台成本的一小部分来计算和存储数据；

-   为处理智能合约交易提供*更高的吞吐量和更低的延迟*；

-   *更具可扩展性*，特别是，IC 可以原生的处理无限量的智能合约数据和计算，因为它可以通过向网络添加更多节点来增加容量。

除了提供智能合约平台外，IC 还被设计成一个*完整的技术堆栈，*这样可以构建完全在 IC 上运行的系统和服务。特别是，IC 上的智能合约可以服务于最终用户创建的 HTTP 请求，因此智能合约可以直接服务于交互式 Web 体验。这意味着可以在不依赖企业云托管服务或私有服务器的情况下创建系统和服务，从而以真正的端到端方式提供智能合约的所有好处。

**实现 Web3 的愿景。** 对于终端用户而言，访问基于 IC 的服务在很大程度上是透明的。他们的个人数据比访问公共或私有云上的应用程序更安全，但与应用程序交互的体验是相同的。

然而，对于创建和管理这些基于 IC 的服务的人来说，IC 消除了与开发和部署现代应用程序和微服务相关的许多成本、风险和复杂性。例如，相比正在垄断整个互联网的大型科技公司推动的整合，IC 平台为提供了另一种选择。此外，其安全协议可确保可靠的消息传递、透明的问责制和弹性，而无需依赖防火墙、备份设施、负载平衡服务或故障转移编排布置。

构建 IC 就是要让互联网恢复其开放、创新和创造性的根基 --- 换句话说，就是实现 Web3 的愿景。*为了专注于几个具体示例，IC 实现了：

-   支持互操作性、共享函数、永久 API 和无主应用程序，所有这些都可以降低平台风险并鼓励创新和协作。

-   将数据自动保存在内存中，从而消除了对数据库服务器和存储管理的需求，提高了计算效率，并简化了软件开发。

-   简化 IT 组织需要集成和管理的技术堆栈，从而提高运营效率

2.  互联网计算机的高层概括

大致上，IC 是一个交互 **复制状态机** 的网络。复制状态机的概念在分布式系统 [\[Sch90\]](\l) 中是一个相当标准的概念，但我们在这里简要介绍一下，从*状态机*的概念开始。

**状态机** 是一种特定的计算模型。这样的机器维护一个 **状态** ，它对应于普通计算机中的主存储器或其他形式的数据存储。这样的机器在离散的 **轮次** 中执行：在每一轮中，它接受一个输入，对*输入*和*当前状态*应用一个 **状态转换函数** ，获得一个 **输出** 和一个*新状态*。*新状态*成为下一轮的*当前状态*。

IC 的状态转换函数是一个 **通用函数**，这意味着存储在状态中的一些输入和数据可能是作用于其他输入和数据的任意 **程序**。因此，这样的状态机代表了一个通用的（即图灵完备的）计算模型。

为了实现 **容错**，可以将状态机复制。复制的状态机包含一个 **子网** 的 **副本** 集合，每个副本都运行同一状态机的副本。即使某些副本出现 **故障**，子网也应继续运行并正常运行。

子网中的每个副本都必须以相同的顺序处理相同的输入。为此，子网中的副本必须运行共识协议 [Fis83]，以确保子网中的所有副本以相同的顺序处理输入。因此，每个副本的内部状态将以完全相同的方式随着时间的推移而演变，并且每个副本将产生完全相同的输出序列。请注意，IC 上复制状态机的输入可能是外部用户的输入，也可能是另一个复制状态机生成的输出。类似地，复制状态机的输出可以是指向外部用户的输出，也可以是另一个复制状态机的输入。

3.  故障模型

在计算机科学的这一领域，通常会考虑两种类型的副本故障：**崩溃故障** 和 **拜占庭故障**。当副本突然停止并且没有恢复时，会发生 **崩溃故障**。 **拜占庭故障** 是副本可能以任意方式偏离其规定协议的故障。 此外，由于拜占庭式故障，一个或多个副本可能直接处于恶意对手的控制之下，该对手可能会协调这些副本的行为。 在这两种类型的故障中，拜占庭式故障可能更具破坏性。

用于共识和实现复制状态机的协议通常会假设 **有多少** 副本可能有故障，以及它们可能的故障 **类型**（崩溃或拜占庭）。 在 IC 中，假设如果给定的子网有 n 个副本，那么这些副本中有不到 n/3 是有故障的，并且这些故障可能是拜占庭的。 （请注意，IC 中不同的子网可能有不同的大小。）

4.  通信模型

用于共识和实现复制状态机的协议通常也会对 **通信模型** 做出假设，对恶意对手延迟副本之间消息传递的能力进行描述。在描述范围的两端，我们有以下模型：

• 在 **同步模型** 中，存在一些已知的有限时间限制δ，因此对于任何发送的消息，它都将在小于时间δ 内传递。

• 在 **异步模型** 中，对于发送的任何消息，攻击者可以将其传递延迟任意有限的时间，因此传递消息的时间没有限制。然而，每条消息 **最终** 都必须被传递。

由于 IC 子网中的副本通常分布在全球各地，因此同步通信模型将非常的不切实际。事实上，攻击者可以通过延迟诚实的副本或它们之间的通信来破坏协议的正确行为。这种攻击通常比控制和破坏诚实的副本更容易实施。

在一个节点分布在全球各地的子网设置中，最现实、最健壮的模型是异步模型。不幸的是，在这个模型中没有已知的真正实用的共识协议（最近的异步共识协议，如 [\[MXC+16\]](\l)，获得了不错的吞吐量，但延迟不是很好）。因此，与大多数其他不依赖同步通信的实用的拜占庭容错系统（例如，PBFT [\[CL99](\l), [BKM18,
AMN+20\]](\l)）一样，IC 选择了一种折衷方案：**部分同步** 通信模型 [\[DLS88\]](\l)。这种部分同步模型可以用各种方式来制定。 IC 使用的部分同步假设粗略地说，对于每个子网，该子网中的副本之间的通信是周期性同步的，时间间隔很短；此外，同步时限 δ 不需要事先知道。这种部分同步假设只需要确保共识协议取得进展（所谓的活性属性）。不需要部分同步假设（也不是最终消息传递假设）来确保共识的正确行为（所谓的安全属性），IC 协议栈中的其他任何地方也不需要它。

在部分同步和拜占庭故障的假设下，目前已知我们对故障数量 *f \<* n/3 的界限设置是最优的。

5.  权限模型

最早的共识协议（例如，PBFT [\[CL99\]](\l)）是**需要许可的（Permissioned）**，因为组成复制状态机的副本由一个中心化的组织管理，该组织决定哪些实体提供副本、网络的拓扑结构，以及可能实现某种中心化的公钥基础设施。虽然许可共识协议通常是最有效的，同时它们确实避免了单点故障，但中心化治理对于某些应用程序来说是不合要求的，它与蓬勃发展的 Web3 时代的精神背道而驰。

最近，我们看到了**无需许可的（Permissionless）** 共识协议的兴起，例如比特币 [\[Nak08\]](\l)、以太坊 [\[But13\]](\l) 和 Algorand [\[GHM+17\]](\l)。此类协议基于 **区块链** ，**工作量证明 (PoW)**（例如，比特币、v2.0 之前的以太坊）或 **权益证明 (PoS)**（例如，Algorand、以太坊 v2.0）。尽管此类协议是完全去中心化的，但它们的效率远低于许可协议。我们还指出，正如 [\[PSS17\]](\l) 中所观察到的，基于 PoW 的共识协议（例如比特币）不能保证异步通信网络中的正确性（即安全性）。

IC 的许可模型是一种 **混合模型** ，在获得需要许可协议的效率的同时提供去中心化 PoS 协议的许多好处。这种混合模型被称为 **DAO 控制的网络** ，并且（粗略地说）工作如下：每个子网运行一个许可的共识协议，但一个去中心化自治组织（DAO）确定哪些实体提供副本，配置网络的拓扑，提供公钥基础设施，并控制将哪个版本的协议部署到副本。 IC 的 DAO 被称为 **网络神经系统 (NNS)** ，它基于 PoS，因此 NNS 做出的所有决定都是由社区成员做出的，其投票权取决于他们质押了多少 IC 的原生治理令牌在 NNS 中（有关此令牌的更多信息，请参见第 1.8 节）。通过这个基于 PoS 的治理系统，可以创建新的子网，可以在现有子网中添加或删除副本，可以部署软件更新，并且可以对 IC 进行其他修改。 NNS 本身就是一个复制状态机，它（与任何其他状态机一样）运行在特定子网上，其子网的成员资格是通过相同的基于 PoS 的治理系统确定的。 NNS 维护一个称为 **注册表** 的数据库，该数据库跟踪 IC 的拓扑结构：哪些副本属于哪些子网、副本的公钥等。 （有关 NNS 的更多详细信息，请参见第 1.10 节。）

因此，人们看到 由 IC 的 DAO 控制的网络使 IC 获得了许可网络的许多实际好处（就更有效的共识而言），同时保持去中心化网络的许多好处（DAO治理）。

运行 IC 协议的副本托管在地理位置分散、独立运营的数据中心的服务器上。这也增强了 IC 的安全性和去中心化的性质。

6.  链密钥密码技术（Chain-key cryptography）

事实上，IC 的共识协议确实使用了区块链，但它也使用了公钥密码学，特别是数字签名：由 NNS 维护的注册表用于将各个公钥绑定到各个副本和子网，形成一个整体。这实现了一个独特而强大的技术集合，我们称之为 **链密钥密码技术** ，它有几个组件。

1.6.1 阈值签名

链密钥密码技术的第一个组成部分是 **阈值签名**：这是一种成熟的加密技术，它允许子网拥有一个公共签名验证密钥，其对应的秘密签名密钥被分成多个部分，这些部分分布在子网的所有副本中，使不诚实的副本持有的份额不会让他们伪造任何签名，而诚实的副本持有的份额允许子网生成与 IC 的策略和协议一致的签名。

这些阈值签名的一个关键应用是

*一个子网的单个输出可以由另一个子网或外部用户通过简单地验证数字签名来验证，用（第一个）子网（在IC上面即NNS）的公共签名验证密钥。*

请注意，子网的公共签名验证密钥可以从 NNS 获得 --- 此公共签名验证密钥在子网的生命周期内保持不变（即使子网的成员可能在该生命周期内发生变化）。这与许多不可扩展的基于区块链的协议形成鲜明对比，后者需要验证整个区块链才能验证任何单个输出。

正如我们将看到的，这些阈值签名在 IC 中还有许多其他应用。一个这样的应用程序是让子网中的每个副本访问不可预测的伪随机位（源自此类签名）。这是共识中使用的 **随机信标** 和执行中使用的 **随机磁带** 的基础。

为了安全地部署阈值签名，IC 使用了一种创新的 **分布式密钥生成 (DKG)** 协议，该协议构建了一个公共签名验证密钥，并为每个副本提供相应的秘密签名密钥的一部份，并在我们的故障和通信模型中工作。

1.6.2 链进化技术

链密钥密码技术还包括一系列复杂的技术，用于随着时间的推移稳健、安全地维护基于区块链的复制状态机，这些技术共同构成了我们所说的 **链进化技术** 。每个子网根据 **epochs** 来运行（每个epoch通常在几百轮/区块的数量级）。使用阈值签名和许多其他技术，链演进技术实现了许多基本的维护活动，这些活动以epochs为基本单位，按一定节奏定期执行：

**垃圾收集：** 在每个 epoch 结束时，所有已处理的输入以及对这些输入排序所需的所有共识级协议消息都可以安全地从每个副本的内存中清除。这对于防止副本的存储需求无限制地增长至关重要。这与许多不可扩展的基于区块链的协议形成对比，它们必须存储从创世块开始的整个区块链。

**快速转发：** 如果子网中的一个副本远远落后于它的对等节点（因为它长时间宕机或与网络断开连接），或者一个新的副本被添加到子网中，它可以通过 **快速转发** 数据更新到最近的epoch的开始位置，无需运行共识协议并无需处理到该点之前的所有输入。这与许多不可扩展的基于区块链的协议形成对比，它们必须处理从创世块开始的整个区块链。

**子网成员变化：** 子网成员（由 NNS 确定，参见第 1.5 节）可能会随着时间而变化。这只能发生在 epoch 的边界，需要小心操作以确保一致和正确的行为。

**主动重新配发秘密：** 我们在上面的 1.6.1 节中提到了 IC 如何使用链密钥密码技术 --- 特别是阈值签名 --- 进行输出验证。这是基于 **秘密共享** 的，它通过将秘密（在本例中为秘密签名密钥）拆分为存储在副本之间的不同部分（shares）来避免任何单点故障。在每个epoch开始时，这些秘密部分(shares)都会被 **主动重新配发**。这实现了两个目标：

-   当子网的成员发生变化时，重新配发将确保任何新成员都拥有秘密恰当的一部分，而不再是成员的任何副本不再拥有秘密的一部分。

-   如果在任何一个epoch甚至是在每个epoch都有少量秘密部分被泄露给攻击者，那么这些秘密部分对攻击者没有帮助。

**协议升级：** 当 IC 协议本身需要升级、修复 bug 或添加新功能时，可以在一个 epoch 开始时使用特殊协议自动完成。

7.  执行模型

如前所述，IC 中的复制状态机可以执行任意程序。 IC 中的基本计算单元称为 **canister** ，它与进程的概念大致相同，因为它包含程序及其状态（随时间变化）。

Canister 程序以 **WebAssembly** 或简称 **Wasm** 编码，这是一种用于基于堆栈的虚拟机的二进制指令格式。 Wasm 是一个开放标准。虽然它最初设计是让网页上支持运行高性能应用程序，但它实际上非常适合通用计算。

IC 提供了一个运行时环境，用于在canister中执行 Wasm 程序，并与其他canisters和外部用户进行通信（通过消息传递）。虽然原则上可以用任何可以编译为 Wasm 的语言编写canister程序，但还是有一种称为 **Motoko** 的语言被设计出来了，它与 IC 的操作语义非常一致。 Motoko 是一种强类型、**基于参与者(actor based)** 的编程语言，内置支持 **正交持久化(orthogonal persistence)** 和 **异步消息传递** 。正交持久化是指canister维护的所有内存都会自动持久化（即，不必将其写入文件）。 Motoko 具有许多生产力和安全特性，包括自动内存管理、泛型、类型推断、模式匹配以及任意精度和固定精度算术。

除了 Motoko，IC 还提供了一种消息接口定义语言和连接格式，叫做 **Candid** ，用于类型化的、高级的和跨语言的互操作性。这允许任何两个canisters，即使是用不同的高级语言编写的，也可以轻松地相互通信。

为了完全支持用任何特定的编程语言进行canister开发，除了该语言的 Wasm 编译器之外，还必须提供某些运行时的支持。目前，除了Motoko，IC还全面支持Rust编程语言用于canister开发。

8.  实用型代币 (Utility token)

IC 使用称为 **ICP** 的 **实用型代币** 。此令牌用于以下功能：

在 NNS 中质押：如第 1.5 节所述，ICP 代币可以在 NNS 中质押以获得投票权，从而参与控制 IC 网络的 DAO。持有 ICP 代币在 NNS 中质押并参与的用户

> NNS 治理还获得新铸造的 ICP 代币作为*投票奖励*。奖励金额由 NNS 制定和执行的政策决定。

**转换为Cycles：** ICP用于支付IC的使用费用。更具体地说，ICP 代币可以转换为 **cycles**（即*烧毁*），这些cycles用于支付创建canister（参见第 1.7 节）和canister使用的资源（存储、CPU 和带宽）的费用。 ICP 转换为cycles的汇率由 NNS 决定。

**向节点提供者支付费用：** ICP 代币用于向节点提供者支付费用 --- 这些实体拥有和运营计算节点来托管构成 IC 的副本。 NNS 定期（目前每月一次）决定每个节点提供者应该接收新铸造代币的数量，并将代币发送到节点提供者的账户。根据 NNS 制定和执行的相关政策，代币支付的条件是向 IC 提供了可靠的服务。

9.  **边界节点**

**边界节点** 提供IC的网络边缘服务。特别是，他们提供

-   明确定义的 IC 入口点，

-   IC 的拒绝服务保护，

-   从传统客户端（例如，网络浏览器）无缝访问 IC。

为了使用传统客户端无缝访问 IC，边界节点提供了将来自用户的标准 HTTPS 请求转换为指向 IC 上canister的入口消息的功能，然后将此入口消息路由到子网上存在这个canister的特定副本。此外，边界节点提供额外的服务来改善用户体验：缓存、负载平衡、速率限制，以及为传统客户端验证来自 IC 的响应。

Canister由 ic0.app 域上的 URL 标识。最初，传统客户端会查找 URL 对应的 DNS 记录，获取边界节点的 IP 地址，然后向该地址发送初始 HTTPS 请求。边界节点返回一个将在传统客户端中执行的基于 javascript 的“service worker”。在此之后，传统客户端和边界节点之间的所有交互都将通过这个 service worker 完成。

Service worker执行的一项基本任务是使用链密钥加密技术验证来自 IC 的响应（参见第 1.6 节）。为此，NNS 的公共验证密钥被硬编码在 service worker 中。

边界节点本身负责将请求路由到托管指定canister的子网上的副本。执行此路由所需的信息由边界节点从 NNS 获得。边界节点保存一个包含了能及时回复的副本的列表，并从该列表中选择一个随机副本。

传统客户端和边界节点之间以及边界节点和副本之间的所有通信都通过 TLS 保护。

除了传统客户端，还可以使用“IC原生”客户端与边界节点交互，这些客户端已经包含了service worker逻辑，不需要从边界节点检索service worker程序。

就像副本一样，边界节点的部署和配置由 NNS 控制。

10. NNS 的更多细节

如第 1.5 节所述，网络神经系统（NNS）是一种控制 IC 的算法治理系统。它是通过一个特殊系统子网上的一组canisters来实现的。这个子网与任何其他子网类似，但配置有所不同（例如，系统子网上的容器不为其使用的周期收费）。一些NNS最相关的canisters是

-   **注册表canister** ，它存储 IC 的配置，即哪些副本属于哪个子网、与子网和各个副本关联的公钥等。

-   **治理canister** ，管理有关 IC 应如何发展的决策和投票。

-   **账本canister** ，用于跟踪用户的 ICP 实用型代币账户和他们之间的交易。

1.  NNS 的决策

任何人都可以通过在所谓的 **神经元** 中质押 ICP 代币来参与 NNS 治理。然后，神经元持有者可以对 **提案** 提出建议和投票，这些提案是关于应该如何更改 IC 的建议，例如，应该如何更改子网拓扑结构或协议。神经元对决策的投票权是基于权益证明。直观地说，拥有更多质押 ICP 代币的神经元拥有更多的投票权。然而，投票权还取决于其他一些神经元特征，例如，更多的投票权被赋予给承诺将其代币质押更长时间的神经元持有者。

每个提案都有一个确定的投票期。如果在投票期结束时，总投票权的简单多数投票赞成该提案，并且这些赞成票构成总投票权的给定法定人数（目前为 3%），则该提案 **被采纳** 。否则，该提议 **被拒绝** 。此外，如果绝对多数（超过总投票权的一半）赞成或反对该提案，则该提案会被立即通过或拒绝。

如果提案被采纳，治理canister会自动执行决策。例如，如果提案建议更改网络拓扑结构并被采纳，则治理canister会自动使用新配置更新注册表。

![image](https://user-images.githubusercontent.com/98205496/150631058-dcba9bc5-3bf8-47c1-a11d-d4d87428525b.png)

图 1：互联网计算机协议的层级

11. 进行中的工作

IC 的架构仍在不断发展和扩展。以下是一些即将部署的新功能：

**由DAO控制的canister。** 就像 IC 的整体配置由 NNS 控制一样，任何canister也可能由其自己的DAO控制，这个DAO称为 **服务神经系统(SNS)**。控制canister的 DAO 可以控制canister逻辑的更新，以及发布特权命令让canister去执行。

**阈值 ECDSA。** ECDSA 签名 [JMV01] 用于加密货币，例如比特币和以太坊，以及许多其他应用。虽然阈值签名已经是 IC 中的重要组成部分，但这些不是阈值 ECDSA 签名。这一新功能将允许单个canister控制 ECDSA 签名密钥，该密钥安全地分布在托管canister的子网的所有副本中。

**比特币和以太坊的整合。** 基于新的阈值 ECDSA 功能，此功能将允许canister与比特币和以太坊区块链进行交互，包括签署交易的能力。

**HTTP 集成。** 此功能将允许canister读取任意网页（IC以外的）。
