---
title: Attributs en C++
ms.date: 06/01/2018
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: 81de2816c208d5ddc879f04d70912c3dddcd7832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284745"
---
# <a name="attributes-in-c"></a>Attributs en C++

La norme C++ définit un ensemble d’attributs et permet également aux fournisseurs de compilateur définir leurs propres attributs (au sein d’un espace de noms spécifiques au fournisseur), mais les compilateurs sont nécessaires pour reconnaître uniquement les attributs définis dans la norme.

Dans certains cas, les attributs standard se chevauchent avec les paramètres spécifiques au compilateur declspec. Dans Visual C++, vous pouvez utiliser la `[[deprecated]]` attribut au lieu d’utiliser `declspec(deprecated)` et l’attribut est reconnu par n’importe quel compilateur conforme. Pour tous les autres paramètres declspec tels que dllimport et dllexport, il n’est encore aucun équivalent de l’attribut que vous devez continuer à utiliser la syntaxe de declspec. Attributs n’affectent pas le système de type, et ils ne changent la signification d’un programme. Les compilateurs ignorent les valeurs d’attribut qu'ils ne reconnaissent pas.

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : Dans l’étendue d’une liste d’attributs, vous pouvez spécifier l’espace de noms pour tous les noms avec un seul **à l’aide de** introducer :

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Attributs de la norme C++

Dans C ++ 11, les attributs fournissent une méthode standardisée pour annoter des constructions C++ (y compris mais sans limitation de classes, des fonctions, des variables et des blocs) avec des informations supplémentaires qui peuvent être ou non spécifiques au fournisseur. Un compilateur peut utiliser ces informations pour générer des messages d’information, ou pour appliquer une logique spéciale lors de la compilation du code avec attributs. Le compilateur ignore tous les attributs qu’il ne reconnaît pas, ce qui signifie que vous ne pouvez pas définir vos propres attributs personnalisés à l’aide de cette syntaxe. Les attributs sont encadrés par des crochets double :

```cpp
[[deprecated]]
void Foo(int);
```

Les attributs représentent une alternative standardisée aux extensions spécifiques au fournisseur telles que des directives #pragma, __declspec() (Visual C++), ou &#95; &#95;attribut&#95; &#95; (GNU). Toutefois, vous devrez toujours utiliser les constructions spécifiques au fournisseur pour la plupart des cas. Actuellement, la norme spécifie les attributs suivants qui doit pouvoir reconnaître un compilateur conforme :

- `[[noreturn]]` Spécifie qu’une fonction ne retourne jamais ; en d’autres termes, elle lève toujours une exception. Le compilateur peut ajuster ses règles de compilation pour `[[noreturn]]` entités.

- `[[carries_dependency]]` Spécifie que la fonction propage les dépendances de données classement en ce qui concerne la synchronisation de threads. L’attribut peut être appliqué à un ou plusieurs paramètres, pour spécifier que l’argument transmis comporte une dépendance dans le corps de fonction. L’attribut peut être appliqué à la fonction elle-même, pour spécifier que la valeur de retour comporte une dépendance de la fonction. Le compilateur peut utiliser ces informations pour générer le code plus efficace.

- `[[deprecated]]` **Visual Studio 2015 et versions ultérieur :** Spécifie qu’une fonction n’est pas destinée à utiliser et peut ne pas exister dans les futures versions d’une interface de bibliothèque. Le compilateur peut l’utiliser pour générer un message d’information lorsque le code client tente d’appeler la fonction. Peut être appliqué à la déclaration d’une classe, un nom de typedef, une variable, une donnée membre non static, une fonction, un espace de noms, une énumération, un énumérateur ou une spécialisation de modèle.

- `[[fallthrough]]` **Visual Studio 2017 et versions ultérieur :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) le `[[fallthrough]]` attribut peut être utilisé dans le contexte de [basculer](switch-statement-cpp.md) instructions en tant qu’indicateur pour le compilateur (ou toute personne lisant le code) qui le comportement fallthrough est prévu. Le compilateur Visual C++ n’avertit actuellement pas sur le comportement fallthrough, cet attribut n’a aucun comportement de compilateur effet.

- `[[nodiscard]]` **Visual Studio 2017 15.3 et versions ultérieures :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) Spécifie que valeur de retour d’une fonction n’est pas destinée à être ignoré. Déclenche avertissement de C4834, comme illustré dans cet exemple :

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]` **Visual Studio 2017 15.3 et versions ultérieures :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) Spécifie qu’une variable, fonction, classe, typedef, les données membres non statiques, enum ou spécialisation de modèle peut être pas intentionnellement utilisée. Le compilateur ne pas avertit lorsqu’une entité marquée `[[maybe_unused]]` n’est pas utilisé. Une entité est déclarée sans l’attribut ultérieurement peut être redéclarée avec l’attribut et vice versa. Une entité est considérée comme marqué après que sa première déclaration marquée est analysée et pour le reste de la traduction de l’unité de traduction actuelle.

## <a name="microsoft-specific-attributes"></a>Attributs spécifiques à Microsoft

- `[[gsl::suppress(rules)]]` Cet attribut spécifique de Microsoft est utilisé pour supprimer les avertissements à partir des vérificateurs qui appliquent [bibliothèque de prise en charge les instructions (GSL)](https://github.com/Microsoft/GSL) règles dans le code. Par exemple, considérez cet extrait de code :

    ```cpp
    void main()
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

  L’exemple génère ces avertissements :

  - 26494 (tapez règle 5 : Initialisez toujours un objet.)

  - 26485 (3 de règle de limites : Aucun tableau à l’atténuation de pointeur.)

  - 26481 (limites de règle 1 : N’utilisez pas opérations arithmétiques de pointeur. Utilisez span à la place.)

  Les deux premiers avertissements sont activés lorsque vous compilez ce code avec l’outil d’analyse du code CppCoreCheck installé et activé. Mais le troisième avertissement ne se déclenche en raison de l’attribut. Vous pouvez supprimer le profil bounds entière en écrivant [[gsl::suppress(bounds)]] sans inclure un numéro de règle spécifique. Les recommandations C++ Core Guidelines sont conçus pour vous aider à écrire du code de meilleure et plus sûr. L’attribut supprimer rend plus facile de désactiver les avertissements lorsqu’ils ne doivent pas figurer.