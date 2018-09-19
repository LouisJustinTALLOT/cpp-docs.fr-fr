---
title: Compilateur avertissement (niveau 3) C4996 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4996
dev_langs:
- C++
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d618ace9d922daabecf908c76a319e89a9fdedcc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094180"
---
# <a name="compiler-warning-level-3-c4996"></a>Compilateur avertissement (niveau 3) C4996

Le compilateur a rencontré une déclaration déconseillée. **Cet avertissement est toujours un message délibéré à partir de l’auteur de la bibliothèque ou le fichier d’en-tête inclus que vous ne devez pas utiliser le symbole déconseillé sans avoir à comprendre les conséquences.** Le message d’avertissement réelle est spécifié par l’attribut sur le site de la déclaration ou le modificateur de désapprobation.

Il s’agit de quelques messages d’erreur C4996 courants générés par la bibliothèque Runtime C et la bibliothèque Standard, mais pas une liste exhaustive. Suivez les liens ou lisez la suite pour les méthodes pour résoudre le problème ou de désactiver l’avertissement.

- [Le nom POSIX pour cet élément est déconseillé. Au lieu de cela, utilisez le nom conforme ISO C et C++ : *nouveau_nom*. Consultez l’aide en ligne pour plus d’informations.](#posix-function-names)

- [Cette fonction ou cette variable peut être dangereux. Envisagez d’utiliser *version_sécurisée* à la place. Pour désactiver la dépréciation, utilisez \_CRT\_SECURE\_non\_avertissements.  Consultez l’aide en ligne pour plus d’informations.](#unsafe-crt-library-functions)

- [' std ::*function_name*::\_Unchecked\_itérateurs ::\_Deprecate' appel à std ::*nom_fonction*avec des paramètres qui peuvent être non sécurisés - cet appel s’appuie sur l’appelant pour vérifier que les valeurs passées sont corrects. Pour désactiver cet avertissement, utilisez -D_SCL_SECURE_NO_WARNINGS. Consultez la documentation sur l’utilisation de Visual C++ « Itérateurs vérifiés »](#unsafe-standard-library-functions)

- [Cette fonction ou cette variable a été remplacée par une fonctionnalité plus récente du système d’exploitation ou de la bibliothèque. Envisagez d’utiliser *Nouvel_élément* à la place. Consultez l’aide en ligne pour plus d’informations.](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>Cause

L’erreur C4996 se produit lorsque le compilateur rencontre une fonction ou une variable qui est marquée en tant que [déconseillée](../../cpp/deprecated-cpp.md) à l’aide un `__declspec(deprecated)` modificateur, ou lorsque vous essayez d’accéder à une fonction, un membre de classe ou un typedef qui a C ++ 14 [ \[ \[déconseillée\] \] ](../../cpp/attributes.md) attribut. Vous pouvez utiliser la `__declspec(deprecated)` modificateur ou `[[deprecated]]` attribut vous-même dans vos bibliothèques ou des fichiers d’en-tête pour informer vos clients sur les fonctions déconseillées, des variables, des membres ou des typedefs.

## <a name="remarks"></a>Notes

Nombreuses fonctions, fonctions membres, les fonctions de modèle et les variables globales dans les bibliothèques dans Visual Studio sont marqués comme *déconseillée*. Ces fonctions sont déconseillées, car ils peuvent avoir un autre nom préféré, peut-être non sécurisé ou comporte une variante plus sécurisée, ou bien être obsolètes. Nombre de messages de désapprobation inclure une suggestion de remplacement pour la fonction déconseillée ou une variable globale.

Pour résoudre ce problème, nous vous recommandons généralement de que vous modifiez votre code pour utiliser les variables globales ni des fonctions plus sûres ou mis à jour suggérées à la place. Si vous avez besoin d’utiliser les fonctions existantes ou des variables pour des raisons de portabilité, l’avertissement peut être désactivé.

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>Pour désactiver l’avertissement sans résolution du problème

Vous pouvez désactiver l’avertissement pour une ligne de code spécifique à l’aide de la [avertissement](../../preprocessor/warning.md) pragma, `#pragma warning(suppress : 4996)`. Vous pouvez également désactiver l’avertissement dans un fichier à l’aide du pragma warning, `#pragma warning(disable : 4996)`.

Vous pouvez désactiver l’avertissement dans le monde entier dans les versions de ligne de commande à l’aide de la **/wd4996** option de ligne de commande.

Pour désactiver l’avertissement pour un projet entier dans l’IDE Visual Studio :

- Ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet. Pour plus d’informations sur l’utilisation de la boîte de dialogue Pages de propriétés, consultez [Pages de propriétés](../../ide/property-pages-visual-cpp.md).
- Sélectionnez le **propriétés de Configuration**, **C/C++**, **avancé** page.
- Modifier le **désactivation des avertissements spécifiques** propriété à ajouter `4996`. Choisissez **OK** pour appliquer vos modifications.

Vous pouvez également utiliser des macros de préprocesseur pour désactiver certaines classes spécifiques d’avertissements de désapprobation utilisés dans les bibliothèques. Ces macros sont décrits ci-dessous.

Pour définir une macro de préprocesseur dans Visual Studio :

- Ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet. Pour plus d’informations sur l’utilisation de la boîte de dialogue Pages de propriétés, consultez [Pages de propriétés](../../ide/property-pages-visual-cpp.md).
- Développez **propriétés de Configuration > C/C++ > préprocesseur**.
- Dans le **définitions de préprocesseur** propriété, ajoutez le nom de macro. Choisissez **OK** pour enregistrer, puis régénérez votre projet.

Pour définir une macro uniquement dans les fichiers source spécifique, ajoutez une ligne comme `#define EXAMPLE_MACRO_NAME` avant n’importe quelle ligne qui inclut un fichier d’en-tête.

## <a name="specific-c4996-messages"></a>Messages de l’erreur C4996 spécifiques

Voici quelques-unes des sources courantes d’erreurs et avertissements de l’erreur C4996.

### <a name="posix-function-names"></a>Noms de fonction POSIX

**Le nom POSIX pour cet élément est déconseillé. Au lieu de cela, utilisez le nom conforme ISO C et C++ :** *nouveau_nom*. **Consultez l’aide en ligne pour plus d’informations.**

Microsoft a renommé certaines fonctions POSIX dans le CRT se conforme à C99 et C ++ 03 règles pour les noms définis par l’implémentation de fonction globale. Seuls les noms POSIX d’origine sont déconseillés, pas les fonctions elles-mêmes. Dans la plupart des cas, un trait de soulignement de début a été ajouté au nom de fonction POSIX pour créer un nom conforme à la norme. Le compilateur émet un avertissement de désapprobation pour le nom de fonction d’origine et suggère le nom par défaut.

Pour résoudre ce problème, nous recommandons généralement que vous modifiez votre code pour utiliser les noms des fonctions proposées à la place. Toutefois, les noms mis à jour sont spécifiques à Microsoft. Si vous avez besoin utiliser les noms de fonction existante pour des raisons de portabilité, vous pouvez désactiver ces avertissements. Les fonctions POSIX sont toujours disponibles dans la bibliothèque sous leurs noms d’origine.

Pour désactiver les avertissements de désapprobation pour ces fonctions, définissez la macro de préprocesseur  **\_CRT\_NONSTDC\_non\_avertissements**. Vous pouvez définir cette macro en ligne de commande en incluant l’option `/D_CRT_NONSTDC_NO_WARNINGS`.


### <a name="unsafe-crt-library-functions"></a>Fonctions de bibliothèque CRT unsafe

**Cette fonction ou cette variable peut être dangereux. Envisagez d’utiliser** *version_sécurisée* **à la place. Pour désactiver la dépréciation, utilisez \_CRT\_SECURE\_non\_avertissements.  Consultez l’aide en ligne pour plus d’informations.**

Microsoft a déprécié de certaines fonctions CRT et la bibliothèque C++ Standard et les variables globales en faveur des versions plus sécurisées. Dans la plupart des cas, les fonctions dépréciées autorisent unchecked accès en lecture ou écriture aux mémoires tampons, ce qui peut entraîner des problèmes de sécurité sérieux. Le compilateur émet un avertissement indiquant que ces fonctions sont déconseillées et suggère la fonction préférée.

Pour résoudre ce problème, nous vous recommandons d’utiliser la fonction ou variable *version_sécurisée* à la place. Si vous avez vérifié qu’il n’est pas possible pour un remplacement de la mémoire tampon ou overread se produisent dans votre code et vous ne pouvez pas modifier le code pour des raisons de portabilité, vous pouvez désactiver l’avertissement.

Pour désactiver les avertissements déconseillant ces fonctions dans le CRT, définissez  **\_CRT\_SECURE\_non\_avertissements**. Pour désactiver les avertissements concernant les variables globales déconseillées, définissez  **\_CRT\_SECURE\_non\_avertissements\_GLOBALS**. Pour plus d’informations sur ces variables globales et les fonctions déconseillées, consultez [des fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md) et [bibliothèques sécurisées : bibliothèque Standard C++](../../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="unsafe-standard-library-functions"></a>Fonctions de bibliothèque Standard unsafe

__' std ::__*function_name*__::\_Unchecked\_itérateurs ::\_Deprecate' appel à std ::__*function_name* **avec des paramètres qui peuvent être non sécurisés - cet appel s’appuie sur l’appelant pour vérifier que les valeurs passées sont corrects. Pour désactiver cet avertissement, utilisez -D\_SCL\_SECURE\_non\_avertissements. Consultez la documentation sur l’utilisation de Visual C++ « Itérateurs vérifiés »**

Cet avertissement s’affiche dans les versions debug, car certaines fonctions de modèle de bibliothèque C++ Standard ne vérifient pas les paramètres sont corrects. Dans la plupart des cas, il s’agit pas suffisamment d’informations n’étant pas disponible pour la fonction de vérification des limites de conteneur, ou parce que les itérateurs peuvent être utilisés correctement avec la fonction. Cet avertissement permet d’identifier ces utilisations de la fonction, car ils peuvent être une source de failles de sécurité graves dans votre programme. Pour plus d'informations, consultez [Checked Iterators](../../standard-library/checked-iterators.md).

Par exemple, cet avertissement s’affiche en mode débogage si vous passez un pointeur d’élément à `std::copy` au lieu d’un tableau ordinaire. Pour résoudre ce problème, utilisez un tableau déclaré de manière appropriée, afin que la bibliothèque peut vérifier les extensions de tableau et effectuer la vérification des limites.

```cpp
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>

void example(char const * const src) {
    char dest[1234];
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements
}
```

Plusieurs algorithmes de bibliothèque standard ont été mis à jour pour les versions « double range » dans C ++ 14. Si vous utilisez les versions de plage double, la deuxième plage fournit la vérification des limites nécessaires :

```cpp
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>

bool example(
    char const * const left,
    const size_t leftSize,
    char const * const right,
    const size_t rightSize)
{
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead:
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK
    return result;
}
```

Cet exemple montre plusieurs façons plus la bibliothèque standard peut être utilisée pour vérifier l’utilisation d’itérateur, et lorsque l’utilisation non contrôlée peut être dangereuse :

```cpp
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    // NOTE: This applies only when raw arrays are
    // given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (i.e. an overrun triggers undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(),
        stdext::make_checked_array_iterator(p7, 16),
        [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator
    // is marked as checked in debug mode, but it performs no checking,
    // so an overrun triggers undefined behavior
    int a8[16];
    int * p8 = a8;
    transform( v.begin(), v.end(),
        stdext::make_unchecked_array_iterator(p8),
        [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

Si vous avez vérifié que votre code ne peut pas avoir une mémoire tampon en erreur dans les fonctions de bibliothèque Standard qui déclenchent cet avertissement de dépassement, il pouvez que vous souhaitez désactiver cet avertissement. Pour désactiver les avertissements pour ces fonctions, définissez  **\_SCL\_SECURE\_non\_avertissements**.

### <a name="checked-iterators-enabled"></a>Itérateurs vérifiés activés

L’erreur C4996 peut également se produire si vous n’utilisez pas un itérateur vérifié lors de la compilation avec `_ITERATOR_DEBUG_LEVEL` défini sur 1 ou 2. Il est défini à 2 par défaut pour les builds en mode débogage et la valeur 0 pour les versions commerciales. Pour plus d'informations, voir [Checked Iterators](../../standard-library/checked-iterators.md) .

```cpp
// C4996_checked.cpp
// compile with: /EHsc /W4 /MDd C4996_checked.cpp
#define _ITERATOR_DEBUG_LEVEL 2

#include <algorithm>
#include <iterator>

using namespace std;
using namespace stdext;

int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 10, 11, 12 };
    copy(a, a + 3, b + 1);   // C4996
    // try the following line instead:
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK
}
```

### <a name="unsafe-mfc-or-atl-code"></a>Code unsafe MFC ou ATL

L’erreur C4996 peut également se produire si vous utilisez des fonctions MFC ou ATL qui ont été déconseillées pour des raisons de sécurité.

Pour résoudre ce problème, nous vous recommandons vivement de que vous modifiez votre code pour utiliser les fonctions de mise à jour à la place.

Pour plus d’informations sur la façon de supprimer ces avertissements, consultez [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

### <a name="obsolete-crt-functions-and-variables"></a>Variables et fonctions CRT obsolètes

**Cette fonction ou cette variable a été remplacée par une fonctionnalité plus récente du système d’exploitation ou de la bibliothèque. Envisagez d’utiliser** *Nouvel_élément* **à la place. Consultez l’aide en ligne pour plus d’informations.**

Certaines fonctions de la bibliothèque et certaines variables globales sont déconseillées, car elles sont obsolètes. Ces fonctions et variables sont susceptibles d’être supprimées dans une version future de la bibliothèque. Le compilateur émet un avertissement indiquant que ces éléments sont déconseillées et suggère l’alternative préférée.

Pour résoudre ce problème, nous vous recommandons que modifier votre code pour utiliser la fonction suggérée ou la variable.

Pour désactiver les avertissements de désapprobation pour ces éléments, définissez  **\_CRT\_OBSOLETE\_non\_avertissements**. Pour plus d’informations, consultez la documentation pour la fonction ou la variable déconseillée.

### <a name="marshalling-errors-in-clr-code"></a>Marshaling des erreurs dans le code CLR

L’erreur C4996 peut également se produire lorsque vous utilisez la bibliothèque de marshaling CLR. Dans ce cas, C4996 est une erreur, plutôt qu'un avertissement. Cette erreur se produit lorsque vous utilisez [marshal_as](../../dotnet/marshal-as.md) effectuer une conversion entre deux types de données qui nécessitent une [marshal_context Class](../../dotnet/marshal-context-class.md). Vous pouvez également recevoir cette erreur lors de la bibliothèque de marshaling ne prend pas en charge une conversion. Pour plus d’informations sur la bibliothèque de marshaling, consultez [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md).

Cet exemple génère l’erreur C4996, car la bibliothèque de marshaling nécessite un contexte à convertir à partir d’un `System::String` à un `const char *`.

```cpp
// C4996_Marshal.cpp
// compile with: /clr
// C4996 expected
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = marshal_as<const char*>( message );
   return 0;
}
```

## <a name="example-user-defined-deprecated-function"></a>Exemple : Défini par l’utilisateur une fonction déconseillée

Vous pouvez utiliser l’attribut déconseillé dans votre propre code pour avertir les appelants lorsque vous n’en avez plus recommandez l’utilisation de certaines fonctions. Dans cet exemple, l’erreur C4996 est généré pour la ligne sur lequel la fonction déconseillée est déclarée et de la ligne sur laquelle la fonction est utilisée.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

__declspec(deprecated) void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
