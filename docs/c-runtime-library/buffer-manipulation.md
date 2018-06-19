---
title: Manipulation de la mémoire tampon | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7544dfa80ce0c7481846383dd812ce30b78290
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389086"
---
# <a name="buffer-manipulation"></a>Manipulation de la mémoire tampon

Utilisez ces routines pour utiliser des zones de mémoire octet par octet.

## <a name="buffer-manipulation-routines"></a>Routines de manipulation de la mémoire tampon

|Routine|Utilisez|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Copier des caractères d’une mémoire tampon à une autre jusqu’à ce qu’un caractère donné ou un nombre donné de caractères ait été copié|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Retourner le pointeur vers la première occurrence, dans un nombre spécifié de caractères, d’un caractère donné de la mémoire tampon|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Comparer un nombre spécifié de caractères entre deux mémoires tampons|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Copier un nombre spécifié de caractères d’une mémoire tampon à une autre|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Comparer le nombre spécifié de caractères de deux mémoires tampons sans tenir compte de la casse|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Copier un nombre spécifié de caractères d’une mémoire tampon à une autre|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Utiliser un caractère donné pour initialiser le nombre spécifié d’octets dans la mémoire tampon|
|[_swab](../c-runtime-library/reference/swab.md)|Échanger des octets de données et les stocker à l’emplacement spécifié|

Quand les zones source et cible se chevauchent, seul **memmove** garantit la copie correcte de la source complète.

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)
