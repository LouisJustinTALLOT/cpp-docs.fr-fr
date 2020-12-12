---
description: 'En savoir plus sur : les opérations CString relatives aux chaînes de style C'
title: Opérations CString relatives aux chaînes de style C
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- MFC [C++], string handling class
- string conversion [C++], C-style strings
- strings [C++], string operations
- standard run-time library string functions
- null values, Null-terminated string conversion
- string functions
- strings [C++], in C
- string arguments
- C-style strings
- strings [C++], class CString
- casting CString objects
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
ms.openlocfilehash: a9f34ad1a7e38197b4714b073bdb47db046a394c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167134"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>Opérations CString relatives aux chaînes de style C

Un objet [CString](../atl-mfc-shared/using-cstring.md) contient des données de chaîne de caractères. `CString` hérite de l’ensemble des [méthodes et opérateurs](../atl-mfc-shared/reference/cstringt-class.md) définis dans le modèle de classe [CStringT](../atl-mfc-shared/reference/cstringt-class.md) pour travailler avec des données de type chaîne. ( `CString` est un **`typedef`** qui spécialise `CStringT` l’utilisation du type de données caractères `CString` pris en charge par.)

`CString` ne stocke pas les données caractères en interne sous la forme d'une chaîne de style C, terminée par un caractère null. Au lieu de cela, `CString` gère la longueur des données caractères pour pouvoir considérer de façon mieux sécurisée les données et l'espace qu'elles requièrent.

`CString` accepte les chaînes de style C et fournit des moyens d'accéder aux données caractères comme s'il s'agissait d'une chaîne de style C. Cette rubrique contient les sections suivantes, qui expliquent comment utiliser un objet `CString` comme s'il s'agissait d'une chaîne de style C, terminée par le caractère null.

- [Conversion en chaînes de style C terminées par un caractère null](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [Utilisation des fonctions de chaîne de la bibliothèque Runtime standard](#_core_working_with_standard_run.2d.time_library_string_functions)

- [Modification directe du contenu de CString](#_core_modifying_cstring_contents_directly)

- [Utilisation d’objets CString avec des fonctions d’arguments variables](#_core_using_cstring_objects_with_variable_argument_functions)

- [Spécification de paramètres formels CString](#_core_specifying_cstring_formal_parameters)

## <a name="using-cstring-as-a-c-style-null-terminated-string"></a><a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> Utilisation de CString comme chaîne de Null-Terminated de style C

Pour utiliser un `CString` objet comme chaîne de style C, effectuez un cast de l’objet en LPCTSTR. Dans l'exemple suivant, `CString` retourne un pointeur vers une chaîne terminée par le caractère null de style C en lecture seule. La fonction `strcpy` place une copie de la chaîne de style C dans la variable `myString`.

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

Vous pouvez utiliser des méthodes de `CString`, par exemple `SetAt`, pour modifier des caractères individuels dans l'objet string. Toutefois, le pointeur LPCTSTR est temporaire et devient non valide quand une modification est apportée à `CString` . L'objet `CString` peut aussi passer en dehors de l'étendue et être automatiquement supprimé. Nous vous recommandons d’obtenir un nouveau pointeur LPCTSTR d’un `CString` objet chaque fois que vous en utilisez un.

Vous pouvez parfois avoir besoin d'une copie des données de `CString` pour les modifier directement. Utilisez la fonction mieux sécurisée `strcpy_s` (ou la fonction portable Unicode/MBCS `_tcscpy_s`) pour copier l'objet `CString` dans une mémoire tampon distincte. C'est ici que les caractères peuvent être modifiés en toute sécurité, comme le montre l'exemple suivant.

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> Le troisième argument de `strcpy_s` (ou de l’ordinateur portable Unicode/MBCS `_tcscpy_s` ) est de type `const wchar_t*` (Unicode) ou `const char*` (ANSI). L’exemple ci-dessus passe un objet `CString` pour cet argument. Le compilateur C++ applique automatiquement la fonction de conversion définie pour la classe `CString` qui convertit un objet `CString` en un pointeur `LPCTSTR`. La possibilité de définir des opérations de cast d’un type vers un autre type est une des fonctionnalités les plus pratiques de C++.

## <a name="working-with-standard-run-time-library-string-functions"></a><a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> Utilisation des fonctions de chaîne de la bibliothèque de Run-Time standard

Vous devez normalement trouver une méthode de `CString` pour effectuer n'importe quelle opération sur une chaîne, pour laquelle vous pouvez envisager d'utiliser les fonctions de la bibliothèque Runtime C standard, comme `strcmp` (ou la fonction portable Unicode/MBCS `_tcscmp`).

Si vous devez utiliser les fonctions de chaîne Runtime C, vous pouvez utiliser les techniques décrites dans _core_using_cstring_as_a_c. 2d. Style_Null. 2d. terminated_string. Vous pouvez copier l'objet `CString` vers une mémoire tampon de chaîne de style C équivalente, effectuer vos opérations sur la mémoire tampon, puis réaffecter la chaîne de style C résultante à un objet `CString`.

## <a name="modifying-cstring-contents-directly"></a><a name="_core_modifying_cstring_contents_directly"></a> Modification directe du contenu de CString

Dans la plupart des cas, vous devez utiliser des fonctions de membre `CString` pour modifier le contenu d'un objet `CString` ou pour convertir l'objet `CString` en une chaîne de caractères de style C.

Il existe cependant des situations où il est préférable de modifier directement le contenu de `CString`, par exemple quand vous travaillez avec des fonctions du système d'exploitation qui nécessitent une mémoire tampon de caractères.

Les méthodes `GetBuffer` et `ReleaseBuffer` offrent un accès à la mémoire tampon de caractères interne d'un objet `CString` et vous permettent de le modifier directement. Les étapes suivantes montrent comment utiliser ces fonctions à cette fin.

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Pour utiliser GetBuffer et ReleaseBuffer pour accéder à la mémoire tampon de caractères interne d’un objet CString

1. Appelez `GetBuffer` pour un objet `CString` et spécifiez la longueur de la mémoire tampon dont vous avez besoin.

1. Utilisez le pointeur retourné par `GetBuffer` pour écrire des caractères directement dans l'objet `CString`.

1. Appelez `ReleaseBuffer` pour l'objet `CString` pour mettre à jour toutes les informations d'état internes de `CString`, par exemple la longueur de la chaîne. Après avoir modifié directement le contenu d'un objet `CString`, vous devez appeler `ReleaseBuffer` avant d'appeler toute autre fonction de membre de `CString`.

## <a name="using-cstring-objects-with-variable-argument-functions"></a><a name="_core_using_cstring_objects_with_variable_argument_functions"></a> Utilisation d’objets CString avec des fonctions d’arguments variables

Certaines fonctions C prennent un nombre variable d’arguments. `printf_s` en est un bon exemple. En raison de la façon dont ce type de fonction est déclaré, le compilateur ne peut pas être sûr du type des arguments et ne peut pas déterminer quelle opération de conversion effectuer sur chacun des arguments. Il est donc essentiel d’utiliser un cast de type explicite quand vous passez un objet `CString` à une fonction qui prend un nombre variable d’arguments.

Pour utiliser un `CString` objet dans une fonction d’argument de variable, effectuez explicitement un cast `CString` de en une chaîne LPCTSTR, comme indiqué dans l’exemple suivant.

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

## <a name="specifying-cstring-formal-parameters"></a><a name="_core_specifying_cstring_formal_parameters"></a> Spécification de paramètres formels CString

Pour la plupart des fonctions qui ont besoin d’un argument de chaîne, il est préférable de spécifier le paramètre formel dans le prototype de fonction en tant que **`const`** pointeur vers un caractère ( `LPCTSTR` ) au lieu d’un `CString` . Quand un paramètre formel est spécifié en tant que **`const`** pointeur vers un caractère, vous pouvez passer un pointeur vers un tableau TCHAR, une chaîne littérale [ `"hi there"` ] ou un `CString` objet. L' `CString` objet sera automatiquement converti en LPCTSTR. Chaque fois que vous pouvez utiliser un LPCTSTR, vous pouvez également utiliser un `CString` objet.

Vous pouvez également spécifier un paramètre formel sous la forme d’une référence de chaîne constante (c’est-à-dire `const CString&` ) si l’argument ne sera pas modifié. Supprimez le **`const`** modificateur si la chaîne est modifiée par la fonction. Si vous voulez une valeur null par défaut, initialisez-la avec la chaîne null [`""`], comme ci-dessous :

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

Pour les résultats de la plupart des fonctions, vous pouvez simplement retourner un objet `CString` par valeur.

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Réussite de l’argument CString](../atl-mfc-shared/cstring-argument-passing.md)
