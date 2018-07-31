---
title: Irowsetidentityimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 55c9b4b7e14a9572f5a8922b65a41a9a92a0d688
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337707"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl, classe
Implémente la norme OLE DB [IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx) interface, ce qui permet de tester pour l’identité de ligne.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Une classe dérivée de `IRowsetIdentityImpl`.  
  
 *RowClass*  
 L’unité de stockage pour le `HROW`.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[IsSameRow](#issamerow)|Compare deux handles de ligne pour voir si elles font référence à la même ligne.|  
  
## <a name="issamerow"></a> IRowsetIdentityImpl::IsSameRow
Compare deux handles de ligne pour voir si elles font référence à la même ligne.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/library/ms719629.aspx) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  
 Pour comparer les handles de ligne, cette méthode convertit le `HROW` gère à `RowClass` membres et appelle `memcmp` sur les pointeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)