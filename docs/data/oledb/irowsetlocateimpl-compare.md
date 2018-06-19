---
title: IRowsetLocateImpl::Compare | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 208f912e92045daec36066e1dcc06fc38b5a8ed2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105281"
---
# <a name="irowsetlocateimplcompare"></a>IRowsetLocateImpl::Compare
Compare deux signets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (Compare )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="remarks"></a>Notes  
 Une des signets peuvent être une norme définie par OLE DB [signet standard](https://msdn.microsoft.com/en-us/library/ms712954.aspx) (**DBBMK_FIRST**, **DBBMK_LAST**, ou **DBBMK_INVALID**). La valeur retournée dans `pComparison` indique la relation entre les deux signets :  
  
-   **DBCOMPARE_LT** (`cbBookmark1` avant `cbBookmark2`.)  
  
-   **DBCOMPARE_EQ** (`cbBookmark1` est égal à `cbBookmark2`.)  
  
-   **DBCOMPARE_GT** (`cbBookmark1` après `cbBookmark2`.)  
  
-   **DBCOMPARE_NE** (les signets sont égaux, ni classés.)  
  
-   **DBCOMPARE_NOTCOMPARABLE** (les signets ne peuvent pas être comparées).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetLocateImpl, classe](../../data/oledb/irowsetlocateimpl-class.md)