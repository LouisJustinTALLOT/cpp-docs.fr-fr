---
title: Runtimeclass::gettrustlevel, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: adcec3f4a531a6c48e0995468994900124746e4b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015129"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel, méthode

Obtient le niveau de confiance de l’actuel **RuntimeClass** objet.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Paramètres
*trustLvl*  
Lorsque cette opération se termine, le niveau de confiance de l’actuel **RuntimeClass** objet.

## <a name="return-value"></a>Valeur de retour

Toujours S_OK.

## <a name="remarks"></a>Notes

Une erreur d’assertion est émise si `__WRL_STRICT__` ou `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` n’est pas définie.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
 [RuntimeClass, classe](../windows/runtimeclass-class.md)