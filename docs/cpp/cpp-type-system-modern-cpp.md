---
title: Système de type C++ (Modern C++)
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: b947bd6955a80e051d1dab81061b4b2bf2ab19c8
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "69498630"
---
# <a name="c-type-system-modern-c"></a>Système de type C++ (Modern C++)

Le concept de *type* est très important dans C++. Chaque variable, argument de fonction et valeur de retour de fonction doit avoir un type pour être compilé. En outre, chaque expression (y compris les valeurs littérales) reçoit implicitement un type du compilateur avant d'être évaluée. Parmi les exemples de types, citons **int** pour stocker des valeurs intégrales, **double** pour stocker des valeurs à virgule flottante (également appelées types de données *scalaires* ) ou la classe de bibliothèque standard [std :: basic_string](../standard-library/basic-string-class.md) pour stocker du texte. Vous pouvez créer votre propre type en définissant une **classe** ou un **struct**. Le type spécifie la quantité de mémoire qui sera allouée à la variable (ou au résultat de l’expression), les types de valeurs qui peuvent être stockés dans cette variable, la façon dont ces valeurs (en tant que séries de bits) sont interprétées et les opérations qu’il y est possible d’exécuter. Cet article contient une présentation informelle des principales fonctionnalités du système de type C++.

## <a name="terminology"></a>Terminologie

**Variable**: nom symbolique d’une quantité de données afin que le nom puisse être utilisé pour accéder aux données auxquelles il fait référence dans l’étendue du code où il est défini. Dans C++, la *variable* est généralement utilisée pour faire référence à des instances de types de données scalaires, tandis que les instances d’autres types sont généralement appelées *objets*.

**Objet**: pour des raisons de simplicité et de cohérence, cet article utilise le terme *objet* pour faire référence à toute instance d’une classe ou d’une structure, et lorsqu’il est utilisé dans le sens général, il comprend tous les types, y compris les variables scalaires.

**Type Pod** (Plain Old Data) : cette catégorie informelle de types de C++ données dans fait référence à des types qui sont scalaires (consultez la section types fondamentaux) ou des *classes Pod*. Une classe POD ne comporte pas de données membres static qui ne sont pas également des POD et ne comporte également aucun constructeur défini par l'utilisateur, aucun destructeur défini par l'utilisateur ou aucun opérateur d'assignation défini par l'utilisateur. En outre, une classe POD n'a aucune fonction virtuelle, aucune classe de base et aucune donnée membre non static privée ou protégée. Les types POD sont souvent utilisés pour l'échange de données externes, par exemple avec un module écrit en langage C (disposant de types POD uniquement).

## <a name="specifying-variable-and-function-types"></a>Spécification des types de variable et de fonction

C++est un langage *fortement typé* et il est également *typé statiquement*; chaque objet a un type et ce type ne change jamais (à ne pas confondre avec les objets de données statiques).
**Quand vous déclarez une variable** dans votre code, vous devez spécifier explicitement son type ou utiliser le mot clé **auto** pour indiquer au compilateur de déduire le type à partir de l’initialiseur.
**Quand vous déclarez une fonction** dans votre code, vous devez spécifier le type de chaque argument et sa valeur de retour, ou **void** si aucune valeur n’est retournée par la fonction. L’exception se produit lorsque vous utilisez des modèles de fonction, qui autorisent les arguments de types arbitraires.

Après avoir commencé par déclarer une variable, vous ne pouvez pas modifier son type à un stade ultérieur. Toutefois, vous pouvez copier la valeur de la variable ou la valeur de retour d'une fonction dans une autre variable d'un type différent. Ces opérations sont appelées *conversions de type*, qui sont parfois nécessaires mais sont également des sources potentielles de perte de données ou d’inexactitude.

Lorsque vous déclarez une variable de type POD, nous vous recommandons fortement de l'initialiser, ce qui permet de lui attribuer une valeur initiale. Tant que vous n'avez pas initialisé une variable, elle a la valeur « garbage » qui se compose des bits, quels qu'ils soient, présents précédemment dans cet emplacement mémoire. Il s'agit d'un aspect important de C++ à ne pas oublier, surtout si vous venez d'un autre langage qui gère automatiquement l'initialisation. Lorsque vous déclarez une variable de type de classe non POD, le constructeur traite l'initialisation.

L'exemple suivant présente des déclarations de variable simples avec quelques descriptions. L'exemple montre également comment le compilateur utilise les informations de type pour autoriser ou interdire certaines opérations ultérieures sur la variable.

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an intializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>Types fondamentaux (intégrés)

Contrairement à certains langages, C++ n'a aucun type de base universel dont tous les autres types sont dérivés. Le langage comprend de nombreux *types fondamentaux*, également appelés *types intégrés*. Cela comprend les types numériques tels que **int**, **double**, **long**, **bool**, ainsi que les types **char** et **wchar_t** pour les caractères ASCII et Unicode, respectivement. La plupart des types fondamentaux (à l’exception de **bool**, **double**, **wchar_t** et des types connexes) ont tous des versions non signées, qui modifient la plage de valeurs que la variable peut stocker. Par exemple, un **int**, qui stocke un entier signé 32 bits, peut représenter une valeur comprise entre-2 147 483 648 et 2 147 483 647. Un **entier non signé**, qui est également stocké comme 32 bits, peut stocker une valeur comprise entre 0 et 4 294 967 295. Le nombre total de valeurs possibles dans chaque cas est identique ; seule la plage est différente.

Les types fondamentaux sont identifiés par le compilateur, qui dispose de règles intégrées régissant les opérations que vous pouvez exécuter sur ces types, ainsi que la façon dont ces types peuvent être convertis en d'autres types fondamentaux. Pour obtenir la liste complète des types intégrés et leurs limites numériques et de taille, consultez [types fondamentaux](../cpp/fundamental-types-cpp.md).

L'illustration suivante montre les tailles relatives des types intégrés :

![Taille en octets des types&#45;intégrés](../cpp/media/built-intypesizes.png "Taille en octets des types&#45;intégrés")

Le tableau suivant répertorie les types fondamentaux les plus souvent utilisés :

|Tapez|Size|Commentaire|
|----------|----------|-------------|
|int|4 octets|Choix par défaut pour les valeurs intégrales.|
|double|8 octets|Choix par défaut pour les valeurs à virgule flottante.|
|bool|1 octet|Représente des valeurs qui peuvent être true ou false.|
|char|1 octet|À utiliser pour les caractères ASCII dans les chaînes de style C plus anciennes ou les objets std::string qui ne devront jamais être convertis en UNICODE.|
|wchar_t|2 octets|Représente les valeurs à caractères « larges » qui peuvent être encodées au format UNICODE (UTF-16 sur Windows, mais peut varier sur les autres systèmes d'exploitation). Type de caractère utilisé dans les chaînes de type `std::wstring`.|
|unsigned&nbsp;char|1 octet|C++ n'a aucun type `byte` intégré.  Utilisez le caractère non signé pour représenter une valeur d'octet.|
|unsigned int|4 octets|Option par défaut pour les bits indicateurs.|
|long long|8 octets|Représente des valeurs entières très grandes.|

## <a name="the-void-type"></a>Type void

Le type **void** est un type spécial ; vous ne pouvez pas déclarer une variable de type **void**, mais vous pouvez déclarer une variable de type __void \*__ (pointeur vers **void**), ce qui est parfois nécessaire lors de l’allocation de mémoire brute (non typée). Toutefois, les pointeurs vers **void** ne sont pas de type sécurisé et, en général, leur utilisation est vivement déconseillée dans moderne C++. Dans une déclaration de fonction, une valeur de retour **void** signifie que la fonction ne retourne pas de valeur ; Il s’agit d’une utilisation courante et acceptable de **void**. Si le langage C nécessitait des fonctions qui ont des paramètres nuls pour déclarer **void** dans la liste de paramètres, par exemple, `fou(void)`, cette pratique est déconseillée dans moderne C++ et doit être déclarée `fou()`. Pour plus d’informations, consultez [conversions de types et sécurité de type](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>qualificateur de type const

Tout type intégré ou défini par l'utilisateur peut être qualifié par le mot clé const. En outre, les fonctions membres peuvent être qualifiées **const**et même **const**-Overloaded. La valeur d’un type **const** ne peut pas être modifiée une fois qu’elle a été initialisée.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

Le qualificateur **const** est largement utilisé dans les déclarations de fonction et de variable, et « const correctage » est un concept C++important dans ; Cela signifie essentiellement qu’il faut utiliser **const** pour garantir, au moment de la compilation, que les valeurs ne sont pas modifiées par inadvertance. Pour plus d’informations, consultez [const](../cpp/const-cpp.md).

Un type **const** est différent de sa version non const ; par exemple, **const int** est un type distinct de **int**. Vous pouvez utiliser l' C++ opérateur **const_cast** dans les rares occasions où vous devez supprimer *const-* caractère d’une variable. Pour plus d’informations, consultez [conversions de types et sécurité de type](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Types chaîne

Strictement parlant, le C++ langage n’a aucun type de chaîne intégré ; **char** et **wchar_t** stockent des caractères uniques. vous devez déclarer un tableau de ces types pour rapprocher une chaîne, en ajoutant une valeur null de fin (par exemple, ASCII `'\0'`) à l’élément de tableau situé un après le dernier caractère valide (également appelé  *Chaîne de style C*). Les chaînes de style C exigent beaucoup plus de code pour être écrites ou l'utilisation de fonctions de bibliothèque d'utilitaires de chaînes externes. Mais dans moderne C++, nous disposons des types de bibliothèque standard `std::string` (pour les chaînes de caractères de type **char**8 bits) ou `std::wstring` (pour les chaînes de caractères de type **wchar_t**16 bits). Ces C++ conteneurs de bibliothèque standard peuvent être considérés comme des types de chaîne natifs, car ils font partie des bibliothèques standard incluses dans tout C++ environnement de génération conforme. Utilisez simplement la directive `#include <string>` pour rendre ces types disponibles dans votre programme. (Si vous utilisez MFC ou ATL, la classe CString est également disponible, mais ne fait pas partie de la C++ norme.) L’utilisation de tableaux de caractères se terminant par un caractère null (les chaînes de style C mentionnées précédemment) est vivement déconseillée dans moderne C++.

## <a name="user-defined-types"></a>Types définis par l'utilisateur

Lorsque vous définissez une **classe**, une **structure**, une **Union**ou une **énumération**, cette construction est utilisée dans le reste de votre code comme s’il s’agissait d’un type fondamental. Il a une taille connue en mémoire, et certaines règles relatives à son utilisation s’appliquent à celui-ci pour la vérification au moment de la compilation et, au moment de l’exécution, pour la durée de vie de votre programme. Les principales différences entre les types intégrés fondamentaux et les types définis par l'utilisateur sont les suivantes :

- Le compilateur n'a pas connaissance de manière intégrée d'un type défini par l'utilisateur. Il apprend le type lorsqu’il rencontre pour la première fois la définition pendant le processus de compilation.

- Vous spécifiez les opérations qui peuvent être exécutées sur votre type et comment il peut être converti en d'autres types, en définissant (via la surcharge) les opérateurs appropriés, comme membres de classe ou comme fonctions non membres. Pour plus d’informations, consultez [surcharge de fonction](function-overloading.md)

## <a name="pointer-types"></a>Types de pointeur

Comme dans les toutes premières versions du langage C, C++ continue à vous permettre de déclarer une variable d'un type pointeur en utilisant le déclarateur spécial `*` (astérisque). Un type pointeur stocke l'adresse de l'emplacement dans la mémoire où la valeur réelle des données est stockée. Dans moderne C++, ils sont appelés *pointeurs bruts*, et sont accessibles dans votre code par le biais d’opérateurs spéciaux `*` (astérisque) ou `->` (tiret avec supérieur à). C’est ce que l’on appelle le *déréférencement*et celui que vous utilisez varie selon que vous déréférencez un pointeur vers un scalaire ou un pointeur vers un membre d’un objet. L'utilisation des types pointeur a longtemps été l'un des aspects les plus importants et les plus perturbants du développement de programmes en C et C++. Cette section décrit quelques faits et pratiques pour vous aider à utiliser les pointeurs bruts si vous le souhaitez, mais C++ dans moderne, il n’est plus nécessaire (ou recommandé) d’utiliser des pointeurs bruts pour la propriété de l’objet, en raison de l’évolution du [pointeur intelligent](../cpp/smart-pointers-modern-cpp.md) (abordé plus loin). à la fin de cette section). Il est toujours utile et plus sûr d’utiliser des pointeurs bruts pour observer les objets. Toutefois, si vous devez les utiliser pour la propriété des objets, agissez avec précaution et tenez compte de la façon dont les objets détenus sont créés et détruits.

La première chose que vous devez savoir est que la déclaration d'une variable pointeur brut alloue uniquement la mémoire requise pour stocker une adresse de l'emplacement mémoire auquel le pointeur fait référence lorsqu'il est déréférencé. L’allocation de la mémoire pour la valeur de données elle-même (également appelée *magasin*de stockage) n’est pas encore allouée. En d'autres termes, lorsque vous déclarez une variable de pointeur brut, vous créez une variable d'adresse mémoire et pas une variable de données réelle. Déréférencer une variable de pointeur avant de s'assurer qu'elle contient une adresse valide pour un magasin de stockage provoque un comportement indéfini (généralement une erreur irrécupérable) dans votre programme. L'exemple suivant illustre ce type d'erreur :

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

L'exemple déréférence un type pointeur sans avoir de mémoire allouée pour stocker les données entières réelles, ni d'adresse mémoire valide assignée. Le code suivant corrige les erreurs suivantes :

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

L'exemple de code corrigé utilise la mémoire de la pile locale pour créer le magasin de stockage vers lequel pointe `pNumber`. Nous utilisons un type fondamental pour des raisons de simplicité. En pratique, le magasin de stockage pour les pointeurs sont le plus souvent des types définis par l’utilisateur qui sont alloués dynamiquement dans une zone de mémoire appelée *tas* (ou *magasin libre*) à l’aide d’une **nouvelle** expression de mot clé (dans la programmation de style C, l’ancienne @no_ la fonction de la bibliothèque Runtime C _t_3 a été utilisée). Une fois allouées, ces variables sont généralement appelées objets, surtout si elles sont basées sur une définition de classe. La mémoire allouée avec **New** doit être supprimée par une instruction **Delete** correspondante (ou, si vous avez utilisé la fonction `malloc()` pour l’allouer, la fonction C Runtime `free()`).

Toutefois, il est facile d’oublier de supprimer un objet alloué dynamiquement, en particulier dans le code complexe, ce qui provoque un bogue de ressource appelé une *fuite de mémoire*. Pour cette raison, l'utilisation des pointeurs bruts est vivement déconseillée dans le C++ moderne. Il est presque toujours préférable d’inclure dans un wrapper un pointeur brut dans un [pointeur intelligent](../cpp/smart-pointers-modern-cpp.md), ce qui libère automatiquement la mémoire lorsque son destructeur est appelé (quand le code sort de l’étendue du pointeur intelligent). en utilisant des pointeurs intelligents, vous éliminez pratiquement toute une classe de C++ bogues dans vos programmes. Dans l'exemple suivant, supposez que `MyClass` est un type défini par l'utilisateur qui a une méthode `DoSomeWork();`publique

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

Pour plus d’informations sur les pointeurs intelligents, consultez [pointeurs intelligents](../cpp/smart-pointers-modern-cpp.md).

Pour plus d’informations sur les conversions de pointeur, consultez [conversions de types et sécurité de type](../cpp/type-conversions-and-type-safety-modern-cpp.md).

Pour plus d’informations sur les pointeurs en général, consultez [pointeurs](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Types de données Windows

Dans la programmation Win32 classique pour C et C++, la plupart des fonctions utilisent des typedefs spécifiques de Windows et des macros #define (définies dans `windef.h`) pour spécifier les types des paramètres et valeurs de retour. Ces types de données Windows sont principalement des noms spéciaux (alias) donnés aux types CC++ /intégrés. Pour obtenir la liste complète de ces typedefs et définitions de préprocesseur, consultez [types de données Windows](/windows/win32/WinProg/windows-data-types). Certains de ces typedefs, par exemple HRESULT et LCID, sont utiles et descriptifs. D'autres, par exemple INT, n'ont aucune signification particulière et sont simplement des alias pour les types C++ fondamentaux. D'autres types de données Windows ont des noms qui proviennent de l'époque de la programmation en C et des processeurs 16 bits ; ils n'ont aucune finalité ou signification particulière par rapport au matériel ou aux systèmes d'exploitation modernes. Il existe également des types de données spéciaux associés à la bibliothèque de Windows Runtime, répertoriés en tant que [types de données de base Windows Runtime](/windows/win32/WinRT/base-data-types). En C++ moderne, la règle générale consiste à préférer les types fondamentaux C++ sauf si le type Windows communique une certaine signification supplémentaire sur la manière dont la valeur doit être interprétée.

## <a name="more-information"></a>Informations complémentaires

Pour plus d'informations sur le système de types C++, consultez les rubriques suivantes.

|||
|-|-|
|[Types valeur](../cpp/value-types-modern-cpp.md)|Décrit les *types valeur* et les problèmes liés à leur utilisation.|
|[Conversions de types et sécurité de type](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Décrit les problèmes de conversion des types courants et indique comment les éviter.|

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++ (C++ moderne)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
