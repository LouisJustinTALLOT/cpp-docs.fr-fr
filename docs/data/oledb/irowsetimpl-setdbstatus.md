---
title: IRowsetImpl::SetDBStatus | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
dev_langs:
- C++
helpviewer_keywords:
- SetDBStatus method
ms.assetid: b73f526a-4fc6-4adb-9611-c3cca2cddb23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e6e07b6fe1a45a779c5ffe1e1afffaabdcb6d34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103900"
---
# <a name="irowsetimplsetdbstatus"></a>IRowsetImpl::SetDBStatus
Définit le `DBSTATUS` indicateurs d’état pour le champ spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnInfo);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `statusFlags`  
 Le [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) indicateurs à définir pour la colonne.  
  
 `currentRow`  
 La ligne actuelle.  
  
 *columnInfo*  
 La colonne pour laquelle l’état est défini.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Le fournisseur substitue cette fonction pour fournir un traitement spécial pour **DBSTATUS_S_ISNULL** et **DBSTATUS_S_DEFAULT**.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetImpl, classe](../../data/oledb/irowsetimpl-class.md)