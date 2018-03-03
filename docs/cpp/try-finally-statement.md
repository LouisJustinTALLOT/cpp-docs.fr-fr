---
title: Instruction try-finally | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
dev_langs:
- C++
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c57676cace8451de266d30d4c146e3ae0c3cb1b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="try-finally-statement"></a>try-finally, instruction
**Section spécifique à Microsoft**  
  
 La syntaxe suivante décrit l'instruction `try-finally` :  
  
```  
__try {  
   // guarded code  
}  
__finally {  
   // termination code  
}  
```  
  
## <a name="grammar"></a>Grammaire  
 *try-finally-statement* :  
 `__try`*compound-statement*  
  
 `__finally`*compound-statement*  
  
 L'instruction `try-finally` est une extension Microsoft des langages C et C++ qui permet aux applications cibles de garantir l'exécution du code de nettoyage lorsque l'exécution d'un bloc de code est interrompue. Le nettoyage se compose de tâches telles que la désallocation de mémoire, la fermeture de fichiers et la libération des handles de fichiers. L'instruction `try-finally` est particulièrement utile pour les routines qui ont plusieurs endroits où un contrôle est effectué pour une erreur qui peut provoquer un retour prématuré de la routine.  
  
 Pour plus d’informations et un exemple de code, consultez [essayez-EXCEPT, instruction](../cpp/try-except-statement.md). Pour plus d’informations sur les exceptions structurées en général, consultez [gestion structurée des exceptions](../cpp/structured-exception-handling-c-cpp.md). Pour plus d’informations sur la gestion des exceptions dans les applications managées, consultez [la gestion des exceptions sous /clr](../windows/exception-handling-cpp-component-extensions.md).  
  
> [!NOTE]
>  La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour les programmes C++, il est recommandé d’utiliser le mécanisme de gestion des exceptions C++ ([try, catch et throw](../cpp/try-throw-and-catch-statements-cpp.md) instructions).  
  
 L'instruction composée après la clause `__try` est la section protégée. L'instruction composée après la clause `__finally` est le gestionnaire de terminaisons. Le gestionnaire spécifie un jeu d'actions qui s'exécutent lorsque la section protégée est fermée, que la section protégée soit fermée par une exception (fin anormale) ou par un passage standard (fin normale).  
  
 Le contrôle atteint une instruction `__try` par exécution séquentielle simple (passage). Lorsque le contrôle pénètre dans `__try`, son gestionnaire associé devient actif. Si le flux de contrôle atteint la fin du bloc try, l'exécution se produit de la façon suivante :  
  
1.  Le gestionnaire de terminaisons est appelé.  
  
2.  Lorsque le gestionnaire de terminaisons se termine, l'exécution reprend après l'instruction `__finally`. Quelle que soit la façon dont la section protégée se termine (par exemple, via `goto` hors du corps protégé ou via une instruction `return`), le gestionnaire de terminaisons est exécuté avant (`before`) que le flux de contrôle ne sorte de la section protégée.  
  
     A **__finally** instruction ne bloque pas la recherche d’un gestionnaire d’exceptions approprié.  
  
 Si une exception se produit dans le bloc `__try`, le système d'exploitation doit rechercher un gestionnaire pour l'exception, sinon le programme échoue. Si un gestionnaire est trouvé, tous les blocs `__finally` sont exécutés et l'exécution reprend dans le gestionnaire.  
  
 Par exemple, supposons qu'une série d'appels de fonction lie la fonction A à la fonction D, comme indiqué dans l'illustration suivante. Chaque fonction a un gestionnaire de terminaisons. Si une exception est levée dans la fonction D et gérée dans A, les gestionnaires de terminaisons sont appelés dans l'ordre suivant à mesure que le système déroule la pile : D, C, B.  
  
 ![Commande d’arrêt &#45; l’exécution du gestionnaire](../cpp/media/vc38cx1.gif "vc38CX1")  
Fin de l'ordre d'exécution du gestionnaire  
  
> [!NOTE]
>  Le comportement de try-finally est différent d’autres langages qui prennent en charge l’utilisation de **enfin**, tel que c#.  Un `__try` unique peut avoir l'un ou l'autre, `__finally` et `__except`, mais pas les deux.  Si les deux doivent être utilisés conjointement, une instruction try-except externe doit entourer l'instruction try-finally interne.  Les règles qui spécifient le moment d'exécution de chaque blocs sont également différentes.  
  
## <a name="the-leave-keyword"></a>Mot clé __leave  
 Le mot clé `__leave` est valide uniquement dans la section protégée d'une instruction `try-finally` et il permet de sauter à la fin de la section protégée. L'exécution continue à la première instruction dans le gestionnaire de terminaisons.  
  
 Une instruction `goto` peut également sortir de la section protégée, mais elle dégrade les performances, car elle appelle le déroulement de la pile. L'instruction `__leave` est plus efficace, car elle n'entraîne pas le déroulement de la pile.  
  
## <a name="abnormal-termination"></a>Arrêt anormal  
 Quitter un `try-finally` à l’aide de l’instruction la [longjmp](../c-runtime-library/reference/longjmp.md) fonction runtime est considéré comme un arrêt anormal. Il est non conforme de sauter dans une instruction `__try`, mais conforme d'en sortir d'une. Toutes les instructions `__finally` actives entre le point de départ (arrêt normal du bloc `__try`) et la destination (le bloc `__except` qui gère l'exception) doivent être exécutées. Cela s'appelle un déroulement local.  
  
 Si un **essayez** bloc se termine prématurément pour une raison quelconque, y compris un saut hors du bloc, le système exécute associé **enfin** bloc dans le cadre du processus de déroulement de la pile. Dans ce cas, le [AbnormalTermination](http://msdn.microsoft.com/library/windows/desktop/ms679265) fonction retourne la valeur TRUE si elle est appelée depuis le **enfin** bloquer ; sinon, elle retourne FALSE.  
  
 Le gestionnaire de terminaisons n'est pas appelé si un processus est arrêté au milieu de l'exécution d'une instruction `try-finally`.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un gestionnaire de terminaisons](../cpp/writing-a-termination-handler.md)   
 [Exceptions structurées (C/C++)](../cpp/structured-exception-handling-c-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [Syntaxe du Gestionnaire de terminaisons](http://msdn.microsoft.com/library/windows/desktop/ms681393)