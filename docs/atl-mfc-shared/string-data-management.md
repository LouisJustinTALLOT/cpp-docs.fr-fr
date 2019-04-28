---
title: Gestion des données chaînes
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: b247e97f5aa6b5e85a6a6b6f57a64224a9e0f435
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252660"
---
# <a name="string-data-management"></a>Gestion des données chaînes

Visual C++ propose plusieurs façons de gérer les données de type chaîne :

- [Manipulation de chaînes](../c-runtime-library/string-manipulation-crt.md) pour travailler avec des chaînes de style C se terminant par null

- Fonctions API Win32 pour la gestion des chaînes

- La classe MFC [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md), qui fournit des objets chaîne redimensionnables flexible

- Classe [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md), qui fournit un objet de chaîne indépendant des MFC avec les mêmes fonctionnalités que `CString`

Presque tous les programmes fonctionnent avec les données de type chaîne. MFC `CString` classe est souvent la meilleure solution pour la gestion des chaînes flexible. Depuis la version 7.0, `CString` peut être utilisé dans les programmes MFC ou indépendants des MFC. Les deux la bibliothèque d’exécution et `CString` prend en charge les chaînes contenant des caractères multioctets (larges), comme dans la programmation de MBCS ou Unicode.

Cet article décrit les services à usage général qui fournit de la bibliothèque de classes liées à la manipulation de chaînes. Les sujets abordés dans cet article sont les suivantes :

- [Portabilité Unicode et MBCS fournir](#_core_unicode_and_mbcs_provide_portability)

- [CString et pointeurs const char](#_core_cstrings_and_const_char_pointers)

- [Décompte de références CString](#_core_cstring_reference_counting)

Le [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md) classe prend en charge la manipulation de chaînes. Il est destiné à remplacer et étendre la fonctionnalité normalement assurée par le package de chaîne de bibliothèque Runtime C. Le `CString` classe fournit des fonctions membres et des opérateurs pour la gestion simplifiée des chaînes, similaires à celles disponibles dans la base. La classe fournit également les constructeurs et des opérateurs pour la construction, l’affectation et la comparaison `CString`s et C++ standard des types de données string. Étant donné que `CString` n’est pas dérivé `CObject`, vous pouvez utiliser `CString` objets indépendamment de la plupart de la MFC Microsoft Foundation Class Library ().

`CString` les objets suivent la « valeur sémantique. » Un `CString` objet représente une valeur unique. Considérez un `CString` sous forme de chaîne réelle, et non comme un pointeur vers une chaîne.

Un `CString` objet représente une séquence d’un nombre variable de caractères. `CString` objets peuvent être considérés comme des tableaux de caractères.

##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode et MBCS assurent la portabilité

Avec MFC version 3.0 et versions ultérieure, MFC, notamment `CString`, est activée pour Unicode et jeux de caractères multioctets (MBCS). Cette prise en charge facilite l’écriture d’applications portables que vous pouvez créer pour les caractères Unicode ou ANSI. Pour activer cette portabilité, chaque caractère dans un `CString` objet est de type TCHAR, qui est définie comme `wchar_t` si vous définissez le symbole _UNICODE quand vous générez votre application, ou en tant que `char` dans le cas contraire. Une `wchar_t` caractère est la largeur de 16 bits. MBCS est activé si vous générez avec le symbole _MBCS défini. Application MFC elle-même est générée avec le symbole _MBCS (pour les bibliothèques NAFX) ou le symbole _UNICODE (pour les bibliothèques UAFX) défini.

> [!NOTE]
>  Le `CString` exemples dans cet article et les articles qui accompagne cet article sur les chaînes montrent des chaînes littérales correctement mis en forme pour la portabilité Unicode, à l’aide de la macro _T, qui se traduit par la chaîne littérale au formulaire :

`L"literal string"`

> [!NOTE]
>  que le compilateur traite comme une chaîne Unicode. Par exemple, le code suivant :

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
>  la traduction en sous forme de chaîne Unicode si _UNICODE est défini ou sous forme de chaîne ANSI dans le cas contraire. Pour plus d’informations, consultez l’article [Unicode et la prise en charge du jeu de caractères multioctets (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

Un `CString` objet permet de stocker caractères INT_MAX (2 147 483 647). Le type de données TCHAR est utilisé pour obtenir ou définir des caractères individuels à l’intérieur d’un `CString` objet. Contrairement aux tableaux de caractères, la `CString` classe a une fonction d’allocation de mémoire intégrée. Cela permet de `CString` objets à croître automatiquement en fonction des besoins (autrement dit, vous n’avez pas à vous soucier de croissance un `CString` objet en fonction de chaînes plus longues).

##  <a name="_core_cstrings_and_const_char_pointers"></a> CString et pointeurs const char

Un `CString` objet peut également agir comme une littéral chaîne de style C (une `PCXSTR`, qui est le même que **const char** <strong>\*</strong> si pas sous Unicode). Le [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) permet de l’opérateur de conversion `CString` objets à être librement remplacés par des pointeurs de caractères dans les appels de fonction. Le **CString (LPCWSTR** `pszSrc` **)** constructeur permet de pointeurs de caractère pour `CString` objets.

Aucune tentative est effectuée pour plier `CString` objets. Si vous apportez des deux `CString` contenant des objets `Chicago`, par exemple, les caractères dans `Chicago` sont stockées dans deux emplacements. (Cela ne peut pas être vrai pour les versions futures de MFC, donc vous devez en dépendent pas.)

> [!NOTE]
>  Utilisez le [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) fonctions membres lorsque vous avez besoin d’accéder directement à un `CString` en tant que pointeur vers un caractère non constant.

> [!NOTE]
>  Utilisez le [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) et [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) fonctions membres pour allouer et définir des objets BSTR utilisés dans Automation (anciennement appelé OLE Automation).

> [!NOTE]
>  Si possible, allouez `CString` objets sur le frame plutôt que sur le tas. Cela économise de la mémoire et simplifie le passage de paramètres.

Le `CString` classe n’est pas implémentée comme une classe de collection de bibliothèque Microsoft Foundation Class, cependant `CString` objets peuvent certainement être stockés en tant qu’éléments dans les collections.

##  <a name="_core_cstring_reference_counting"></a> Décompte de références CString

Depuis la version 4.0, MFC lorsque [Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md) objets sont copiés, MFC incrémente un décompte de références, plutôt que de copier les données. Cela rend le passage de paramètres par valeur et en retournant `CString` objets par valeur plus efficace. Ces opérations provoquent le constructeur de copie qui sera appelée, parfois plusieurs fois. Incrémentation d’un décompte de références réduit le temps système pour les opérations courantes et facilite l’utilisation de `CString` une option plus attrayante.

Comme chaque copie est détruit, le décompte de références dans l’objet d’origine est décrémenté. La version d’origine `CString` pas détruit tant que son décompte de références est réduite à zéro.

Vous pouvez utiliser la `CString` fonctions membres [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) pour désactiver ou activer le décompte de références.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)
