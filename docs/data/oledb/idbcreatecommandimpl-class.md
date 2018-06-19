---
title: Idbcreatecommandimpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cc032a488626f2d366152f2d2b70b2539b9137b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101524"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl, classe
Fournit une implémentation de la [IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Dérivé de l’objet de session `IDBCreateCommandImpl`.  
  
 `CommandClass`  
 Votre classe de commande.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[CreateCommand](../../data/oledb/idbcreatecommandimpl-createcommand.md)|Crée une nouvelle commande.|  
  
## <a name="remarks"></a>Notes  
 Une interface facultative sur l’objet de session pour obtenir une nouvelle commande.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)