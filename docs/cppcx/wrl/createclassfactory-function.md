---
title: CreateClassFactory (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 323fce053707d6d00d1e17b641613d15607ab6f8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040752"
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
Une combinaison d’une ou plusieurs [RuntimeClassType](runtimeclasstype-enumeration.md) valeurs d’énumération.

*entry*<br/>
Pointeur vers un [CreatorMap](creatormap-structure.md) qui contient des informations d’initialisation et d’inscription sur le paramètre *riid*.

*riid*<br/>
Référence à un ID d’interface.

*ppFactory*<br/>
Si cette opération termine avec succès, un pointeur vers une fabrique de classe.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Une erreur d’assertion est émise si le paramètre de modèle *Factory* n’est pas dérivé d’une interface `IClassFactory`.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](microsoft-wrl-wrappers-details-namespace.md)