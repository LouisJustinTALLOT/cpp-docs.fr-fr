---
title: Limites du compilateur
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9663da06c97886ef1cd20ca2928944795b39dc18
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222194"
---
# <a name="compiler-limits"></a>Limites du compilateur

La norme C++ recommande certaines limites pour diverses constructions de langage. Voici une liste de cas où Microsoft C++ compilateur n’implémente pas les limites recommandées. Le premier nombre est la limite établie dans le fichier ISO C++ standard 11 (INCITS/ISO/IEC 14882-2011 [2012], annexe B) et le deuxième nombre est la limite implémentée par Microsoft C++ compilateur :

- Niveaux d’imbrication des instructions composées, structures de contrôle d’itération et structures de contrôle de sélection - C++ standard : 256, Microsoft C++ compilateur : dépend de la combinaison d’instructions qui sont imbriquées, mais en général entre 100 et 110.

- Paramètres dans une définition de macro - C++ standard : 256, Microsoft C++ compilateur : 127.

- Arguments dans un appel de macro - C++ standard : 256, Microsoft C++ compilateur 127.

- Littéral de chaîne large ou littéral de chaîne de caractères dans un caractère (après concaténation) - C++ standard : Microsoft 65536, C++ compilateur : 65 535 caractères codés sur un octet, y compris le terminateur NULL et 32 767 caractères codés sur deux, y compris le terminateur NULL.

- Niveaux de la classe imbriquée, structure ou unions définitions dans un seul `struct-declaration-list` - C++ standard : 256, Microsoft C++ compilateur : 16.

- Initialiseurs de membres dans une définition de constructeur - C++ standard : 6144, Microsoft C++ compilateur : au moins 6144.

- Portée des qualifications d’un identificateur - C++ standard : 256, Microsoft C++ compilateur : 127.

- Imbriqué **extern** spécifications - C++ standard : 1024, Microsoft C++ compilateur : 9 (sans compter le caractère implicite **extern** spécification dans la portée globale, ou 10, si vous compter le caractère implicite **extern** spécification dans la portée globale...

- Arguments template dans une déclaration de modèle - C++ standard : 1024, Microsoft C++ compilateur : 2046.

## <a name="see-also"></a>Voir aussi

[Comportement non standard](../cpp/nonstandard-behavior.md)