---
title: IRowsetLocateImpl, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 06e860425215d9fde268b780c001301b14a1caa1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210429"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl, classe

Implémente l’interface OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , qui extrait des lignes arbitraires d’un ensemble de lignes.

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
Classe dérivée de `IRowsetLocateImpl`.

*RowsetInterface*<br/>
Classe dérivée de `IRowsetImpl`.

*RowClass*<br/>
Unité de stockage pour le `HROW`.

*MapClass*<br/>
Unité de stockage de tous les descripteurs de lignes détenues par le fournisseur.

*BookmarkKeyType*<br/>
Type du signet, tel qu’une valeur LONG ou une chaîne. Les signets ordinaires doivent avoir une longueur d’au moins deux octets. (Une longueur sur un octet est réservée aux [signets standard](/previous-versions/windows/desktop/ms712954(v=vs.85)) OLE DB`DBBMK_FIRST`, `DBBMK_LAST`et `DBBMK_INVALID`.)

*BookmarkType*<br/>
Mécanisme de mappage pour gérer les relations de signets vers des données.

*BookmarkMapClass*<br/>
Unité de stockage de tous les descripteurs de lignes détenues par le signet.

## <a name="requirements"></a>Spécifications

**En-tête**: Atldb. h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

|||
|-|-|
|[Compare](#compare)|Compare deux signets.|
|[GetRowsAt](#getrowsat)|Extrait des lignes en commençant par la ligne spécifiée par un offset à partir d’un signet.|
|[GetRowsByBookmark](#getrowsbybookmark)|Récupère les lignes qui correspondent aux signets spécifiés.|
|[Code de hachage](#hash)|Retourne des valeurs de hachage pour les signets spécifiés.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Tableau de signets.|

## <a name="remarks"></a>Notes

`IRowsetLocateImpl` est l’implémentation OLE DB templates de l’interface [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) . `IRowsetLocate` est utilisé pour extraire des lignes arbitraires d’un ensemble de lignes. Un ensemble de lignes qui n’implémente pas cette interface est un ensemble de lignes `sequential`. Lorsque `IRowsetLocate` est présent sur un ensemble de lignes, la colonne 0 est le signet des lignes ; la lecture de cette colonne permet d’obtenir une valeur de signet qui peut être utilisée pour repositionner sur la même ligne.

`IRowsetLocateImpl` est utilisé pour implémenter la prise en charge des signets dans les fournisseurs. Les signets sont des espaces réservés (index sur un ensemble de lignes) qui permettent au consommateur de retourner rapidement à une ligne, ce qui permet un accès rapide aux données. Le fournisseur détermine les signets qui peuvent identifier une ligne de manière unique. À l’aide de `IRowsetLocateImpl` méthodes, vous pouvez comparer des signets, extraire des lignes par décalage, extraire des lignes par signet et retourner des valeurs de hachage pour les signets.

Pour prendre en charge les signets OLE DB dans un ensemble de lignes, faites en sorte que l’ensemble de lignes hérite de cette classe.

Pour plus d’informations sur l’implémentation de la prise en charge des signets, consultez [prise en charge des](../../data/oledb/provider-support-for-bookmarks.md) signets par le fournisseur dans le *Guide du programmeur Visual C++*  et les [signets](/previous-versions/windows/desktop/ms709728(v=vs.85)) dans le Guide de *Référence du programmeur* de la plateforme OLE DB.

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a>IRowsetLocateImpl :: compare

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

Consultez [IRowsetLocate :: compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

L’un des signets peut être un [signet standard](/previous-versions/windows/desktop/ms712954(v=vs.85)) défini par l’OLE DB standard (`DBBMK_FIRST`, `DBBMK_LAST`ou `DBBMK_INVALID`). La valeur retournée dans `pComparison` indique la relation entre les deux signets :

- DBCOMPARE_LT (`cbBookmark1` est avant `cbBookmark2`.)

- DBCOMPARE_EQ (`cbBookmark1` est égal à `cbBookmark2`.)

- DBCOMPARE_GT (`cbBookmark1` est après `cbBookmark2`.)

- DBCOMPARE_NE (les signets sont égaux et non ordonnés.)

- DBCOMPARE_NOTCOMPARABLE (les signets ne peuvent pas être comparés).

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a>IRowsetLocateImpl :: GetRowsAt

Extrait des lignes en commençant par la ligne spécifiée par un offset à partir d’un signet.

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

Consultez [IRowsetLocate :: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Pour récupérer à partir de la position du curseur à la place, utilisez [IRowset :: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)).

`IRowsetLocateImpl::GetRowsAt` ne modifie pas la position du curseur.

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a>IRowsetLocateImpl :: GetRowsByBookmark

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
dans Correspond au paramètre *hChapter* en [IRowsetLocate :: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)).

Pour les autres paramètres, consultez [IRowsetLocate :: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Le signet peut être une valeur que vous définissez ou un OLE DB des [signets standard](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST` ou `DBBMK_LAST`). Ne modifie pas la position du curseur.

## <a name="irowsetlocateimplhash"></a><a name="hash"></a>IRowsetLocateImpl :: Hash

Retourne des valeurs de hachage pour les signets spécifiés.

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
dans Correspond au paramètre *hChapter* en [IRowsetLocate :: Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)).

Pour les autres paramètres, consultez [IRowsetLocate :: Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a>IRowsetLocateImpl :: m_rgBookmarks

Tableau de signets.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate :](/previous-versions/windows/desktop/ms721190(v=vs.85)) [prise en charge du fournisseur de
IRowset pour les signets](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Signets](/previous-versions/windows/desktop/ms709728(v=vs.85))
