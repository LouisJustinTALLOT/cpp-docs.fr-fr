---
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
ms.openlocfilehash: 44d06f317661059bea92d8c6f27955606a964bb7
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335948"
---
# <a name="creatormap-structure"></a>CreatorMap (structure)

Prend en charge l’infrastructure de la bibliothèque de modèles Windows Runtime C++ et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Notes

Contient des informations sur la façon d’initialiser, inscrire et annuler l’inscription d’objets.

`CreatorMap` contient les informations suivantes :

- Guide pratique pour initialiser, inscrire et annuler l’inscription d’objets.

- Comment comparer les données d’activation en fonction d’une fabrique classique COM ou Windows Runtime.

- Informations sur la fabrique du cache et nom de serveur pour une interface.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

Nom                                          | Description
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Représente un ID d’objet qui est identifié par un ID de classe COM classique ou un nom de Windows Runtime.
[CreatorMap::factoryCache](#factorycache)     | Stocke le pointeur vers le cache de fabrication pour le `CreatorMap`.
[CreatorMap::factoryCreator](#factorycreator) | Crée une fabrique pour spécifié `CreatorMap`.
[CreatorMap::serverName](#servername)         | Stocke le nom du serveur pour le `CreatorMap`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CreatorMap`

## <a name="requirements"></a>Spécifications

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="activationid"></a>CreatorMap::activationId

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
ID d’interface.

*getRuntimeName*<br/>
Une fonction qui Récupère le nom du runtime Windows d’un objet.

### <a name="remarks"></a>Notes

Représente un ID d’objet qui est identifié par un ID de classe COM classique ou un nom de runtime de Windows.

## <a name="factorycache"></a>CreatorMap::factoryCache

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Notes

Stocke le pointeur vers le cache de fabrication pour le `CreatorMap`.

## <a name="factorycreator"></a>CreatorMap::factoryCreator

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Paramètres

*currentflags*<br/>
Parmi les [RuntimeClassType](runtimeclasstype-enumeration.md) énumérateurs.

*entry*<br/>
Un CreatorMap.

*iidClassFactory*<br/>
L’ID d’interface d’une fabrique de classe.

*factory*<br/>
Lorsque l’opération terminée, l’adresse d’une fabrique de classe.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Crée une fabrique pour la CreatorMap spécifié.

## <a name="servername"></a>CreatorMap::serverName

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Notes

Stocke le nom du serveur pour le CreatorMap.
