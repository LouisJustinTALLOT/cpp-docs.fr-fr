---
title: Gestion des erreurs et des exceptions (Modern C++)
ms.date: 09/17/2018
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: d6192ab800667ceb35bf2e18dcbdc0be95ec70f5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523286"
---
# <a name="errors-and-exception-handling-modern-c"></a>Gestion des erreurs et des exceptions (Modern C++)

En C++ moderne, dans la plupart des scénarios, la meilleure façon de signaler et gérer les erreurs de logique et erreurs d’exécution est d’utiliser des exceptions. Cela est particulièrement vrai lorsque la pile peut contenir plusieurs appels de fonction entre la fonction qui détecte l’erreur et la fonction qui possède le contexte pour savoir comment la gérer. Les exceptions fournissent un moyen formel et bien défini pour le code qui détecte les erreurs pour passer les informations de la pile des appels.

Erreurs du programme sont généralement réparties en deux catégories : les erreurs de logique qui sont provoquées par les erreurs de programmation, par exemple, une erreur « index hors limites » et les erreurs d’exécution qui sont contrôlés par le programmeur, par exemple, un « network service indisponible » erreur. Dans la programmation de style C et en COM, le rapport d’erreurs est géré en retournant une valeur qui représente un code d’erreur ou un code d’état pour une fonction particulière, soit en définissant une variable globale que l’appelant peut éventuellement extraire après chaque appel de fonction pour afficher Indique si des erreurs ont été signalées. Par exemple, programmation COM utilise la valeur de retour HRESULT pour communiquer des erreurs à l’appelant, et l’API Win32 a la fonction GetLastError pour récupérer la dernière erreur qui a été signalée par la pile des appels. Dans ces deux cas, c’est à l’appelant d’identifier le code et y répondre en conséquence. Si l’appelant ne gère pas explicitement le code d’erreur, le programme peut se bloquer sans avertissement, ou continuer à s’exécuter avec des données incorrectes et produire des résultats incorrects.

Les exceptions sont préférées en C++ moderne pour les raisons suivantes :

- Une exception force le code appelant pour reconnaître une condition d’erreur et la gérer. Exceptions non gérées arrêtent l’exécution du programme.

- Une exception accède au point dans la pile des appels qui peut gérer l’erreur. Fonctions intermédiaires peuvent permettre à l’exception de se propager. Ils n’ont pas à coordonner avec d’autres couches.

- Le mécanisme de déroulement de pile d’exception détruit tous les objets dans l’étendue en fonction de règles bien définies après qu’une exception est levée.

- Une exception permet une séparation nette entre le code qui détecte l’erreur et le code qui gère l’erreur.

L’exemple simplifié suivant illustre la syntaxe nécessaire pour lever et intercepter des exceptions dans C++.

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

Les exceptions en C++ ressemblent à celles des langages tels que c# et Java. Dans le **essayez** bloquer, si une exception est *levée* il sera *interceptée* par le premier associé **catch** bloc dont le type correspond à celui de la exception. En d’autres termes, l’exécution passe à partir de la **lever** instruction à la **catch** instruction. Si aucun bloc catch utilisable n’est trouvée, `std::terminate` est appelé et le programme se termine. En C++, n’importe quel type peut être levé ; Toutefois, nous vous recommandons de lever un type qui dérive directement ou indirectement de `std::exception`. Dans l’exemple précédent, le type d’exception, [invalid_argument](../standard-library/invalid-argument-class.md), est défini dans la bibliothèque standard dans le [ \<stdexcept >](../standard-library/stdexcept.md) fichier d’en-tête. C++ ne fournit pas et ne requiert pas, un **enfin** bloc pour vous assurer que toutes les ressources sont libérées si une exception est levée. Resource acquisition is idiome RAII (initialization), qui utilise des pointeurs intelligents, fournit les fonctionnalités requises pour le nettoyage des ressources. Pour plus d’informations, consultez [Comment : conception pour la sécurité de l’Exception](../cpp/how-to-design-for-exception-safety.md). Pour plus d’informations sur le mécanisme de déroulement de pile C++, consultez [Exceptions et déroulement de pile](../cpp/exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Recommandations de base

Gestion des erreurs fiable sont difficile dans n’importe quel langage de programmation. Bien que les exceptions fournissent plusieurs fonctionnalités qui prennent en charge de la bonne gestion des erreurs, ils ne peuvent pas faire tout le travail pour vous. Pour profiter des avantages du mécanisme d’exception, gardez les exceptions à l’esprit lorsque vous concevez votre code.

- Utilisez les assertions pour vérifier les erreurs qui ne doivent jamais se produire. Utilisez les exceptions pour rechercher les erreurs qui peuvent se produire, par exemple, les erreurs de validation des entrées sur les paramètres de fonctions publiques. Pour plus d’informations, consultez la section intitulée **vs d’Exceptions. Assertions**.

- Utiliser des exceptions lorsque le code qui gère l’erreur peut être séparé du code qui détecte l’erreur par un ou plusieurs appels de fonction intermédiaires. Pensez à utiliser à la place des codes d’erreur dans des boucles critiques pour les performances lorsque le code qui gère l’erreur est étroitement lié au code qui détecte que celui-ci.

- Pour chaque fonction qui peut lever ou propager une exception, vous pouvez fournir d’une des trois garanties d’exception : la garantie forte, la garantie de base ou la garantie nothrow (noexcept). Pour plus d’informations, consultez [Comment : conception pour la sécurité de l’Exception](../cpp/how-to-design-for-exception-safety.md).

- Lever des exceptions par valeur, les intercepter par référence. N’interceptez ne peut pas gérer.

- N’utilisez pas les spécifications d’exceptions, qui sont déconseillées dans C ++ 11. Pour plus d’informations, consultez la section intitulée **spécifications d’Exception et noexcept**.

- Utilisez les types d’exception de bibliothèque standard lorsqu’elles s’appliquent. Dériver des types d’exceptions personnalisées à partir de la [exception, classe](../standard-library/exception-class.md) hiérarchie.

- Ne pas autoriser les exceptions à échapper à partir de destructeurs ou de fonctions de désallocation de mémoire.

## <a name="exceptions-and-performance"></a>Exceptions et performances

Le mécanisme d’exception a un coût si aucune exception n’est levée minimal sur les performances. Si une exception est levée, le coût de la traversée de la pile et déroulement sont approximativement comparable au coût d’un appel de fonction. Structures de données supplémentaires sont nécessaires au suivi de la pile des appels après un **essayez** bloc est entré, et des instructions supplémentaires sont nécessaires pour dérouler la pile si une exception est levée. Toutefois, dans la plupart des scénarios, le coût de performances et l’encombrement de mémoire n’est pas significatif. L’effet négatif des exceptions sur les performances est susceptible d’être significatif uniquement sur les systèmes très limités en mémoire ou dans boucles aux performances critiques où une erreur est susceptible de se produire régulièrement et le code de gestion est étroitement lié au code qui signale. Dans tous les cas, il est impossible de connaître le coût réel des exceptions sans profilage et mesurage. Même dans les rares cas lorsque le coût est significatif, vous pouvez le mesurer à l’exactitude accrue, de facilité et d’autres avantages fournis par une stratégie d’exception bien conçue.

## <a name="exceptions-vs-assertions"></a>Exceptions et assertions

Exceptions et les assertions sont deux mécanismes distincts pour la détection des erreurs d’exécution dans un programme. Utilisez les assertions pour tester les conditions au cours du développement qui ne doit jamais être vrai si tout votre code est correct. Il est inutile de gérer une telle erreur à l’aide d’une exception, car l’erreur indique que quelque chose dans le code doit être corrigé et ne représente pas une condition que le programme doit récupérer au moment de l’exécution. Une assertion interrompt l’exécution à l’instruction afin que vous puissiez inspecter l’état du programme dans le débogueur ; une exception poursuit l’exécution à partir du premier gestionnaire catch approprié. Utiliser des exceptions pour vérifier les conditions d’erreur qui peuvent se produire au moment de l’exécution, même si votre code est correct, par exemple, « fichier introuvable » ou « mémoire insuffisante. » Vous souhaiterez peut-être récupérer à partir de ces conditions, même si la récupération uniquement, un message dans un journal et arrête le programme. Vérifiez toujours les arguments aux fonctions publiques en utilisant des exceptions. Même si votre fonction est exempte d’erreurs, ne peut pas avoir un contrôle complet sur les arguments qu’un utilisateur peut passer à celle-ci.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Exceptions C++ et des exceptions SEH de Windows

Les programmes C et C++ peuvent utiliser la mécanisme (SEH) dans le système d’exploitation Windows structurée des exceptions. Les concepts de gestion des exceptions structurées ressemblent à ceux des exceptions C++, mais utilise SEH le **__try**, **__except**, et **__finally** construit au lieu de **essayez** et **catch**. Dans Visual C++, les exceptions C++ sont implémentées pour SEH. Toutefois, lorsque vous écrivez du code C++, utilisez la syntaxe d’exception C++.

Pour plus d’informations sur la gestion structurée des exceptions, consultez [structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a>Spécifications d’exception et noexcept

Les spécifications d’exceptions ont été introduites dans C++ qui permet de spécifier les exceptions qu’une fonction peut lever. Toutefois, les spécifications d’exceptions se sont révélées problématiques dans la pratique et sont déconseillées dans la norme C ++ 11 brouillon. Nous vous recommandons de ne pas utiliser les spécifications d’exceptions à l’exception de `throw()`, ce qui indique que la fonction n’autorise aucune exception d’échapper. Si vous devez utiliser des spécifications d’exception du type `throw(` *type*`)`, n’oubliez pas que Visual C++ s’éloigne de la norme de certaines façons. Pour plus d’informations, consultez [spécifications d’Exception (throw)](../cpp/exception-specifications-throw-cpp.md). Le `noexcept` spécificateur est introduit dans C ++ 11 en tant que l’alternative recommandée à `throw()`.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour établir une interface entre le code exceptionnel et le code non exceptionnel](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)