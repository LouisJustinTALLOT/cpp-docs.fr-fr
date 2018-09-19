---
title: IRowsetLocateImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
dev_langs:
- C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6a8e41561057250f4936e8e72a14f0324cfcdac1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065309"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl, classe

Implémente la norme OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190\(v=vs.85\)) interface, qui extrait des lignes arbitraires à partir d’un ensemble de lignes.  
  
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
  
### <a name="parameters"></a>Paramètres  

*T*<br/>
Une classe dérivée de `IRowsetLocateImpl`.  
  
*RowsetInterface*<br/>
Une classe dérivée de `IRowsetImpl`.  
  
*RowClass*<br/>
L’unité de stockage pour le `HROW`.  
  
*MapClass*<br/>
L’unité de stockage pour tous les handles de ligne détenus par le fournisseur.  
  
*BookmarkKeyType*<br/>
Le type du signet, telles qu’un LONG ou une chaîne. Signets ordinaires doivent avoir une longueur au moins deux octets. (Longueur d’octet est réservé pour OLE DB [signets standards](/previous-versions/windows/desktop/ms712954\(v=vs.85\))`DBBMK_FIRST`, `DBBMK_LAST`, et `DBBMK_INVALID`.)  
  
*BookmarkType*<br/>
Le mécanisme de mappage pour gérer les relations de signet des données.  
  
*BookmarkMapClass*<br/>
L’unité de stockage pour tous les handles de ligne détenus par le signet.  

## <a name="requirements"></a>Configuration requise  

**En-tête**: atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[Compare](#compare)|Compare deux signets.|  
|[GetRowsAt](#getrowsat)|Extrait les lignes en commençant à la ligne spécifiée par un décalage à partir d’un signet.|  
|[GetRowsByBookmark](#getrowsbybookmark)|Extrait les lignes qui correspondent aux signets spécifiés.|  
|[hachage](#hash)|Retourne des valeurs pour les signets spécifiés de hachage.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_rgBookmarks](#rgbookmarks)|Un tableau de signets.|  
  
## <a name="remarks"></a>Notes  

`IRowsetLocateImpl` est l’implémentation de modèles OLE DB de la [IRowsetLocate](/previous-versions/windows/desktop/ms721190\(v=vs.85\)) interface. `IRowsetLocate` est utilisé pour extraire des lignes arbitraires à partir d’un ensemble de lignes. Un ensemble de lignes qui n’implémente pas cette interface est un `sequential` ensemble de lignes. Lorsque `IRowsetLocate` est présent sur un ensemble de lignes, la colonne 0 est le signet pour les lignes ; en lisant cette rubrique Obtient une valeur de signet qui peut être utilisée pour les repositionner à la même ligne.  
  
`IRowsetLocateImpl` est utilisé pour implémenter la prise en charge de signet dans les fournisseurs. Les signets sont des espaces réservés (index sur un ensemble de lignes) qui permettent au consommateur de revenir rapidement à une ligne, ce qui permet un accès rapide aux données. Le fournisseur détermine que signets peuvent uniquement identifier une ligne. À l’aide de `IRowsetLocateImpl` méthodes, vous pouvez comparer des signets, les lignes de l’extraction en décalage, l’extraction des lignes par signet et retournent des valeurs de hachage de signets.  
  
Pour prendre en charge des signets de OLE DB dans un ensemble de lignes, vérifiez l’ensemble de lignes à hériter de cette classe.  
  
Pour plus d’informations sur l’implémentation de prise en charge de signet, consultez [fournisseur prend en charge des signets par](../../data/oledb/provider-support-for-bookmarks.md) dans le *-Guide du programmeur Visual C++* et [signets](/previous-versions/windows/desktop/ms709728\(v=vs.85\)) dans les *Référence du programmeur OLE DB* dans le kit Platform SDK.  

## <a name="compare"></a> IRowsetLocateImpl::Compare

Compare deux signets.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IRowsetLocate::Compare](/previous-versions/windows/desktop/ms709539\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Une des signets peuvent être une norme définie par OLE DB [signet standard](/previous-versions/windows/desktop/ms712954\(v=vs.85\)) (`DBBMK_FIRST`, `DBBMK_LAST`, ou `DBBMK_INVALID`). La valeur retournée dans `pComparison` indique la relation entre les deux signets :  
  
- DBCOMPARE_LT (`cbBookmark1` est avant `cbBookmark2`.)  
  
- DBCOMPARE_EQ (`cbBookmark1` est égal à `cbBookmark2`.)  
  
- DBCOMPARE_GT (`cbBookmark1` est après `cbBookmark2`.)  
  
- DBCOMPARE_NE (les signets sont égales et non ordonné).  
  
- DBCOMPARE_NOTCOMPARABLE (les signets ne peuvent pas être comparées). 

## <a name="getrowsat"></a> IRowsetLocateImpl::GetRowsAt

Extrait les lignes en commençant à la ligne spécifiée par un décalage à partir d’un signet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,  
   HCHAPTER hReserved2,  
   DBBKMARK cbBookmark,  
   const BYTE* pBookmark,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IRowsetLocate::GetRowsAt](/previous-versions/windows/desktop/ms723031\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Pour extraire à partir de la position du curseur au lieu de cela, utilisez [IRowset::GetRowsAt](/previous-versions/windows/desktop/ms723031\(v=vs.85\)).  
  
`IRowsetLocateImpl::GetRowsAt` ne modifie pas la position du curseur. 

## <a name="getrowsbybookmark"></a> IRowsetLocateImpl::GetRowsByBookmark

Extrait une ou plusieurs lignes qui correspondent aux signets spécifiés.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Paramètres  

*hReserved*<br/>
[in] Correspond à *hChapter* paramètre [IRowsetLocate::GetRowsByBookmark](/previous-versions/windows/desktop/ms725420\(v=vs.85\)).  
  
Pour les autres paramètres, consultez [IRowsetLocate::GetRowsByBookmark](/previous-versions/windows/desktop/ms725420\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Le signet peut être une valeur que vous définissez ou OLE DB [signets standards](/previous-versions/windows/desktop/ms712954\(v=vs.85\)) (`DBBMK_FIRST` ou `DBBMK_LAST`). ne modifie pas la position du curseur.  

## <a name="hash"></a> IRowsetLocateImpl::Hash

Retourne des valeurs pour les signets spécifiés de hachage.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmarks,  
   const DBBKMARK* rgcbBookmarks[],  
   const BYTE* rgpBookmarks[],  
   DBHASHVALUE rgHashValues[],  
   DBROWSTATUS rgBookmarkStatus[]);  
```  
  
#### <a name="parameters"></a>Paramètres  

*hReserved*<br/>
[in] Correspond à *hChapter* paramètre [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697\(v=vs.85\)).  
  
Pour les autres paramètres, consultez [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="rgbookmarks"></a> IRowsetLocateImpl::m_rgBookmarks

Un tableau de signets.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;  
```  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:IRowset](/previous-versions/windows/desktop/ms721190\(v=vs.85\))   
[Prise en charge des signets par le fournisseur](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Signets](/previous-versions/windows/desktop/ms709728\(v=vs.85\))