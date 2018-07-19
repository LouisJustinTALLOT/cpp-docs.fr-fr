---
title: Utilisation de setjmp-longjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f68cd13304e73282735ad1227510b289b19caed8
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939765"
---
# <a name="using-setjmplongjmp"></a>Utilisation de setjmp/longjmp
Lorsque [setjmp](../c-runtime-library/reference/setjmp.md) et [longjmp](../c-runtime-library/reference/longjmp.md) sont utilisés conjointement, ils fournissent un moyen d’exécuter non local **goto**. Ils sont généralement utilisés pour passer le contrôle d'exécution au code de gestion des erreurs ou le code récupération dans une routine appelée précédemment sans utiliser l'appel standard ou les conventions de retour.  
  
> [!CAUTION]
>  Toutefois, étant donné que `setjmp` et `longjmp` ne prennent pas en charge la sémantique d'objet C++, et qu'ils peuvent diminuer les performances en empêchant l'optimisation sur les variables locales, nous vous recommandons de ne pas les utiliser dans les programmes C++. Nous vous recommandons d’utiliser **essayez**/**catch** construit à la place.  
  
 Si vous décidez d’utiliser `setjmp` / `longjmp` dans un programme C++, également inclure \<setjmp.h > ou \<setjmpex.h > afin d’assurer une bonne interaction entre les fonctions et la gestion des exceptions C++. Si vous utilisez [/EH](../build/reference/eh-exception-handling-model.md) pour compiler, les destructeurs des objets locaux sont appelés pendant le déroulement de pile. Si vous utilisez **/EHs** à la compilation et celui de vos fonctions appelle une fonction qui utilise [nothrow](../cpp/nothrow-cpp.md) et la fonction qui utilise **nothrow** appels `longjmp`, puis le déroulement du destructeur ne soient pas exécutées, en fonction de l’optimiseur.  
  
 Dans le code portable, lorsque non local **goto** qui appelle `longjmp` est exécutée, destruction correcte des objets basés sur le frame peut être non fiable.  
  
## <a name="see-also"></a>Voir aussi  
 [Mélange d’exceptions C (structurées) et d’exceptions C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)