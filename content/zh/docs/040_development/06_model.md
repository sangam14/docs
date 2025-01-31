---
title: "资源模型"
weight: 6
description:
  介绍Cloudpods的资源模型
---

云平台的资源大概分为 **"虚拟资源"** 和 **"基础设施"** 两类，有了基础设施类型的资源才能在其之上构建虚拟化的资源，具体分类如下:

- infra: 表示基础设施类型
- virtual: 表示虚拟资源类型，属于具体的项目

| 名称         | 抽象资源                 | 作用                                          | 类型    |
|--------------|--------------------------|-----------------------------------------------|---------|
| cloudregion  | 云平台地域               | 标记数据中心所在地域                          | infra   |
| zone         | 云平台数据中心           | 标记数据中心                                  | infra   |
| vpc          | 逻辑隔离网络空间         | 抽象虚拟化网络的集合                          | infra   |
| wire         | 对应二层扁平网络的广播域 | 抽象二层扁平网络广播域                        | infra   |
| storage      | 存储                     | 标记存储，提供云硬盘能力                      | infra   |
| host         | 服务器                   | 标记服务器，提供计算虚拟化                    | infra   |
| server       | 云主机                   | 运行在 host 上，使用虚拟化技术提供计算能力    | virtual |
| disk         | 云硬盘                   | 创建在 storage 上，使用虚拟化技术提供存储能力 | virtual |
| network      | 网络                     | 创建在 vpc 中，使用虚拟化技术提供网络         | virtual |
| image        | 镜像                     | 安装了操作系统的虚拟机磁盘，也属于 disk 一类  | virtual |
| eip          | 外网浮动 ip              | 对应外网可用 ip                               | virtual |
| loadbalancer | 负载均衡器               | 标记负载均衡器，提供服务负载均衡              | virtual |

除了上面介绍的常见资源外，为了做多云管理，我们还引入了以下的概念:

| 名称         | 资源         | 作用                               | 类型  |
|--------------|--------------|------------------------------------|-------|
| cloudaccount | 云平台的账户 | 对应各个云平台的认证信息           | infra |
| project      | 项目         | Cloudpods 内部对虚拟机资源的划分    | infra |
| schedtag     | 调度标签     | 可以标记多种资源，提供资源调度能力 | infra |
| sku          | 套餐信息     | 对应创建虚拟资源的规格信息         | infra |
