---
title: Module::unregisterwinrtobject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterWinRTObject method
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88cafb7796ba0dfd1e37902821872e860ddc4baf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592182"
---
# <a name="moduleunregisterwinrtobject-method"></a>Module::UnregisterWinRTObject, méthode

Annule l’inscription d’un ou plusieurs objets Windows Runtime afin que les autres applications ne peuvent pas s’y connecter.

## <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Paramètres

*Cookie*  
Pointeur vers une valeur qui identifie l’objet de classe dont l’inscription doit être révoqué.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
[Module, classe](../windows/module-class.md)