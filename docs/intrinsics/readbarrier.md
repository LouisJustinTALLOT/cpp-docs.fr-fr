---
title: _ReadBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: d898f85398fffa79a9b484f0f82343b1675b61e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565163"
---
# <a name="readbarrier"></a>_ReadBarrier

**Section spécifique à Microsoft**

Limite les optimisations du compilateur qui peuvent réordonnancer les opérations d'accès à la mémoire sur le point de l'appel.

> [!CAUTION]
>  Les intrinsèques `_ReadBarrier`, `_WriteBarrier` et `_ReadWriteBarrier` du compilateur et la macro `MemoryBarrier` sont tous déconseillés et ne doivent pas être utilisés. Pour la communication entre threads, utilisez des mécanismes tels que [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) et [std::atomic\<T >](../standard-library/atomic.md) qui sont définies dans le [bibliothèque Standard C++](../standard-library/cpp-standard-library-reference.md). Pour accéder au matériel, utilisez le [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur avec la [volatile](../cpp/volatile-cpp.md) mot clé.

## <a name="syntax"></a>Syntaxe

```
void _ReadBarrier(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_ReadBarrier`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

L'intrinsèque `_ReadBarrier` limite les optimisations du compilateur qui peuvent supprimer ou réordonnancer les opérations d'accès à la mémoire sur le point de l'appel.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)