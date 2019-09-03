---
title: _WriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: a41f4c6c5cdd6b72e76a596622912e88fbd03f34
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219316"
---
# <a name="_writebarrier"></a>_WriteBarrier

**Section spécifique à Microsoft**

Limite les optimisations du compilateur qui peuvent réordonnancer les opérations d'accès à la mémoire sur le point de l'appel.

> [!CAUTION]
> Les intrinsèques `_ReadBarrier`, `_WriteBarrier` et `_ReadWriteBarrier` du compilateur et la macro `MemoryBarrier` sont tous déconseillés et ne doivent pas être utilisés. Pour la communication entre threads, utilisez des mécanismes tels que [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) et [std:\<: Atomic T >](../standard-library/atomic.md), qui sont définis dans la [ C++ bibliothèque standard](../standard-library/cpp-standard-library-reference.md). Pour l’accès au matériel, utilisez l’option de compilateur [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) avec le mot clé [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Syntaxe

```C
void _WriteBarrier(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L'intrinsèque `_WriteBarrier` limite les optimisations du compilateur qui peuvent supprimer ou réordonnancer les opérations d'accès à la mémoire sur le point de l'appel.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
