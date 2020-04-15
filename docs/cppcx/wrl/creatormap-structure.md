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
ms.openlocfilehash: 1527f81694d1d809d585f3f6504c0e6433a2c26b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372603"
---
# <a name="creatormap-structure"></a>CreatorMap (structure)

Prend en charge l’infrastructure windows Runtime CMD Template Library et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Notes

Contient des informations sur la façon d’initialiser, de vous inscrire et de ne pas enregistrer les objets.

`CreatorMap` contient les informations suivantes :

- Comment initialiser, enregistrer et désinscrire les objets.

- Comment comparer les données d’activation en fonction d’une usine CLASSIQUE COM ou Windows Runtime.

- Informations sur le cache d’usine et le nom du serveur pour une interface.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

Nom                                          | Description
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Représente un identifiant d’objet qui est identifié soit par un IDENTIFIANT de classe COM classique ou un nom Windows Runtime.
[CreatorMap::factoryCache](#factorycache)     | Stocke le pointeur à `CreatorMap`la cache d’usine pour le .
[CreatorMap::factoryCreator](#factorycreator) | Crée une usine `CreatorMap`pour les spécifiés .
[CreatorMap::serverName](#servername)         | Stocke le nom `CreatorMap`du serveur pour le .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CreatorMap`

## <a name="requirements"></a>Spécifications

**En-tête:** module.h

**Espace nom:** Microsoft::WRL::Details

## <a name="creatormapactivationid"></a><a name="activationid"></a>CreatorMap::activationId

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

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
Une fonction qui récupère le nom Windows runtime d’un objet.

### <a name="remarks"></a>Notes

Représente un identifiant d’objet qui est identifié soit par un IDENTIFIANT de classe COM classique ou un nom Windows runtime.

## <a name="creatormapfactorycache"></a><a name="factorycache"></a>CreatorMap::factoryCache

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Notes

Stocke le pointeur à `CreatorMap`la cache d’usine pour le .

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a>CreatorMap::factoryCreator

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
L’un des enumérateurs [RuntimeClassType.](runtimeclasstype-enumeration.md)

*Entrée*<br/>
Un CreatorMap.

*iidClassFactory iidClassFactory*<br/>
L’interface ID d’une usine de classe.

*usine*<br/>
Lorsque l’opération se termine, l’adresse d’une usine de classe.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Crée une usine pour le CreatorMap spécifié.

## <a name="creatormapservername"></a><a name="servername"></a>CreatorMap::serverName

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Notes

Stocke le nom du serveur pour le CreatorMap.
