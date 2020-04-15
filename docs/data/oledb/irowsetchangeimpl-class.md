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
ms.openlocfilehash: ae4ceea53ec91cc3f9593dd3789fcf61e0702274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376948"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl Class

L’OLE DB Templates mise en œuvre de l’interface [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) dans les spécifications OLE DB.

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
Une classe `IRowsetChangeImpl`dérivée de .

*Stockage*<br/>
L’enregistrement de l’utilisateur.

*BaseInterface*<br/>
La classe de base pour `IRowsetChange`l’interface, comme .

*Classe Row*<br/>
L’unité de stockage pour la poignée de ligne.

*MapClass (en)*<br/>
L’unité de stockage pour toutes les poignées de ligne détenues par le fournisseur.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisé avec IRowsetChange)

|||
|-|-|
|[DeleteRows (DeleteRows)](#deleterows)|Supprime les lignes du rowset.|
|[InsertRow](#insertrow)|Insère une rangée dans le rame.|
|[Setdata](#setdata)|Définit les valeurs de données dans une ou plusieurs colonnes.|

### <a name="implementation-method-callback"></a>Méthode de mise en œuvre (Rappel)

|||
|-|-|
|[FlushData (FlushData)](#flushdata)|Remplacé par le fournisseur d’engager des données à son magasin.|

## <a name="remarks"></a>Notes

Cette interface est responsable de l’écriture immédiate des opérations dans un magasin de données. « Immédiate » signifie que lorsque l’utilisateur final (la personne qui utilise le consommateur) apporte des modifications, ces modifications sont immédiatement transmises au magasin de données (et ne peuvent pas être annulées).

`IRowsetChangeImpl`implémente l’interface OLE DB, `IRowsetChange` qui permet de mettre à jour les valeurs des colonnes dans les rangées existantes, de supprimer les lignes et d’insérer de nouvelles lignes.

La mise en œuvre OLE DB Templates prend en charge toutes les méthodes de base (`SetData`, `InsertRow`et `DeleteRows`).

> [!IMPORTANT]
> Il est fortement recommandé que vous lisiez la documentation suivante AVANT de tenter de mettre en œuvre votre fournisseur :

- [Création d’un fournisseur Updatable](../../data/oledb/creating-an-updatable-provider.md)

- Chapitre 6 de la *référence du programmeur OLE DB*

- Voyez également `RUpdateRowset` comment la classe est utilisée dans l’échantillon [UpdatePV.](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl::DeleteRows

Supprime les lignes du rowset.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Paramètres

Voir [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v=vs.85)) in the *OLE DB Programmer’s Reference*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl::InsertRow

Crée et initialise une nouvelle ligne dans le ramage.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Paramètres

Voir [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) in the *OLE DB Programmer’s Reference*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl::SetData

Définit les valeurs de données dans une ou plusieurs colonnes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Paramètres

Voir [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) in the *OLE DB Programmer’s Reference*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl::FlushData

Remplacé par le fournisseur d’engager des données à son magasin.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Paramètres

*hRowToFlush*<br/>
[dans] Gérer les lignes pour les données. Le type de cette ligne est déterminé à `IRowsetImpl` partir`CSimpleRow` de l’argument du modèle *RowClass* de la classe (par défaut).

*hAccessorToFlush*<br/>
[dans] Poignée à l’accesseur, qui contient des `PROVIDER_MAP` informations contraignantes et des informations de type dans son (voir [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
