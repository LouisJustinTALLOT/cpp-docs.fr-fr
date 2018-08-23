---
title: Comptr::Detach, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: b9016775-1ade-4581-be1f-0d6f9c2ca658
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84db0a82dfe6f9333f6a533aa9bc2bb529854fa2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593410"
---
# <a name="comptrdetach-method"></a>ComPtr::Detach, méthode

Il dissocie **ComPtr** objet à partir de l’interface qu’elle représente.

## <a name="syntax"></a>Syntaxe

```cpp
T* Detach();
```

## <a name="return-value"></a>Valeur de retour

Un pointeur vers l’interface qui a été représenté par cet **ComPtr** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ComPtr, classe](../windows/comptr-class.md)