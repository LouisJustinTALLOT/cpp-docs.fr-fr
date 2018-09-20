---
title: Createactivationfactory, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aed52e5ba209a826130b1a85aa866fe024174818
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424636"
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
Une combinaison d’une ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeurs d’énumération.

*entry*<br/>
Pointeur vers un [CreatorMap](../windows/creatormap-structure.md) qui contient des informations d’initialisation et d’inscription sur le paramètre *riid*.

*riid*<br/>
Référence à un ID d’interface.

*ppFactory*<br/>
Si cette opération termine avec succès, un pointeur vers une fabrique d’activation.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Une erreur d’assertion est émise si le paramètre de modèle *Factory* n’est pas dérivé d’une interface `IActivationFactory`.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](../windows/microsoft-wrl-wrappers-details-namespace.md)