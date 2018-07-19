---
title: Opérations CString de base | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccda8d6a1abd51f3463630435a14096edc30439d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879918"
---
# <a name="basic-cstring-operations"></a>Opérations CString de base
Cette rubrique explique la base suivante [CString](../atl-mfc-shared/reference/cstringt-class.md) opérations :  
  
- [Création d’objets CString à partir des chaînes littérales C standards](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
- [Accès aux caractères individuels dans un objet CString](#_core_accessing_individual_characters_in_a_cstring)  
  
- [Concaténation de deux objets CString](#_core_concatenating_two_cstring_objects)  
  
- [Comparaison d’objets CString](#_core_comparing_cstring_objects)  
  
- [Conversion d’objets CString](#_core_converting_cstring_objects)  
  
 `Class CString` est basé sur le modèle de classe [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md). `CString` est un **typedef** de `CStringT`. Plus précisément, `CString` est un **typedef** d’un *spécialisation explicite* de `CStringT`, qui est une façon courante d’utiliser un modèle de classe pour définir une classe. Classes de la même façon définies sont `CStringA` et `CStringW`.  
  
 `CString`, `CStringA`, et `CStringW` sont définis dans atlstr.h. `CStringT` est défini dans cstringt.h.  
  
 `CString`, `CStringA`, et `CStringW` chacun obtenir un ensemble des méthodes et des opérateurs définis par `CStringT` pour une utilisation avec les données de chaîne prises en charge. Certaines des méthodes en double et, dans certains cas, dépassent les services de chaîne des bibliothèques Runtime C.  
  
 Remarque : `CString` est une classe native. Pour une classe de chaîne qui est pour une utilisation en C / c++ / CLI géré le projet, utilisez `System.String`.  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> Création d’objets CString à partir de chaînes littérales C Standard  
 Vous pouvez affecter des chaînes littérales de style C à un `CString` tout comme vous pouvez affecter un `CString` objet vers un autre.  
  
-   Affectez la valeur d’une chaîne littérale C à un `CString` objet.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]  
  
-   Affectez la valeur d’un `CString` vers un autre `CString` objet.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]  
  
     Le contenu d’un `CString` objet sont copiés lorsqu’un `CString` objet est assigné à un autre. Par conséquent, les deux chaînes ne partagent pas une référence pour les caractères réels qui composent la chaîne. Pour plus d’informations sur l’utilisation `CString` objets en tant que valeurs, consultez [sémantique CString](../atl-mfc-shared/cstring-semantics.md).  
  
    > [!NOTE]
    >  Pour écrire votre application afin qu’il peut être compilé pour Unicode ou pour ANSI, les chaînes littérales de code à l’aide de la macro _T. Pour plus d’informations, consultez [Unicode et la prise en charge du jeu de caractères multioctets (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> Accès aux caractères individuels dans un objet CString  
 Vous pouvez accéder à des caractères individuels d’un `CString` objet à l’aide de la `GetAt` et `SetAt` méthodes. Vous pouvez également utiliser l’opérateur élément ou d’indice, tableau ([]) au lieu de `GetAt` pour obtenir des caractères individuels. (Cela ressemble à l’accès aux éléments de tableau par index, comme dans les chaînes de style C standards.) Indexer les valeurs pour `CString` caractères sont de base zéro.  
  
##  <a name="_core_concatenating_two_cstring_objects"></a> Concaténation de deux objets CString  
 Pour concaténer deux `CString` objets, utilisez les opérateurs de concaténation (+ ou +=), comme suit.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]  
  
 Au moins un argument pour les opérateurs de concaténation (+ ou +=) doit être un `CString` objet, mais vous pouvez utiliser une chaîne de caractères constante (par exemple, `"big"`) ou un **char** (par exemple, « x ») pour l’autre argument.  
  
##  <a name="_core_comparing_cstring_objects"></a> Comparaison d’objets CString  
 Le `Compare` (méthode) et le ==, opérateur pour `CString` sont équivalentes. `Compare`, **opérateur ==**, et `CompareNoCase` connaissent MBCS et Unicode ; `CompareNoCase` respecte également la casse. Le `Collate` méthode de `CString` respecte les paramètres régionaux et est souvent plus lent que `Compare`. Utilisez `Collate` uniquement où vous devez respecter le tri des règles comme spécifié par les paramètres régionaux actuels.  
  
 Le tableau suivant montre la disposition [CString](../atl-mfc-shared/reference/cstringt-class.md) fonctions de comparaison et leurs fonctions portable Unicode/MBCS équivalentes dans la bibliothèque Runtime C.  
  
|CString (fonction)|Fonction MBCS|Unicode (fonction)|  
|----------------------|-------------------|----------------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 Le `CStringT` modèle de classe définit les opérateurs relationnels (<, \<=, > =, >, == et ! =), qui sont disponibles pour une utilisation par `CString`. Vous pouvez comparer deux `CStrings` à l’aide de ces opérateurs, comme illustré dans l’exemple suivant.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a> Conversion d’objets CString  
 Pour plus d’informations sur la conversion d’objets CString à d’autres types de chaîne, consultez [Comment : convertir entre différents Types de chaînes](../text/how-to-convert-between-various-string-types.md).  
  
## <a name="using-cstring-with-wcout"></a>Utilisation de CString avec wcout  
 Pour utiliser un objet CString avec `wcout` vous devez caster explicitement l’objet à un `const wchar_t*` comme indiqué dans l’exemple suivant :  
  
```  
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;  
 
```  
  
 Sans le cast, `cs` est traité comme un `void*` et `wcout` imprime l’adresse de l’objet. Ce comportement est dû à des interactions subtiles entre modèle déduction et la surcharge de résolution des arguments dits correcte et conforme à la norme C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT, classe](../atl-mfc-shared/reference/cstringt-class.md)   
 [Spécialisation de modèle](../cpp/template-specialization-cpp.md)   
 [Guide pratique pour effectuer une conversion entre différents types de chaînes](../text/how-to-convert-between-various-string-types.md)

