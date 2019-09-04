---
title: __faststorefence
ms.date: 09/02/2019
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: d11a20666612fe1bca22f5d46b93e898dae375f6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222181"
---
# <a name="__faststorefence"></a>__faststorefence

**Section spécifique à Microsoft**

Garantit que chaque référence mémoire précédente, y compris les références mémoire de charge et de stockage, est globalement visible avant toute référence mémoire suivante.

## <a name="syntax"></a>Syntaxe

```C
void __faststorefence();
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__faststorefence`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Génère une séquence d’instructions de barrière de mémoire complète qui garantit que les opérations de chargement et de stockage émises avant que l’intrinsèque soient visibles globalement avant la poursuite de l’exécution. L'effet est comparable à l'intrinsèque `_mm_mfence` sur toutes les plateformes x64, mais plus rapide que ce dernier.

Sur la plateforme AMD64, cette routine génère une instruction qui est une délimitation de stockage plus rapide que l'instruction `sfence`. Pour le code à durée critique, utilisez cet intrinsèque à la place de `_mm_sfence` uniquement sur les plateformes AMD64. Sur les plateformes Intel x64, l'instruction `_mm_sfence` est plus rapide.

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
