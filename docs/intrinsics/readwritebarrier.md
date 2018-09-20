---
title: L’intrinsèque _ReadWriteBarrier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadWriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d9b970453e33aa12590f935689361d239025af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440366"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Section spécifique à Microsoft**

Limite les optimisations du compilateur qui peuvent réordonnancer les accès à la mémoire sur le point de l'appel.

> [!CAUTION]
>  Les intrinsèques `_ReadBarrier`, `_WriteBarrier` et `_ReadWriteBarrier` du compilateur et la macro `MemoryBarrier` sont tous déconseillés et ne doivent pas être utilisés. Pour la communication entre threads, utilisez des mécanismes tels que [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) et [std::atomic\<T >](../standard-library/atomic.md), qui sont définies dans le [bibliothèque Standard C++](../standard-library/cpp-standard-library-reference.md). Pour accéder au matériel, utilisez le [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur avec la [volatile](../cpp/volatile-cpp.md) mot clé.

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