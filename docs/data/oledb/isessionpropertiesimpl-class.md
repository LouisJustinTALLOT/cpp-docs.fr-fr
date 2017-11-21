---
title: Isessionpropertiesimpl, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ISessionPropertiesImpl
dev_langs: C++
helpviewer_keywords: ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8824ac2081ffd214402a23c6a5975e027ecf9ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl, classe
Fournit une implémentation de la [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `ISessionPropertiesImpl`.  
  
 `PropClass`  
 Une classe de propriété définis par l’utilisateur par défaut est `T`.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|Retourne la liste des propriétés dans le groupe de propriétés de Session qui sont actuellement définies sur la session.|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|Définit les propriétés dans le groupe de propriétés de Session.|  
  
## <a name="remarks"></a>Remarques  
 Une interface obligatoire sur les sessions. Cette classe implémente les propriétés d’une session en appelant une fonction statique définie par le [propriété mappage](../../data/oledb/begin-propset-map.md). Le mappage d’ensemble de propriété doit être spécifié dans votre classe session.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)