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
ms.openlocfilehash: a9d59ca1d404e56e7d85a8f0edfe653dc5692558
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584319"
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

*arg1*  
Argument 1.

*Arg2*  
Argument 2.

*Arg3*  
Argument 3.

*Arg4*  
Argument 4.

*Arg5*  
Argument 5.

*Arg6*  
Argument 6.

*Arg7*  
Argument 7.

*Arg8*  
Argument 8.

*Arg9*  
Argument 9.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une valeur HRESULT qui décrit l’erreur.

## <a name="remarks"></a>Notes

Appelle le Gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[InvokeHelper, structure](../windows/invokehelper-structure.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)