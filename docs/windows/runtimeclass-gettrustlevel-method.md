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
ms.openlocfilehash: c714f37a53e111c90333352610fd73532ac86fe7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599830"
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