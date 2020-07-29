---
title: Attributs en C++
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: efdc62e2343135aee483520f633bac99519455b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229205"
---
# <a name="attributes-in-c"></a>Attributs en C++

La norme C++ définit un ensemble d’attributs et permet également aux fournisseurs de compilateur de définir leurs propres attributs (dans un espace de noms spécifique au fournisseur), mais les compilateurs sont tenus de reconnaître uniquement les attributs définis dans la norme.

Dans certains cas, les attributs standard se chevauchent avec les paramètres declspec spécifiques au compilateur. Dans Visual C++, vous pouvez utiliser l' `[[deprecated]]` attribut au lieu de `declspec(deprecated)` et l’attribut sera reconnu par tout compilateur conforme. Pour tous les autres paramètres declspec tels que dllimport et dllexport, il n’y a pas encore d’attribut équivalent. vous devez donc continuer à utiliser la syntaxe declspec. Les attributs n’affectent pas le système de type et ne modifient pas la signification d’un programme. Les compilateurs ignorent les valeurs d’attribut qu’ils ne reconnaissent pas.

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : dans la liste étendue d’un attribut, vous pouvez spécifier l’espace de noms pour tous les noms avec un seul **`using`** introducteur :

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Attributs standard C++

En C++ 11, les attributs fournissent une méthode standardisée pour annoter les constructions C++ (y compris, mais sans s’y limiter, les classes, les fonctions, les variables et les blocs) avec des informations supplémentaires qui peuvent ou non être spécifiques au fournisseur. Un compilateur peut utiliser ces informations pour générer des messages d’information ou pour appliquer une logique spéciale lors de la compilation du code avec attributs. Le compilateur ignore tous les attributs qu’il ne reconnaît pas, ce qui signifie que vous ne pouvez pas définir vos propres attributs personnalisés à l’aide de cette syntaxe. Les attributs sont placés entre crochets doubles :

```cpp
[[deprecated]]
void Foo(int);
```

Les attributs représentent une alternative standardisée aux extensions spécifiques au fournisseur, telles que les directives de #pragma, le __declspec () (Visual C++) ou la&#95;&#95;  d’attributs &#95;&#95;(GNU). Toutefois, vous devrez toujours utiliser les constructions spécifiques au fournisseur dans la plupart des cas. La norme spécifie actuellement les attributs suivants qu’un compilateur conforme doit reconnaître :

- `[[noreturn]]`Spécifie qu’une fonction ne retourne jamais ; en d’autres termes, il lève toujours une exception. Le compilateur peut ajuster ses règles de compilation pour les `[[noreturn]]` entités.

- `[[carries_dependency]]`Spécifie que la fonction propage l’ordonnancement des dépendances de données par rapport à la synchronisation des threads. L’attribut peut être appliqué à un ou plusieurs paramètres, pour spécifier que l’argument passé porte une dépendance dans le corps de la fonction. L’attribut peut être appliqué à la fonction elle-même, pour spécifier que la valeur de retour porte une dépendance à partir de la fonction. Le compilateur peut utiliser ces informations pour générer du code plus efficace.

- `[[deprecated]]`**Visual Studio 2015 et versions ultérieures :** Spécifie qu’une fonction n’est pas destinée à être utilisée et qu’elle n’existe pas dans les versions ultérieures d’une interface de bibliothèque. Le compilateur peut l’utiliser pour générer un message d’information lorsque le code client tente d’appeler la fonction. Peut être appliqué à la déclaration d’une classe, à un nom de typedef, à une variable, à un membre de données non statique, à une fonction, à un espace de noms, à une énumération, à un énumérateur ou à une spécialisation de modèle.

- `[[fallthrough]]`**Visual Studio 2017 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) l' `[[fallthrough]]` attribut peut être utilisé dans le contexte des instructions [switch](switch-statement-cpp.md) en tant qu’indicateur pour le compilateur (ou toute personne lisant le code) auquel le comportement FallThrough est destiné. Le compilateur Microsoft C++ n’avertit pas actuellement le comportement de FallThrough. cet attribut n’a donc aucun effet sur le comportement du compilateur.

- `[[nodiscard]]`**Visual Studio 2017 version 15,3 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) spécifie que la valeur de retour d’une fonction n’est pas destinée à être ignorée. Déclenche un avertissement C4834, comme illustré dans cet exemple :

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]`**Visual Studio 2017 version 15,3 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) spécifie qu’une variable, une fonction, une classe, un typedef, un membre de données non statiques, un enum ou une spécialisation de modèle peut ne pas être utilisé intentionnellement. Le compilateur n’avertit pas lorsqu’une entité marquée `[[maybe_unused]]` n’est pas utilisée. Une entité déclarée sans l’attribut peut être redéclarée ultérieurement avec l’attribut et vice versa. Une entité est considérée comme marquée après sa première déclaration marquée comme étant analysée et pour le reste de la traduction de l’unité de traduction actuelle.

## <a name="microsoft-specific-attributes"></a>Attributs spécifiques à Microsoft

- `[[gsl::suppress(rules)]]`Cet attribut spécifique à Microsoft est utilisé pour supprimer les avertissements des contrôleurs qui appliquent des règles de la [bibliothèque de prise en charge des instructions (GSL)](https://github.com/Microsoft/GSL) dans le code. Par exemple, considérez cet extrait de code :

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning C26494 will be fired
        int* p = arr; // GSL warning C26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning C26481 suppressed
            p = q--; // GSL warning C26481 suppressed
        }
    }
    ```

  L’exemple déclenche ces avertissements :

  - 26494 (type règle 5 : toujours initialiser un objet.)

  - 26485 (règle de limite 3 : aucune dégradation de tableau en pointeur.)

  - 26481 (règle de limites 1 : n’utilisez pas l’arithmétique de pointeur. Utilisez à la place span.)

  Les deux premiers avertissements se déclenchent quand vous compilez ce code avec l’outil d’analyse du code CppCoreCheck installé et activé. Mais le troisième avertissement ne se déclenche pas en raison de l’attribut. Vous pouvez supprimer le profil de limites entier en écrivant [[GSL :: Suppress (Bounds)]] sans inclure un numéro de règle spécifique. Les C++ Core Guidelines sont conçus pour vous aider à écrire du code plus sécurisé. L’attribut de suppression permet de désactiver facilement les avertissements lorsqu’ils ne sont pas souhaités.
  