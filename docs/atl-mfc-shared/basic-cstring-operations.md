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
ms.openlocfilehash: 68947dc37e5398ac7caa4754e9af40223cec7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317959"
---
# <a name="basic-cstring-operations"></a>Opérations CString de base

Ce sujet explique les opérations [CString](../atl-mfc-shared/reference/cstringt-class.md) de base suivantes :

- [Création d’objets CString à partir de cordes littérales C standard](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Accès à des personnages individuels dans un CString](#_core_accessing_individual_characters_in_a_cstring)

- [Concatenating deux objets CString](#_core_concatenating_two_cstring_objects)

- [Comparaison d’objets CString](#_core_comparing_cstring_objects)

- [Convertir les objets CString](#_core_converting_cstring_objects)

`Class CString`est basé sur le modèle de classe [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md). `CString`est un **dactylo de** `CStringT`. Plus exactement, `CString` est un **tapdef d’une** *spécialisation explicite* de , qui est un moyen commun d’utiliser un modèle de `CStringT`classe pour définir une classe. Les classes `CStringA` définies de la même façon sont et `CStringW`.

`CString`, `CStringA`, `CStringW` et sont définis dans atlstr.h. `CStringT`est défini en cstringt.h.

`CString`, `CStringA`et `CStringW` chacun obtenir un ensemble des `CStringT` méthodes et des opérateurs définis par pour une utilisation avec les données de chaîne qu’ils prennent en charge. Certaines des méthodes dupliquent et, dans certains cas, surpassent les services de cordes des bibliothèques C run-time.

Remarque `CString` : est une classe autochtone. Pour une classe de cordes qui est à utiliser dans `System.String`un projet géré par L’IMC/CLI, utilisez .

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Création d’objets CString à partir de chaînes littérales C standard

Vous pouvez attribuer des chaînes littérales `CString` de style C `CString` à un tout comme vous pouvez attribuer un objet à un autre.

- Attribuer la valeur d’une chaîne `CString` littérale C à un objet.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Attribuer la valeur `CString` de `CString` l’un à l’autre objet.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Le contenu `CString` d’un objet `CString` est copié lorsqu’un objet est assigné à un autre. Par conséquent, les deux cordes ne partagent pas une référence aux caractères réels qui composent la chaîne. Pour plus d’informations `CString` sur la façon d’utiliser les objets comme valeurs, voir [CString Semantics](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Pour écrire votre application afin qu’elle puisse être compilée pour Unicode ou pour ANSI, codez les chaînes littérales en utilisant la macro _T. Pour plus d’informations, voir [Unicode et Multibyte Character Set (MBCS) Support](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Accès à des personnages individuels dans un CString

Vous pouvez accéder à `CString` des caractères individuels dans un objet en utilisant les `GetAt` méthodes et les `SetAt` méthodes. Vous pouvez également utiliser l’élément de tableau, ou `GetAt` sous-scriptum, opérateur ( [ ] ) au lieu d’obtenir des caractères individuels. (Cela ressemble à l’accès aux éléments de tableau par index, comme dans les chaînes standard de style C.) Les valeurs `CString` indiciels des caractères sont basées à zéro.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Concatenating Two CString Objects

Pour concatenate `CString` deux objets, utilisez les opérateurs de concatenation (ou ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Au moins un argument pour les opérateurs de concatenation `CString` (ou ' ) doit être un `"big"`objet, mais vous pouvez utiliser une chaîne de caractères constante (par exemple, ) ou un **char** (par exemple, 'x') pour l’autre argument.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Comparaison des objets CString

La `Compare` méthode et l’opérateur pour `CString` l’opérateur sont équivalents. `Compare`, **opérateur,** et `CompareNoCase` sont MBCS et Unicode conscients; `CompareNoCase` est également insensible aux cas. La `Collate` méthode `CString` de est sensible aux `Compare`lieux et est souvent plus lente que . N’utilisez `Collate` que lorsque vous devez respecter les règles de tri telles que spécifiées par le lieu actuel.

Le tableau suivant montre les fonctions de comparaison [CString](../atl-mfc-shared/reference/cstringt-class.md) disponibles et leurs fonctions équivalentes Unicode/MBCS-portables dans la bibliothèque C run-time.

|Fonction CString|Fonction MBCS|Fonction Unicode|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

Le `CStringT` modèle de classe définit les opérateurs relationnels (<, \<>, >, et ! , qui sont disponibles `CString`pour une utilisation par . Vous pouvez `CStrings` comparer deux en utilisant ces opérateurs, comme indiqué dans l’exemple suivant.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>Convertir les objets CString

Pour plus d’informations sur la conversion des objets CString à d’autres types de chaînes, voir [Comment : Convertir entre les différents types de cordes.](../text/how-to-convert-between-various-string-types.md)

## <a name="using-cstring-with-wcout"></a>Utilisation de CString avec wcout

Pour utiliser un CString avec `wcout` vous devez `const wchar_t*` explicitement jeter l’objet à un comme indiqué dans l’exemple suivant:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Sans la `cs` fonte, est `void*` `wcout` traité comme un et imprime l’adresse de l’objet. Ce comportement est causé par des interactions subtiles entre la déduction d’argument de modèle et la résolution de surcharge qui sont en eux-mêmes correctes et conformes à la norme de C.

## <a name="see-also"></a>Voir aussi

[Cordes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Spécialisation de modèle](../cpp/template-specialization-cpp.md)<br/>
[Comment : effectuer une conversion entre différents types de chaînes](../text/how-to-convert-between-various-string-types.md)
