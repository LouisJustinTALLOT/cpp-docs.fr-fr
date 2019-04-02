---
title: ActivationFactoryCallback (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 93db10e19cce0658bf731c14e7ac76b575841bf3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784402"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback (fonction)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Paramètres

*activationId*<br/>
Handle vers une chaîne qui spécifie un nom de classe runtime.

*ppFactory*<br/>
Lorsque cette opération se termine, une fabrique d’activation qui correspond au paramètre *activationId*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. HRESULT d’échec probable sont CLASS_E_CLASSNOTAVAILABLE et E_INVALIDARG.

## <a name="remarks"></a>Notes

Obtient la fabrique d’activation pour l’ID d’activation spécifié.

Le Runtime Windows appelle cette fonction de rappel pour demander un objet spécifié par son nom de classe runtime.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)