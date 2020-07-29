---
title: Opérations CString de base
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: fa46e82f19d87c49f652779d0e86e78549935965
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220897"
---
# <a name="basic-cstring-operations"></a>Opérations CString de base

Cette rubrique décrit les opérations [CString](../atl-mfc-shared/reference/cstringt-class.md) de base suivantes :

- [Création d’objets CString à partir de chaînes littérales C standard](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Accès à des caractères individuels dans une CString](#_core_accessing_individual_characters_in_a_cstring)

- [Concaténation de deux objets CString](#_core_concatenating_two_cstring_objects)

- [Comparaison d’objets CString](#_core_comparing_cstring_objects)

- [Conversion d’objets CString](#_core_converting_cstring_objects)

`Class CString`est basé sur la classe du modèle de classe [CStringT](../atl-mfc-shared/reference/cstringt-class.md). `CString`est **`typedef`** de `CStringT` . Plus exactement, `CString` est une **`typedef`** *spécialisation explicite* de `CStringT` , qui est un moyen courant d’utiliser un modèle de classe pour définir une classe. Les classes définies de la même façon sont `CStringA` et `CStringW` .

`CString`, `CStringA` et `CStringW` sont définis dans atlstr. h. `CStringT`est défini dans CStringT. h.

`CString`, `CStringA` et `CStringW` obtiennent chacun un ensemble des méthodes et des opérateurs définis par `CStringT` pour une utilisation avec les données de chaîne qu’ils prennent en charge. Certaines des méthodes dupliquent et, dans certains cas, surpassent les services de chaîne des bibliothèques Runtime C.

Remarque : `CString` est une classe native. Pour une classe de chaîne qui est destinée à être utilisée dans un projet managé C++/CLI, utilisez `System.String` .

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Création d’objets CString à partir de chaînes littérales C standard

Vous pouvez assigner des chaînes littérales de style C à un `CString` tout comme vous pouvez assigner un `CString` objet à un autre.

- Assignez la valeur d’une chaîne littérale C à un `CString` objet.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Assignez la valeur d’un `CString` à un autre `CString` objet.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Le contenu d’un `CString` objet est copié lorsqu’un `CString` objet est affecté à un autre. Par conséquent, les deux chaînes ne partagent pas de référence aux caractères réels qui composent la chaîne. Pour plus d’informations sur l’utilisation d' `CString` objets en tant que valeurs, consultez [sémantique de CString](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Pour écrire votre application afin qu’elle puisse être compilée pour Unicode ou pour ANSI, les chaînes littérales de code à l’aide de la macro _T. Pour plus d’informations, consultez [prise en charge des jeux de caractères Unicode et MBCS](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Accès à des caractères individuels dans une CString

Vous pouvez accéder à des caractères individuels dans un `CString` objet à l’aide des `GetAt` `SetAt` méthodes et. Vous pouvez également utiliser l’opérateur d’élément de tableau ou d’indice ([]) au lieu de `GetAt` pour recevoir des caractères individuels. (Cela ressemble à l’accès aux éléments de tableau par index, comme dans les chaînes de style C standard.) Les valeurs d’index pour les `CString` caractères sont de base zéro.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Concaténation de deux objets CString

Pour concaténer deux `CString` objets, utilisez les opérateurs de concaténation (+ ou + =) comme suit.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Au moins un argument pour les opérateurs de concaténation (+ ou + =) doit être un `CString` objet, mais vous pouvez utiliser une chaîne de caractères constante (par exemple, `"big"` ) ou un **`char`** (par exemple, 'x') pour l’autre argument.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Comparaison d’objets CString

La `Compare` méthode et l’opérateur = = pour `CString` sont équivalents. `Compare`, **Operator = =** et `CompareNoCase` sont compatibles MBCS et Unicode ; ne respecte pas `CompareNoCase` non plus la casse. La `Collate` méthode de `CString` est sensible aux paramètres régionaux et est souvent plus lente que `Compare` . À utiliser `Collate` uniquement lorsque vous devez respecter les règles de tri comme spécifié par les paramètres régionaux actuels.

Le tableau suivant présente les fonctions de comparaison [CString](../atl-mfc-shared/reference/cstringt-class.md) disponibles et leurs fonctions portables Unicode/MBCS équivalentes dans la bibliothèque Runtime C.

|Fonction CString|MBCS, fonction|Fonction Unicode|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

Le `CStringT` modèle de classe définit les opérateurs relationnels (<, \<=, > =, >, = = et ! =), qui sont disponibles pour une utilisation par `CString` . Vous pouvez comparer deux `CStrings` à l’aide de ces opérateurs, comme indiqué dans l’exemple suivant.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>Conversion d’objets CString

Pour plus d’informations sur la conversion d’objets CString en d’autres types chaîne, consultez Guide pratique [pour effectuer une conversion entre différents types de chaînes](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>Utilisation de CString avec wcout

Pour utiliser un CString avec `wcout` , vous devez effectuer un cast explicite de l’objet vers un `const wchar_t*` comme indiqué dans l’exemple suivant :

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Sans le cast, `cs` est traité comme un **`void*`** et `wcout` imprime l’adresse de l’objet. Ce comportement est dû à des interactions subtiles entre la déduction d’argument de modèle et la résolution de surcharge qui sont elles-mêmes correctes et conformes à la norme C++.

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT (classe)](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Spécialisation de modèle](../cpp/template-specialization-cpp.md)<br/>
[Comment : effectuer une conversion entre différents types de chaînes](../text/how-to-convert-between-various-string-types.md)
