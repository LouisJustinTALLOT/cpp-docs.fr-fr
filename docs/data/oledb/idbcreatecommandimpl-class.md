---
title: Idbcreatecommandimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b06d6c730562203cdef1191a9d73012c3b19c2c8
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083961"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl, classe

Fournit une implémentation de la [IDBCreateCommand](/previous-versions/windows/desktop/ms711625) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>Paramètres  

*T*<br/>
Dérivé de l’objet de session `IDBCreateCommandImpl`.  
  
*CommandClass*<br/>
Votre classe de commande.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[CreateCommand](#createcommand)|Crée une nouvelle commande.|  
  
## <a name="remarks"></a>Notes  

Une interface facultative sur l’objet de session pour obtenir une nouvelle commande.  

## <a name="createcommand"></a> IDBCreateCommandImpl::CreateCommand

Crée une nouvelle commande et retourne l’interface demandée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772) dans le *de référence du programmeur OLE DB*.  
  
Certains paramètres correspondent aux *de référence du programmeur OLE DB* des noms différents, qui sont décrites dans les paramètres `IDBCreateCommand::CreateCommand`:  
  
|Paramètres de modèle OLE DB|*Référence du programmeur OLE DB* paramètres|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)