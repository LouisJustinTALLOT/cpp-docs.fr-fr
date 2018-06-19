---
title: Gestion des données de chaîne | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acf14ebec5417179a94d0a6ffefdb473966f0c2e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361234"
---
# <a name="string-data-management"></a>Gestion des données chaînes
Visual C++ propose plusieurs façons de gérer les données de type chaîne :  
  
-   [Manipulation de chaîne](../c-runtime-library/string-manipulation-crt.md) pour manipuler des chaînes de style C se terminant par null  
  
-   Fonctions API Win32 pour la gestion des chaînes  
  
-   La classe MFC [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md), qui fournit des objets chaîne redimensionnables flexible  
  
-   Classe [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md), qui fournit un objet de chaîne indépendant des MFC avec les mêmes fonctionnalités que `CString`  
  
 Presque tous les programmes fonctionnent avec des données de chaîne. MFC `CString` classe est souvent la meilleure solution pour la gestion des chaînes flexible. Depuis la version 7.0, `CString` peut être utilisé dans les programmes MFC ou indépendants des MFC. La bibliothèque d’exécution et `CString` prend en charge les chaînes contenant des caractères multioctets (étendus), comme dans la programmation MBCS ou Unicode.  
  
 Cet article décrit les services à usage général qui fournit de la bibliothèque de classes liées à la manipulation de chaînes. Les rubriques abordées dans cet article sont les suivantes :  
  
-   [Unicode et MBCS fournissent la portabilité](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CString et pointeurs const char](#_core_cstrings_and_const_char_pointers)  
  
-   [Décompte de références CString](#_core_cstring_reference_counting)  
  
 Le [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md) classe prend en charge la manipulation de chaînes. Elle est destinée à remplacer et étendre la fonctionnalité normalement fournie par le package de chaîne de bibliothèque Runtime C. La `CString` classe fournit les fonctions membres et des opérateurs pour la gestion simplifiée des chaînes, similaires à ceux de Basic. La classe fournit également les constructeurs et des opérateurs pour la construction, l’affectation et la comparaison **classes CString** et types de données de chaîne C++ standard. Étant donné que `CString` n’est pas dérivé `CObject`, vous pouvez utiliser `CString` objets indépendamment de la plupart de la bibliothèque Microsoft Foundation classe (MFC).  
  
 `CString` les objets suivent la « sémantique des valeurs ». A `CString` objet représente une valeur unique. Imaginez un `CString` sous forme de chaîne réelle, et non comme un pointeur vers une chaîne.  
  
 A `CString` objet représente une séquence d’un nombre variable de caractères. `CString` objets peuvent être considérés comme des tableaux de caractères.  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode et MBCS assurent la portabilité  
 Avec MFC version 3.0 et versions ultérieure, MFC, y compris les `CString`, est activée pour Unicode et jeux de caractères multioctets (MBCS). Cette prise en charge facilite l’écriture d’applications portables que vous pouvez générer des caractères Unicode ou ANSI. Pour activer cette portabilité, chaque caractère dans un `CString` objet est de type **TCHAR**, qui est définie comme `wchar_t` si vous définissez le symbole **_UNICODE** lorsque vous générez votre application, ou en tant que `char` si ce n’est pas le cas. Une `wchar_t` caractère est la largeur de 16 bits. MBCS est activé si vous générez avec le symbole **_MBCS** défini. Application MFC elle-même est générée à l’aide d’un le **_MBCS** symbole (pour les bibliothèques NAFX) ou le **_UNICODE** symbole (pour les bibliothèques UAFX) défini.  
  
> [!NOTE]
>  Le `CString` exemples de cette et les articles d’accompagnement sur Afficher les chaînes littérales correctement mis en forme pour la portabilité Unicode, à l’aide de la **_T** (macro), ce qui se traduit par la chaîne littérale au formulaire :  
  
 `L"literal string"`  
  
> [!NOTE]
>  que le compilateur traite comme une chaîne Unicode. Par exemple, le code suivant :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]  
  
> [!NOTE]
>  est converti en une chaîne Unicode si **_UNICODE** est défini ou en tant que ANSI de chaîne dans le cas contraire. Pour plus d’informations, consultez l’article [Unicode et la prise en charge de la valeur de caractère multioctets (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
 A `CString` objet peut stocker jusqu'à **INT_MAX** (2 147 483 647) caractères. Le **TCHAR** type de données est utilisé pour obtenir ou définir des caractères individuels à l’intérieur d’un `CString` objet. Contrairement aux tableaux de caractères, la `CString` classe a une fonction d’allocation de mémoire intégrées. Cela permet de `CString` objets à croître automatiquement en fonction des besoins (autrement dit, il est inutile à vous soucier de croissance un `CString` objet en fonction de chaînes plus longues).  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a> CString et pointeurs const char  
 A `CString` objet peut également agir comme une chaîne de style C littérale (une `PCXSTR`, qui est le même que **const char\***  si pas sous Unicode). Le [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) permet de l’opérateur de conversion `CString` objets à être librement remplacés par des pointeurs de caractères dans les appels de fonction. Le **CString (LPCWSTR** `pszSrc` **)** constructeur permet des pointeurs de caractères à remplacer pour `CString` objets.  
  
 Aucune tentative n’est effectuée `CString` objets. Si vous effectuez deux `CString` contenant des objets `Chicago`, par exemple, les caractères de `Chicago` sont stockées dans deux emplacements. (Cela ne peut pas être vrai pour les futures versions de MFC, donc vous ne devez pas dépendre il.)  
  
> [!NOTE]
>  Utilisez le [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) les fonctions membres lorsque vous avez besoin accéder directement à un `CString` comme un pointeur non constant d’un caractère.  
  
> [!NOTE]
>  Utilisez le [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) et [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) des fonctions membres pour allouer et définir `BSTR` objets utilisés dans Automation (anciennement appelé OLE Automation).  
  
> [!NOTE]
>  Lorsque cela est possible, allouez `CString` objets sur le frame plutôt que sur le tas. Cela vous permet de mémoire et simplifie le passage de paramètres.  
  
 Le `CString` classe n’est pas implémentée comme une classe de collection de bibliothèque Microsoft Foundation Class, bien que `CString` objets certainement peuvent être stockés en tant qu’éléments dans des collections.  
  
##  <a name="_core_cstring_reference_counting"></a> Décompte de références CString  
 Depuis la version 4.0, MFC lorsque [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md) objets sont copiés, MFC incrémente un décompte de références au lieu de copier les données. Cela rend le passage de paramètres par valeur et en retournant `CString` objets par valeur plus efficace. Ces opérations entraînent le constructeur de copie être appelées, parfois plusieurs fois. Incrémentation d’un décompte de références réduit le temps système pour ces opérations courantes et facilite l’utilisation de `CString` une option plus attrayante.  
  
 Comme chaque copie est détruit, le nombre de références dans l’objet d’origine est décrémenté. La version d’origine `CString` objet n’est pas détruit tant que son décompte de références est réduit à zéro.  
  
 Vous pouvez utiliser la `CString` fonctions membres [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) pour désactiver ou activer un comptage de références.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)

