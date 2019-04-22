---
title: _ReadWriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: 9da26b685be90bd349d6bfe56c4ad980541d09c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026751"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Section spécifique à Microsoft**

Limite les optimisations du compilateur qui peuvent réordonnancer les accès à la mémoire sur le point de l'appel.

> [!CAUTION]
>  Les intrinsèques `_ReadBarrier`, `_WriteBarrier` et `_ReadWriteBarrier` du compilateur et la macro `MemoryBarrier` sont tous déconseillés et ne doivent pas être utilisés. Pour la communication entre threads, utilisez des mécanismes tels que [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) et [std::atomic\<T >](../standard-library/atomic.md), qui sont définies dans le [ C++ debibliothèqueStandard](../standard-library/cpp-standard-library-reference.md). Pour accéder au matériel, utilisez le [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur avec la [volatile](../cpp/volatile-cpp.md) mot clé.

## <a name="syntax"></a>Syntaxe

```
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_ReadWriteBarrier`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

L'intrinsèque `_ReadWriteBarrier` limite les optimisations du compilateur qui peuvent supprimer ou réordonnancer les accès à la mémoire sur le point de l'appel.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_WriteBarrier](../intrinsics/writebarrier.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)