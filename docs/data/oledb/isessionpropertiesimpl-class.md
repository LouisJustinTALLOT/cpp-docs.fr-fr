---
title: ISessionPropertiesImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: a6b2abc97a44117c0fdd7c08c61de7ba900d1115
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556307"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl, classe

Fournit une implémentation de la [ISessionProperties](https://docs.microsoft.com/previous-versions/windows/desktop/ms713721(v=vs.85)) interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `ISessionPropertiesImpl`.

*PropClass*<br/>
Une classe de propriété définis par l’utilisateur par défaut est *T*.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[GetProperties](#getproperties)|Retourne la liste des propriétés dans le groupe de propriétés de Session qui sont actuellement définies sur la session.|
|[SetProperties](#setproperties)|Définit les propriétés dans le groupe de propriétés de Session.|

## <a name="remarks"></a>Notes

Une interface obligatoire sur les sessions. Cette classe implémente les propriétés d’une session en appelant une fonction statique définie par le [mappage de jeu de propriétés](../../data/oledb/begin-propset-map.md). Le mappage de jeu de propriétés doit être spécifié dans votre classe session.

## <a name="getproperties"></a> ISessionPropertiesImpl::GetProperties

Retourne la liste des propriétés dans le `DBPROPSET_SESSION` groupe de propriétés qui sont actuellement définies sur la session.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Paramètres

Consultez [ISessionProperties::GetProperties](https://docs.microsoft.com/previous-versions/windows/desktop/ms723643(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="setproperties"></a> ISessionPropertiesImpl::SetProperties

Définit les propriétés dans le `DBPROPSET_SESSION` groupe de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [ISessionProperties::SetProperties](https://docs.microsoft.com/previous-versions/windows/desktop/ms714405(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)