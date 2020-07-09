---
title: Avertissement du compilateur (niveau 3) C4996
description: Explique pourquoi l’avertissement du compilateur C4996 se produit et décrit la marche à suivre.
ms.date: 11/25/2019
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 98662dc0b5439c1f8857e4f2ad259793a4d03e41
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "79419377"
---
# <a name="compiler-warning-level-3-c4996"></a>Avertissement du compilateur (niveau 3) C4996

Votre code utilise une fonction, un membre de classe, une variable ou un typedef marqué comme *déconseillé*. Les symboles sont déconseillés à l’aide d’un modificateur [__declspec (déconseillé)](../../cpp/deprecated-cpp.md) ou de l’attribut [ \[ \[ déconseillé \] \] ](../../cpp/attributes.md) c++ 14. Le message d’avertissement C4996 réel est spécifié par le `deprecated` modificateur ou l’attribut de la déclaration.

> [!IMPORTANT]
> Cet avertissement est toujours un message délibéré de l’auteur du fichier d’en-tête qui déclare le symbole. N’utilisez pas le symbole déconseillé sans comprendre les conséquences.

## <a name="remarks"></a>Notes

De nombreuses fonctions, fonctions membres, fonctions de modèle et variables globales dans les bibliothèques Visual Studio sont *déconseillées*. Certains, tels que POSIX et les fonctions spécifiques à Microsoft, sont déconseillés, car ils ont maintenant un nom préféré différent. Certaines fonctions de la bibliothèque Runtime C sont dépréciées, car elles ne sont pas sécurisées et ont une variante plus sécurisée. D’autres sont dépréciées, car elles sont obsolètes. Les messages de désapprobation incluent généralement un remplacement suggéré pour la fonction ou la variable globale déconseillée.

## <a name="turn-off-the-warning"></a>Désactiver l’avertissement

Pour résoudre un problème C4996, nous vous recommandons généralement de modifier votre code. Utilisez à la place les variables globales et les fonctions suggérées. Si vous devez utiliser les fonctions ou variables existantes pour des raisons de portabilité, vous pouvez désactiver l’avertissement.

Pour désactiver l’avertissement pour une ligne de code spécifique, utilisez le pragma [Warning](../../preprocessor/warning.md) , `#pragma warning(suppress : 4996)` .

Pour désactiver l’avertissement dans un fichier, utilisez le pragma warning, `#pragma warning(disable : 4996)` .

Pour désactiver globalement l’avertissement dans les générations à partir de la ligne de commande, utilisez l’option de ligne de commande [/wd4996](../../build/reference/compiler-option-warning-level.md) .

Pour désactiver l’avertissement pour l’intégralité d’un projet dans l’IDE de Visual Studio :

1. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet. Pour plus d’informations sur l’utilisation de la boîte de dialogue pages de propriétés, consultez [pages de propriétés](../../build/reference/property-pages-visual-cpp.md).

1. Sélectionnez la page **Propriétés de configuration**  >  **C/C++**  >  **avancé** .

1. Modifiez la propriété **Désactiver les avertissements spécifiques** à ajouter `4996` . Choisissez **OK** pour appliquer vos modifications.

Vous pouvez également utiliser des macros de préprocesseur pour désactiver certaines classes spécifiques d’avertissements de désapprobation utilisés dans les bibliothèques. Ces macros sont décrites ci-dessous.

Pour définir une macro de préprocesseur dans Visual Studio :

1. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet. Pour plus d’informations sur l’utilisation de la boîte de dialogue pages de propriétés, consultez [pages de propriétés](../../build/reference/property-pages-visual-cpp.md).

1. Développez **Propriétés de Configuration > préprocesseur > C/C++**.

1. Dans la propriété **définitions de préprocesseur** , ajoutez le nom de la macro. Choisissez **OK** pour enregistrer, puis régénérez votre projet.

Pour définir une macro uniquement dans des fichiers sources spécifiques, ajoutez une ligne telle que `#define EXAMPLE_MACRO_NAME` avant toute ligne qui comprend un fichier d’en-tête.

Voici quelques-unes des sources courantes d’avertissements et d’erreurs C4996 :

## <a name="posix-function-names"></a>Noms des fonctions POSIX

**Le nom POSIX pour cet élément est déconseillé. Au lieu de cela, utilisez le nom conforme ISO C et C++ :** *New-Name*. **Pour plus d’informations, consultez l’aide en ligne.**

Microsoft a renommé des fonctions POSIX et de bibliothèque spécifiques à Microsoft dans le CRT pour se conformer aux contraintes C99 et C++ 03 sur les noms réservés et globaux définis par l’implémentation. *Seuls les noms sont déconseillés, pas les fonctions elles-mêmes*. Dans la plupart des cas, un trait de soulignement de début a été ajouté au nom de la fonction pour créer un nom conforme. Le compilateur émet un avertissement de désapprobation pour le nom de la fonction d’origine et suggère le nom préféré.

Pour résoudre ce problème, nous vous recommandons généralement de modifier votre code pour utiliser les noms de fonctions suggérés à la place. Toutefois, les noms mis à jour sont spécifiques à Microsoft. Si vous devez utiliser les noms de fonctions existants pour des raisons de portabilité, vous pouvez désactiver ces avertissements. Les fonctions sont toujours disponibles dans la bibliothèque sous leurs noms d’origine.

Pour désactiver les avertissements de désapprobation pour ces fonctions, définissez la macro de préprocesseur ** \_ \_ NONSTDC \_ aucun \_ Avertissement**. Vous pouvez définir cette macro sur la ligne de commande en incluant l’option `/D_CRT_NONSTDC_NO_WARNINGS` .

## <a name="unsafe-crt-library-functions"></a>Fonctions de la bibliothèque CRT non sécurisée

**Cette fonction ou variable peut être non sécurisée. Envisagez plutôt d’utiliser** *Safe-version* **. Pour désactiver la désapprobation, utilisez \_ CRT \_ Secure \_ no \_ warnings.  Pour plus d’informations, consultez l’aide en ligne.**

Microsoft a déconseillé certaines fonctions et fonctionnalités globales de la bibliothèque CRT et C++ standard, car des versions plus sécurisées sont disponibles. La plupart des fonctions déconseillées autorisent un accès en lecture ou en écriture non contrôlé aux mémoires tampons. Leur utilisation abusive peut entraîner de sérieux problèmes de sécurité. Le compilateur émet un avertissement indiquant que ces fonctions sont déconseillées et suggère la fonction préférée.

Pour résoudre ce problème, nous vous recommandons d’utiliser à la place la fonction ou la variable *Safe-version* . Parfois, vous ne pouvez pas, à des fins de portabilité ou de compatibilité descendante. Vérifiez avec soin qu’il n’est pas possible de remplacer ou de délire une mémoire tampon dans votre code. Ensuite, vous pouvez désactiver l’avertissement.

Pour désactiver les avertissements de désapprobation pour ces fonctions dans la bibliothèque CRT, définissez ** \_ CRT \_ sécurisé \_ sans \_ avertissements**.

Pour désactiver les avertissements concernant les variables globales déconseillées, définissez ** \_ CRT \_ ne pas sécuriser les \_ \_ avertissements \_ globaux**.

Pour plus d’informations sur ces fonctions et globales déconseillées, consultez [fonctionnalités de sécurité dans les bibliothèques CRT](../../c-runtime-library/security-features-in-the-crt.md) et [Safe : bibliothèque standard C++](../../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="unsafe-standard-library-functions"></a>Fonctions de la bibliothèque standard non sécurisée

__'std ::__*function_name*__:: \_ \_ iterator itérateurs :: \_ Deprecated’appel à std ::__*function_name* **avec des paramètres qui peuvent être non sécurisés : cet appel s’appuie sur l’appelant pour vérifier que les valeurs passées sont correctes. Pour désactiver cet avertissement, utilisez-D \_ SCL \_ sécurisé \_ aucun \_ avertissement. Consultez la documentation sur l’utilisation d’Visual C++ itérateurs vérifiés**

Cet avertissement apparaît dans les versions Debug, car certaines fonctions de modèle de la bibliothèque C++ standard ne vérifient pas que les paramètres sont corrects. C’est souvent parce qu’il n’y a pas assez d’informations disponibles pour la fonction pour vérifier les limites du conteneur. Ou, car les itérateurs peuvent être utilisés de manière incorrecte avec la fonction. Cet avertissement vous aide à identifier ces fonctions, car elles peuvent constituer une source de failles de sécurité importantes dans votre programme. Pour plus d’informations, consultez [itérateurs vérifiés](../../standard-library/checked-iterators.md).

Par exemple, cet avertissement s’affiche en mode débogage si vous transmettez un pointeur d’élément à `std::copy` , au lieu d’un tableau ordinaire. Pour résoudre ce problème, utilisez un tableau déclaré de manière appropriée, afin que la bibliothèque puisse vérifier les étendues du tableau et effectuer la vérification des limites.

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

Plusieurs algorithmes de bibliothèque standard ont été mis à jour pour avoir des versions « double plage » en C++ 14. Si vous utilisez les versions à deux plages, la deuxième plage fournit la vérification des limites nécessaires :

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

Cet exemple illustre plusieurs autres façons dont la bibliothèque standard peut être utilisée pour vérifier l’utilisation de l’itérateur, et quand une utilisation non vérifiée peut être dangereuse :

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

Si vous avez vérifié que votre code ne peut pas avoir une erreur de dépassement de mémoire tampon, vous pouvez désactiver cet avertissement. Pour désactiver les avertissements pour ces fonctions, définissez la ** \_ \_ sécurité SCL \_ sans \_ avertissements**.

## <a name="checked-iterators-enabled"></a>Itérateurs vérifiés activés

L’C4996 peut également se produire si vous n’utilisez pas d’itérateur vérifié lorsque `_ITERATOR_DEBUG_LEVEL` est défini sur 1 ou 2. Elle est définie sur 2 par défaut pour les builds en mode débogage et sur 0 pour les versions commerciales. Pour plus d’informations, consultez [itérateurs vérifiés](../../standard-library/checked-iterators.md).

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

## <a name="unsafe-mfc-or-atl-code"></a>Code MFC ou ATL non sécurisé

L’C4996 peut se produire si vous utilisez des fonctions MFC ou ATL qui ont été dépréciées pour des raisons de sécurité.

Pour résoudre ce problème, nous vous recommandons vivement de modifier votre code pour utiliser des fonctions mises à jour à la place.

Pour plus d’informations sur la façon de supprimer ces avertissements, consultez [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

## <a name="obsolete-crt-functions-and-variables"></a>Variables et fonctions CRT obsolètes

**Cette fonction ou cette variable a été remplacée par une version plus récente du système d’exploitation ou de la bibliothèque. Envisagez plutôt d’utiliser** *new_item* **. Pour plus d’informations, consultez l’aide en ligne.**

Certaines fonctions de la bibliothèque et certaines variables globales sont déconseillées, car elles sont obsolètes. Ces fonctions et variables sont susceptibles d’être supprimées dans une version future de la bibliothèque. Le compilateur émet un avertissement indiquant que ces éléments sont déconseillées et suggère l’alternative préférée.

Pour résoudre ce problème, nous vous recommandons de modifier votre code pour utiliser la fonction ou la variable suggérée.

Pour désactiver les avertissements de désapprobation pour ces éléments, définissez ** \_ CRT \_ obsolète \_ aucun \_ Avertissement**. Pour plus d’informations, consultez la documentation pour la fonction ou la variable déconseillée.

## <a name="marshaling-errors-in-clr-code"></a>Marshaling des erreurs dans le code CLR

L’C4996 peut également se produire lorsque vous utilisez la bibliothèque de marshaling CLR. Dans ce cas, C4996 est une erreur, et non un avertissement. L’erreur se produit lorsque vous utilisez [marshal_as](../../dotnet/marshal-as.md) pour effectuer une conversion entre deux types de données qui requièrent une [classe marshal_context](../../dotnet/marshal-context-class.md). Vous pouvez également recevoir cette erreur lorsque la bibliothèque de marshaling ne prend pas en charge une conversion. Pour plus d’informations sur la bibliothèque de marshaling, consultez [vue d’ensemble du marshaling en C++](../../dotnet/overview-of-marshaling-in-cpp.md).

Cet exemple génère l’C4996, car la bibliothèque de marshaling requiert un contexte pour effectuer la conversion d’un `System::String` en `const char *` .

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

## <a name="example-user-defined-deprecated-function"></a>Exemple : fonction déconseillée définie par l’utilisateur

Vous pouvez utiliser l’attribut deprecated dans votre propre code pour avertir les appelants lorsque vous n’êtes plus recommandé d’utiliser certaines fonctions. Dans cet exemple, l’C4996 est généré à deux emplacements : un pour la ligne sur laquelle la fonction déconseillée est déclarée, et une pour la ligne où la fonction est utilisée.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
