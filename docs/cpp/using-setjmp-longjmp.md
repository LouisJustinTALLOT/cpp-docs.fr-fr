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
ms.openlocfilehash: 2073729fc5445fc36e3d8a6f52c4f69b079c8b47
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462129"
---
# <a name="using-setjmplongjmp"></a>Utilisation de setjmp/longjmp
Lorsque [setjmp](../c-runtime-library/reference/setjmp.md) et [longjmp](../c-runtime-library/reference/longjmp.md) sont utilisés conjointement, ils fournissent un moyen d’exécuter non local **goto**. Ils sont généralement utilisés pour passer le contrôle d'exécution au code de gestion des erreurs ou le code récupération dans une routine appelée précédemment sans utiliser l'appel standard ou les conventions de retour.  
  
> [!CAUTION]
>  Toutefois, étant donné que **setjmp** et **longjmp** ne prennent pas en charge la sémantique d’objet C++ et car elles peuvent dégrader les performances en empêchant l’optimisation sur les variables locales, nous vous recommandons de ne pas utiliser les programmes C++. Nous vous recommandons d’utiliser **essayez**/**catch** construit à la place.  
  
 Si vous décidez d’utiliser **setjmp**/**longjmp** dans un programme C++, également inclure \<setjmp.h > ou \<setjmpex.h > afin d’assurer une bonne interaction entre le les fonctions et la gestion des exceptions C++. Si vous utilisez [/EH](../build/reference/eh-exception-handling-model.md) pour compiler, les destructeurs des objets locaux sont appelés pendant le déroulement de pile. Si vous utilisez **/EHs** à la compilation et celui de vos fonctions appelle une fonction qui utilise [nothrow](../cpp/nothrow-cpp.md) et la fonction qui utilise **nothrow** appels **longjmp**, puis le déroulement du destructeur n’ait pas lieu, en fonction de l’optimiseur.  
  
 Dans le code portable, lorsque non local **goto** qui appelle **longjmp** est exécutée, destruction correcte des objets basés sur le frame peut être non fiable.  
  
## <a name="see-also"></a>Voir aussi  
 [Mélange d’exceptions C (structurées) et d’exceptions C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)