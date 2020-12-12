---
description: 'En savoir plus sur : fonction Activationfactorycallback ('
title: ActivationFactoryCallback (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 9398b3f681e32c7a73b46de549ce7c41a3af6196
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204613"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback (fonction)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Paramètres

*activationId*<br/>
Handle vers une chaîne qui spécifie un nom de classe au moment de l’exécution.

*ppFactory*<br/>
Lorsque cette opération est terminée, une fabrique d’activation qui correspond au paramètre *activationId*.

## <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. Les HRESULT d’échec probables sont CLASS_E_CLASSNOTAVAILABLE et E_INVALIDARG.

## <a name="remarks"></a>Notes

Obtient la fabrique d’activation pour l’ID d’activation spécifié.

Le Windows Runtime appelle cette fonction de rappel pour demander un objet spécifié par son nom de classe d’exécution.

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
