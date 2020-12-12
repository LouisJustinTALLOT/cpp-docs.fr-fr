---
description: 'En savoir plus sur : fonction Createclassfactory,'
title: CreateClassFactory (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 99565ee732843f57426f10375ffabc7680ef3c62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273057"
---
# <a name="createclassfactory-function"></a>CreateClassFactory (fonction)

Crée une fabrique produisant des instances de la classe spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>Paramètres

*flags*<br/>
Combinaison d’une ou de plusieurs valeurs d’énumération [RuntimeClassType](runtimeclasstype-enumeration.md) .

*mention*<br/>
Pointeur vers un [CreatorMap](creatormap-structure.md) qui contient les informations d’initialisation et d’inscription relatives au paramètre *riid*.

*riid*<br/>
Référence à un ID d’interface.

*ppFactory*<br/>
Si cette opération se termine correctement, pointeur vers une fabrique de classe.

## <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Une erreur d’assertion est émise si la *fabrique* de paramètres de modèle ne dérive pas de l’interface `IClassFactory` .

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL :: wrappers ::D espace de noms étails](microsoft-wrl-wrappers-details-namespace.md)
