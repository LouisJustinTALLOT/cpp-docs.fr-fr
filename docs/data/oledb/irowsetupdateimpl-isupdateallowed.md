---
title: IRowsetUpdateImpl::IsUpdateAllowed | Documents Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs:
- C++
helpviewer_keywords:
- IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 363626cedddea3da57e829a43c21c63b5c2b05cd
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122002"
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
Substituez cette méthode pour contrôler la sécurité, l’intégrité, et ainsi de suite avant les mises à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *status*  
 [in] L’état des opérations sur les lignes en attente.  
  
 *hRowUpdate*  
 [in] Handle pour les lignes que l’utilisateur veut mettre à jour.  
  
 *pRowStatus*  
 [out] L’état renvoyé à l’utilisateur.  
  
## <a name="remarks"></a>Notes  
 Si vous déterminez qu’une mise à jour doit être autorisé, retourne `S_OK`; sinon, retourne **E_FAIL**. Si vous autorisez une mise à jour, vous devez également définir le **DBROWSTATUS** dans [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) aux [état de la ligne](https://msdn.microsoft.com/en-us/library/ms722752.aspx).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetUpdateImpl, classe](../../data/oledb/irowsetupdateimpl-class.md)