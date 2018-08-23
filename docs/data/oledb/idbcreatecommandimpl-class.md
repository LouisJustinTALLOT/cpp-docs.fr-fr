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
ms.openlocfilehash: 8b67fc55a8af2bed554254732832cbd6486d2420
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572650"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl, classe
Fournit une implémentation de la [IDBCreateCommand](/previous-versions/windows/desktop/ms711625\(v=vs.85\)) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Dérivé de l’objet de session `IDBCreateCommandImpl`.  
  
 *CommandClass*  
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
 Consultez [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
 Certains paramètres correspondent aux *de référence du programmeur OLE DB* des noms différents, qui sont décrites dans les paramètres `IDBCreateCommand::CreateCommand`:  
  
|Paramètres de modèle OLE DB|*Référence du programmeur OLE DB* paramètres|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)