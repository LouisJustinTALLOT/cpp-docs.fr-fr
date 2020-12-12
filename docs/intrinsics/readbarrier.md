---
description: 'En savoir plus sur : _ReadBarrier'
title: _ReadBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: 94ade7c8f602cf279ac75a5f0a56387c344d0fb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257488"
---
# <a name="_readbarrier"></a>_ReadBarrier

**Spécifique à Microsoft**

Limite les optimisations du compilateur qui peuvent réordonnancer les opérations d'accès à la mémoire sur le point de l'appel.

> [!CAUTION]
> Les intrinsèques `_ReadBarrier`, `_WriteBarrier` et `_ReadWriteBarrier` du compilateur et la macro `MemoryBarrier` sont tous déconseillés et ne doivent pas être utilisés. Pour la communication entre threads, utilisez des mécanismes tels que [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) et [std : \<T> : Atomic](../standard-library/atomic.md) qui sont définis dans la [bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md). Pour l’accès au matériel, utilisez l’option de compilateur [/volatile : ISO](../build/reference/volatile-volatile-keyword-interpretation.md) avec le mot clé [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Syntaxe

```C
void _ReadBarrier(void);
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_ReadBarrier`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L'intrinsèque `_ReadBarrier` limite les optimisations du compilateur qui peuvent supprimer ou réordonnancer les opérations d'accès à la mémoire sur le point de l'appel.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
