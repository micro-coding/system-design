
# System Design Course

Hey, welcome to the course. I hope this course provides a great learning experience.

_This course is also available on my [website](https://karanpratapsingh.com/courses/system-design) and as an ebook on [leanpub](https://leanpub.com/systemdesign). Please leave a ⭐ as motivation if this was helpful!_

# Table of contents

- **Getting Started**

  - [What is system design?](#what-is-system-design)

- **Chapter I**

  - [IP](#ip)
  - [OSI Model](#osi-model)
  - [TCP and UDP](#tcp-and-udp)
  - [Domain Name System (DNS)](#domain-name-system-dns)
  - [Load Balancing](#load-balancing)
  - [Clustering](#clustering)
  - [Caching](#caching)
  - [Content Delivery Network (CDN)](#content-delivery-network-cdn)
  - [Proxy](#proxy)
  - [Availability](#availability)
  - [Scalability](#scalability)
  - [Storage](#storage)

- **Chapter II**

  - [Databases and DBMS](#databases-and-dbms)
  - [SQL databases](#sql-databases)
  - [NoSQL databases](#nosql-databases)
  - [SQL vs NoSQL databases](#sql-vs-nosql-databases)
  - [Database Replication](#database-replication)
  - [Indexes](#indexes)
  - [Normalization and Denormalization](#normalization-and-denormalization)
  - [ACID and BASE consistency models](#acid-and-base-consistency-models)
  - [CAP theorem](#cap-theorem)
  - [PACELC Theorem](#pacelc-theorem)
  - [Transactions](#transactions)
  - [Distributed Transactions](#distributed-transactions)
  - [Sharding](#sharding)
  - [Consistent Hashing](#consistent-hashing)
  - [Database Federation](#database-federation)

- **Chapter III**

  - [N-tier architecture](#n-tier-architecture)
  - [Message Brokers](#message-brokers)
  - [Message Queues](#message-queues)
  - [Publish-Subscribe](#publish-subscribe)
  - [Enterprise Service Bus (ESB)](#enterprise-service-bus-esb)
  - [Monoliths and Microservices](#monoliths-and-microservices)
  - [Event-Driven Architecture (EDA)](#event-driven-architecture-eda)
  - [Event Sourcing](#event-sourcing)
  - [Command and Query Responsibility Segregation (CQRS)](#command-and-query-responsibility-segregation-cqrs)
  - [API Gateway](#api-gateway)
  - [REST, GraphQL, gRPC](#rest-graphql-grpc)
  - [Long polling, WebSockets, Server-Sent Events (SSE)](#long-polling-websockets-server-sent-events-sse)

- **Chapter IV**

  - [Geohashing and Quadtrees](#geohashing-and-quadtrees)
  - [Circuit breaker](#circuit-breaker)
  - [Rate Limiting](#rate-limiting)
  - [Service Discovery](#service-discovery)
  - [SLA, SLO, SLI](#sla-slo-sli)
  - [Disaster recovery](#disaster-recovery)
  - [Virtual Machines (VMs) and Containers](#virtual-machines-vms-and-containers)
  - [OAuth 2.0 and OpenID Connect (OIDC)](#oauth-20-and-openid-connect-oidc)
  - [Single Sign-On (SSO)](#single-sign-on-sso)
  - [SSL, TLS, mTLS](#ssl-tls-mtls)

- **Chapter V**

  - [System Design Interviews](#system-design-interviews)
  - [URL Shortener](#url-shortener)
  - [WhatsApp](#whatsapp)
  - [Twitter](#twitter)
  - [Netflix](#netflix)
  - [Uber](#uber)

- **Appendix**

  - [Next Steps](#next-steps)
  - [References](#references)

# 系统设计是什么?

在我们开始本课程之前，让我们先谈谈系统设计是什么。

系统设计是为满足特定需求的系统定义架构、接口和数据的过程。系统设计通过连贯高效的系统满足您的业务或组织的需求。它要求我们采用系统的方式构建和管理系统。良好的系统设计要求我们考虑一切，从基础设施一直到数据以及数据的存储方式。

## 为什么系统设计如此重要?

系统设计可帮助我们定义满足业务要求的解决方案。它是我们建立系统时可以做出的最早的决定之一。通常，必须从高层次考虑这些决定，因为日后很难修改。它也使得在系统演化过程中更容易推理和管理架构变化。

# IP

IP 地址是一个唯一地址，用于标识互联网或本地网络上的设备。IP 代表“互联网协议”，它是控制通过互联网或本地网络发送的数据格式的一组规则。
一个IP地址是一个唯一的地址，用于标识互联网或局域网上的设备。

本质上，IP 地址是允许在网络上的设备之间发送信息的标识符：它们包含位置信息，并使设备可进行通信。互联网需要一种区分不同计算机、路由器和网站的方法。IP 地址提供了一种实现此目标的方式，并且是互联网工作原理中的关键组成部分。

## 版本

现在，让我们了解一下IP地址的不同版本。

### IPv4

最初的互联网协议是 IPv4，其 IP 地址是一个32 位的二进制数，通常用点分十进制表示。它允许大约 40 亿个 IP 地址，起初，它绰绰有余。然而，随着互联网应用的增长，这些地址已经被分配殆尽，我们需要更好的解决方案。

_例如: `102.22.192.181`_

### IPv6

IPv6 是 1998 年推出的一个新协议。2000 年代中期开始商用，由于互联网用户成倍增长，协议目前仍在完善中。

这个新协议使用 128 位二进制数代表 IP 地址，采用冒号分十六进制格式表示。这意味着 IPv6 可以提供大约 ~340e+36 个 IP 地址。这足以满足未来几年不断增长的需求。

_例如: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`_

## 类型

我们来讨论一下 IP 地址的类型：

### 公共

公共 IP 地址是与整个网络关联的主要地址。在此类型的IP地址中，每个连接的设备都具有相同的IP地址。
_例如：由 ISP 提供给路由器的IP地址。_

### 私有

私有IP地址是分配给连接到家庭互联网的每台设备的唯一IP地址，其中包括家庭中使用的计算机，平板电脑，智能手机等设备。

_例如：由家庭路由器生成的 IP 地址。_

### 静态

静态 IP 地址不会更改，通常为手动创建，而不是自动分配。静态 IP 地址往往更加昂贵但也更加可靠。

_例如: 通常用于地理位置服务、远程访问、服务器托管等重要场景。_

### 动态

动态 IP 地址会不时更改。它由动态主机配置协议（DHCP）服务器分配。动态IP地址是最常见的互联网协议地址类型。它们的部署成本较低，允许我们根据需要在网络中重复使用 IP 地址。

_例如: 常用于消费类设备和个人使用。_

# OSI 模型

开放式系统互联模型（英语：Open System Interconnection Model，缩写：OSI；简称为OSI模型）是一种网络通信概念模型，它定义了系统间如何互连和通信。OSI模型还定义了一个逻辑网络，通过各种协议层有效地描述了计算机数据包传输。

OSI 模型可以被看作是计算机网络的通用语言。它基于将通信系统分为七个抽象层，逐层堆叠而成的概念。

## 为什么 OSI 模型很重要?

开放系统互联（OSI）模型定义了在网络讨论和文档中使用的通用术语。这使我们能够拆分一个非常复杂的通信过程并评估其组件。

虽然这个模型没有在如今最常见的 TCP/IP 网络中直接实现，但它仍然可以帮到我们很多，例如：

- 使故障诊断更容易，并帮助识别整个协议栈中的威胁。
- 鼓励硬件制造商开发可在网络上彼此通信的网络产品。
- 对于培养安全第一的思维方式至关重要。
- 将复杂的功能分解成更简单的组件。

## Layers

OSI 模型的七个抽象层定义如下，从上到下依次是：

![osi-model](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/osi-model/osi-model.png)

### 应用层(Application)

应用层是唯一直接与用户数据交互的层。Web 浏览器和电子邮件客户端等软件应用程序依赖于应用程序层来发起通信。但应该明确的是，客户端软件应用程序不是应用层的一部分；相反，应用层负责软件依赖的协议和数据操作，以向用户呈现有意义的数据。应用层协议包括​​HTTP​​和 SMTP（简单邮件传输协议是实现电子邮件通信的协议之一）。

### 表现层(Presentation)

表现层也被称为翻译层。来自应用层的数据在这里被提取出来，并按照要求的格式进行处理，以便在网络上传输。表现层的功能是翻译、加密/解密和压缩。

### 会话层(Session)

这是负责打开和关闭两个设备之间的通信的层。通信打开和关闭之间的时间称为会话。会话层确保会话保持打开足够长的时间以传输所有正在交换的数据，然后及时关闭会话以避免浪费资源。会话层还将数据传输与检查点同步。

### 传输层(Transport)

传输层负责两个设备之间的端到端通信。这包括从会话层获取数据，并将其分解为称为段的块，然后再将其发送到网络层。接收设备上的传输层负责将这些段重新组装成会话层可以使用的数据。

传输层还负责流量控制和错误控制。流量控制确定最佳传输速度，以确保具有快速连接的发送方不会压倒具有慢速连接的接收方。传输层对接收端执行错误控制，确保接收到的数据是完整的，如果不是，则请求重传。

### 网络层(Network)

网络层负责促进两个不同网络之间的数据传输。网络层在发送方设备上将传输层的数据段分解成较小的单元，称为数据包，并在接收设备上重新组装这些数据包。网络层还为数据找到到达目的地的最佳物理路径，这被称为路由。如果通信的两个设备是在同一个网络上，那么网络层就没有必要。

### 数据链路层(Data Link)

数据链路层与网络层非常相似，除了数据链路层促进了是同一网络上两个设备之间的数据传输。数据链路层从网络层获取数据包，并将其分成较小的片段，称为帧。

### 物理层(Physical)

该层包括参与数据传输的物理设备，如电缆和交换机。这也是数据被转换为比特流的一层，比特流是一串 1 和 0 。两个设备的物理层还必须就信号约定达成一致，以便在两个设备上区分 1 和 0。

# TCP 和 UDP

## TCP

传输控制协议（ransmission Control Protocol，简称 TCP 协议）是面向连接的，这意味着一旦建立了连接，数据就可以在两个方向上传输。TCP具有内置系统来检查错误并保证数据按发送顺序交付，这使其成为传输图像，文件和网页等信息的完美协议。

![tcp](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/tcp-and-udp/tcp.png)

TCP 协议本质上是可靠的，但其反馈机制也会导致更大的开销，进而占用更多的网络可用带宽。

## UDP

用户数据报协议（User Datagram Protocol，简称 UDP 协议）是一种无连接的传输层协议。UDP 假定错误检查和更正在应用程序中并不重要，所以，UDP 虽然提供数据完整性的校验，但是不提供校正错误的机制。数据被不断发送给接收者，无论他们是否收到。

![udp](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/tcp-and-udp/udp.png)

UDP 协议主要用于实时通信，如广播或多播网络传输。当我们需要最低延迟且数据延迟比数据丢失更糟糕时，应该使用 UDP 而不是 TCP。

## TCP vs UDP

TCP 是一种面向连接的协议，而 UDP 是一种无连接协议。TCP 比 UDP 要慢，这是两种协议的主要区别之一。总的来说，UDP 是一种更快、更简单、更高效的协议。但是只有 TCP 允许对丢失的数据包进行重新传输。

TCP 和 UDP 的另一个区别是 TCP 可以确保数据的有序传输。UDP 不是为端到端通信而设计的，并不会检查接收方的就绪情况，因此它需要相对更少的开销。

| 特性     | TCP                              | UDP                             |
| -------- | -------------------------------- | ------------------------------- |
| 连接     | 需要已建立的连接                 | 无连接的协议                    |
| 保证传输 | 可以保证数据的送达               | 无法保证数据的送达              |
| 重传机制 | 可以重传丢失的数据包             | 不能重传丢失的数据包            |
| 速度     | 比UDP慢                          | 比TCP快                         |
| 广播     | 不支持                           | 支持                            |
| 应用场景 | HTTPS, HTTP, SMTP, POP, FTP, etc | Video streaming, DNS, VoIP, etc |

# Domain Name System （DNS）

在之前，我们学习了能使机器与其他机器相连接的 IP 地址。但正如我们所知，人类更容易记住名字，而不是数字。举个例子，我们更容易记住 `google.com` 而不是 `122.250.192.232`。

因此，这就有了域名系统（Domain Name System，简称 DNS）。它是一个分层的、分散的命名系统，用于将人能够阅读的域名翻译成 IP 地址。

## DNS 如何工作的

![how-dns-works](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/domain-name-system/how-dns-works.png)

DNS查询包括以下八个步骤。

1. 用户在浏览器中输入  [example.com](http://example.com)，该查询被传送到互联网并被 DNS 解析器接收。
2. DNS 解析器向根域名服务器发送请求。
3. 根域名服务器返回 `.com` 顶级域名服务器(TLD 服务器)的 IP 地址。
4. DNS 解析器向 `.com` 顶级域名服务器发送请求。
5. 顶级域名服务器返回 [example.com](http://example.com) 权威域名服务器的 IP 地址。
6. DNS 解析器向权威域名服务器发送请求。
7. 权威域名服务器返回 [example.com](http://example.com) 的 IP 地址。
8. DNS 解析器响应 web 浏览器的请求，返回请求域名的 IP 地址。

一旦IP地址被解析，客户端就能够从获得的 IP 地址请求内容。例如，向浏览器返回一个网页。

## 服务器类型

现在，让我们看看组成 DNS 基础设施的四类关键服务器。

### DNS 解析器（DNS resolver）

DNS 解析器（也称为 DNS 递归解析器）是 DNS 查询中的第一站。递归解析器作为客户端与 DNS 域名服务器的中间人。从 Web 客户端收到 DNS 查询后，递归解析器将使用缓存的数据进行响应，或者将向根域名服务器发送请求，接着向 TLD 域名服务器发送另一个请求，然后向权威性域名服务器发送最后一个请求。收到来自包含已请求 IP 地址的权威性域名服务器的响应后，递归解析器将向客户端发送响应。

### DNS 根域名服务器（DNS root server）

根服务器接受包含域名的递归解析器的查询，根域名服务器根据该域的扩展名（.com、.net、.org 等），通过将递归解析器定向到 TLD 域名服务器进行响应。根域名服务器由一家名为 Internet 名称与数字地址分配机构(ICANN) 的非营利组织进行监督。

每个递归解析器都知道 13 个 DNS 根域名服务器，注意，尽管有 13 个根域名服务器，但这并不意味着根域名服务器系统中只有 13 台计算机。根域名服务器有 13 种类型，但在世界各地每个类型都有多个副本，它们使用 [Anycast 路由](https://en.wikipedia.org/wiki/Anycast)来提供快速响应。

### TLD 域名服务器（TLD nameserver）

TLD 域名服务器维护共享通用域扩展名的所有域名的信息，例如 .com、.net 或 url 中最后一个点之后的任何内容。

TLD 域名服务器的管理由 [Internet 编号分配机构（IANA）](https://www.iana.org) 加以处理，其为 ICANN 的一个分支机构。IANA 将 TLD 服务器分为两个主要组：

- **通用顶级域**：这些是非特定国家/地区的域，一些最知名的通用 TLD 包括 .com、.org、.net、.edu 和 .gov。
- **国家/地区代码顶级域**：这些包括特定于某个国家/地区或州的任何域。例如，uk、.us、.ru 和 .jp 等。

### 权威性域名服务器（Authoritative DNS server）

权威性域名服务器通常是解析器查找 IP 地址过程中的最后一步。权威名称服务器包含特定于其服务域名的信息（例如，google.com）权威性域名服务器包含特定于其所服务的域名的信息（例如 google.com），并且它可为递归解析器提供在 DNS A 记录中找到的服务器的 IP 地址，或者如果该域具有 CNAME 记录（别名），它将为递归解析器提供一个别名域，这时递归解析器将必须执行全新 DNS 查找，以便从权威性域名服务器获取记录（通常为包含 IP 地址的 A 记录）。如果它不能找到该域名，则返回 NXDOMAIN 消息。

## 查询类型

在一个DNS系统中，有三种类型的查询。

### 递归

在递归查询中，DNS 客户端要求 DNS 服务器（通常是 DNS 递归解析器）使用请求的资源记录或错误消息（如果找不到记录）响应客户端。

### 迭代

在迭代查询中，DNS 客户端提供一个主机名，而 DNS 解析器则返回它所能提供的最佳答案。如果 DNS 解析器在其缓存中拥有相关的 DNS 记录，它将返回这些记录。如果没有，它就会向 DNS 客户端返回 DNS 根服务器或另一个离所需 DNS 区域最近的权威名称服务器。然后，DNS 客户端对它被推荐的 DNS 服务器重新查询。

### 非递归

非递归查询是指 DNS 解析器已经知道答案的查询。如果它已经在本地缓存中存储了 DNS 记录，则立即返回一个 DNS 记录。否则，查询一个 DNS 名称服务器，该服务器是此记录的权威服务器，这意味着它绝对持有该主机名的正确 IP。在这两种情况下，无需进行额外的查询（如递归或迭代查询）。相反，立即向客户端返回响应。

## DNS 记录

DNS 记录（又名区域文件）是位于权威 DNS 服务器中的指令，提供一个域的相关信息，包括哪些 IP 地址与该域关联，以及如何处理对该域的请求。

这些记录由一系列以所谓的 DNS 语法编写的文本文件组成。DNS 语法是用作命令的字符串，这些命令告诉 DNS 服务器执行什么操作。此外，所有 DNS 记录都有一个 _"TTL"_，其代表生存时间，指示 DNS 服务器多久刷新一次该记录。

常见的 DNS 记录：

- **A 记录 (Address record)**：保存域的 IP 地址的记录。
- **AAAA 记录(Canonical Name record)**： 包含域的 IPv6 地址的记录（与 A 记录相反，A 记录列出的是 IPv4 地址）。
- **CNAME 记录(Canonical Name record)**： 将一个域或子域转发到另一个域，不提供 IP 地址。
- **MX 记录 (Mail exchanger record)**： 将邮件定向到电子邮件服务器。
- **TXT 记录(Text Record)**： 可让管理员在记录中存储文本注释。这些记录通常用于电子邮件安全。
- **NS 记录(Text Record)**： 存储 DNS 条目的名称服务器。
- **SOA 记录(Start of Authority)**： 存储域的管理信息。
- **SRV 记录(Service Location record)**： 指定用于特定服务的端口。
- **PTR 记录(Reverse-lookup Pointer records)**： 在反向查询中提供域名。
- **CERT 记录 (Certificate record)**： "证书记录"，存储公钥证书。

## 子域名

子域名是主域的扩展，它通常用于在逻辑上将一个网站分成几个部分。我们可以在主域上创建多个子域。

例如，`blog.example.com`，其中 `blog` 是子域，`example` 是主域，`.com` 是顶级域（TLD）。类似的例子可以是 `support.example.com` 或 `careers.example.com`。
