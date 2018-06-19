---
title: ICommandTextImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f49326dba4868ad490dc1a7122eed68271bdfa15
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100198"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl, classe
Fournit une implémentation pour la [ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Dérivé de la classe de commande **ICommandTextImpl**.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|Retourne la commande de texte définie par le dernier appel à [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|Définit le texte de commande, en remplaçant le texte de commande existant.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|Stocke le texte de commande.|  
  
## <a name="remarks"></a>Notes  
 Une interface obligatoire sur les commandes.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** altdb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)