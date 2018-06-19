---
title: Alignement avec malloc | Documents Microsoft
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
ms.openlocfilehash: d503d0dd891c651a405cb79bb5ce50996f46cff6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368663"
---
# <a name="malloc-alignment"></a>Alignement avec malloc
[malloc](../c-runtime-library/reference/malloc.md) est garantie pour retourner la mémoire qui est obligatoirement aligné correctement pour le stockage de tout objet comportant un alignement fondamentaux et qui peut être contenue quantité de mémoire qui est allouée. A *alignement fondamentaux* est un alignement est inférieur ou égal à l’alignement du plus grand qui est pris en charge par l’implémentation d’une spécification d’alignement. (Dans Visual C++, il s’agit l’alignement est requis pour un `double`, ou 8 octets. Dans un code qui cible les plateformes 64 bits, il s’agit de 16 octets.) Par exemple, une allocation de quatre octets est alignée sur une limite qui prend en charge de n’importe quel objet de quatre octets ou plus petit.  
  
 Visual C++ autorise des types qui ont *étendus alignement*, qui sont également appelés *trop forte aligné* types. Par exemple, les types SSE [__m128](../cpp/m128.md) et `__m256`et les types sont déclarés à l’aide de `__declspec(align( n ))` où `n` est supérieure à 8, avez étendu l’alignement. Alignement de mémoire sur une limite qui est adaptée à un objet qui nécessite un alignement de l’étendue n’est pas garanti par `malloc`. Pour allouer de la mémoire pour les types alignés de manière excessive, utilisez [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) et des fonctions associées.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la pile](../build/stack-usage.md)   
 [Aligner](../cpp/align-cpp.md)   
 [__declspec](../cpp/declspec.md)