---
title: Irowsetinfoimpl, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 659d3d55635f957ffab2893f2a042564d62abad1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl, classe
Fournit une implémentation pour la [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IRowsetInfoImpl`.  
  
 `PropClass`  
 Une classe de propriété définis par l’utilisateur par défaut est `T`.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)|Retourne les paramètres actuels de toutes les propriétés prises en charge par l’ensemble de lignes.|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|Retourne un pointeur d’interface à l’ensemble de lignes auquel s’applique un signet.|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|Retourne un pointeur d’interface sur l’objet (commande ou session) qui a créé cet ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 Une interface obligatoire sur les ensembles de lignes. Cette classe implémente les propriétés de l’ensemble de lignes à l’aide de la [mappage de jeu de propriétés](../../data/oledb/begin-propset-map.md) définies dans votre classe de commande. Bien que la classe de l’ensemble de lignes s’affiche pour être à l’aide de la propriété de la classe de commande définit l’ensemble de lignes est fourni avec sa propre copie des propriétés d’exécution, lorsqu’il est créé par un objet de commande ou de la session.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** altdb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)