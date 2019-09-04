---
title: _ReadWriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: d755d045970da01d2eee33377c1452191eac4fe2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217975"
---
# <a name="_readwritebarrier"></a>_ReadWriteBarrier

**Section spécifique à Microsoft**

Limite les optimisations du compilateur qui peuvent réordonnancer les accès à la mémoire sur le point de l'appel.

> [!CAUTION]
> Les intrinsèques `_ReadBarrier`, `_WriteBarrier` et `_ReadWriteBarrier` du compilateur et la macro `MemoryBarrier` sont tous déconseillés et ne doivent pas être utilisés. Pour la communication entre threads, utilisez des mécanismes tels que [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) et [std:\<: Atomic T >](../standard-library/atomic.md), qui sont définis dans la [ C++ bibliothèque standard](../standard-library/cpp-standard-library-reference.md). Pour l’accès au matériel, utilisez l’option de compilateur [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) avec le mot clé [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Syntaxe

```C
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_ReadWriteBarrier`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L'intrinsèque `_ReadWriteBarrier` limite les optimisations du compilateur qui peuvent supprimer ou réordonnancer les accès à la mémoire sur le point de l'appel.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_WriteBarrier](../intrinsics/writebarrier.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
