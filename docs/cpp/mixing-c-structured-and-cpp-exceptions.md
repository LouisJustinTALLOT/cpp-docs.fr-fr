---
title: Mélange d’exceptions C (structurées) et des Exceptions C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e9544e10ff0af41c0ff08fa51293c67c9977f2b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420104"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mélange d'exceptions C (structurées) et d'exceptions C++
Si vous voulez écrire du code plus portable, l'utilisation d'une gestion des exceptions structurées dans un programme C++ n'est pas recommandée. Toutefois, vous voudrez parfois compiler avec **/EHa** et combiner des exceptions structurées et code source C++ et le besoin d’une fonctionnalité pour gérer ces deux types d’exceptions. Car il n’y a aucun concept d’objets ou des exceptions typées pour un gestionnaire d’exceptions structuré, il ne peut pas gérer les exceptions levées par du code C++ ; Toutefois, C++ **catch** gestionnaires peuvent gérer les exceptions structurées. En tant que telle, syntaxe exceptions C++ (**essayez**, `throw`, **catch**) n’est pas accepté par le compilateur C, mais la syntaxe de gestion structurée des exceptions (`__try`, `__except`, `__finally`) est pris en charge par le compilateur C++.  
  
 Consultez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) pour plus d’informations sur la gestion des exceptions structurées comme des exceptions C++.  
  
 Si vous combinez des exceptions structurées et C++, notez les éléments suivants :  
  
1.  Les exceptions C++ et les exceptions structurées ne peuvent pas être mélangées dans la même fonction.  
  
2.  Les gestionnaires de terminaisons (blocs `__finally`) sont toujours exécutés, même pendant le déroulement après qu'une exception soit levée.  
  
3.  Gestion des exceptions C++ peuvent intercepter et conserver sémantiques de déroulement dans tous les modules compilés avec les [/EH](../build/reference/eh-exception-handling-model.md) option du compilateur (cette option active les sémantiques de déroulement).  
  
4.  Il peut exister des situations où les fonctions de destructeur ne sont pas appelées pour tous les objets. Par exemple, si une exception structurée se produit lors d'une tentative d'appel de fonction via un pointeur fonction non initialisé, et si cette fonction prend comme paramètres des objets ayant été construits avant l'appel, ces objets n'auront pas leurs destructeurs appelés durant le déroulement de pile.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Utilisation de setjmp ou longjmp dans les programmes C++](../cpp/using-setjmp-longjmp.md)  
  
-   [Différences entre SEH et C++ EH](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)