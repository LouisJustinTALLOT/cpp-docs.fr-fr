---
title: Makeallocator::Allocate, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4dd68a3c678b7877db63167fd2c0d48a1daa7ad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411831"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline void* Allocate();
```

## <a name="return-value"></a>Valeur de retour

Si l’opération réussit, un pointeur vers la mémoire allouée ; Sinon, **nullptr**.

## <a name="remarks"></a>Notes

Alloue de la mémoire et l’associe à actuel **MakeAllocator** objet.

La taille de la mémoire allouée est la taille du type spécifié par l’actuel **MakeAllocator** paramètre de modèle.

Un développeur a besoin remplacer uniquement le **Allocate()** méthode pour implémenter un modèle d’allocation de mémoire différentes.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[MakeAllocator, classe](../windows/makeallocator-class.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)