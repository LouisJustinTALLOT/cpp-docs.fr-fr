---
title: CUtlProps, classe
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
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
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: bbeae4faad4d650d8dc44a61a22b1fcc63a0bc15
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441035"
---
# <a name="cutlprops-class"></a>CUtlProps, classe

Implémente des propriétés pour diverses OLE DB interfaces de propriété (par exemple, `IDBProperties`, `IDBProperties`et `IRowsetInfo`).

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe qui contient l' `BEGIN_PROPSET_MAP`.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[GetPropValue](#getpropvalue)|Obtient une propriété à partir d’un jeu de propriétés.|
|[IsValidValue](#isvalidvalue)|Utilisé pour valider une valeur avant de définir une propriété.|
|[OnInterfaceRequested](#oninterfacerequested)|Gère les demandes pour une interface facultative lorsqu’un consommateur appelle une méthode sur une interface de création d’objet.|
|[OnPropertyChanged](#onpropertychanged)|Appelée après la définition d’une propriété pour gérer les propriétés chaînées.|
|[SetPropValue](#setpropvalue)|Définit une propriété dans un jeu de propriétés.|

## <a name="remarks"></a>Notes

La plupart de cette classe est un détail d’implémentation.

`CUtlProps` contient deux membres pour la définition des propriétés en interne : [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) et [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).

Pour plus d’informations sur les macros utilisées dans un mappage de jeu de propriétés, consultez [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) et [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="getpropvalue"></a>CUtlProps :: GetPropValue

Obtient une propriété à partir d’un jeu de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Paramètres

*pguidPropSet*<br/>
dans GUID pour PropSet.

*dwPropId*<br/>
dans Index de la propriété.

*pvValue*<br/>
à Pointeur vers un variant qui contient la nouvelle valeur de propriété.

### <a name="return-value"></a>Valeur de retour

`Failure` en cas d’échec et S_OK en cas de réussite.

## <a name="isvalidvalue"></a>CUtlProps :: IsValidValue

Utilisé pour valider une valeur avant de définir une propriété.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Paramètres

*iCurSet*<br/>
Index dans le tableau de jeux de propriétés ; zéro s’il n’y a qu’un seul jeu de propriétés.

*pDBProp*<br/>
L’ID de propriété et la nouvelle valeur dans une structure [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) .

### <a name="return-value"></a>Valeur de retour

HRESULT standard. La valeur de retour par défaut est S_OK.

### <a name="remarks"></a>Notes

Si vous souhaitez exécuter des routines de validation sur une valeur que vous allez utiliser pour définir une propriété, vous devez remplacer cette fonction. Par exemple, vous pouvez valider DBPROP_AUTH_PASSWORD par rapport à une table de mots de passe pour déterminer une valeur valide.

## <a name="oninterfacerequested"></a>CUtlProps :: OnInterfaceRequested

Gère les demandes pour une interface facultative lorsqu’un consommateur appelle une méthode sur l’une des interfaces de création d’objet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Paramètres

*riid*<br/>
dans IID de l’interface demandée. Pour plus d’informations, consultez la description du paramètre *riid* de `ICommand::Execute` dans le *Guide de référence du programmeur OLE DB* (dans le *Kit de développement logiciel (SDK) MDAC*).

### <a name="remarks"></a>Notes

`OnInterfaceRequested` gère les demandes de consommateur pour une interface facultative lorsqu’un consommateur appelle une méthode sur l’une des interfaces de création d’objet (par exemple, `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`ou `ICommand`). Elle définit la propriété OLE DB correspondante pour l’interface demandée. Par exemple, si le consommateur demande `IID_IRowsetLocate`, `OnInterfaceRequested` définit l’interface `DBPROP_IRowsetLocate`. Cela maintient l’état correct lors de la création de l’ensemble de lignes.

Cette méthode est appelée lorsque le consommateur appelle `IOpenRowset::OpenRowset` ou `ICommand::Execute`.

Si un consommateur ouvre un objet et demande une interface facultative, le fournisseur doit définir la propriété associée à cette interface sur VARIANT_TRUE. Pour autoriser le traitement spécifique à la propriété, `OnInterfaceRequested` est appelé avant l’appel de la méthode `Execute` du fournisseur. Par défaut, `OnInterfaceRequested` gère les interfaces suivantes :

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Si vous souhaitez gérer d’autres interfaces, remplacez cette fonction dans la source de données, la session, la commande ou la classe rowset pour traiter les fonctions. Votre remplacement doit passer par les interfaces de propriétés set/obten normales pour s’assurer que les propriétés de définition définissent également toutes les propriétés chaînées (consultez [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).

## <a name="onpropertychanged"></a>CUtlProps :: OnPropertyChanged

Appelée après la définition d’une propriété pour gérer les propriétés chaînées.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Paramètres

*iCurSet*<br/>
Index dans le tableau de jeux de propriétés ; zéro s’il n’y a qu’un seul jeu de propriétés.

*pDBProp*<br/>
L’ID de propriété et la nouvelle valeur dans une structure [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) .

### <a name="return-value"></a>Valeur de retour

HRESULT standard. La valeur de retour par défaut est S_OK.

### <a name="remarks"></a>Notes

Si vous souhaitez gérer les propriétés chaînées, telles que les signets ou les mises à jour dont les valeurs sont dépendantes de la valeur d’une autre propriété, vous devez substituer cette fonction.

### <a name="example"></a>Exemple

Dans cette fonction, l’utilisateur obtient l’ID de propriété à partir du paramètre `DBPROP*`. À présent, il est possible de comparer l’ID par rapport à une propriété à chaîner. Lorsque la propriété est trouvée, `SetProperties` est appelée avec la propriété qui est maintenant définie conjointement avec l’autre propriété. Dans ce cas, si l’un d’eux obtient la propriété `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`ou `DBPROP_ORDEREDBOOKMARKS`, vous pouvez définir la propriété `DBPROP_BOOKMARKS`.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="setpropvalue"></a>CUtlProps :: SetPropValue

Définit une propriété dans un jeu de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Paramètres

*pguidPropSet*<br/>
dans GUID pour PropSet.

*dwPropId*<br/>
dans Index de la propriété.

*pvValue*<br/>
dans Pointeur vers un variant qui contient la nouvelle valeur de propriété.

### <a name="return-value"></a>Valeur de retour

`Failure` en cas d’échec et S_OK en cas de réussite.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)