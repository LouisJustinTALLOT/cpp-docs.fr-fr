---
title: (C/C++) de gestion structurée des exceptions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5b6aafa91ecfde27cc38cccc52f36af43ad21ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424268"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)
Bien que Windows et Visual C++ prennent en charge la gestion structurée des exceptions (SEH), nous vous recommandons d'utiliser la gestion des exceptions C++ conforme à la norme ISO, car elle rend le code plus portable et plus flexible. Néanmoins, vous devrez peut-être encore utiliser SEH dans le code existant ou pour des types particuliers de programmes.  
  
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
  
## <a name="grammar"></a>Grammaire  
 *try-except-statement* :  
  
 `__try` *instruction composée*  
  
 `__except` ( `expression` ) *compound-statement*  
  
## <a name="remarks"></a>Notes  
 Avec SEH, vous pouvez garantir que les ressources telles que les blocs de mémoire et les fichiers seront corrects si l'exécution se termine de façon inattendue. Vous pouvez également gérer des problèmes spécifiques (par exemple, une mémoire insuffisante) en utilisant un code structuré concis qui ne repose pas sur les instructions `goto` ni sur des tests élaborés de codes de retour.   
  
 Les instructions try-except et try-finally référencées dans cet article sont des extensions Microsoft du langage C. Elles prennent en charge SEH en permettant aux applications de prendre le contrôle d'un programme après des événements qui termineraient sinon son exécution. Bien que la gestion SEH fonctionne avec des fichiers sources C++, elle n'est pas spécifiquement conçue pour C++. Si vous l’utilisez dans un programme C++ que vous compilez à l’aide de la [/EH](../build/reference/eh-exception-handling-model.md) option — avec certains modificateurs, les destructeurs d’objets locaux sont appelés, mais d’autres comportements d’exécution non à vos attentes. (Pour obtenir une illustration, consultez l'exemple présenté plus loin dans cet article.)  Dans la plupart des cas, au lieu de SEH nous vous recommandons d’utiliser à la norme ISO [gestion des exceptions C++](../cpp/try-throw-and-catch-statements-cpp.md), lequel Visual C++ prend également en charge. En utilisant la gestion des exceptions C++, vous pouvez garantir que votre code est plus portable et gérer les exceptions de tout type.  
  
 Si vous avez des modules C qui utilisent SEH, vous pouvez les mélanger avec des modules C++ qui utilisent la gestion des exceptions C++. Pour plus d’informations, consultez [différences de gestion des exceptions](../cpp/exception-handling-differences.md).  
  
 Il existe deux mécanismes de gestion SEH :  
  
-   [Gestionnaires d’exceptions](../cpp/writing-an-exception-handler.md), qui peut répondre à ou la faire disparaître de l’exception.  
  
-   [Gestionnaires de terminaisons](../cpp/writing-a-termination-handler.md), qui sont appelés quand une exception provoque l’arrêt d’un bloc de code.  
  
 Ces deux types de gestionnaires sont distincts, mais sont étroitement liés via un processus appelé « déroulement de la pile ». Quand une exception se produit, Windows cherche le gestionnaire d'exceptions le plus récemment installé qui est actif. Le gestionnaire peut effectuer l'une des trois opérations suivantes :  
  
-   Il ne reconnaît pas l'exception et passe le contrôle à d'autres gestionnaires.  
  
-   Il reconnaît l'exception, mais la fait disparaître.  
  
-   Il reconnaît l'exception et la gère.  
  
 Le gestionnaire d'exceptions qui reconnaît l'exception peut ne pas être dans la fonction qui s'exécutait quand l'exception s'est produite. Dans certains cas, il peut s'agir d'une fonction beaucoup plus élevée dans la pile. La fonction en cours d'exécution et toutes les autres fonctions sur le frame de pile sont terminées. Pendant ce processus, la pile est « déroulée »; autrement dit, les variables locales des fonctions terminées, sauf si elles ont la valeur `static`, sont effacées de la pile.  
  
 Tout en déroulant la pile, le système d'exploitation appelle tous les gestionnaires de terminaisons que vous avez écrits pour chaque fonction. En utilisant un gestionnaire de terminaisons, vous pouvez nettoyer les ressources qui autrement resteraient ouvertes en raison d'un achèvement anormal. Si vous êtes entré dans une section critique, vous pouvez la quitter via le gestionnaire de terminaisons. Si le programme doit s'arrêter, vous pouvez effectuer d'autres tâches de gestion interne telles que la fermeture et la suppression des fichiers temporaires.  
  
 Pour plus d'informations, voir :  
  
-   [Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)  
  
-   [Écriture d’un gestionnaire de terminaisons](../cpp/writing-a-termination-handler.md)  
  
-   [Utilisation de la gestion structurée des exceptions avec C++](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## <a name="example"></a>Exemple  
 Comme indiqué précédemment, les destructeurs pour les objets locaux sont appelés si vous utilisez SEH dans un programme C++ et le compilez à l’aide de la **/EH** option avec certains modificateurs, par exemple, **/EHsc** et **/EHa**. Toutefois, le comportement pendant l'exécution peut ne pas être celui prévu si vous utilisez également des exceptions C++. L'exemple suivant illustre ces différences de comportement.  
  
```cpp  
#include <stdio.h>  
#include <Windows.h>  
#include <exception>  
  
class TestClass  
{  
public:  
    ~TestClass()  
    {  
        printf("Destroying TestClass!\r\n");  
    }  
};  
  
__declspec(noinline) void TestCPPEX()  
{  
#ifdef CPPEX  
    printf("Throwing C++ exception\r\n");  
    throw std::exception("");  
#else  
    printf("Triggering SEH exception\r\n");  
    volatile int *pInt = 0x00000000;  
    *pInt = 20;  
#endif  
}  
  
__declspec(noinline) void TestExceptions()  
{  
    TestClass d;  
    TestCPPEX();  
}  
  
int main()  
{  
    __try  
    {  
        TestExceptions();  
    }  
    __except(EXCEPTION_EXECUTE_HANDLER)  
    {  
        printf("Executing SEH __except block\r\n");  
    }  
  
    return 0;  
}  
  
```  
  
 Si vous utilisez **/EHsc** pour compiler ce code, mais le contrôle de test local `CPPEX` est non défini, il n’est exécuté le `TestClass` destructeur et la sortie ressemble à ceci :  
  
```Output  
Triggering SEH exception  
Executing SEH __except block  
```  
  
 Si vous utilisez **/EHsc** pour compiler le code et `CPPEX` est défini à l’aide de `/DCPPEX` (afin qu’une exception C++ soit levée), la `TestClass` destructeur s’exécute et la sortie ressemble à ceci :  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 Si vous utilisez **/EHa** pour compiler le code, le `TestClass` destructeur s’exécute indépendamment de si l’exception a été levée à l’aide de `std::throw` ou à l’aide de la gestion structurée des exceptions pour déclencher l’exception (`CPPEX` défini ou non). La sortie ressemble à ceci :  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md).  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [\<exception>](../standard-library/exception.md)   
 [Erreurs et la gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [(Windows) de gestion structurée des exceptions](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)