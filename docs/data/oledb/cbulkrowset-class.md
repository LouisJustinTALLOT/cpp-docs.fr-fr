---
title: CBulkRowset, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: 5c1c7bc381d30f701bad123807689b08ea47f65d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838462"
---
# <a name="cbulkrowset-class"></a>CBulkRowset, classe

Récupère et manipule des lignes pour travailler en bloc sur les données en extrayant plusieurs descripteurs de ligne avec un seul appel.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Classe d’accesseur.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[AddRefRows](#addrefrows)|Incrémente le décompte de références.|
|[CBulkRowset](#cbulkrowset)|Constructeur.|
|[MoveFirst](#movefirst)|Récupère la première ligne de données, en effectuant une nouvelle extraction en bloc si nécessaire.|
|[MoveLast](#movelast)|Passe à la dernière ligne.|
|[MoveNext](#movenext)|Récupère la ligne de données suivante.|
|[MovePrev](#moveprev)|Passe à la ligne précédente.|
|[MoveToBookmark](#movetobookmark)|Extrait la ligne marquée par un signet ou la ligne à un décalage spécifié à partir de ce signet.|
|[MoveToRatio](#movetoratio)|Extrait des lignes à partir d’une position fractionnaire dans l’ensemble de lignes.|
|[ReleaseRows](#releaserows)|Définit la ligne actuelle ( `m_nCurrentRow` ) à zéro et libère toutes les lignes.|
|[SetRows](#setrows)|Définit le nombre de handles de ligne à récupérer par un appel.|

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de la `CBulkRowset` classe.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="cbulkrowsetaddrefrows"></a><a name="addrefrows"></a> CBulkRowset :: AddRefRows

Appelle [IRowset :: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) pour incrémenter le décompte de références pour toutes les lignes récupérées actuellement de l’ensemble de lignes en bloc.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="cbulkrowsetcbulkrowset"></a><a name="cbulkrowset"></a> CBulkRowset :: CBulkRowset

Crée un nouvel `CBulkRowset` objet et définit le nombre de lignes par défaut sur 10.

### <a name="syntax"></a>Syntaxe

```cpp
CBulkRowset();
```

## <a name="cbulkrowsetmovefirst"></a><a name="movefirst"></a> CBulkRowset :: MoveFirst

Récupère la première ligne de données.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="cbulkrowsetmovelast"></a><a name="movelast"></a> CBulkRowset :: MoveLast

Passe à la dernière ligne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="cbulkrowsetmovenext"></a><a name="movenext"></a> CBulkRowset :: MoveNext

Récupère la ligne de données suivante.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard. Lorsque la fin de l’ensemble de lignes a été atteinte, retourne DB_S_ENDOFROWSET.

## <a name="cbulkrowsetmoveprev"></a><a name="moveprev"></a> CBulkRowset :: MovePrev

Passe à la ligne précédente.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="cbulkrowsetmovetobookmark"></a><a name="movetobookmark"></a> CBulkRowset :: MoveToBookmark

Extrait la ligne marquée par un signet ou la ligne à un décalage spécifié (*lSkip*) à partir de ce signet.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Paramètres

*bookmark*<br/>
dans Signet marquant l’emplacement à partir duquel vous souhaitez extraire des données.

*lSkip*<br/>
dans Nombre de lignes du signet à la ligne cible. Si *lSkip* est égal à zéro, la première ligne extraite est la ligne avec signet. Si *lSkip* est 1, la première ligne extraite est la ligne qui suit la ligne marquée par un signet. Si *lSkip* est-1, la première ligne extraite est la ligne avant la ligne avec signet.

### <a name="return-value"></a>Valeur renvoyée

Consultez [IRowset :: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="cbulkrowsetmovetoratio"></a><a name="movetoratio"></a> CBulkRowset :: MoveToRatio

Extrait des lignes à partir d’une position fractionnaire dans l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Paramètres

*nNumerator*<br/>
dans Numérateur utilisé pour déterminer la position fractionnaire à partir de laquelle récupérer les données.

*nDenominator*<br/>
dans Dénominateur utilisé pour déterminer la position fractionnaire à partir de laquelle récupérer des données.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

`MoveToRatio` Récupère les lignes approximativement en fonction de la formule suivante :

`(nNumerator *  RowsetSize ) / nDenominator`

Où `RowsetSize` est la taille de l’ensemble de lignes, mesurée en lignes. La précision de cette formule dépend du fournisseur spécifique. Pour plus d’informations, consultez [IRowsetScroll :: GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="cbulkrowsetreleaserows"></a><a name="releaserows"></a> CBulkRowset :: ReleaseRows

Appelle [IRowset :: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) pour décrémenter le décompte de références pour toutes les lignes récupérées actuellement de l’ensemble de lignes en bloc.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="cbulkrowsetsetrows"></a><a name="setrows"></a> CBulkRowset :: SetRows

Définit le nombre de handles de ligne récupérés par chaque appel.

### <a name="syntax"></a>Syntaxe

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Paramètres

*nRows*<br/>
dans Nouvelle taille de l’ensemble de lignes (nombre de lignes).

### <a name="remarks"></a>Notes

Si vous appelez cette fonction, elle doit être avant l’ouverture de l’ensemble de lignes.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
