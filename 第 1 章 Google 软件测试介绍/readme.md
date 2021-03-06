## 第 1 章 Google 软件测试介绍

在 Google，软件测试团队归属于一个被称为“工程生产力”（Engineering Productivity，也译为工程效率或工程生产率）的中心组织部门，这个部门的职责横跨开发测试人员使用工具的研发、产品发布和各种级别的测试，从单元级别的测试到探索性级别的测试。

GTAC（Google Test Automation Conference，Google 测试自动化大会）成了测试行业的旗帜性会议。

Google 是一家以创新和速度为基础的公司，快速地发布有用的代码（如果失败，也只有少数早期用户会失望）、迭代地增加早期用户希望使用的功能（最大化用户反馈）。

绝大多数 Google 源代码都是开源的，这些代码对外公开。

Google 的测试方法看起来有点违背常理——在整个公司，只有非常少的专职测试人员，甚至比我们竞争对手公司的单个产品的测试人员还要少。

>    Google 成功的关键是什么
>
>   第一个建议就是，不要招聘太多的而测试人员。

在 Google，写代码的开发人员也承担了质量的重任。质量从来就不仅仅是一些测试人员的问题。在 Google，每个写代码的开发者本身就是测试者，质量在名义上也由这样的开发测试组合共同承担。在 Google，谈论开发测试比，本身没有任何意义。

### 1.1 质量不等于测试

质量不是被测试出来的。

有一个简单的办法可以解决这个难题，那就是停止开发与测试的隔离对立。开发和测试应该并肩齐驱。你需要在写完每一段代码后立刻测试这段代码，当完成了更多的代码时就要做更多的测试。测试不是独立隔离的活动，它本身就是开发过程的一部分。质量不等于测试，当你把开发过程和测试放到一起，直到不能区分彼此的时候，你就得到了质量。

在 Google，目标就是把开发过程和测试融合在一起——开发和测试必须同时开展。写一段代码就立刻测试这段代码，完成更多的代码就做更多的测试。但关键是由谁来做这些测试？

在 Google，专职测试人员的数量非常稀少，与开发相比根本不成比例，唯一可能去做这些的就只能是开发人员。

Google 能用如此少的专职人员的原因，就是开发对质量的负责。如果某个产品出了问题，第一个跳出来的肯定式导致这个问题发生的开发人员，而不是遗漏这个 bug 的测试人员。

这意味着质量更像是一种预防行为，而不是检测。质量是开发过程的问题，而不是测试问题。

Google 已经成功地将测试实践融入为开发过程的一部分，并创建了一个增量上线的流程。如果一些项目在线上被证实的确是 bug 重重，它将会被回滚到之前的版本。在确保不出现回滚级别 bug 发生的前提下，预防了许多客户问题的同时，也很大程度降低了专职测试人员的数量。在 Google，测试的目标就是来判断这种预防工作做得怎么样。

### 1.2 角色

>   you build it, you break it, you fix it

原意指在构建实验室（Build Lab）的人永远不会去修复构建失败（build break）的问题，只有开发人员自己才能修复。这里的意思是开发人员自己要对自己写的代码负责，比专职的测试人员更适合做测试工作。

#### 1.2.1 软件开发工程师（SWE）

SWE（software engineer），是一个传统上的开发角色，他们的工作是实现最终用户所使用的功能代码。他们创建设计文档、选择最优的数据结构和整体架构，并且花费大量时间在代码实现与代码审核上。SWE 需要编写与测试代码，包括测试驱动的设计、单元测试、参与构建各种大小规模的测试等。

SWE 会对他们编写、修复以及修改的代码承担质量责任。

#### 1.2.2 软件测试开发工程师（SET）

SET（software engineer in test）也是一个开发角色，只是工作重心在可测试性和通用测试基础框架上。他们参与设计评审，非常近距离地观察代码质量与风险。为了增加可测试性，他们甚至会对代码进行重构，并编写单元测试框架和自动化测试框架。SET 是 SWE 在代码库上的合作伙伴，相比较 SWE 是在增加功能性代码或是提高性能的代码，SET 更加关注于质量提升和测试覆盖率的增加。

#### 1.2.3 测试工程师（TE）

TE（test engineer），是一个和 SET 关系密切的角色，有自己不同的关注点——把用户放在第一位来思考，代表用户的利益。