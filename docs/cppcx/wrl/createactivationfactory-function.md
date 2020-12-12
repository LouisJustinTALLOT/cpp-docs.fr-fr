---
description: 'En savoir plus sur : fonction Createactivationfactory,'
title: CreateActivationFactory (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: 25f2181a00bb018361b05ea6570ebbadc6f7a975
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273104"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory (fonction)

Crée une fabrique qui produit des instances de la classe spécifiée pouvant être activées par le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Factory>
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,
      REFIID riid,
   _Outptr_ IUnknown **ppFactory) throw();
```

### <a name="parameters"></a>Paramètres

*flags*<br/>
Combinaison d’une ou de plusieurs valeurs d’énumération [RuntimeClassType](runtimeclasstype-enumeration.md) .

*mention*<br/>
Pointeur vers un [CreatorMap](creatormap-structure.md) qui contient les informations d’initialisation et d’inscription relatives au paramètre *riid*.

*riid*<br/>
Référence à un ID d’interface.

*ppFactory*<br/>
Si cette opération se termine correctement, pointeur vers une fabrique d’activation.

## <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Une erreur d’assertion est émise si la *fabrique* de paramètres de modèle ne dérive pas de l’interface `IActivationFactory` .

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL :: wrappers ::D espace de noms étails](microsoft-wrl-wrappers-details-namespace.md)
