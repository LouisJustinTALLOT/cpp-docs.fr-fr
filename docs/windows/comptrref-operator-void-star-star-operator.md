---
title: ComPtrRef::operator void **, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 468b38dac2082e47e94e4bd52af50d77327f5ef4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590687"
---
# <a name="comptrrefoperator-void-operator"></a>ComPtrRef::operator void\* \* opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
operator void**() const;
```

## <a name="remarks"></a>Notes

Supprime actuel **ComPtrRef** d’objet, convertit le pointeur vers l’interface qui a été représenté par le **ComPtrRef** objet sous la forme d’un pointeur à pointeur-à **void**, puis Retourne le pointeur de cast.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[ComPtrRef, classe](../windows/comptrref-class.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)