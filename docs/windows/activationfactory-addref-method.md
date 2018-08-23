---
title: Activationfactory::AddRef, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method
ms.assetid: dfe96189-ddbe-410a-9f8d-5d8ecc8cc7e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9b3790e0fb3d1b304359677ddedab2b65dcfe89d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575739"
---
# <a name="activationfactoryaddref-method"></a>ActivationFactory::AddRef, méthode

Incrémente le décompte de références du courant **ActivationFactory** objet.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

## <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ActivationFactory, classe](../windows/activationfactory-class.md)