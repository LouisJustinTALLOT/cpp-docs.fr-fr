---
title: Meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs
description: Comment le C++ moderne prend en charge les styles de programmation exceptionnels par rapport aux codes d’erreur.
ms.date: 08/24/2020
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: b402c93ea5af3cc7dab418b6dea58446ae300c67
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898371"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>Meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs

Dans la plupart des scénarios, en C++ moderne, la meilleure façon de signaler et de gérer les erreurs logiques et les erreurs d’exécution consiste à utiliser des exceptions. Cela est particulièrement vrai lorsque la pile peut contenir plusieurs appels de fonction entre la fonction qui détecte l’erreur et la fonction qui possède le contexte pour gérer l’erreur. Les exceptions fournissent une méthode formelle et bien définie pour le code qui détecte les erreurs pour transmettre les informations vers le haut de la pile des appels.

## <a name="use-exceptions-for-exceptional-code"></a>Utiliser des exceptions pour le code exceptionnel

Les erreurs de programme sont souvent divisées en deux catégories : les erreurs logiques provoquées par des erreurs de programmation, par exemple, une erreur « index hors limites ». Et les erreurs d’exécution qui dépassent le contrôle du programmeur, par exemple, une erreur « service réseau non disponible ». Dans la programmation de style C et dans COM, le rapport d’erreurs est géré en retournant une valeur qui représente un code d’erreur ou un code d’État pour une fonction particulière, ou en définissant une variable globale que l’appelant peut éventuellement récupérer après chaque appel de fonction pour vérifier si des erreurs ont été signalées. Par exemple, la programmation COM utilise la valeur de retour HRESULT pour communiquer des erreurs à l’appelant. Et l’API Win32 possède la `GetLastError` fonction permettant de récupérer la dernière erreur signalée par la pile des appels. Dans ces deux cas, l’appelant doit reconnaître le code et y répondre de manière appropriée. Si l’appelant ne gère pas explicitement le code d’erreur, le programme peut se bloquer sans avertissement. Ou encore, il peut continuer à s’exécuter à l’aide de données incorrectes et produire des résultats incorrects.

Les exceptions sont préférées dans le C++ moderne pour les raisons suivantes :

- Une exception force le code appelant à reconnaître une condition d’erreur et à la gérer. Les exceptions non gérées empêchent l’exécution du programme.

- Une exception se déplace jusqu’au point dans la pile des appels qui peut gérer l’erreur. Les fonctions intermédiaires peuvent permettre à l’exception de se propager. Ils n’ont pas besoin de se coordonner avec d’autres couches.

- Le mécanisme de déroulement de la pile d’exception détruit tous les objets de la portée après la levée d’une exception, en fonction de règles bien définies.

- Une exception permet une séparation nette entre le code qui détecte l’erreur et le code qui gère l’erreur.

L’exemple simplifié suivant illustre la syntaxe nécessaire pour lever et intercepter les exceptions en C++.

```cpp
#include <stdexcept>
#include <limits>
#include <iostream>

using namespace std;

void MyFunc(int c)
{
    if (c > numeric_limits< char> ::max())
        throw invalid_argument("MyFunc argument too large.");
    //...
}

int main()
{
    try
    {
        MyFunc(256); //cause an exception to throw
    }

    catch (invalid_argument& e)
    {
        cerr << e.what() << endl;
        return -1;
    }
    //...
    return 0;
}
```

Les exceptions en C++ sont similaires à celles des langages tels que C# et Java. Dans le **`try`** bloc, si une exception est *levée* , elle est *interceptée* par le premier **`catch`** bloc associé dont le type correspond à celui de l’exception. En d’autres termes, l’exécution passe de l' **`throw`** instruction à l' **`catch`** instruction. Si aucun bloc catch utilisable n’est trouvé, `std::terminate` est appelé et le programme se termine. En C++, tout type peut être levé ; Toutefois, nous vous recommandons de lever un type qui dérive directement ou indirectement de `std::exception` . Dans l’exemple précédent, le type d’exception, [`invalid_argument`](../standard-library/invalid-argument-class.md) , est défini dans la bibliothèque standard dans le [`<stdexcept>`](../standard-library/stdexcept.md) fichier d’en-tête. C++ ne fournit pas ou n’a pas besoin d’un **`finally`** bloc pour s’assurer que toutes les ressources sont libérées si une exception est levée. L’idiome de l’initialisation des ressources (RAII), qui utilise des pointeurs intelligents, fournit les fonctionnalités requises pour le nettoyage des ressources. Pour plus d’informations, consultez [Comment : concevoir pour la sécurité des exceptions](how-to-design-for-exception-safety.md). Pour plus d’informations sur le mécanisme de déroulement de pile C++, consultez [exceptions et déroulement](exceptions-and-stack-unwinding-in-cpp.md)de la pile.

## <a name="basic-guidelines"></a>Instructions de base

La gestion des erreurs fiable est complexe dans tout langage de programmation. Bien que les exceptions fournissent plusieurs fonctionnalités qui prennent en charge une bonne gestion des erreurs, elles ne peuvent pas faire tout le travail pour vous. Pour tirer parti des avantages du mécanisme d’exception, gardez à l’esprit les exceptions au fur et à mesure que vous concevez votre code.

- Utilisez des assertions pour vérifier les erreurs qui ne doivent jamais se produire. Utilisez des exceptions pour rechercher les erreurs qui peuvent se produire, par exemple, les erreurs de validation d’entrée sur les paramètres des fonctions publiques. Pour plus d’informations, consultez la section [exceptions et assertions](#exceptions_versus_assertions) .

- Utilisez des exceptions lorsque le code qui gère l’erreur est séparé du code qui détecte l’erreur par un ou plusieurs appels de fonction intermédiaires. Déterminez s’il est nécessaire d’utiliser des codes d’erreur à la place dans les boucles critiques pour les performances, lorsque le code qui gère l’erreur est étroitement couplé au code qui le détecte.

- Pour chaque fonction qui peut lever ou propager une exception, fournissez l’une des trois garanties d’exception : la garantie forte, la garantie de base ou la garantie nothrow (noexcept). Pour plus d’informations, consultez [Comment : concevoir pour la sécurité des exceptions](how-to-design-for-exception-safety.md).

- Lever des exceptions par valeur, les intercepter par référence. N’interceptez pas ce que vous ne pouvez pas gérer.

- N’utilisez pas de spécifications d’exceptions, qui sont dépréciées dans C++ 11. Pour plus d’informations, consultez les [spécifications et `noexcept` ](#exception_specifications_and_noexcept) la section des exceptions.

- Utilisez les types d’exception de bibliothèque standard lorsqu’ils s’appliquent. Dérivez les types d’exceptions personnalisées de la hiérarchie de [ `exception` classes](../standard-library/exception-class.md) .

- N’autorisez pas les exceptions à échapper des destructeurs ou des fonctions de désallocation de mémoire.

## <a name="exceptions-and-performance"></a>Exceptions et performances

Le mécanisme d’exception a un coût de performance minimal si aucune exception n’est levée. Si une exception est levée, le coût du parcours et du déroulement de la pile est à peu près comparable au coût d’un appel de fonction. Des structures de données supplémentaires sont requises pour suivre la pile des appels après l’entrée d’un **`try`** bloc, et des instructions supplémentaires sont requises pour dérouler la pile si une exception est levée. Toutefois, dans la plupart des scénarios, le coût des performances et de l’encombrement mémoire n’est pas significatif. L’effet négatif des exceptions sur les performances est susceptible d’être significatif uniquement sur les systèmes limités en mémoire. Ou, dans les boucles critiques en matière de performances, où une erreur est susceptible de se produire régulièrement et qu’il y a un couplage étroit entre le code pour le gérer et le code qui le signale. Dans tous les cas, il est impossible de connaître le coût réel des exceptions sans profilage ni mesure. Même dans les rares cas où le coût est significatif, vous pouvez le comparer à l’exactitude accrue, à la facilité de maintenance et à d’autres avantages fournis par une stratégie d’exception bien conçue.

## <a name="exceptions-versus-assertions"></a><a name="exceptions_versus_assertions"></a> Exceptions et assertions

Les exceptions et les assertions sont deux mécanismes distincts pour détecter les erreurs d’exécution dans un programme. Utilisez `assert` les instructions pour tester les conditions pendant le développement qui ne doivent jamais être vraies si tout votre code est correct. Il n’y a aucun point dans la gestion d’une telle erreur en utilisant une exception, car l’erreur indique que le code doit être corrigé. Il ne représente pas une condition à partir de laquelle le programme doit être récupéré au moment de l’exécution. `assert`Arrête l’exécution au niveau de l’instruction afin que vous puissiez inspecter l’état du programme dans le débogueur. Une exception continue l’exécution à partir du premier gestionnaire catch approprié. Utilisez les exceptions pour vérifier les conditions d’erreur qui peuvent se produire au moment de l’exécution même si votre code est correct, par exemple, « fichier introuvable » ou « mémoire insuffisante ». Les exceptions peuvent gérer ces conditions, même si la récupération envoie simplement un message à un journal et met fin au programme. Vérifiez toujours les arguments des fonctions publiques à l’aide d’exceptions. Même si votre fonction est exempte d’erreurs, vous n’avez peut-être pas le contrôle complet sur les arguments qu’un utilisateur peut lui passer.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Exceptions C++ par rapport aux exceptions SEH Windows

Les programmes C et C++ peuvent utiliser le mécanisme de gestion structurée des exceptions (SEH) dans le système d’exploitation Windows. Les concepts de SEH ressemblent à ceux des exceptions C++, à ceci près que le SEH utilise les **`__try`** **`__except`** constructions, et **`__finally`** au lieu de **`try`** et **`catch`** . Dans le compilateur Microsoft C++ (MSVC), les exceptions C++ sont implémentées pour SEH. Toutefois, lorsque vous écrivez du code C++, utilisez la syntaxe d’exception C++.

Pour plus d’informations sur SEH, consultez [gestion structurée des exceptions (C/C++)](structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a><a name="exception_specifications_and_noexcept"></a> Spécifications d’exception et `noexcept`

Les spécifications d’exception ont été introduites en C++ comme un moyen de spécifier les exceptions qu’une fonction peut lever. Toutefois, les spécifications d’exceptions se sont avérées problématiques dans la pratique et sont dépréciées dans la norme préliminaire C++ 11. Nous vous recommandons de ne pas utiliser **`throw`** les spécifications d’exception, à l’exception de `throw()` , qui indique que la fonction n’autorise aucune exception à échapper. Si vous devez utiliser des spécifications d’exception de la forme déconseillée `throw( type-name )` , la prise en charge de MSVC est limitée. Pour plus d’informations, consultez [spécifications d’exception (throw)](exception-specifications-throw-cpp.md). Le **`noexcept`** spécificateur est introduit dans c++ 11 comme alternative préférée à `throw()` .

## <a name="see-also"></a>Voir aussi

[Comment : établir une interface entre du code exceptionnel et non exceptionnel](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
