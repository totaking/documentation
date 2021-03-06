---
title:
keywords: sample homepage
sidebar: DID_zh
permalink: ontology_DID_zh.html
folder: doc_zh/DID
giturl: https://github.com/ontio/ontology-DID/blob/master/README_cn.md
---

[English](./ontology_DID_en.html) / 中文


<h1 align="center">本体分布式身份框架(ONTID)  </h1>
<p align="center" class="version">Version 0.7.0 </p>

## 为什么需要去中心化身份

美国时间2018年3月18日，美国社交媒体巨头Facebook被爆出超过5000万用户信息数据被泄露。3月27日，Facebook CEO扎克伯格在多家报纸上刊登文章，进行公开道歉，表示“辜负了用户的信任”。他说：“我们有责任保护你们的信息，如果我们不能，我们也不配，这是一种违背信任的行为，我很抱歉我们当时没有做更多的事情。” 
显然，Facebook信息泄露丑闻只是问题的一次集中爆发。对于公众而言，扎克伯格的道歉更多是情感的表达，更需要的是通过法律、技术等方式来保护用户的数据隐私，保护健康的网络公共领域环境。

## ONT ID 是什么？

ONT ID为每个用户，公司，物品等任何实体建立基于密码学的数字身份，数字身份基于本体区块链技术，不受制于任何中心化机构，完全由用户自己掌控，并具有安全、可信的特点。

你第一次拥有了基于区块链的数字身份 ONT ID。为了让你的ONT ID 更可信，更多源，你可以通过不同领域的信任源对ONT ID进行认证和背书，如eID、CA、政府、机构、学校、公司、社群、个人等等。认证授权后，你将拥有不同身份信任源的区块链证书（即区块链可信声明）。
![](https://github.com/ontio/ontology-DID/raw/master/images/ontid.jpg)


## 为什么需要集成ONT ID

* 强大的本体信任网络

本体的信任生态已经连接了覆盖全球的信任锚（TrustAnchor），可以对ONT ID进行认证，建立多维度的可信证书，从而可以帮助用户证明自己的身份。了解本体[>> 信任锚](https://info.ont.io/trust-anchor/en)。

* 用户隐私保护

我们使用多种方法帮助用户保护隐私。首先ONT ID为每个人/机构生成公钥等完整属性信息（称之为：DDO），并将这些信息登记到区块链，只有拥有私钥的拥有者才可以控制。出于隐私保护的考虑，区块链上的DDO不包含任何实体真实身份相关的明文，而是采用HASH算法或其他加密算法生成的密文。ONT ID还采用了零知识证明协议和C-L签名算法来保护用户的隐私，数据所有者可指定特定的数据进行开放，使数据的开放和提供增强针对性和匹配性。比如说，某交易所希望证明用户的中国中国公民身份和年收入大于300,000的证明，用户无需提供身份证照片和银行流水信息，而是说，提供一个Y/N的可信证明结果，大大降低用户隐私暴露风险。


## 工作原理

在使用ONT ID之前，您可以先大致了解ONT ID的工作原理。

在整个ONT ID使用和协作过程中,会包括以下参与角色.

* **用户Recipient** ONT ID的持有者,可以接受Verifier签发的可信声明,也可以为他人签发可信声明。 

* **声明发行方 Claim Issuer** 可以是本体生态的任何一个ONT ID持有者，其中包括本体生态上的信任锚（提供认证服务的合作方），其可能是政府机关、大学、银行、第三方认证服务机构（比如CA机构）、生物识别科技公司等等，这些企业为本体ONT ID的持有者（Owner）提供多维度的认证，并第一时间通过Ontology BlockChain来记录认证行为和认证结果HASH，从而为用户认证需求方/场景方提供了标准化、可信的认证方式。

* **声明验证方 Claim Verifier** 接受用户可信声明,并进行验证的场景,比如需要验证面试者的身份信息/学历/行业技能等雇主.

* **应用开发者 Developer** 基于ONT ID协议和接口为用户和各种场景提供各种应用开发服务。

![](https://github.com/ontio/ontology-DID/raw/master/images/claim_workflow_cn.png)

## 开始使用

进入 [>>快速开发指南](https://github.com/ontio/ontology-DID/blob/master/docs/cn/get_started_cn.html)开始使用。

## 了解ONT ID协议

ONT ID协议体系包括两个部分，身份标识协议（Ontology DID）和可信声明协议（Verifiable Claim Protocol）。

Ontology DID是一个去中心化的身份标识协议，基于[W3C](https://www.w3.org/2017/vc/WG/)的[DID规范](https://w3c-ccg.github.io/did-spec/)。本体ONT ID基于这个协议来标识和管理链上的数字身份。[>> 详细了解身份标识协议](./docs/cn/ONTID_protocol_spec_cn.md)

可信声明(Verifiable Claim)是指，一个实体对另一个实体（包括自己）的某些属性作出的描述性声明，并附加自己的数字签名，用以证明这些属性的真实性，可被其他实体验证。可验证声明协议详细描述了声明的签发、存储、验证等流程及规范。本体可验证声明协议建立去中心化的信任模型和分布式信任传递体系，同时引入C-L签名算法、西格玛协议等密码学技术来实现可验证声明的隐私保护。
[>> 详细了解可信声明协议](./docs/cn/claim_spec_cn.md)

## 信任锚

信任锚Trust Anchor是指在本体生态上提供认证服务的合作方，其可能是政府机关、大学、银行、第三方认证服务机构（比如CA机构）、生物识别科技公司等等，我们欢迎加入本体生态，共建新一代分布式信任链网。

希望成为信任锚，[这里](https://info.ont.io/cooperation/zh)申请加入。

如果您是信任锚，请进入[>> 本体信任锚接入标准](./verification_provider_specification_zh.html)了解接入流程和标准。
