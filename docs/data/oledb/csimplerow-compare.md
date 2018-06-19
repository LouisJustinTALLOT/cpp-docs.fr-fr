---
title: CSimpleRow::Compare | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75d79e753f1f4af630c26ef07fbb7241576535ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098963"
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
Compare deux lignes pour voir s’ils font référence à la même instance de ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Compare(CSimpleRow* pRow);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRow`  
 Un pointeur vers un `CSimpleRow` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Un `HRESULT` valeur généralement `S_OK`, indiquant les deux lignes sont la même instance de ligne, ou **S_FALSE**, indiquant les deux lignes sont différentes. Consultez [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) dans les *de référence du programmeur OLE DB* pour d’autres valeurs de retournés possibles.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [CSimpleRow (classe)](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)