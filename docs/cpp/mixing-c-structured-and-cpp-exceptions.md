---
title: C (structurées) et d’Exceptions de C++ | Microsoft Docs
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
ms.openlocfilehash: 6e632faddb3b4f59733710a915ed121a12f4e0c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404861"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mélange d'exceptions C (structurées) et d'exceptions C++
Si vous voulez écrire du code plus portable, l'utilisation d'une gestion des exceptions structurées dans un programme C++ n'est pas recommandée. Toutefois, vous souhaiterez parfois compiler avec **/EHa** et combiner des exceptions structurées et code source C++ et avez besoin d’un autre mécanisme pour gérer ces deux types d’exceptions. Étant donné que le Gestionnaire d’exceptions structuré n’a aucun concept d’objets ou des exceptions typées, il ne peut pas gérer les exceptions levées par du code C++ ; Toutefois, C++ **catch** gestionnaires peuvent gérer les exceptions structurées. En tant que tel, syntaxe exceptions C++ (**essayez**, **lever**, **catch**) n’est pas accepté par le compilateur C, mais la syntaxe de gestion structurée des exceptions (**__try** , **__except**, **__finally**) est pris en charge par le compilateur C++.  
  
 Consultez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) pour plus d’informations sur la gestion des exceptions structurées en tant qu’exceptions C++.  
  
 Si vous combinez des exceptions structurées et C++, notez les éléments suivants :  
  
1.  Les exceptions C++ et les exceptions structurées ne peuvent pas être mélangées dans la même fonction.  
  
2.  Gestionnaires de terminaisons (**__finally** blocs) sont toujours exécutés, même pendant le déroulement après qu’une exception est levée.  
  
3.  Gestion des exceptions C++ peuvent intercepter et conserver sémantiques de déroulement dans tous les modules compilés avec la [/EH](../build/reference/eh-exception-handling-model.md) option du compilateur (cette option active les sémantiques de déroulement).  
  
4.  Il peut exister des situations où les fonctions de destructeur ne sont pas appelées pour tous les objets. Par exemple, si une exception structurée se produit lors d'une tentative d'appel de fonction via un pointeur fonction non initialisé, et si cette fonction prend comme paramètres des objets ayant été construits avant l'appel, ces objets n'auront pas leurs destructeurs appelés durant le déroulement de pile.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Utilisation de setjmp ou longjmp dans les programmes C++](../cpp/using-setjmp-longjmp.md)  
  
-   [Différences entre SEH et C++ EH](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)