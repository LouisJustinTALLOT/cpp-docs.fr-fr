---
title: ICommandImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandImpl class
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d69ff56ec92fd3acb622aa4c0399893fb44c4d1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101141"
---
# <a name="icommandimpl-class"></a>ICommandImpl, classe
Fournit l’implémentation pour la [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `ICommandImpl`.  
  
 `CommandBase`  
 Une interface de commande. La valeur par défaut est `ICommand`.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|Annule l’exécution de la commande actuelle.|  
|[Annuler](../../data/oledb/icommandimpl-cancel.md)|Annule l’exécution de la commande actuelle.|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|Crée un objet d’ensemble de lignes.|  
|[Exécuter](../../data/oledb/icommandimpl-execute.md)|Exécute la commande.|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|Retourne un pointeur d’interface à la session qui a créé la commande.|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|Constructeur.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|Indique si la commande doit être annulée.|  
|[m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|Indique si la commande doit être annulée lors de l’exécution.|  
|[m_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|Indique si la commande est en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
 Une interface obligatoire sur l’objet de commande.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)