---
description: 'En savoir plus sur : IDBSchemaRowsetImpl, classe'
title: IDBSchemaRowsetImpl (classe)
ms.date: 11/04/2016
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
ms.openlocfilehash: 392f74793f363c203b740b14b00b605d8256bef5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287279"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl (classe)

Fournit l’implémentation pour les ensembles de lignes de schéma.

## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>Paramètres

*SessionClass*<br/>
Classe par laquelle `IDBSchemaRowsetImpl` est hérité. En général, cette classe est la classe session de l’utilisateur.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[CheckRestrictions](#checkrestrictions)|Vérifie la validité des restrictions par rapport à un ensemble de lignes de schéma.|
|[CreateSchemaRowset](#createschemarowset)|Implémente une fonction de création d’objet COM pour l’objet spécifié par le paramètre de modèle.|
|[SetRestrictions](#setrestrictions)|Spécifie les restrictions que vous prenez en charge sur un ensemble de lignes de schéma particulier.|

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[GetRowset](#getrowset)|Retourne un ensemble de lignes de schéma.|
|[GetSchemas](#getschemas)|Retourne une liste d’ensembles de lignes de schéma accessibles par [IDBSchemaRowsetImpl::GetRowset](#getrowset).|

## <a name="remarks"></a>Notes

Cette classe implémente l’interface [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) et la fonction de créateur mise en modèle [CreateSchemaRowset](#createschemarowset).

OLE DB utilise les ensembles de lignes de schéma pour retourner des données à propos des données d’un fournisseur. Ces données sont souvent appelées « métadonnées ». Par défaut, un fournisseur doit toujours prendre en charge `DBSCHEMA_TABLES` , `DBSCHEMA_COLUMNS` et `DBSCHEMA_PROVIDER_TYPES` , comme décrit dans [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le *guide de référence du programmeur OLE DB*. Les ensembles de lignes de schéma sont désignés dans un mappage de schéma. Pour plus d’informations sur les entrées de mappage de schéma, consultez [SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry).

L’Assistant Fournisseur OLE DB, dans l’Assistant Objet ATL, génère automatiquement le code pour les ensembles de lignes de schéma dans votre projet. (Par défaut, l’Assistant prend en charge les ensembles de lignes de schéma obligatoires mentionnés précédemment.) Lorsque vous créez un consommateur à l’aide de l’Assistant objet ATL, l’Assistant utilise les ensembles de lignes de schéma pour lier les données correctes à un fournisseur. Si vous n’implémentez pas vos ensembles de lignes de schéma pour fournir les métadonnées correctes, l’Assistant ne lie pas les bonnes données.

Pour plus d’informations sur la prise en charge des ensembles de lignes de schéma dans votre fournisseur, consultez [Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md).

Pour plus d’informations sur les ensembles de lignes de schéma, consultez [Ensembles de lignes de schéma](/previous-versions/windows/desktop/ms712921(v=vs.85)) dans les *Informations de référence du programmeur OLE DB*.

## <a name="idbschemarowsetimplcheckrestrictions"></a><a name="checkrestrictions"></a> IDBSchemaRowsetImpl :: CheckRestrictions

Vérifie la validité des restrictions par rapport à un ensemble de lignes de schéma.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>Paramètres

*rguidSchema*<br/>
[in] Référence au GUID d’ensemble de lignes de schéma demandé (par exemple, `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Nombre de restrictions passées par le consommateur pour l’ensemble de lignes de schéma.

*rgRestrictions*<br/>
[in] Tableau de longueur *cRestrictions* des valeurs de restriction à définir. Pour plus d’informations, consultez la description du paramètre *rgRestrictions* dans [SetRestrictions](#setrestrictions).

### <a name="remarks"></a>Notes

Utilisez la méthode `CheckRestrictions` pour vérifier la validité des restrictions par rapport à un ensemble de lignes de schéma. Elle vérifie les restrictions pour les `DBSCHEMA_TABLES` `DBSCHEMA_COLUMNS` ensembles de lignes de schéma, et `DBSCHEMA_PROVIDER_TYPES` . Appelez-le pour déterminer si l’appel d’un consommateur à `IDBSchemaRowset::GetRowset` est correct. Si vous voulez prendre en charge d’autres ensembles de lignes de schéma que ceux répertoriés ci-dessus, vous devez créer votre propre fonction pour mener à bien cette tâche.

`CheckRestrictions` détermine si le consommateur appelle [GetRowset](#getrowset) avec la restriction correcte et le type de restriction correct (par exemple, une VT_BSTR pour une chaîne) que le fournisseur prend en charge. De même, elle détermine si le nombre correct de restrictions est pris en charge. Par défaut, `CheckRestrictions` demande au fournisseur, via l’appel [SetRestrictions](#setrestrictions) , quelles restrictions il prend en charge dans un ensemble de lignes donné. La méthode compare ensuite les restrictions du consommateur à celles que prend en charge le fournisseur avant d’aboutir ou d’échouer.

Pour plus d’informations sur les ensembles de lignes de schéma, consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows.

## <a name="idbschemarowsetimplcreateschemarowset"></a><a name="createschemarowset"></a> IDBSchemaRowsetImpl :: CreateSchemaRowset

Implémente une fonction de création d’objet COM pour l’objet spécifié par le paramètre de modèle.

### <a name="syntax"></a>Syntaxe

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
dans [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) externe lors de l’agrégation ; sinon, null.

*cRestrictions*<br/>
[in] Nombre de restrictions appliquées à l’ensemble de lignes du schéma.

*rgRestrictions*<br/>
[in] Tableau de `cRestrictions`**s de** à appliquer à l’ensemble de lignes.

*riid*<br/>
dans Interface à [QueryInterface](../../atl/queryinterface.md) pour sur la sortie `IUnknown` .

*cPropertySets*<br/>
[in] Nombre de sets de propriétés à définir.

*rgPropertySets*<br/>
[in] Tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) qui spécifient les propriétés définies.

*ppRowset*<br/>
à Sortant `IUnknown` demandé par *riid*. Il `IUnknown` s’agit d’une interface sur l’objet d’ensemble de lignes de schéma.

*pSchemaRowset*<br/>
[out] Pointeur vers une instance de la classe d’ensemble de lignes du schéma. Ce paramètre n’est généralement pas utilisé, mais il peut l’être si vous devez effectuer des tâches supplémentaires sur l’ensemble de lignes du schéma avant de le passer à un objet COM. La durée de vie de *pSchemaRowset* est liée par *ppRowset*.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction implémente un créateur générique pour tous les types d’ensembles de lignes du schéma. En règle générale, l’utilisateur n’appelle pas cette fonction. Elle est appelée par l’implémentation du mappage de schéma.

## <a name="idbschemarowsetimplsetrestrictions"></a><a name="setrestrictions"></a> IDBSchemaRowsetImpl :: SetRestrictions

Spécifie les restrictions que vous prenez en charge sur un ensemble de lignes de schéma particulier.

### <a name="syntax"></a>Syntaxe

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>Paramètres

*cRestrictions*<br/>
dans Nombre de restrictions dans le tableau *rgRestrictions* et nombre de GUID dans le tableau *rguidSchema* .

*rguidSchema*<br/>
[in] Tableau des GUID des ensembles de lignes de schéma pour lesquels les restrictions doivent être récupérées. Chaque élément de tableau contient le GUID d’un ensemble de lignes de schéma (par exemple, `DBSCHEMA_TABLES`).

*rgRestrictions*<br/>
[in] Tableau de longueur *cRestrictions* des valeurs de restriction à définir. Chaque élément correspond aux restrictions de l’ensemble de lignes de schéma identifié par le GUID. Si un ensemble de lignes de schéma n’est pas pris en charge par le fournisseur, la valeur définie de l’élément est zéro. Dans le cas contraire, la valeur **ULONG** contient un masque de bits qui représente les restrictions prises en charge sur cet ensemble de lignes de schéma. Pour plus d’informations sur les restrictions correspondant à un ensemble de lignes de schéma particulier, consultez la table des GUID d’ensembles de lignes de schéma dans [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows.

### <a name="remarks"></a>Notes

L' `IDBSchemaRowset` objet appelle `SetRestrictions` pour déterminer les restrictions que vous prenez en charge sur un ensemble de lignes de schéma particulier (il est appelé par [GetSchemas](#getschemas) via un pointeur converti). Les restrictions permettent aux consommateurs de récupérer uniquement les lignes correspondantes (par exemple, toutes les colonnes de la table « MaTable »). Les restrictions sont facultatives, et dans le cas où aucune n’est prise en charge (par défaut), toutes les données sont systématiquement retournées.

L’implémentation par défaut de cette méthode affecte la valeur 0 aux éléments du tableau *rgRestrictions* . Remplacez la valeur par défaut dans votre classe session pour définir d’autres restrictions que celle par défaut.

Pour plus d’informations sur l’implémentation de la prise en charge des ensembles de lignes de schéma, consultez [Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md).

Pour obtenir un exemple de fournisseur qui prend en charge les ensembles de lignes de schéma, consultez l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

Pour plus d’informations sur les ensembles de lignes de schéma, consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows.

## <a name="idbschemarowsetimplgetrowset"></a><a name="getrowset"></a> IDBSchemaRowsetImpl :: GetRowset

Retourne un ensemble de lignes de schéma.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
dans Externe lors de l' `IUnknown` agrégation ; sinon, null.

*rguidSchema*<br/>
[in] Référence au GUID d’ensemble de lignes de schéma demandé (par exemple, `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Nombre de restrictions à appliquer à l’ensemble de lignes.

*rgRestrictions*<br/>
[in] Tableau d’objets `cRestrictions`**VARIANT** qui représentent les restrictions.

*riid*<br/>
[in] IID associé à la demande portant sur l’ensemble de lignes de schéma nouvellement créé.

*cPropertySets*<br/>
[in] Nombre de sets de propriétés à définir.

*rgPropertySets*<br/>
[in/out] Tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) à définir sur l’ensemble de lignes de schéma nouvellement créé.

*ppRowset*<br/>
[out] Pointeur désignant l’interface demandée sur l’ensemble de lignes de schéma nouvellement créé.

### <a name="remarks"></a>Notes

Cette méthode impose à l’utilisateur de disposer d’un mappage de schéma dans la classe session. À l’aide des informations de mappage de schéma, `GetRowset` crée un objet d’ensemble de lignes donné si le paramètre *rguidSchema* est égal à l’un des GUID d’entrée de mappage. Consultez [SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry) pour obtenir une description de l’entrée de mappage.

Consultez [IDBSchemaRowset :: GetRowset](/previous-versions/windows/desktop/ms722634(v=vs.85)) dans le SDK Windows.

## <a name="idbschemarowsetimplgetschemas"></a><a name="getschemas"></a> IDBSchemaRowsetImpl :: GetSchemas

Retourne une liste d’ensembles de lignes de schéma accessibles par [IDBSchemaRowsetImpl::GetRowset](#getrowset).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>Paramètres

*pcSchemas*<br/>
[out] Pointeur désignant un **ULONG** complété du nombre de schémas.

*prgSchemas*<br/>
[out] Pointeur désignant un tableau de GUID complété d’un pointeur désignant un tableau de GUID d’ensembles de lignes de schéma.

*prgRest*<br/>
[out] Pointeur désignant un tableau de **ULONG** qui doit être complété du tableau de restrictions.

### <a name="remarks"></a>Notes

Cette méthode retourne un tableau de tous les ensembles de lignes de schéma pris en charge par le fournisseur. Consultez [IDBSchemaRowset :: GetSchemas](/previous-versions/windows/desktop/ms719605(v=vs.85)) dans la SDK Windows.

L’implémentation de cette fonction impose à l’utilisateur de disposer d’un mappage de schéma dans la classe session. À partir des informations de mappage de schéma, elle répond ensuite avec le tableau de GUID des schémas contenus dans le mappage. Il s’agit des schémas pris en charge par le fournisseur.

## <a name="see-also"></a>Voir aussi

[Classes d’ensemble de lignes de schéma et classes typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider)
