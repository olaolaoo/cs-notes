# Yarn 资源调度器

## Yarn 基础架构

ResourceManager--资源控制老大

NodeManager--每个节点的老大

ApplicationMaster--每个job的老大

Container--Container 是 YARN 中的 资源 抽象，它封装了某个节点上的多 维度资源，如内存、 CPU、磁盘、 网络等。

## Yarn 工作机制（面试）