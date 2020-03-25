---
title: CreateClassFactory, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 0467a9a1341e29a61a3b32d999769b01385f641f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214056"
---
# <a name="createclassfactory-function"></a>CreateClassFactory, fonction

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

*entry*<br/>
Pointeur vers un [CreatorMap](creatormap-structure.md) qui contient les informations d’initialisation et d’inscription relatives au paramètre *riid*.

*riid*<br/>
Référence à un ID d’interface.

*ppFactory*<br/>
Si cette opération se termine correctement, pointeur vers une fabrique de classe.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Une erreur d’assertion est émise si la *fabrique* de paramètres de modèle ne dérive pas de l’interface `IClassFactory`.

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](microsoft-wrl-wrappers-details-namespace.md)
