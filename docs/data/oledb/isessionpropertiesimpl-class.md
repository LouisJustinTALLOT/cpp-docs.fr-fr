---
description: 'En savoir plus sur : classe Isessionpropertiesimpl,'
title: ISessionPropertiesImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- ISessionPropertiesImpl.SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: 6b20331de5419de868d6739a010eb5df1548a94e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287032"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl, classe

Fournit une implémentation de l’interface [ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `ISessionPropertiesImpl` .

*PropClass*<br/>
Classe de propriété définissable par l’utilisateur qui A par défaut la valeur *T*.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[GetProperties](#getproperties)|Retourne la liste des propriétés dans le groupe de propriétés de session qui sont actuellement définies sur la session.|
|[SetProperties](#setproperties)|Définit les propriétés du groupe de propriétés de session.|

## <a name="remarks"></a>Notes

Interface obligatoire sur les sessions. Cette classe implémente les propriétés de session en appelant une fonction statique définie par le [mappage de jeu de propriétés](./macros-for-ole-db-provider-templates.md#begin_propset_map). Le mappage de jeu de propriétés doit être spécifié dans votre classe de session.

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a> Isessionpropertiesimpl, :: GetProperties

Retourne la liste des propriétés du groupe de propriétés `DBPROPSET_SESSION` qui sont actuellement définies sur la session.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Paramètres

Consultez [ISessionProperties :: GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a> Isessionpropertiesimpl, :: SetProperties

Définit des propriétés dans le `DBPROPSET_SESSION` groupe de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [ISessionProperties :: SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
