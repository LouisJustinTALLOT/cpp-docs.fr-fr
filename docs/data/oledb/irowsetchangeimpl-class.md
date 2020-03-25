---
title: IRowsetChangeImpl Class
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: b069cd08814855a0528806ac6d19ed8f5beb6f37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210455"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl Class

L’implémentation des modèles OLE DB de l’interface [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) dans la spécification OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `IRowsetChangeImpl`.

*Stockage*<br/>
Enregistrement de l’utilisateur.

*BaseInterface*<br/>
Classe de base pour l’interface, telle que `IRowsetChange`.

*RowClass*<br/>
Unité de stockage pour le descripteur de ligne.

*MapClass*<br/>
Unité de stockage de tous les descripteurs de lignes détenues par le fournisseur.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisées avec IRowsetChange)

|||
|-|-|
|[DeleteRows](#deleterows)|Supprime des lignes de l’ensemble de lignes.|
|[InsertRow](#insertrow)|Insère une ligne dans l’ensemble de lignes.|
|[SetData](#setdata)|Définit des valeurs de données dans une ou plusieurs colonnes.|

### <a name="implementation-method-callback"></a>Méthode d’implémentation (callback)

|||
|-|-|
|[FlushData](#flushdata)|Remplacé par le fournisseur pour valider les données dans son magasin.|

## <a name="remarks"></a>Notes

Cette interface est responsable des opérations d’écriture immédiates dans un magasin de données. « Immediate » signifie que lorsque l’utilisateur final (la personne qui utilise le consommateur) apporte des modifications, ces modifications sont immédiatement transmises au magasin de données (et ne peuvent pas être annulées).

`IRowsetChangeImpl` implémente l’interface `IRowsetChange` OLE DB, qui permet la mise à jour de valeurs de colonnes dans des lignes existantes, la suppression de lignes et l’insertion de nouvelles lignes.

L’implémentation des modèles OLE DB prend en charge toutes les méthodes de base (`SetData`, `InsertRow`et `DeleteRows`).

> [!IMPORTANT]
>  Nous vous recommandons vivement de lire la documentation suivante avant d’essayer d’implémenter votre fournisseur :

- [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)

- Chapitre 6 du *Guide de référence du programmeur OLE DB*

- Voyez également comment la classe `RUpdateRowset` est utilisée dans l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl ::D eleteRows

Supprime des lignes de l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetChange ::D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl :: InsertRow

Crée et Initialise une nouvelle ligne dans l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetChange :: InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl :: SetData

Définit des valeurs de données dans une ou plusieurs colonnes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetChange :: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl :: FlushData

Remplacé par le fournisseur pour valider les données dans son magasin.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Paramètres

*hRowToFlush*<br/>
dans Handle vers les lignes pour les données. Le type de cette ligne est déterminé à partir de l’argument de modèle *RowClass* de la classe `IRowsetImpl` (`CSimpleRow` par défaut).

*hAccessorToFlush*<br/>
dans Handle de l’accesseur, qui contient des informations de liaison et des informations de type dans son `PROVIDER_MAP` (consultez [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
