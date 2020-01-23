---
title: Attributs dansC++
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: 5967974d419299778e4aadaa235ee21c62e16d34
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518294"
---
# <a name="attributes-in-c"></a>Attributs dansC++

La C++ norme définit un ensemble d’attributs et permet également aux fournisseurs de compilateur de définir leurs propres attributs (dans un espace de noms spécifique au fournisseur), mais les compilateurs sont tenus de reconnaître uniquement les attributs définis dans la norme.

Dans certains cas, les attributs standard se chevauchent avec les paramètres declspec spécifiques au compilateur. En Visual C++, vous pouvez utiliser l’attribut `[[deprecated]]` au lieu d’utiliser `declspec(deprecated)` et l’attribut sera reconnu par tout compilateur conforme. Pour tous les autres paramètres declspec tels que dllimport et dllexport, il n’y a pas encore d’attribut équivalent. vous devez donc continuer à utiliser la syntaxe declspec. Les attributs n’affectent pas le système de type et ne modifient pas la signification d’un programme. Les compilateurs ignorent les valeurs d’attribut qu’ils ne reconnaissent pas.

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : dans la liste étendue d’un attribut, vous pouvez spécifier l’espace de noms pour tous les noms avec une seule **utilisation** d’introducteur :

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C++Attributs standard

En C++ 11, les attributs fournissent une méthode standardisée pour C++ annoter des constructions (y compris, mais sans s’y limiter, des classes, des fonctions, des variables et des blocs) avec des informations supplémentaires qui peuvent ou non être spécifiques au fournisseur. Un compilateur peut utiliser ces informations pour générer des messages d’information ou pour appliquer une logique spéciale lors de la compilation du code avec attributs. Le compilateur ignore tous les attributs qu’il ne reconnaît pas, ce qui signifie que vous ne pouvez pas définir vos propres attributs personnalisés à l’aide de cette syntaxe. Les attributs sont placés entre crochets doubles :

```cpp
[[deprecated]]
void Foo(int);
```

Les attributs représentent une alternative standardisée aux extensions spécifiques au fournisseur, telles que les directives de #pragma, C++__declspec () &#95; &#95;(&#95; &#95; visuel) ou un attribut (GNU). Toutefois, vous devrez toujours utiliser les constructions spécifiques au fournisseur dans la plupart des cas. La norme spécifie actuellement les attributs suivants qu’un compilateur conforme doit reconnaître :

- `[[noreturn]]` spécifie qu’une fonction ne retourne jamais ; en d’autres termes, il lève toujours une exception. Le compilateur peut ajuster ses règles de compilation pour les entités `[[noreturn]]`.

- `[[carries_dependency]]` spécifie que la fonction propage l’ordonnancement des dépendances de données en ce qui concerne la synchronisation des threads. L’attribut peut être appliqué à un ou plusieurs paramètres, pour spécifier que l’argument passé porte une dépendance dans le corps de la fonction. L’attribut peut être appliqué à la fonction elle-même, pour spécifier que la valeur de retour porte une dépendance à partir de la fonction. Le compilateur peut utiliser ces informations pour générer du code plus efficace.

- `[[deprecated]]` **Visual Studio 2015 et versions ultérieures :** spécifie qu’une fonction n’est pas destinée à être utilisée et qu’elle n’existe pas dans les versions ultérieures d’une interface de bibliothèque. Le compilateur peut l’utiliser pour générer un message d’information lorsque le code client tente d’appeler la fonction. Peut être appliqué à la déclaration d’une classe, à un nom de typedef, à une variable, à un membre de données non statique, à une fonction, à un espace de noms, à une énumération, à un énumérateur ou à une spécialisation de modèle.

- `[[fallthrough]]` **Visual Studio 2017 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) l’attribut `[[fallthrough]]` peut être utilisé dans le contexte des instructions [switch](switch-statement-cpp.md) en tant qu’indicateur pour le compilateur (ou toute personne lisant le code) auquel le comportement FallThrough est destiné. Actuellement, C++ le compilateur Microsoft n’émet pas d’avertissement sur le comportement FallThrough. cet attribut n’a donc aucun effet sur le comportement du compilateur.

- `[[nodiscard]]` **Visual Studio 2017 version 15,3 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) spécifie que la valeur de retour d’une fonction n’est pas destinée à être ignorée. Déclenche un avertissement C4834, comme illustré dans cet exemple :

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]` **Visual Studio 2017 version 15,3 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) spécifie qu’une variable, une fonction, une classe, un typedef, une donnée membre non statique, une énumération ou une spécialisation de modèle peut ne pas être utilisé intentionnellement. Le compilateur n’avertit pas lorsqu’une entité marquée `[[maybe_unused]]` n’est pas utilisée. Une entité déclarée sans l’attribut peut être redéclarée ultérieurement avec l’attribut et vice versa. Une entité est considérée comme marquée après sa première déclaration marquée comme étant analysée et pour le reste de la traduction de l’unité de traduction actuelle.

## <a name="microsoft-specific-attributes"></a>Attributs spécifiques à Microsoft

- `[[gsl::suppress(rules)]]` cet attribut spécifique à Microsoft est utilisé pour supprimer les avertissements des contrôleurs qui appliquent des règles de la [bibliothèque de prise en charge des instructions (GSL)](https://github.com/Microsoft/GSL) dans le code. Par exemple, considérez cet extrait de code :

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning 26494 will be fired
        int* p = arr; // GSL warning 26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning 26481 suppressed
            p = q--; // GSL warning 26481 suppressed
        }
    }
    ```

  L’exemple déclenche ces avertissements :

  - 26494 (type règle 5 : toujours initialiser un objet.)

  - 26485 (règle de limite 3 : aucune dégradation de tableau en pointeur.)

  - 26481 (règle de limites 1 : n’utilisez pas l’arithmétique de pointeur. Utilisez à la place span.)

  Les deux premiers avertissements se déclenchent quand vous compilez ce code avec l’outil d’analyse du code CppCoreCheck installé et activé. Mais le troisième avertissement ne se déclenche pas en raison de l’attribut. Vous pouvez supprimer le profil de limites entier en écrivant [[GSL :: Suppress (Bounds)]] sans inclure un numéro de règle spécifique. Les C++ recommandations de base sont conçues pour vous aider à écrire du code plus sécurisé. L’attribut de suppression permet de désactiver facilement les avertissements lorsqu’ils ne sont pas souhaités.
  