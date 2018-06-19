---
title: Opérations CString de base | Documents Microsoft
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
ms.openlocfilehash: b66b6fc5578960e4b6ec9b392622256b66db9cfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359092"
---
# <a name="basic-cstring-operations"></a>Opérations CString de base
Cette rubrique explique basic suivant [CString](../atl-mfc-shared/reference/cstringt-class.md) opérations :  
  
- [Création d’objets CString à partir des chaînes littérales C standards](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
- [L’accès à des caractères individuels dans un objet CString](#_core_accessing_individual_characters_in_a_cstring)  
  
- [Concaténation de deux objets CString](#_core_concatenating_two_cstring_objects)  
  
- [Comparaison d’objets CString](#_core_comparing_cstring_objects)  
  
- [Conversion d’objets CString](#_core_converting_cstring_objects)  
  
 `Class CString` est basé sur le modèle de classe [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md). `CString` est un `typedef` de `CStringT`. Plus précisément, `CString` est un `typedef` d’un *spécialisation explicite* de `CStringT`, qui est une méthode courante pour utiliser un modèle de classe pour définir une classe. Classes de la même façon définies sont `CStringA` et `CStringW`.  
  
 `CString`, `CStringA`, et `CStringW` sont définis dans atlstr.h. `CStringT` est défini dans cstringt.h.  
  
 `CString`, `CStringA`, et `CStringW` chacun obtenir un ensemble des méthodes et des opérateurs définis par `CStringT` pour une utilisation avec les données de chaîne prises en charge. Certaines méthodes en double et, dans certains cas, dépassent les services de chaîne des bibliothèques Runtime C.  
  
 Remarque : `CString` est une classe native. Pour une classe de chaîne qui doit être utilisée dans un C + c++ / CLI géré de projet, utilisez `System.String`.  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> Création d’objets CString à partir de chaînes littérales C Standard  
 Vous pouvez assigner des chaînes littérales de style C à un `CString` tout comme vous pouvez affecter un `CString` objet vers un autre.  
  
-   Affectez la valeur de chaîne littérale C à un `CString` objet.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]  
  
-   Affecter la valeur d’un `CString` vers un autre `CString` objet.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]  
  
     Le contenu d’un `CString` objet sont copiés lorsqu’au moins une `CString` objet est assigné à un autre. Par conséquent, les deux chaînes ne partagent pas une référence pour les caractères réels qui composent la chaîne. Pour plus d’informations sur l’utilisation de `CString` objets sous forme de valeurs, consultez [sémantique CString](../atl-mfc-shared/cstring-semantics.md).  
  
    > [!NOTE]
    >  Pour écrire votre application afin qu’il peut être compilé pour Unicode ou pour ANSI, les chaînes littérales de code à l’aide de la macro _T. Pour plus d’informations, consultez [Unicode et la prise en charge de la valeur de caractère multioctets (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> L’accès à des caractères individuels dans un objet CString  
 Vous pouvez accéder à des caractères individuels dans un `CString` objet à l’aide de la `GetAt` et `SetAt` méthodes. Vous pouvez également utiliser l’opérateur élément ou, indice de tableau ([]) au lieu de `GetAt` pour obtenir des caractères individuels. (Cela ressemble à l’accès aux éléments de tableau par index, comme dans les chaînes de style C standards.) Pour les valeurs d’index `CString` caractères sont de base zéro.  
  
##  <a name="_core_concatenating_two_cstring_objects"></a> Concaténation de deux objets CString  
 Pour concaténer deux `CString` objets, utilisez les opérateurs de concaténation (+ ou +=), comme suit.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]  
  
 Au moins un argument pour les opérateurs de concaténation (+ ou +=) doit être un `CString` objet, mais vous pouvez utiliser une chaîne de caractères constante (par exemple, `"big"`) ou un `char` (par exemple, « x ») pour l’autre argument.  
  
##  <a name="_core_comparing_cstring_objects"></a> Comparaison d’objets CString  
 Le `Compare` (méthode) et le ==, opérateur pour `CString` sont équivalents. `Compare`, `operator==`, et `CompareNoCase` connaissent MBCS et Unicode ; `CompareNoCase` respecte également la casse. Le `Collate` méthode `CString` est sensible aux paramètres régionaux et est souvent plus lente que `Compare`. Utilisez `Collate` uniquement lorsque vous devez respecter l’ordre de tri des règles comme spécifié par les paramètres régionaux actuels.  
  
 Le tableau suivant présente les [CString](../atl-mfc-shared/reference/cstringt-class.md) des fonctions de comparaison et leurs fonctions portable Unicode/MBCS équivalentes dans la bibliothèque Runtime C.  
  
|CString (fonction)|Fonction MBCS|Unicode (fonction)|  
|----------------------|-------------------|----------------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 Le `CStringT` modèle de classe définit les opérateurs relationnels (<, \<=, > =, >, == et ! =), qui sont disponible pour une utilisation par `CString`. Vous pouvez comparer deux `CStrings` à l’aide de ces opérateurs, comme illustré dans l’exemple suivant.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a> Conversion d’objets CString  
 Pour plus d’informations sur la conversion d’objets CString à d’autres types de chaîne, consultez [Comment : convertir entre différents Types de chaînes](../text/how-to-convert-between-various-string-types.md).  
  
## <a name="using-cstring-with-wcout"></a>Utilisation de CString avec wcout  
 Pour utiliser un objet CString avec `wcout` vous devez caster explicitement l’objet à un `const wchar_t*` comme indiqué dans l’exemple suivant :  
  
```  
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;  
 
```  
  
 Sans le cast, `cs` est traité comme un `void*` et `wcout` imprime l’adresse de l’objet. Ce problème est causé par des interactions subtiles entre le modèle déduction et surcharge de résolution des arguments qui sont eux-mêmes correcte et conforme à la norme C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT (classe)](../atl-mfc-shared/reference/cstringt-class.md)   
 [Spécialisation de modèle](../cpp/template-specialization-cpp.md)   
 [Guide pratique pour effectuer une conversion entre différents types de chaînes](../text/how-to-convert-between-various-string-types.md)

