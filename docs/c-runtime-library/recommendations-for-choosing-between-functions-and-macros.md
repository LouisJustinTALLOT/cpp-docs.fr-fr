---
title: Recommandations relatives au choix entre une fonction et une macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.functions
dev_langs:
- C++
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4577ac1a0e1cac90a3436809722978d119c6b557
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389632"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Recommandations relatives au choix entre une fonction et une macro
La plupart des routines de bibliothèque du Runtime Microsoft sont des fonctions compilées ou assemblées, mais certaines routines sont implémentées sous forme de macros. Lorsqu’un fichier d’en-tête déclare une fonction et une version macro d’une routine, la définition de macro est prioritaire, car elle apparaît toujours après la déclaration de fonction. Lorsque vous appelez une routine qui est implémentée à la fois comme une fonction et comme une macro, vous pouvez forcer le compilateur à utiliser la version de la fonction de deux manières :  
  
-   Mettre entre parenthèses le nom de la routine.  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   « Annuler la définition » de la définition de macro avec la directive `#undef` :  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 Si vous devez choisir entre une implémentation de fonction et de macro d’une routine de bibliothèque, considérez les compromis suivants :  
  
-   **Vitesse et taille** Le principal avantage de l’utilisation des macros est la durée d’exécution plus rapide. Lors du prétraitement, une macro est développée (remplacée par sa définition) en ligne chaque fois qu’elle est utilisée. Une définition de fonction se produit une seule fois, quel que soit le nombre d’appels dont elle fait l’objet. Les macros peuvent augmenter la taille du code, mais n’ont pas la surcharge associée aux appels de fonction.  
  
-   **Évaluation de la fonction** Une fonction correspond à une adresse ; ce n’est pas le cas d’une macro. Par conséquent, vous ne pouvez pas utiliser un nom de macro dans des contextes nécessitant un pointeur. Par exemple, vous pouvez déclarer un pointeur vers une fonction, mais pas un pointeur vers une macro.  
  
-   **Vérification de type** Lorsque vous déclarez une fonction, le compilateur peut vérifier les types d’arguments. Étant donné que vous ne pouvez pas déclarer une macro, le compilateur ne peut pas vérifier les types d’arguments d’une macro ; il peut cependant vérifier le nombre d’arguments que vous passez à une macro.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)