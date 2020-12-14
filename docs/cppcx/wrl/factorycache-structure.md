---
description: 'En savoir plus sur : structure FactoryCache'
title: FactoryCache (structure)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 3e9ee084a063eb8094c309dee412a8793801921b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198547"
---
# <a name="factorycache-structure"></a>FactoryCache (structure)

Prend en charge l’infrastructure de la bibliothèque de modèles C++ Windows Runtime et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Notes

Contient l’emplacement d’une fabrique de classe et d’une valeur qui identifie un objet de classe WRT ou COM inscrit.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

Nom                              | Description
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache :: cookie](#cookie)   | Contient une valeur qui identifie un Windows Runtime inscrit ou un objet de classe COM, et qui est ensuite utilisée pour annuler l’inscription de l’objet.
[FactoryCache :: Factory](#factory) | Pointe vers une fabrique de classes Windows Runtime ou COM.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FactoryCache`

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="factorycachecookie"></a><a name="cookie"></a> FactoryCache :: cookie

Prend en charge l’infrastructure de la bibliothèque de modèles C++ Windows Runtime et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Notes

Contient une valeur qui identifie un Windows Runtime inscrit ou un objet de classe COM, et qui est ensuite utilisée pour annuler l’inscription de l’objet.

## <a name="factorycachefactory"></a><a name="factory"></a> FactoryCache :: Factory

Prend en charge l’infrastructure de la bibliothèque de modèles C++ Windows Runtime et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Notes

Pointe vers une fabrique de classes Windows Runtime ou COM.
