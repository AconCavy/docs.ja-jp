---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: b5ca524d223fad7ded0d56def3293eb40be69fa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703721"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド

指定されたメモリ領域を列挙しようとした結果をデバッガーに報告するために、 [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) によって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `address`  
 から列挙されたメモリ領域の開始アドレス。  
  
 `size`  
 からメモリ領域のサイズ (バイト単位)。  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `ICLRDataEnumMemoryRegions::EnumMemoryRegions` メモリ領域を列挙するたびに、このコールバックメソッドを呼び出します。 このメソッドがエラーを示す HRESULT を返す場合でも、列挙は続行されます。  
  
 このコールバックによって報告されたリージョンが重複しているか、重複している可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataEnumMemoryRegionsCallback インターフェイス](iclrdataenummemoryregionscallback-interface.md)
