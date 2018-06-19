---
title: Limites du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc7cd26add0a46bab8df7669fb6dfb6060b0010e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412135"
---
# <a name="compiler-limits"></a>Limites du compilateur
La norme C++ recommande certaines limites pour diverses constructions de langage. La liste suivante indique les cas où le compilateur Visual C++ n'implémente pas les limites recommandées. Le premier nombre est la limite établie dans la norme ISO C++ 11 (INCITS/ISO/IEC 14882-2011[2012], Annexe B) et le deuxième nombre est la limite implémentée par Visual C++ :  
  
-   Niveaux d’imbrication des instructions composées, structures de contrôle d’itération et sélection de contrôlent les structures - standard C++ : 256, compilateur Visual C++ : dépend de la combinaison d’instructions imbriquées, mais généralement entre 100 et 110.  
  
-   Paramètres de définition d’une macro - norme C++ : 256, compilateur Visual C++ : 127.  
  
-   Arguments dans une seule invocation macro - norme C++ : 256, compilateur Visual C++ 127.  
  
-   Littéral de chaîne littéral ou étendu de chaîne de caractères dans un caractère (après concaténation) - norme C++ : 65536, compilateur Visual C++ : 65 535 caractères codés sur un octet, y compris le `null` marque de fin et 32 767 caractères codés sur deux octets, y compris le `null` marque de fin.  
  
-   Niveaux de la classe imbriquée, structure ou unions définitions dans un seul `struct-declaration-list` -norme C++ : 256, compilateur Visual C++ : 16.  
  
-   Initialiseurs de membres dans une définition de constructeur - norme C++ : 6144, compilateur Visual C++ : au moins 6144.  
  
-   Portée qualifications d’un identificateur - norme C++ : 256, compilateur Visual C++ : 127.  
  
-   Imbriqués `extern` spécifications - norme C++ : 1024, le compilateur Visual C++ : 9 (sans compter l’implicite `extern` spécification dans la portée globale ou 10, si vous comptez implicite `extern` spécification dans la portée globale...  
  
-   Arguments de modèle dans une déclaration de modèle - norme C++ : 1024, le compilateur Visual C++ : 2046.  
  
## <a name="see-also"></a>Voir aussi  
 [Comportement non standard](../cpp/nonstandard-behavior.md)