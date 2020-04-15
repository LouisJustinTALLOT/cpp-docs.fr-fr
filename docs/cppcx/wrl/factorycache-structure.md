---
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
ms.openlocfilehash: 507d35179b9fa86399e56b18171800f41eaf1f10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371483"
---
# <a name="factorycache-structure"></a>FactoryCache (structure)

Prend en charge l’infrastructure windows Runtime CMD Template Library et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Notes

Contient l’emplacement d’une usine de classe et une valeur qui identifie un wrt enregistré ou un objet de classe COM.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

Nom                              | Description
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::cookie](#cookie)   | Contient une valeur qui identifie un objet enregistré de classe Windows Runtime ou COM, et est plus tard utilisé pour déenregistrer l’objet.
[FactoryCache::usine](#factory) | Points vers une usine windows Runtime ou com.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FactoryCache`

## <a name="requirements"></a>Spécifications

**En-tête:** module.h

**Espace nom:** Microsoft::WRL::Details

## <a name="factorycachecookie"></a><a name="cookie"></a>FactoryCache::cookie

Prend en charge l’infrastructure windows Runtime CMD Template Library et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Notes

Contient une valeur qui identifie un objet enregistré de classe Windows Runtime ou COM, et est plus tard utilisé pour déenregistrer l’objet.

## <a name="factorycachefactory"></a><a name="factory"></a>FactoryCache::usine

Prend en charge l’infrastructure windows Runtime CMD Template Library et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Notes

Points vers une usine windows Runtime ou com.
