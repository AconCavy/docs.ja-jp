---
title: IMetaDataImport::GetFieldProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 462512fd2c2b33905b45bb67599b23b301fc71f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437995"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="1dd49-102">IMetaDataImport::GetFieldProps メソッド</span><span class="sxs-lookup"><span data-stu-id="1dd49-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="1dd49-103">指定した FieldDef トークンによって参照されるフィールドに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="1dd49-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd49-104">構文</span><span class="sxs-lookup"><span data-stu-id="1dd49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd49-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1dd49-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="1dd49-106">から関連付けられたメタデータを取得する対象のフィールドを表す FieldDef トークン。</span><span class="sxs-lookup"><span data-stu-id="1dd49-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="1dd49-107">入出力フィールドが属するクラスの型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1dd49-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="1dd49-108">入出力フィールドの名前。</span><span class="sxs-lookup"><span data-stu-id="1dd49-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="1dd49-109">から*Szfield*のバッファーのサイズ (ワイド文字単位)。</span><span class="sxs-lookup"><span data-stu-id="1dd49-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="1dd49-110">入出力返されたバッファーの実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1dd49-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="1dd49-111">入出力フィールドのメタデータに関連付けられているフラグ。</span><span class="sxs-lookup"><span data-stu-id="1dd49-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="1dd49-112">からフィールドを説明するバイナリメタデータ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1dd49-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="1dd49-113">入出力`ppvSigBlob`のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="1dd49-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="1dd49-114">入出力フィールドの値の型を指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="1dd49-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1dd49-115">入出力フィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="1dd49-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="1dd49-116">入出力`ppValue`の文字数のサイズ。文字列が存在しない場合は0。</span><span class="sxs-lookup"><span data-stu-id="1dd49-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd49-117">要件</span><span class="sxs-lookup"><span data-stu-id="1dd49-117">Requirements</span></span>  
 <span data-ttu-id="1dd49-118">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dd49-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd49-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1dd49-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dd49-120">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1dd49-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd49-121">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd49-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd49-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dd49-122">See also</span></span>

- [<span data-ttu-id="1dd49-123">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1dd49-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1dd49-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1dd49-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
