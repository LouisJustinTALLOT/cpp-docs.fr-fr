---
title: IRowsetUpdateImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34efd252f67a0e3da9827ef97cff8bcab0a45532
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110436"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl, classe
L’implémentation de modèles OLE DB de la [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une classe dérivée de `IRowsetUpdateImpl`.  
  
 `Storage`  
 L’enregistrement d’utilisateur.  
  
 `UpdateArray`  
 Tableau contenant les données mises en cache pour la mise à jour de l’ensemble de lignes.  
  
 `RowClass`  
 L’unité de stockage pour le **HROW**.  
  
 `MapClass`  
 L’unité de stockage pour tous les descripteurs de ligne détenus par le fournisseur.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisés avec IRowsetChange)  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|Définit les valeurs de données dans une ou plusieurs colonnes.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Méthodes d’interface (utilisés avec IRowsetUpdate)  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|Obtient les données récemment transmis ou obtenu à partir de la source de données, en ignorant les modifications en attente.|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|Retourne une liste des lignes avec des modifications en attente.|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|Retourne l’état des lignes spécifiées.|  
|[Annuler](../../data/oledb/irowsetupdateimpl-undo.md)|Annule toutes les modifications à la ligne depuis la dernière extraction ou de la mise à jour.|  
|[Mettre à jour](../../data/oledb/irowsetupdateimpl-update.md)|Transmet toutes les modifications apportées à la ligne depuis la dernière extraction ou de la mise à jour.|  
  
### <a name="implementation-methods-callback"></a>Méthodes d’implémentation (rappel)  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|Permet de contrôler la sécurité, l’intégrité, et ainsi de suite avant d’autoriser les mises à jour.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|Contient les données d’origine pour l’opération différée.|  
  
## <a name="remarks"></a>Notes  
 Vous devez tout d’abord lire et comprendre la documentation de [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx), car tous les éléments y s’appliquent également ici. Vous devez également lire le chapitre 6 de la *de référence du programmeur OLE DB* sur la définition de données.  
  
 `IRowsetUpdateImpl` implémente le OLE DB `IRowsetUpdate` interface, ce qui permet aux consommateurs de retarder la transmission des modifications apportées avec `IRowsetChange` de source de données et annuler les modifications avant la transmission.  
  
> [!IMPORTANT]
>  Il est fortement recommandé de lire la documentation suivante avant de tenter d’implémenter votre fournisseur :  
  
-   [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Chapitre 6 de la *de référence du programmeur OLE DB*  
  
-   Consultez également la `RUpdateRowset` classe est utilisée dans l’exemple UpdatePV  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)