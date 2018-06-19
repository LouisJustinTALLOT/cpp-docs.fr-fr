---
title: IRowsetCreatorImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0492994193130ffa6a547691490b4da1ae557c8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102135"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl, classe
Exécute les mêmes fonctions que `IObjectWithSite` mais permet également de propriétés OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une classe dérivée de **IRowsetCreator**.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|Définit le site qui contient l’objet d’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 Cette classe hérite de [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) et remplacements [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). Lorsqu’un objet de commande ou de la session du fournisseur crée un ensemble de lignes, il appelle `QueryInterface` sur l’objet d’ensemble de lignes recherchez `IObjectWithSite` et appelle `SetSite` en passant l’objet de l’ensemble de lignes **IUnkown** interface en tant que l’interface du site.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)