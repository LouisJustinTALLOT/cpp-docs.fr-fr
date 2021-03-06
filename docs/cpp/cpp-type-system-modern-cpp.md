---
description: 'En savoir plus sur : système de type C++'
title: Système de type C++
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 1be39124e51fc2e812ce5a2779ce701d727c81e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339577"
---
# <a name="c-type-system"></a>Système de type C++

Le concept de *type* est très important en C++. Chaque variable, argument de fonction et valeur de retour de fonction doit avoir un type pour être compilé. En outre, chaque expression (y compris les valeurs littérales) reçoit implicitement un type du compilateur avant d'être évaluée. Voici quelques exemples de types : **`int`** pour stocker des valeurs intégrales, **`double`** pour stocker des valeurs à virgule flottante (également appelées types de données *scalaires* ) ou la classe de bibliothèque Standard [std :: basic_string](../standard-library/basic-string-class.md) pour stocker du texte. Vous pouvez créer votre propre type en définissant une **`class`** ou une **`struct`** . Le type spécifie la quantité de mémoire qui sera allouée à la variable (ou au résultat de l’expression), les types de valeurs qui peuvent être stockés dans cette variable, la façon dont ces valeurs (en tant que séries de bits) sont interprétées et les opérations qu’il y est possible d’exécuter. Cet article contient une présentation informelle des principales fonctionnalités du système de type C++.

## <a name="terminology"></a>Terminologie

**Variable**: nom symbolique d’une quantité de données afin que le nom puisse être utilisé pour accéder aux données auxquelles il fait référence dans l’étendue du code où il est défini. En C++, la *variable* est généralement utilisée pour faire référence à des instances de types de données scalaires, tandis que les instances d’autres types sont généralement appelées *objets*.

**Objet**: pour des raisons de simplicité et de cohérence, cet article utilise le terme *objet* pour faire référence à toute instance d’une classe ou d’une structure, et lorsqu’il est utilisé dans le sens général, il comprend tous les types, y compris les variables scalaires.

**Type Pod** (Plain Old Data) : cette catégorie informelle de types de données en C++ fait référence aux types qui sont scalaires (consultez la section relative aux types fondamentaux) ou qui sont des *classes Pod*. Une classe POD ne comporte pas de données membres static qui ne sont pas également des POD et ne comporte également aucun constructeur défini par l'utilisateur, aucun destructeur défini par l'utilisateur ou aucun opérateur d'assignation défini par l'utilisateur. En outre, une classe POD n'a aucune fonction virtuelle, aucune classe de base et aucune donnée membre non static privée ou protégée. Les types POD sont souvent utilisés pour l'échange de données externes, par exemple avec un module écrit en langage C (disposant de types POD uniquement).

## <a name="specifying-variable-and-function-types"></a>Spécification des types de variable et de fonction

C++ est un langage *fortement typé* qui est également *typé statiquement*. chaque objet a un type et ce type ne change jamais (à ne pas confondre avec les objets de données statiques). Quand vous déclarez une variable dans votre code, vous devez spécifier explicitement son type ou utiliser le **`auto`** mot clé pour indiquer au compilateur de déduire le type de l’initialiseur. Quand vous déclarez une fonction dans votre code, vous devez spécifier le type de chaque argument et sa valeur de retour, ou **`void`** si aucune valeur n’est retournée par la fonction. L’exception se produit lorsque vous utilisez des modèles de fonction, qui autorisent les arguments de types arbitraires.

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

Contrairement à certains langages, C++ n'a aucun type de base universel dont tous les autres types sont dérivés. Le langage comprend de nombreux *types fondamentaux*, également appelés *types intégrés*. Cela comprend les types numériques tels que **`int`** , **`double`** ,, **`long`** **`bool`** , ainsi que les **`char`** **`wchar_t`** types et pour les caractères ASCII et Unicode, respectivement. La plupart des types fondamentaux intégraux (à l’exception de,, **`bool`** **`double`** et des **`wchar_t`** types connexes) ont tous des **`unsigned`** versions, qui modifient la plage de valeurs que la variable peut stocker. Par exemple, un **`int`** , qui stocke un entier signé 32 bits, peut représenter une valeur comprise entre-2 147 483 648 et 2 147 483 647. **`unsigned int`**, Qui est également stocké comme 32 bits, peut stocker une valeur comprise entre 0 et 4 294 967 295. Le nombre total de valeurs possibles dans chaque cas est identique ; seule la plage est différente.

Les types fondamentaux sont identifiés par le compilateur, qui dispose de règles intégrées régissant les opérations que vous pouvez exécuter sur ces types, ainsi que la façon dont ces types peuvent être convertis en d'autres types fondamentaux. Pour obtenir la liste complète des types intégrés et leurs limites numériques et de taille, consultez [types intégrés](../cpp/fundamental-types-cpp.md).

L’illustration suivante montre les tailles relatives des types intégrés dans l’implémentation de Microsoft C++ :

![Taille en octets des&#45;générées dans les types](../cpp/media/built-intypesizes.png "Taille en octets des&#45;générées dans les types")

Le tableau suivant répertorie les types fondamentaux les plus fréquemment utilisés et leurs tailles dans l’implémentation de Microsoft C++ :

| Type | Taille | Commentaire |
|--|--|--|
| **`int`** | 4 octets | Choix par défaut pour les valeurs intégrales. |
| **`double`** | 8 octets | Choix par défaut pour les valeurs à virgule flottante. |
| **`bool`** | 1 octet | Représente des valeurs qui peuvent être true ou false. |
| **`char`** | 1 octet | À utiliser pour les caractères ASCII dans les chaînes de style C plus anciennes ou les objets std::string qui ne devront jamais être convertis en UNICODE. |
| **`wchar_t`** | 2 octets | Représente les valeurs à caractères « larges » qui peuvent être encodées au format UNICODE (UTF-16 sur Windows, mais peut varier sur les autres systèmes d'exploitation). Type de caractère utilisé dans les chaînes de type `std::wstring`. |
| **`unsigned char`** | 1 octet | C++ n’a aucun type d’octet intégré.  Utilisez **`unsigned char`** pour représenter une valeur d’octet. |
| **`unsigned int`** | 4 octets | Option par défaut pour les bits indicateurs. |
| **`long long`** | 8 octets | Représente des valeurs entières très grandes. |

D’autres implémentations C++ peuvent utiliser des tailles différentes pour certains types numériques. Pour plus d’informations sur les tailles et les relations de taille requises par la norme C++, consultez [types intégrés](fundamental-types-cpp.md).

## <a name="the-void-type"></a>Type void

Le **`void`** type est un type spécial ; vous ne pouvez pas déclarer une variable de type **`void`** , mais vous pouvez déclarer une variable de type `void *` (pointeur vers **`void`** ), ce qui est parfois nécessaire lors de l’allocation de mémoire brute (non typée). Toutefois, les pointeurs vers **`void`** ne sont pas de type sécurisé et, en général, leur utilisation est fortement déconseillée dans le C++ moderne. Dans une déclaration de fonction, une **`void`** valeur de retour signifie que la fonction ne retourne pas de valeur ; il s’agit d’une utilisation courante et acceptable de **`void`** . Si le langage C nécessitait des fonctions qui ont des paramètres nuls pour déclarer **`void`** dans la liste de paramètres, par exemple, `fou(void)` cette pratique est déconseillée dans le C++ moderne et doit être déclarée `fou()` . Pour plus d’informations, consultez [conversions de types et sécurité de type](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>qualificateur de type const

Tout type intégré ou défini par l'utilisateur peut être qualifié par le mot clé const. En outre, les fonctions membres peuvent être **`const`** qualifiées et même **`const`** surchargées. La valeur d’un **`const`** type ne peut pas être modifiée après son initialisation.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

Le **`const`** qualificateur est largement utilisé dans les déclarations de fonction et de variable, et « const correctage » est un concept important en C++; cela signifie essentiellement **`const`** que, au moment de la compilation, les valeurs ne sont pas modifiées par inadvertance. Pour plus d’informations, consultez [`const`](../cpp/const-cpp.md).

Un **`const`** type est différent de sa version non const ; par exemple, **`const int`** est un type distinct de **`int`** . Vous pouvez utiliser l' **`const_cast`** opérateur C++ dans les rares occasions où vous devez supprimer *const-* caractère d’une variable. Pour plus d’informations, consultez [conversions de types et sécurité de type](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Types chaîne

Strictement parlant, le langage C++ n’a aucun type de chaîne intégré ; **`char`** et **`wchar_t`** stockent des caractères uniques. vous devez déclarer un tableau de ces types pour rapprocher une chaîne, en ajoutant une valeur null de fin (par exemple, ASCII `'\0'` ) à l’élément de tableau situé un après le dernier caractère valide (également appelé *chaîne de style C*). Les chaînes de style C exigent beaucoup plus de code pour être écrites ou l'utilisation de fonctions de bibliothèque d'utilitaires de chaînes externes. Mais en C++ moderne, nous disposons des types de bibliothèque standard `std::string` (pour les chaînes de caractères de type 8 bits **`char`** ) ou `std::wstring` (pour les **`wchar_t`** chaînes de caractères de type 16 bits). Ces conteneurs de bibliothèque standard C++ peuvent être considérés comme des types de chaîne natifs, car ils font partie des bibliothèques standard incluses dans tout environnement de génération C++ conforme. Utilisez simplement la directive `#include <string>` pour rendre ces types disponibles dans votre programme. (Si vous utilisez MFC ou ATL, la `CString` classe est également disponible, mais ne fait pas partie de la norme C++.) L’utilisation de tableaux de caractères se terminant par un caractère null (les chaînes de style C mentionnées précédemment) est vivement déconseillée dans le C++ moderne.

## <a name="user-defined-types"></a>Types définis par l'utilisateur

Quand vous définissez un **`class`** , **`struct`** , **`union`** ou **`enum`** , cette construction est utilisée dans le reste de votre code comme s’il s’agissait d’un type fondamental. Il a une taille connue en mémoire, et certaines règles relatives à son utilisation s’appliquent à celui-ci pour la vérification au moment de la compilation et, au moment de l’exécution, pour la durée de vie de votre programme. Les principales différences entre les types intégrés fondamentaux et les types définis par l'utilisateur sont les suivantes :

- Le compilateur n'a pas connaissance de manière intégrée d'un type défini par l'utilisateur. Il apprend le type lorsqu’il rencontre pour la première fois la définition pendant le processus de compilation.

- Vous spécifiez les opérations qui peuvent être exécutées sur votre type et comment il peut être converti en d'autres types, en définissant (via la surcharge) les opérateurs appropriés, comme membres de classe ou comme fonctions non membres. Pour plus d’informations, consultez [surcharge de fonction](function-overloading.md)

## <a name="pointer-types"></a>Types de pointeur

En revenons aux premières versions du langage C, C++ continue à vous permettre de déclarer une variable d’un type pointeur en utilisant le déclarateur spécial **`*`** (astérisque). Un type pointeur stocke l'adresse de l'emplacement dans la mémoire où la valeur réelle des données est stockée. En C++ moderne, ils sont appelés *pointeurs bruts* et sont accessibles dans votre code par le biais d’opérateurs spéciaux **`*`** (astérisque) ou **`->`** (tiret avec supérieur à). C’est ce que l’on appelle le *déréférencement* et celui que vous utilisez varie selon que vous déréférencez un pointeur vers un scalaire ou un pointeur vers un membre d’un objet. L'utilisation des types pointeur a longtemps été l'un des aspects les plus importants et les plus perturbants du développement de programmes en C et C++. Cette section décrit certains faits et pratiques pour vous aider à utiliser des pointeurs bruts si vous le souhaitez, mais en C++ moderne, il n’est plus nécessaire (ou recommandé) d’utiliser des pointeurs bruts pour la propriété de l’objet, en raison de l’évolution du [pointeur intelligent](../cpp/smart-pointers-modern-cpp.md) (abordé plus loin à la fin de cette section). Il est toujours utile et plus sûr d’utiliser des pointeurs bruts pour observer les objets. Toutefois, si vous devez les utiliser pour la propriété des objets, agissez avec précaution et tenez compte de la façon dont les objets détenus sont créés et détruits.

La première chose que vous devez savoir est que la déclaration d'une variable pointeur brut alloue uniquement la mémoire requise pour stocker une adresse de l'emplacement mémoire auquel le pointeur fait référence lorsqu'il est déréférencé. L’allocation de la mémoire pour la valeur de données elle-même (également appelée *magasin* de stockage) n’est pas encore allouée. En d'autres termes, lorsque vous déclarez une variable de pointeur brut, vous créez une variable d'adresse mémoire et pas une variable de données réelle. Déréférencer une variable de pointeur avant de s'assurer qu'elle contient une adresse valide pour un magasin de stockage provoque un comportement indéfini (généralement une erreur irrécupérable) dans votre programme. L'exemple suivant illustre ce type d'erreur :

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

L'exemple de code corrigé utilise la mémoire de la pile locale pour créer le magasin de stockage vers lequel pointe `pNumber`. Nous utilisons un type fondamental pour des raisons de simplicité. En pratique, le magasin de stockage pour les pointeurs sont le plus souvent des types définis par l’utilisateur qui sont alloués dynamiquement dans une zone de mémoire appelée *tas* (ou *magasin libre*) à l’aide d’une **`new`** expression de mot clé (dans la programmation de style c, l’ancienne fonction de la `malloc()` bibliothèque Runtime c a été utilisée). Une fois allouées, ces variables sont généralement appelées objets, surtout si elles sont basées sur une définition de classe. La mémoire allouée avec **`new`** doit être supprimée par une **`delete`** instruction correspondante (ou, si vous avez utilisé la `malloc()` fonction pour l’allouer, la fonction C Runtime `free()` ).

Toutefois, il est facile d’oublier de supprimer un objet alloué dynamiquement, en particulier dans le code complexe, ce qui provoque un bogue de ressource appelé une *fuite de mémoire*. Pour cette raison, l'utilisation des pointeurs bruts est vivement déconseillée dans le C++ moderne. Il est presque toujours préférable d’inclure dans un wrapper un pointeur brut dans un [pointeur intelligent](../cpp/smart-pointers-modern-cpp.md), ce qui libère automatiquement la mémoire lorsque son destructeur est appelé (quand le code sort de l’étendue du pointeur intelligent). en utilisant des pointeurs intelligents, vous éliminez pratiquement toute une classe de bogues dans vos programmes C++. Dans l'exemple suivant, supposez que `MyClass` est un type défini par l'utilisateur qui a une méthode `DoSomeWork();`publique

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

Dans la programmation Win32 classique pour C et C++, la plupart des fonctions utilisent des typedefs et des `#define` macros spécifiques à Windows (définis dans `windef.h` ) pour spécifier les types de paramètres et de valeurs de retour. Ces types de données Windows sont principalement des noms spéciaux (alias) donnés aux types intégrés C/C++. Pour obtenir la liste complète de ces typedefs et définitions de préprocesseur, consultez [types de données Windows](/windows/win32/WinProg/windows-data-types). Certains de ces typedefs, tels que `HRESULT` et `LCID` , sont utiles et descriptifs. D’autres, telles que `INT` , n’ont aucune signification particulière et sont simplement des alias pour les types C++ fondamentaux. D'autres types de données Windows ont des noms qui proviennent de l'époque de la programmation en C et des processeurs 16 bits ; ils n'ont aucune finalité ou signification particulière par rapport au matériel ou aux systèmes d'exploitation modernes. Il existe également des types de données spéciaux associés à la bibliothèque de Windows Runtime, répertoriés en tant que [types de données de base Windows Runtime](/windows/win32/WinRT/base-data-types). En C++ moderne, la règle générale consiste à préférer les types fondamentaux C++ sauf si le type Windows communique une certaine signification supplémentaire sur la manière dont la valeur doit être interprétée.

## <a name="more-information"></a>Informations complémentaires

Pour plus d'informations sur le système de types C++, consultez les rubriques suivantes.

[Types valeur](../cpp/value-types-modern-cpp.md)\
Décrit les *types valeur* et les problèmes liés à leur utilisation.

[Conversions de types et sécurité de type](../cpp/type-conversions-and-type-safety-modern-cpp.md)\
Décrit les problèmes de conversion des types courants et indique comment les éviter.

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
