---
title: Attributs de la norme C++ | Documents Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.topic: language-reference
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: 7bd7fd4e01fb210069f4dbae42a671e4dd9c64c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416195"
---
# <a name="attributes-in-c"></a>Attributs en C++

La norme C++ définit un ensemble d’attributs et permet également aux fournisseurs de compilateur définir leurs propres attributs (au sein d’un espace de noms spécifiques au fournisseur), mais les compilateurs sont nécessaires pour reconnaître uniquement les attributs définis dans la norme.

Dans certains cas, les attributs standard se chevauchent avec les paramètres spécifiques au compilateur declspec. Dans Visual C++, vous pouvez utiliser la `[[deprecated]]` attribut au lieu d’utiliser `declspec(deprecated)` et l’attribut n’est reconnu par un compilateur conforme. Pour tous les autres paramètres declspec tels que dllimport et dllexport, il n’existe encore aucun équivalent de l’attribut que vous devez continuer à utiliser la syntaxe de declspec. Attributs n’affectent pas le système de type, et elles ne modifient pas la signification d’un programme. Les compilateurs ignorent les valeurs d’attribut qu'ils ne reconnaissent pas.

**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : dans l’étendue d’une liste d’attributs, vous pouvez spécifier l’espace de noms pour tous les noms avec un seul `using` introducer :

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Attributs de la norme C++

Dans C ++ 11, les attributs fournissent une méthode normalisée pour annoter des constructions C++ (y compris mais non limité à des classes, des fonctions, des variables et des blocs) avec des informations supplémentaires qui peuvent être ou non spécifiques au fournisseur. Un compilateur peut utiliser ces informations pour générer des messages d’information ou d’appliquer une logique spéciale lors de la compilation du code avec attributs. Le compilateur ignore tous les attributs qu’il ne reconnaît pas, ce qui signifie que vous ne pouvez pas définir vos propres attributs personnalisés à l’aide de cette syntaxe. Les attributs sont placés entre crochets doubles :

```cpp
[[deprecated]]
void Foo(int);
```

Les attributs représentent une alternative standardisée aux extensions spécifiques au fournisseur comme directives #pragma, __declspec() (Visual C++), ou &#95; &#95;attribut&#95; &#95; (GNU). Toutefois, vous devrez toujours utiliser les constructions spécifiques au fournisseur pour la plupart des cas. Actuellement, la norme spécifie un compilateur conforme doit reconnaître les attributs suivants :

- `[[noreturn]]` Spécifie qu’une fonction ne retourne jamais ; en d’autres termes, elle lève toujours une exception. Le compilateur peut ajuster ses règles de compilation de `[[noreturn]]` entités.

- `[[carries_dependency]]` Spécifie que la fonction propage les dépendances de données classement en ce qui concerne la synchronisation de threads. L’attribut peut être appliqué à un ou plusieurs paramètres pour spécifier que l’argument passé dans comporte une dépendance dans le corps de la fonction. L’attribut peut être appliqué à la fonction elle-même, pour spécifier que la valeur de retour comporte une dépendance de la fonction. Le compilateur peut utiliser ces informations pour générer du code plus efficace.

- `[[deprecated]]` **Visual Studio 2015 et versions ultérieur :** Spécifie qu’une fonction n’est pas destinée à être utilisé et peut ne pas exister dans les futures versions d’une interface de bibliothèque. Le compilateur peut l’utiliser pour générer un message d’information lorsque le code client tente d’appeler la fonction. Peut être appliqué à la déclaration d’une classe, un nom de typedef, une variable, un membre de données non statiques, une fonction, un espace de noms, une énumération, un énumérateur ou une spécialisation de modèle.  

- `[[fallthrough]]` **Visual Studio 2017 et versions ultérieur :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) le `[[fallthrough]]` attribut peut être utilisé dans le contexte de [commutateur](switch-statement-cpp.md) en tant qu’indicateur pour le compilateur (ou toute personne qui lit les instructions le code) qui le comportement fallthrough est destiné. Le compilateur Visual C++ n’avertit actuellement pas sur le comportement de fallthrough, afin de cet attribut n’a aucun comportement de compilateur d’effet.

- `[[nodiscard]]` **Visual Studio 2017 15,3 et versions ultérieures :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) Spécifie que la valeur de retour d’une fonction n’est pas conçue pour être rejetés. Déclenche avertissement C4834, comme illustré dans cet exemple :

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]` **Visual Studio 2017 15,3 et versions ultérieures :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) indique que variable, fonction, classe, typedef, les données membres non statiques, enum ou spécialisation de modèle peut délibérément pas utilisée. Le compilateur ne pas avertit lorsqu’une entité marquée `[[maybe_unused]]` n’est pas utilisé. Une entité qui est déclarée sans l’attribut peut être redéclarée ultérieurement avec l’attribut et vice versa. Une entité est considérée comme marqué après que sa première déclaration est marquée est analysée et pour le reste de la traduction de l’unité de traduction actuelle.

## <a name="microsoft-specific-attributes"></a>Attributs spécifiques à Microsoft

- `[[gsl::suppress(rules)]]` Cet attribut spécifique à Microsoft est utilisé pour supprimer les avertissements à partir des outils d’analyse afin d’appliquer des [bibliothèque de prise en charge des instructions (GSL)](https://github.com/Microsoft/GSL) règles dans le code. Par exemple, considérez cet extrait de code :

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

   L’exemple déclenche ces avertissements :

   - 26494 (type de règle 5 : toujours initialiser un objet.)

   - 26485 (limites règle 3 : aucun tableau pour l’atténuation de pointeur.)

   - 26481 (limites règle 1 : ne pas utiliser l’opération arithmétique de pointeur. Utilisez étendue à la place.)

   Les deux premiers avertissements sont activés lorsque vous compilez ce code avec l’outil d’analyse du code CppCoreCheck installé et activé. Mais le troisième avertissement n’est pas déclenché en raison de l’attribut. Vous pouvez supprimer tout le profil de limites en écrivant [[gsl::suppress(bounds)]] sans inclure un numéro de règle spécifique. Les instructions de base C++ sont conçues pour vous aider à écrire du code une meilleure et plus sûr. L’attribut supprimer facilite la désactiver les avertissements lorsqu’ils ne sont pas souhaités.
