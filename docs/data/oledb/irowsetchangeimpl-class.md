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
- SetData
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
ms.openlocfilehash: 13dadfdcaf912e5cb2d82361de997d09961f1ceb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514606"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl Class

L’implémentation de modèles OLE DB de la [IRowsetChange](/previous-versions/windows/desktop/ms715790) interface dans la spécification OLE DB.

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
Une classe dérivée de `IRowsetChangeImpl`.

*Stockage*<br/>
L’enregistrement utilisateur.

*BaseInterface*<br/>
La classe de base pour l’interface, tel que `IRowsetChange`.

*RowClass*<br/>
L’unité de stockage pour le handle de ligne.

*MapClass*<br/>
L’unité de stockage pour tous les handles de ligne détenus par le fournisseur.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisés avec IRowsetChange)

|||
|-|-|
|[DeleteRows](#deleterows)|Supprime des lignes de l’ensemble de lignes.|
|[InsertRow](#insertrow)|Insère une ligne dans l’ensemble de lignes.|
|[SetData](#setdata)|Définit les valeurs de données dans une ou plusieurs colonnes.|

### <a name="implementation-method-callback"></a>Méthode d’implémentation (rappel)

|||
|-|-|
|[FlushData](#flushdata)|Substitué par le fournisseur pour valider des données dans son magasin.|

## <a name="remarks"></a>Notes

Cette interface est responsable des opérations d’écriture immédiate à une banque de données. « Immédiats » signifie que lorsque l’utilisateur final (la personne à l’aide du consommateur) effectue toutes les modifications, ces modifications sont immédiatement transmises aux données stocker (et ne peut pas être annulée).

`IRowsetChangeImpl` implémente la norme OLE DB `IRowsetChange` interface, ce qui permet la mise à jour des valeurs des colonnes dans les lignes existantes, la suppression de lignes et l’insertion de nouvelles lignes.

L’implémentation de modèles OLE DB prend en charge toutes les méthodes de base (`SetData`, `InsertRow`, et `DeleteRows`).

> [!IMPORTANT]
>  Il est fortement recommandé que vous lire la documentation suivante avant de tenter d’implémenter votre fournisseur :

- [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)

- Chapitre 6 de la *de référence du programmeur OLE DB*

- Consultez également comment la `RUpdateRowset` classe est utilisée dans le [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) exemple.

## <a name="deleterows"></a> IRowsetChangeImpl::DeleteRows

Supprime des lignes de l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v%3dvs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="insertrow"></a> IRowsetChangeImpl::InsertRow

Crée et initialise une nouvelle ligne dans l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921) dans le *de référence du programmeur OLE DB*.

## <a name="setdata"></a> IRowsetChangeImpl::SetData

Définit les valeurs de données dans une ou plusieurs colonnes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232) dans le *de référence du programmeur OLE DB*.

## <a name="flushdata"></a> IRowsetChangeImpl::FlushData

Substitué par le fournisseur pour valider des données dans son magasin.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Paramètres

*hRowToFlush*<br/>
[in] Handle vers les lignes pour les données. Le type de cette ligne est déterminé à partir de la *RowClass* argument template de la `IRowsetImpl` classe (`CSimpleRow` par défaut).

*hAccessorToFlush*<br/>
[in] Handle de l’accesseur qui contient les informations de liaison et les informations de type dans ses `PROVIDER_MAP` (consultez [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)