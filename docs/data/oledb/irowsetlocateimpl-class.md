---
title: IRowsetLocateImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: db8d0b5d81a53a71413998b39947eb71a1bd508a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111027"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl, classe
Implémente le OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interface, qui extrait des lignes arbitraires à partir d’un ensemble de lignes.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
       T,   
       RowsetInterface,   
       RowClass,   
       MapClass>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une classe dérivée de `IRowsetLocateImpl`.  
  
 `RowsetInterface`  
 Une classe dérivée de `IRowsetImpl`.  
  
 `RowClass`  
 L’unité de stockage pour le **HROW**.  
  
 `MapClass`  
 L’unité de stockage pour tous les descripteurs de ligne détenus par le fournisseur.  
  
 `BookmarkKeyType`  
 Le type du signet, par exemple un entier LONG ou une chaîne. Les signets ordinaires doivent avoir une longueur au moins deux octets. (Longueur d’octet est réservée pour OLE DB [signets standards](https://msdn.microsoft.com/en-us/library/ms712954.aspx)**DBBMK_FIRST**, **DBBMK_LAST**, et **DBBMK_INVALID**.)  
  
 `BookmarkType`  
 Le mécanisme de mappage pour gérer les relations de données-signet.  
  
 `BookmarkMapClass`  
 L’unité de stockage pour tous les descripteurs de ligne détenus par le signet.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[Compare](../../data/oledb/irowsetlocateimpl-compare.md)|Compare deux signets.|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|Extrait les lignes en commençant à la ligne spécifiée par un décalage à partir d’un signet.|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|Extrait les lignes qui correspondent aux signets spécifiés.|  
|[hachage](../../data/oledb/irowsetlocateimpl-hash.md)|Retourne des valeurs pour les signets spécifiés de hachage.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|Un tableau de signets.|  
  
## <a name="remarks"></a>Notes  
 `IRowsetLocateImpl` est l’implémentation de modèles OLE DB de la [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interface. `IRowsetLocate` est utilisé pour extraire des lignes arbitraires à partir d’un ensemble de lignes. Un ensemble de lignes qui n’implémente pas cette interface est une `sequential` ensemble de lignes. Lorsque `IRowsetLocate` est présent sur un ensemble de lignes, la colonne 0 est le signet pour les lignes ; la lecture de cette colonne obtiendra la valeur d’un signet qui peut être utilisée pour repositionner à la même ligne.  
  
 `IRowsetLocateImpl` est utilisé pour implémenter la prise en charge signets dans les fournisseurs. Les signets sont des espaces réservés (index sur un ensemble de lignes) qui permettent au consommateur de revenir rapidement à une ligne, ce qui permet un accès rapide aux données. Le fournisseur détermine ce que les signets peuvent uniquement identifier une ligne. À l’aide de `IRowsetLocateImpl` méthodes, vous pouvez comparer des signets, les lignes de l’extraction en décalage, l’extraction des lignes par un signet et retournent des valeurs de hachage de signets.  
  
 Pour prendre en charge les signets OLE DB dans un ensemble de lignes, vérifiez l’ensemble de lignes héritent de cette classe.  
  
 Pour plus d’informations sur l’implémentation de prise en charge de signet, consultez [fournisseur prend en charge des signets par](../../data/oledb/provider-support-for-bookmarks.md) dans les *Guide du programmeur Visual C++* et [signets](https://msdn.microsoft.com/en-us/library/ms709728.aspx) dans les *De référence du programmeur OLE DB* dans la Kit de développement logiciel de plateforme.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête**: atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [Prise en charge du fournisseur pour les signets](../../data/oledb/provider-support-for-bookmarks.md)   
 [Signets](https://msdn.microsoft.com/en-us/library/ms709728.aspx)