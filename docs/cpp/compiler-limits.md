---
title: Limites du compilateur
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9e61cae1638c87f03b6fa775552408961bde6859
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189574"
---
# <a name="compiler-limits"></a>Limites du compilateur

La norme C++ recommande certaines limites pour diverses constructions de langage. La liste suivante répertorie les cas où le compilateur C++ Microsoft n’implémente pas les limites recommandées. Le premier nombre correspond à la limite établie dans la norme ISO C++ 11 (INCITS/ISO/IEC 14882-2011 [2012], annexe B) et le deuxième nombre correspond à la limite implémentée par le compilateur C++ Microsoft :

- Imbrication des niveaux d’instructions composées, de structures de contrôle d’itération et de C++ structures de contrôle de sélection C++ -standard : 256, compilateur Microsoft : dépend de la combinaison d’instructions imbriquées, mais généralement entre 100 et 110.

- Paramètres dans une définition de macro C++ : standard : 256, C++ compilateur Microsoft : 127.

- Arguments dans un appel de macro- C++ standard : 256, compilateur C++ Microsoft 127.

- Caractères dans un littéral de chaîne de caractères ou un littéral de chaîne étendu (après C++ concaténation) : standard C++ : 65536, compilateur Microsoft : 65535 caractères codés sur un octet, y compris le terminateur null et 32767 caractères codés sur deux octets, y compris la marque de fin null.

- Niveaux de définitions de classes, de structures ou d’unions imbriquées dans un C++ seul `struct-declaration-list`-standard : C++ 256, compilateur Microsoft : 16.

- Initialiseurs de membres dans une définition de C++ constructeur-standard : 6144 C++ , compilateur Microsoft : au moins 6144.

- Qualifications de l’étendue d’un identificateur C++ : standard : 256, C++ compilateur Microsoft : 127.

- Spécifications **extern** imbriquées- C++ standard : 1024, compilateur C++ Microsoft : 9 (sans compter la spécification **extern** implicite dans la portée globale, ou 10 si vous comptez la spécification **extern** implicite dans la portée globale.)

- Arguments template dans une déclaration de modèle C++ -standard : 1024, C++ compilateur Microsoft : 2046.

## <a name="see-also"></a>Voir aussi

[Comportement non standard](../cpp/nonstandard-behavior.md)
