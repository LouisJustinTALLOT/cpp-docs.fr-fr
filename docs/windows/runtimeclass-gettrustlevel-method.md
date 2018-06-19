---
title: Runtimeclass::gettrustlevel, méthode | Documents Microsoft
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
ms.openlocfilehash: bc588950cc8752a7c2b8e1ddf00b2193aaf0f395
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892629"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel, méthode

Obtient le niveau de confiance de l’objet RuntimeClass actuel.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Paramètres

*trustLvl*  
Lorsque cette opération est terminée, le niveau de confiance de l’objet RuntimeClass actuel.

## <a name="return-value"></a>Valeur de retour

Toujours S_OK.

## <a name="remarks"></a>Notes

Une erreur d’assertion est émise si &#95; &#95;WRL_STRICT&#95; &#95; ou &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; n’est pas définie.

## <a name="requirements"></a>Spécifications

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](../windows/runtimeclass-class.md)