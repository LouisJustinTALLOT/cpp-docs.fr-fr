---
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: 4ac79c23379dd1bf1c85521fdf0c28947d3b7ab9
ms.sourcegitcommit: 20a1356193fbe0ddd1002e798b952917eafc3439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661581"
---
# <a name="staticassert"></a>static_assert

Teste une assertion logicielle au moment de la compilation. Si l’expression constante spécifiée a la valeur FALSe, le compilateur affiche le message spécifié, s’il est fourni, et la compilation échoue avec l’erreur C2338; dans le cas contraire, la déclaration n’a aucun effet.

## <a name="syntax"></a>Syntaxe

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*constant-expression*|Expression constante intégrale pouvant être convertie en expression booléenne.<br /><br /> Si l’expression évaluée est égale à zéro (false), le paramètre *de littéral de chaîne* est affiché et la compilation échoue avec une erreur. Si l’expression est différente de zéro (true), la Déclaration **static_assert** n’a aucun effet.|
|*string-literal*|Message qui s’affiche si le paramètre *de l’expression constante* est égal à zéro. Le message est une chaîne de caractères dans le [jeu de caractères de base](../c-language/ascii-character-set.md) du compilateur; autrement dit, il ne s’agit pas de [caractères multioctets ou larges](../c-language/multibyte-and-wide-characters.md).|

## <a name="remarks"></a>Notes

Le paramètre d' *expression constante* d’une déclaration **static_assert** représente une *assertion logicielle*. Une assertion logicielle spécifie une condition supposée être vraie en un point particulier de votre programme. Si la condition est true, la Déclaration **static_assert** n’a aucun effet. Si la condition est false, l’assertion échoue, le compilateur affiche le message dans le paramètre de *littéral de chaîne* et la compilation échoue avec une erreur. Dans Visual Studio 2017 et versions ultérieures, le paramètre de littéral de chaîne est facultatif.

La Déclaration **static_assert** teste une assertion logicielle au moment de la compilation. En revanche, la [macro Assert et les fonctions _ Assert et wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) testent une assertion logicielle au moment de l’exécution et entraînent un coût d’exécution en espace ou en temps. La Déclaration **static_assert** est particulièrement utile pour déboguer des modèles, car les arguments template peuvent être inclus dans le paramètre d' *expression constante* .

Le compilateur examine la Déclaration **static_assert** pour rechercher les erreurs de syntaxe lorsque la déclaration est rencontrée. Le compilateur évalue immédiatement le paramètre de l' *expression constante* s’il ne dépend pas d’un paramètre de modèle. Sinon, le compilateur évalue le paramètre d' *expression constante* lorsque le modèle est instancié. Par conséquent, le compilateur peut publier un message de diagnostic une fois la déclaration rencontrée, puis à nouveau lorsque le modèle est instancié.

Vous pouvez utiliser le mot clé **static_assert** au niveau de l’espace de noms, de la classe ou de la portée de bloc. (Le mot clé **static_assert** est techniquement une déclaration, même s’il n’introduit pas de nouveau nom dans votre programme, car il peut être utilisé au niveau de la portée espace de noms.)

## <a name="description"></a>Description

Dans l’exemple suivant, la Déclaration **static_assert** a une portée espace de noms. Comme le compilateur connaît la taille du type `void *`, l'expression est évaluée immédiatement.

## <a name="example"></a>Exemple

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>Description

Dans l’exemple suivant, la Déclaration **static_assert** a une portée de classe. Le **static_assert** vérifie qu’un paramètre de modèle est un type Pod ( *Plain Old Data* ). Le compilateur examine la Déclaration **static_assert** lorsqu’elle est déclarée, mais n’évalue pas le paramètre de l' *expression constante* tant que le `basic_string` modèle de classe `main()`n’est pas instancié dans.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iosfwd>
namespace std {
template <class CharT, class Traits = std::char_traits<CharT> >
class basic_string {
    static_assert(std::is_pod<CharT>::value,
                  "Template argument CharT must be a POD type in class template basic_string");
    // ...
    };
}

struct NonPOD {
    NonPOD(const NonPOD &) {}
    virtual ~NonPOD() {}
};

int main()
{
    std::basic_string<char> bs;
}
```

## <a name="description"></a>Description

Dans l’exemple suivant, la Déclaration **static_assert** a une portée de bloc. Le **static_assert** vérifie que la taille de la structure VMPage est égale à la taille de page de mémoire virtuelle du système.

## <a name="example"></a>Exemples

```cpp
#include <sys/param.h> // defines PAGESIZE
class VMMClient {
public:
    struct VMPage { // ...
           };
    int check_pagesize() {
    static_assert(sizeof(VMPage) == PAGESIZE,
        "Struct VMPage must be the same size as a system virtual memory page.");
    // ...
    }
// ...
};
```

## <a name="see-also"></a>Voir aussi

[Assertion et messages fournis par l’utilisateur (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error, directive (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Modèles](../cpp/templates-cpp.md)<br/>
[Jeu de caractères ASCII](../c-language/ascii-character-set.md)<br/>
[Déclarations et définitions](declarations-and-definitions-cpp.md)