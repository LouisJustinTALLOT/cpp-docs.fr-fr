---
title: Limites du compilateur
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: e0e2381d88c727466b06a97c72826d2d5e15a87b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233767"
---
# <a name="compiler-limits"></a>Limites du compilateur

La norme C++ recommande certaines limites pour diverses constructions de langage. La liste suivante répertorie les cas où le compilateur Microsoft C++ n’implémente pas les limites recommandées. Le premier nombre correspond à la limite établie dans la norme ISO C++ 11 (INCITSs/ISO/IEC 14882-2011 [2012], annexe B) et le deuxième nombre correspond à la limite implémentée par le compilateur Microsoft C++ :

- Imbrication des niveaux d’instructions composées, de structures de contrôle d’itération et de structures de contrôle de sélection-norme C++ : 256, compilateur Microsoft C++ : dépend de la combinaison d’instructions imbriquées, mais généralement entre 100 et 110.

- Paramètres dans une définition de macro-norme C++ : 256, compilateur Microsoft C++ : 127.

- Arguments dans un appel de macro-norme C++ : 256, compilateur Microsoft C++ 127.

- Caractères dans un littéral de chaîne de caractères ou un littéral de chaîne étendu (après concaténation)-norme C++ : 65536, compilateur Microsoft C++ : 65535 caractères codés sur un octet, y compris le terminateur NULL et 32767 caractères codés sur deux octets, y compris la marque de fin NULL.

- Niveaux de définitions de classes, de structures ou d’unions imbriquées dans une `struct-declaration-list` norme C++ unique : 256, compilateur Microsoft C++ : 16.

- Initialiseurs de membres dans une définition de constructeur-norme C++ : 6144, compilateur Microsoft C++ : au moins 6144.

- Qualifications de l’étendue d’un identificateur-norme C++ : 256, compilateur Microsoft C++ : 127.

- Spécifications imbriquées **`extern`** -C++ standard : 1024, compilateur Microsoft C++ : 9 (sans compter la spécification implicite **`extern`** dans la portée globale, ou 10 si vous comptez la spécification implicite **`extern`** dans la portée globale.)

- Arguments template dans une déclaration de modèle-norme C++ : 1024, compilateur Microsoft C++ : 2046.

## <a name="see-also"></a>Voir aussi

[Comportement non standard](../cpp/nonstandard-behavior.md)
