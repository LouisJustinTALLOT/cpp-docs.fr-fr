---
title: Fonction de rappel (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
ms.openlocfilehash: b39b4268213d0a4e093c27b1425cc6656b47b912
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514245"
---
# <a name="callback-function-wrl"></a>Fonction de rappel (WRL)

Crée un objet dont la fonction membre est une méthode de rappel.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   typename TDelegateInterface,
   typename TCallback
>
ComPtr<TDelegateInterface> Callback(
   TCallbackcallback
);
template<
   typename TDelegateInterface,
   typename TCallbackObject
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)()
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8,
   TArg9)
);
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
Paramètre de modèle qui spécifie l'interface du délégué à appeler lorsqu'un événement se produit.

*TCallback*<br/>
Paramètre de modèle qui spécifie le type d'un objet qui représente un objet et sa fonction membre de rappel.

*TCallbackObject*<br/>
Paramètre de modèle qui spécifie l'objet dont la fonction membre est la méthode à appeler lorsqu'un événement se produit.

*TArg1*<br/>
Paramètre de modèle qui spécifie le type du premier argument de la méthode de rappel.

*TArg2*<br/>
Paramètre de modèle qui spécifie le type du second argument de la méthode de rappel.

*TArg3*<br/>
Paramètre de modèle qui spécifie le type du troisième argument de la méthode de rappel.

*TArg4*<br/>
Paramètre de modèle qui spécifie le type du quatrième argument de la méthode de rappel.

*TArg5*<br/>
Paramètre de modèle qui spécifie le type du cinquième argument de la méthode de rappel.

*TArg6*<br/>
Paramètre de modèle qui spécifie le type du sixième argument de la méthode de rappel.

*TArg7*<br/>
Paramètre de modèle qui spécifie le type du septième argument de la méthode de rappel.

*TArg8*<br/>
Paramètre de modèle qui spécifie le type du huitième argument de la méthode de rappel.

*TArg9*<br/>
Paramètre de modèle qui spécifie le type du neuvième argument de la méthode de rappel.

*rappel*<br/>
Objet qui représente l'objet de rappel et sa fonction membre.

*object*<br/>
Objet dont la fonction membre est appelée lorsqu'un événement se produit.

*(Méthode)*<br/>
Fonction membre à appeler lorsqu'un événement se produit.

## <a name="return-value"></a>Valeur de retour

Objet dont la fonction membre est la méthode de rappel spécifiée.

## <a name="remarks"></a>Notes

La base d’un objet délégué doit être `IUnknown`, et non `IInspectable`.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)