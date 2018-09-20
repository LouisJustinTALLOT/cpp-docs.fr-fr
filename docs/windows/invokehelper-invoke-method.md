---
title: InvokeHelper::Invoke, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Invoke method
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d1addd96456a33b30259182e4490df70335d0d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408360"
---
# <a name="invokehelperinvoke-method"></a>InvokeHelper::Invoke, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>Paramètres

*arg1*<br/>
Argument 1.

*Arg2*<br/>
Argument 2.

*Arg3*<br/>
Argument 3.

*Arg4*<br/>
Argument 4.

*Arg5*<br/>
Argument 5.

*Arg6*<br/>
Argument 6.

*Arg7*<br/>
Argument 7.

*Arg8*<br/>
Argument 8.

*Arg9*<br/>
Argument 9.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une valeur HRESULT qui décrit l’erreur.

## <a name="remarks"></a>Notes

Appelle le Gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[InvokeHelper, structure](../windows/invokehelper-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)