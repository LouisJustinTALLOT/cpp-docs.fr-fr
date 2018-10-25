---
title: CUtlProps, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- CUtlProps
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
dev_langs:
- C++
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7d398f33f6f3cded62ca95cc49314bcb0119f10
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075087"
---
# <a name="cutlprops-class"></a>CUtlProps, classe

Implémente des propriétés d’une série d’interfaces de propriété OLE DB (par exemple, `IDBProperties`, `IDBProperties`, et `IRowsetInfo`).

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Paramètres

*T*<br/>
La classe qui contient le `BEGIN_PROPSET_MAP`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[GetPropValue](#getpropvalue)|Obtient une propriété à partir d’un jeu de propriétés.|
|[IsValidValue](#isvalidvalue)|Utilisé pour valider une valeur avant de définir une propriété.|
|[OnInterfaceRequested](#oninterfacerequested)|Gère les demandes d’une interface facultative lorsqu’un consommateur appelle une méthode sur une interface de la création d’objet.|
|[OnPropertyChanged](#onpropertychanged)|Appelé après la définition d’une propriété de gérer des propriétés chaînées.|
|[SetPropValue](#setpropvalue)|Définit une propriété dans un jeu de propriétés.|

## <a name="remarks"></a>Notes

La plupart de cette classe est un détail d’implémentation.

`CUtlProps` contient deux membres pour définir les propriétés en interne : [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) et [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).

Pour plus d’informations sur les macros utilisées dans un mappage de jeu de propriétés, consultez [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) et [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="getpropvalue"></a> CUtlProps::GetPropValue

Obtient une propriété à partir d’un jeu de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Paramètres

*pguidPropSet*<br/>
[in] Le GUID pour le PropSet.

*dwPropId*<br/>
[in] L’index de la propriété.

*pvValue*<br/>
[out] Un pointeur vers un variant qui contient la nouvelle valeur de propriété.

### <a name="return-value"></a>Valeur de retour

`Failure` sur la défaillance et S_OK en cas de réussite.

## <a name="isvalidvalue"></a> CUtlProps::IsValidValue

Utilisé pour valider une valeur avant de définir une propriété.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Paramètres

*iCurSet*<br/>
L’index dans le tableau de jeu de propriétés ; zéro s’il n'existe qu’une seule propriété ensemble.

*pDBProp*<br/>
L’ID de propriété et la nouvelle valeur dans un [DBPROP](/previous-versions/windows/desktop/ms717970) structure.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard. La valeur de retour par défaut est S_OK.

### <a name="remarks"></a>Notes

Si vous avez des routines de validation à exécuter sur une valeur que vous allez utiliser pour définir une propriété, vous devez substituer cette fonction. Par exemple, vous pourriez valider DBPROP_AUTH_PASSWORD sur une table de mot de passe pour déterminer une valeur valide.

## <a name="oninterfacerequested"></a> CUtlProps::OnInterfaceRequested

Gère les demandes d’une interface facultative lorsqu’un consommateur appelle une méthode sur l’un de l’objet des interfaces de création.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Paramètres

*riid*<br/>
[in] IID pour l’interface demandée. Pour plus d’informations, consultez la description de la *riid* paramètre de `ICommand::Execute` dans le *de référence du programmeur OLE DB* (dans le *MDAC SDK*).

### <a name="remarks"></a>Notes

`OnInterfaceRequested` gère les demandes de consommateur d’une interface facultative lorsqu’un consommateur appelle une méthode sur l’un de l’objet des interfaces de création (tel que `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`, ou `ICommand`). Il définit la propriété OLE DB correspondante pour l’interface demandée. Par exemple, si le consommateur demande `IID_IRowsetLocate`, `OnInterfaceRequested` définit le `DBPROP_IRowsetLocate` interface. Cela tient à jour l’état correct lors de la création de l’ensemble de lignes.

Cette méthode est appelée lorsque le consommateur appelle `IOpenRowset::OpenRowset` ou `ICommand::Execute`.

Si un consommateur s’ouvre un objet et demande une interface facultative, le fournisseur doit définir la propriété associée à cette interface avec la valeur VARIANT_TRUE. Pour permettre le traitement spécifique à la propriété, `OnInterfaceRequested` est appelée avant que le fournisseur `Execute` méthode est appelée. Par défaut, `OnInterfaceRequested` gère les interfaces suivantes :

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Si vous souhaitez gérer d’autres interfaces, remplacez cette fonction dans votre classe de source, de session, de commande ou d’ensemble de lignes de données pour les fonctions de processus. Votre substitution doit passer par les interfaces de propriétés set/get normal pour vous assurer que la définition des propriétés définit également toutes les propriétés chaînées (consultez [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).

## <a name="onpropertychanged"></a> CUtlProps::OnPropertyChanged

Appelé après la définition d’une propriété de gérer des propriétés chaînées.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Paramètres

*iCurSet*<br/>
L’index dans le tableau de jeu de propriétés ; zéro s’il n'existe qu’une seule propriété ensemble.

*pDBProp*<br/>
L’ID de propriété et la nouvelle valeur dans un [DBPROP](/previous-versions/windows/desktop/ms717970) structure.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard. La valeur de retour par défaut est S_OK.

### <a name="remarks"></a>Notes

Si vous souhaitez gérer des propriétés chaînées, telles que les signets ou mises à jour dont les valeurs dépendent de la valeur d’une autre propriété, vous devez substituer cette fonction.

### <a name="example"></a>Exemple

Dans cette fonction, l’utilisateur obtient l’ID de propriété à partir de la `DBPROP*` paramètre. À présent, il est possible de comparer l’identificateur par rapport à une propriété de chaîne. Lorsque la propriété est trouvée, `SetProperties` est appelée avec la propriété qui sera désormais être définie conjointement avec l’autre propriété. Dans ce cas, si elles Obtient le `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, ou `DBPROP_ORDEREDBOOKMARKS` propriété, peut définir le `DBPROP_BOOKMARKS` propriété.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="setpropvalue"></a> CUtlProps::SetPropValue

Définit une propriété dans un jeu de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Paramètres

*pguidPropSet*<br/>
[in] Le GUID pour le PropSet.

*dwPropId*<br/>
[in] L’index de la propriété.

*pvValue*<br/>
[in] Un pointeur vers un variant qui contient la nouvelle valeur de propriété.

### <a name="return-value"></a>Valeur de retour

`Failure` sur la défaillance et S_OK en cas de réussite.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)