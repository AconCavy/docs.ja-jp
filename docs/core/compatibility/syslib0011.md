---
title: SYSLIB0011 警告
description: コンパイル時の警告 SYSLIB0011 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2b363e565ce1143c162679c6b74621885378d7ff
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333074"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a>SYSLIB0011:BinaryFormatter は旧型式

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の[セキュリティの脆弱性](../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)により、.NET 5.0 以降、次の API は古いものとしてマークされています。 これらをコードで使用すると、コンパイル時に警告 `SYSLIB0011` が生成されます。

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workaround"></a>回避策

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の代わりに、<xref:System.Text.Json.JsonSerializer> または <xref:System.Xml.Serialization.XmlSerializer> の使用を検討してください。

推奨される操作の詳細については、「[BinaryFormatter の廃止と無効化に関するエラーの解決](https://aka.ms/binaryformatter)」をご覧ください。

## <a name="see-also"></a>関連項目

- [BinaryFormatter の旧型式と無効化に関するエラーの解決](https://aka.ms/binaryformatter)
- [BinaryFormatter シリアル化メソッドが古い形式になり、ASP.NET アプリでは使用不可に](corefx.md#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
