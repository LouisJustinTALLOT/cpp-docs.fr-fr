---
title: Alignement avec malloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa6e2748691eeb8a11834bcf8e6962252be7ab3f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712060"
---
# <a name="malloc-alignment"></a>Alignement avec malloc

[malloc](../c-runtime-library/reference/malloc.md) est garanti pour retourner une mémoire qui est correctement alignée pour stocker un objet qui a un alignement simple et qui peut contenir la quantité de mémoire qui est allouée. Un *alignement fondamental* est un alignement qui est inférieure ou égale à la plus grand alignement pris en charge par l’implémentation sans spécification d’alignement. (Dans Visual C++, il s’agit d’alignement qui est requis pour un `double`, ou 8 octets. Dans un code qui cible les plateformes 64 bits, il s’agit de 16 octets.) Par exemple, une allocation de quatre octets serait alignée sur une limite qui prend en charge de n’importe quel objet de quatre octets ou plus petits.

Visual C++ permet les types qui ont *alignement étendu*, également appelés *sur-alignés* types. Par exemple, les types de SSE [__m128](../cpp/m128.md) et `__m256`et les types qui sont déclarés à l’aide de `__declspec(align( n ))` où `n` est supérieure à 8, ont un alignement étendu. Alignement de la mémoire sur une limite qui est adaptée à un objet qui requiert l’alignement étendu n’est pas garanti par `malloc`. Pour allouer de mémoire pour les types sur-alignés, utilisez [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) et des fonctions associées.

## <a name="see-also"></a>Voir aussi

[Utilisation de la pile](../build/stack-usage.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)