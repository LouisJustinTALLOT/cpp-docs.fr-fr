---
title: Structured Exception Handling (C/C++)
description: Vue d’ensemble de la gestion structurée des exceptions dans Microsoft C/C++.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 142e89bc82adbe7938e8825029908e814df6055c
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898635"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

La gestion structurée des exceptions (SEH) est une extension Microsoft de C permettant de gérer certaines situations de code exceptionnelles, telles que les défaillances matérielles, en douceur. Bien que Windows et Microsoft C++ prennent en charge SEH, nous vous recommandons d’utiliser la gestion des exceptions C++ standard ISO. Cela rend votre code plus portable et plus flexible. Toutefois, pour gérer le code existant ou pour certains genres de programmes, vous devrez peut-être utiliser la gestion des exceptions STRUCTURÉes.

**Spécifique à Microsoft :**

## <a name="grammar"></a>Grammaire

> *`try-except-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__except`** **`(`** *`expression`* **`)`** *`compound-statement`*
>
> *`try-finally-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

## <a name="remarks"></a>Notes

Avec SEH, vous pouvez vous assurer que les ressources, telles que les blocs de mémoire et les fichiers, sont libérées correctement si l’exécution se termine de manière inattendue. Vous pouvez également gérer des problèmes spécifiques (par exemple, une mémoire insuffisante) à l’aide d’un code structuré concis qui ne repose pas sur des **`goto`** instructions ou sur des tests élaborés de codes de retour.

Les `try-except` `try-finally` instructions et mentionnées dans cet article sont des extensions Microsoft du langage C. Elles prennent en charge SEH en permettant aux applications de prendre le contrôle d'un programme après des événements qui termineraient sinon son exécution. Bien que la gestion SEH fonctionne avec des fichiers sources C++, elle n'est pas spécifiquement conçue pour C++. Si vous utilisez SEH dans un programme C++ que vous compilez à l’aide de l’option [ `/EHa` ou `/EHsc` ](../build/reference/eh-exception-handling-model.md) , les destructeurs des objets locaux sont appelés, mais d’autres comportements d’exécution peuvent ne pas correspondre à ce que vous attendez. Pour obtenir une illustration, consultez l’exemple plus loin dans cet article. Dans la plupart des cas, au lieu de SEH, nous vous recommandons d’utiliser la [gestion des exceptions c++](../cpp/try-throw-and-catch-statements-cpp.md)standard ISO, que le compilateur Microsoft c++ prend également en charge. En utilisant la gestion des exceptions C++, vous pouvez garantir que votre code est plus portable et gérer les exceptions de tout type.

Si vous avez du code C qui utilise SEH, vous pouvez le mélanger avec du code C++ qui utilise la gestion des exceptions C++. Pour plus d’informations, consultez [gérer les exceptions structurées en C++](../cpp/exception-handling-differences.md).

Il existe deux mécanismes de gestion SEH :

- [Gestionnaires d’exceptions](../cpp/writing-an-exception-handler.md), ou **`__except`** blocs, qui peuvent répondre à l’exception ou la faire disparaître.

- [Gestionnaires de terminaisons](../cpp/writing-a-termination-handler.md), ou **`__finally`** blocs, qui sont toujours appelés, si une exception provoque l’arrêt ou non.

Ces deux types de gestionnaires sont distincts, mais sont étroitement liés par un processus appelé *déroulement de la pile*. Lorsqu’une exception structurée se produit, Windows recherche le gestionnaire d’exceptions installé le plus récemment qui est actuellement actif. Le gestionnaire peut effectuer l'une des trois opérations suivantes :

- Il ne reconnaît pas l'exception et passe le contrôle à d'autres gestionnaires.

- Il reconnaît l'exception, mais la fait disparaître.

- Il reconnaît l'exception et la gère.

Le gestionnaire d'exceptions qui reconnaît l'exception peut ne pas être dans la fonction qui s'exécutait quand l'exception s'est produite. Elle peut se trouver dans une fonction plus élevée sur la pile. La fonction en cours d'exécution et toutes les autres fonctions sur le frame de pile sont terminées. Pendant ce processus, la pile est *déroulée*. Autrement dit, les variables locales non statiques des fonctions terminées sont effacées de la pile.

Tout en déroulant la pile, le système d'exploitation appelle tous les gestionnaires de terminaisons que vous avez écrits pour chaque fonction. En utilisant un gestionnaire de terminaisons, vous nettoyez des ressources qui seraient autrement restées ouvertes en raison d’un arrêt anormal. Si vous avez entré une section critique, vous pouvez la quitter dans le gestionnaire de terminaisons. Lorsque le programme va s’arrêter, vous pouvez effectuer d’autres tâches de maintenance, telles que la fermeture et la suppression des fichiers temporaires.

## <a name="next-steps"></a>Étapes suivantes

- [Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)

- [Écriture d’un gestionnaire des arrêts](../cpp/writing-a-termination-handler.md)

- [Gérer les exceptions structurées en C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Exemple

Comme indiqué précédemment, les destructeurs des objets locaux sont appelés si vous utilisez SEH dans un programme C++ et le compilez à l’aide de l' **`/EHa`** **`/EHsc`** option ou. Toutefois, le comportement au cours de l’exécution peut ne pas être celui que vous attendez si vous utilisez également des exceptions C++. Cet exemple illustre ces différences de comportement.

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

Si vous utilisez **`/EHsc`** pour compiler ce code, mais que la macro de contrôle de test local `CPPEX` n’est pas définie, le `TestClass` destructeur ne s’exécute pas. Le résultat se présente ainsi :

```Output
Triggering SEH exception
Executing SEH __except block
```

Si vous utilisez **`/EHsc`** pour compiler le code et `CPPEX` que est défini à l’aide de `/DCPPEX` (afin qu’une exception C++ soit levée), le `TestClass` destructeur s’exécute et le résultat ressemble à ceci :

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Si vous utilisez **`/EHa`** pour compiler le code, le `TestClass` destructeur s’exécute si l’exception a été levée à l’aide de `std::throw` ou à l’aide de SEH pour déclencher l’exception. Autrement dit, si `CPPEX` est défini ou non. Le résultat se présente ainsi :

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Pour plus d’informations, consultez [ `/EH` (modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[`<exception>`](../standard-library/exception.md)<br/>
[Erreurs et gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Gestion structurée des exceptions (Windows)](/windows/win32/debug/structured-exception-handling)
