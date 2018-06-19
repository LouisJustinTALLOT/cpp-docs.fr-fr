---
title: IRowsetImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetImpl class
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ca6d35eeea1dbfae4f2a5bb1b2ee93553e53519
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108436"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl, classe
Fournit une implémentation de l’interface `IRowset`.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*>>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IRowsetImpl`.  
  
 `RowsetInterface`  
 Une classe dérivée de `IRowsetImpl`.  
  
 `RowClass`  
 Unité de stockage pour le **HROW**.  
  
 `MapClass`  
 Unité de stockage pour tous les descripteurs de ligne détenus par le fournisseur.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|Ajoute un décompte de références à un handle de ligne existant.|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|Appelé par [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) pour allouer une nouvelle **HROW**. Pas appelé directement par l’utilisateur.|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|Récupère les données à partir de la copie de l’ensemble de lignes de la ligne.|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|Retourne l’état pour le champ spécifié.|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|Extrait des lignes séquentiellement, sans oublier la position précédente.|  
|[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)|Constructeur. Pas appelé directement par l’utilisateur.|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|Appelé par [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) et [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). Pas appelé directement par l’utilisateur.|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|Libère des lignes.|  
|[RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|Repositionne la prochaine position d’extraction à sa position initiale ; Autrement dit, sa position lors de l’ensemble de lignes est initialement créé.|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|Définit les indicateurs d’état pour le champ spécifié.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|Indique si un fournisseur prend en charge l’extraction vers l’arrière.|  
|[m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|Indique si un fournisseur peut avoir un son défilement de curseur vers l’arrière.|  
|[m_bReset](../../data/oledb/irowsetimpl-m-breset.md)|Indique si un fournisseur a réinitialisé à sa position de curseur. Cela a une signification spéciale lorsque le défilement vers l’arrière ou l’extraction vers l’arrière dans [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|  
|[m_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|Un index à l’ensemble de lignes, qui représente le curseur.|  
|[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|Une liste de descripteurs de lignes.|  
  
## <a name="remarks"></a>Notes  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) est l’interface de l’ensemble de lignes de base.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)