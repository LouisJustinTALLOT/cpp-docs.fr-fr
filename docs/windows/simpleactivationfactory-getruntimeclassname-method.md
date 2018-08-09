---
title: Simpleactivationfactory::getruntimeclassname, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
dev_langs:
- C++
ms.assetid: 3aa07487-9a42-46f8-8893-37ba6315e50b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c6c6731c4c7787f3d81a4e67eac2861a46bfe1a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644406"
---
# <a name="simpleactivationfactorygetruntimeclassname-method"></a>SimpleActivationFactory::GetRuntimeClassName, méthode

Obtient le nom de classe d’exécution d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Paramètres

*runtimeName*  
Lorsque cette opération se termine, le nom de la classe runtime.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Si &#95; &#95;WRL_STRICT&#95; &#95; est défini, une erreur d’assertion est émise si la classe spécifiée par le `Base` n’est pas dérivé de paramètre de modèle de classe [RuntimeClass](../windows/runtimeclass-class.md), ou n’est pas configuré avec le WinRt ou WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeur d’énumération.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
 [SimpleActivationFactory, classe](../windows/simpleactivationfactory-class.md)