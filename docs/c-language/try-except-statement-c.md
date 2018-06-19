---
title: try-except, instruction (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c55ff2599fac14be0be9ac852727167dd34e02d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391712"
---
# <a name="try-except-statement-c"></a>try-except, instruction (C)
**Section spécifique à Microsoft**  
  
 L’instruction **try-except** est une extension Microsoft du langage C qui permet aux applications d’assumer le contrôle d’un programme lorsque surviennent des événements qui terminent normalement l’exécution. Ces événements sont appelés « exceptions » et le mécanisme de gestion des exceptions s'appelle « gestion structurée des exceptions ».  
  
 Les exceptions peuvent être basées sur le matériel ou sur le logiciel. Même quand les applications ne peuvent pas complètement récupérer à partir d'exceptions matérielles ou logicielles, la gestion structurée des exceptions permet d'afficher des informations sur l'erreur et d'intercepter l'état interne de l'application pour favoriser le diagnostic du problème. Ceci s'avère particulièrement utile pour les problèmes intermittents qui ne peuvent pas être facilement reproduits.  
  
## <a name="syntax"></a>Syntaxe  
 *try-except-statement* :  
 **__try**  *compound-statement*  
  
 **__except (**  *expression*  **)**  *compound-statement*  
  
 L'instruction composée après la clause `__try` est la section protégée. L'instruction composée après la clause `__except` constitue le gestionnaire d'exceptions. Le gestionnaire spécifie un ensemble d'actions à exécuter si une exception est levée pendant l'exécution de la section protégée. L'exécution se déroule comme suit :  
  
1.  La section protégée est exécutée.  
  
2.  Si aucune exception ne se produit pendant l'exécution de la section protégée, l'exécution se poursuit à l'instruction située après la clause `__except`.  
  
3.  Si une exception est levée pendant l’exécution de la section protégée ou dans toute routine appelée par la section protégée, l’expression `__except` est évaluée et la valeur retournée détermine comment l’exception est gérée. Il existe trois valeurs :  
  
     `EXCEPTION_CONTINUE_SEARCH` L’exception n’est pas reconnue. Poursuivre la recherche d’un gestionnaire dans la pile, en premier pour qu’il contienne des instructions **try-except**, puis pour les gestionnaires avec la priorité la plus élevée suivante.  
  
     `EXCEPTION_CONTINUE_EXECUTION` L’exception est reconnue, mais ignorée. Poursuivre l'exécution au point où l'exception s'est produite.  
  
     `EXCEPTION_EXECUTE_HANDLER` L’exception est reconnue. Transférez le contrôle au gestionnaire d'exceptions en exécutant l'instruction composée `__except`, puis continuez l'exécution au point où l'exception s'est produite.  
  
 L'expression `__except` étant évaluée comme une expression C, elle est limitée à une valeur unique, l'opérateur d'expression conditionnelle, ou l'opérateur virgule. Si un traitement plus étendu est requis, l'expression peut appeler une routine qui retourne l'une des trois valeurs répertoriées ci-dessus.  
  
> [!NOTE]
>  La gestion structurée des exceptions fonctionne avec les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, le mécanisme de gestion des exceptions C++ est beaucoup plus souple, car il peut gérer les exceptions de tout type.  
  
> [!NOTE]
>  Pour les programmes C++, la gestion des exceptions C++ doit être utilisée à la place de la gestion structurée des exceptions. Pour plus d’informations, consultez [Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md) dans le *Guide de référence du langage C++*.  
  
 Chaque routine dans une application peut avoir son propre gestionnaire d'exceptions. L'expression `__except` s'exécute dans la portée du corps `__try`. Cela signifie qu'elle a accès à toutes les variables locales déclarées à cet endroit.  
  
 Le mot clé `__leave` est valide dans un bloc d’instructions **try-except**. `__leave` a comme conséquence d’accéder à la fin du bloc **try-except**. L'exécution reprend après la fin du gestionnaire d'exceptions. Bien qu'une instruction `goto` puisse être utilisée pour obtenir le même résultat, une instruction `goto` provoque le déroulement de pile. L'instruction `__leave` est plus efficace car elle n'implique pas le déroulement de pile.  
  
 Le fait de quitter une instruction **try-except** à l’aide de la fonction runtime `longjmp` est considéré comme un arrêt anormal. Il est non conforme de sauter dans une instruction `__try`, mais conforme d'en sortir d'une. Le gestionnaire d’exceptions n’est pas appelé si un processus est tué au milieu de l’exécution d’une instruction **try-except**.  
  
## <a name="example"></a>Exemple  
 Voici un exemple de gestionnaire d'exceptions et de gestionnaire d'arrêt. Pour plus d’informations sur les gestionnaires d’arrêt, consultez [Instruction try-finally](../c-language/try-finally-statement-c.md).  
  
```  
.  
.  
.  
puts("hello");  
__try{  
   puts("in try");  
   __try{  
      puts("in try");  
      RAISE_AN_EXCEPTION();  
   }__finally{  
      puts("in finally");  
   }  
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){  
   puts("in except");  
}  
puts("world");  
```  
  
 Voici la sortie de l'exemple, avec le commentaire ajouté à droite :  
  
```  
hello  
in try              /* fall into try                     */  
in try              /* fall into nested try                */  
in filter           /* execute filter; returns 1 so accept  */  
in finally          /* unwind nested finally                */  
in except           /* transfer control to selected handler */  
world               /* flow out of handler                  */  
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [try-except, instruction](../cpp/try-except-statement.md)