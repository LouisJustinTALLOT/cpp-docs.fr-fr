---
description: 'En savoir plus sur : structure CreatorMap'
title: CreatorMap (structure)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 0ef3b441390a22a6c4b35f274857ccb58de030d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273044"
---
# <a name="creatormap-structure"></a>CreatorMap (structure)

Prend en charge l’infrastructure de la bibliothèque de modèles C++ Windows Runtime et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Notes

Contient des informations sur l’initialisation, l’inscription et l’annulation de l’inscription d’objets.

`CreatorMap` contient les informations suivantes :

- Comment initialiser, inscrire et désinscrire des objets.

- Comparaison des données d’activation selon une fabrique COM ou Windows Runtime classique.

- Informations sur le cache de fabrique et le nom de serveur pour une interface.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

Nom                                          | Description
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap :: activationId](#activationid)     | Représente un ID d’objet identifié par un ID de classe COM classique ou un nom de Windows Runtime.
[CreatorMap :: factoryCache](#factorycache)     | Stocke le pointeur dans le cache de fabrique pour le `CreatorMap` .
[CreatorMap :: FactoryCreator,](#factorycreator) | Crée une fabrique pour le spécifié `CreatorMap` .
[CreatorMap :: NomServeur](#servername)         | Stocke le nom du serveur pour le `CreatorMap` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CreatorMap`

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="creatormapactivationid"></a><a name="activationid"></a> CreatorMap :: activationId

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
ID d’interface.

*getRuntimeName*<br/>
Fonction qui récupère le nom Windows Runtime d’un objet.

### <a name="remarks"></a>Notes

Représente un ID d’objet identifié par un ID de classe COM classique ou un nom Windows Runtime.

## <a name="creatormapfactorycache"></a><a name="factorycache"></a> CreatorMap :: factoryCache

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Notes

Stocke le pointeur dans le cache de fabrique pour le `CreatorMap` .

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a> CreatorMap :: FactoryCreator,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Paramètres

*currentflags*<br/>
Un des énumérateurs [RuntimeClassType](runtimeclasstype-enumeration.md) .

*mention*<br/>
CreatorMap.

*iidClassFactory*<br/>
ID d’interface d’une fabrique de classe.

*usine*<br/>
Une fois l’opération terminée, l’adresse d’une fabrique de classe.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Crée une fabrique pour le CreatorMap spécifié.

## <a name="creatormapservername"></a><a name="servername"></a> CreatorMap :: NomServeur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Notes

Stocke le nom du serveur pour le CreatorMap.
