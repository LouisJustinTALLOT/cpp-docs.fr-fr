---
title: Runtimeclass::Release, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 0bd6f9e2-ad90-4de6-adef-a6286f458cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0cb7af376e577a53f888425519108dedf01b7f1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612050"
---
# <a name="runtimeclassrelease-method"></a>RuntimeClass::Release, méthode

Effectue une opération de libération de COM sur actuel **RuntimeClass** objet.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Si le décompte de références devient égal à zéro, le **RuntimeClass** objet est supprimé.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](../windows/runtimeclass-class.md)