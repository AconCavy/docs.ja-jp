---
title: AssemblyOptions 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: 352e1acd1fdd8297754e18b2e8c6448ea723a557
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717032"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions 列挙体

アセンブリオプションを列挙します。  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>フィールド  
  
|フィールド|説明|  
|-----------|-----------------|  
|optAssemTitle|String-アセンブリのタイトルを表します。|  
|optAssemDescription|String-アセンブリの説明が含まれています。|  
|optAssemConfig|String-アセンブリ構成が含まれています。|  
|optAssemOS|"DwOSPlatformId" としてエンコードされた文字列。|  
|optAssemProcessor|ULONG|  
|optAssemLocale|String-アセンブリロケールを格納します。|  
|optAssemVersion|"Major. Minor. Build. Revision" としてエンコードされた文字列。|  
|optAssemCompany|文字列-会社を含みます。|  
|optAssemProduct|文字列-製品名が含まれます。|  
|optAssemProductVersion|文字列 (InformationalVersion とも呼ばれます)。|  
|optAssemCopyright|文字列-著作権情報が含まれています。|  
|optAssemTrademark|String-商標情報が含まれています。|  
|optAssemKeyFile|文字列 (ファイル名)。|  
|optAssemKeyName|文字列 (キー名)。|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (DelaySign とも呼ばれます)。|  
|optAssemFileVersion|"Major. Minor. Build. Revision" としてエンコードされた文字列。 ProductVersion と同じです。|  
|optAssemSatelliteVer|"Major. Minor. Build. Revision" としてエンコードされた文字列。|  
|optlastassemoopt|要素数のカウンター。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** alink  
  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目

- [Al.exe (アセンブリ リンカー)](../../tools/al-exe-assembly-linker.md)
