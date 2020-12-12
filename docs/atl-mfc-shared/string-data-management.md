---
description: 'En savoir plus sur : String Gestion des données'
title: Gestion des données chaînes
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 37a3a13dc58641cc23e8ea5c31e12a4d4d9582fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166510"
---
# <a name="string-data-management"></a>Gestion des données chaînes

Visual C++ offre plusieurs moyens de gérer les données de chaîne :

- [Manipulation](../c-runtime-library/string-manipulation-crt.md) de chaînes pour travailler avec des chaînes de style C se terminant par un caractère null

- Fonctions de l’API Win32 pour la gestion des chaînes

- Classe MFC [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md), qui fournit des objets de chaîne flexibles et redimensionnables

- Classe [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md), qui fournit un objet String indépendant de MFC avec les mêmes fonctionnalités que `CString`

Presque tous les programmes fonctionnent avec des données de type chaîne. `CString`La classe MFC est souvent la meilleure solution pour la gestion flexible des chaînes. À partir de la version 7,0, `CString` peut être utilisé dans les programmes MFC ou indépendants des MFC. La bibliothèque Runtime et `CString` prennent en charge des chaînes contenant des caractères multioctets (larges), comme dans la programmation Unicode ou MBCS.

Cet article décrit les services à usage général que la bibliothèque de classes fournit en relation avec la manipulation de chaînes. Les sujets abordés dans cet article sont les suivants :

- [Unicode et MBCS offrent une portabilité](#_core_unicode_and_mbcs_provide_portability)

- [CStrings et pointeurs const char](#_core_cstrings_and_const_char_pointers)

- [Comptage de références CString](#_core_cstring_reference_counting)

La classe [CStringT](../atl-mfc-shared/reference/cstringt-class.md) fournit la prise en charge de la manipulation des chaînes. Il est destiné à remplacer et à étendre les fonctionnalités normalement fournies par le package de chaîne de la bibliothèque Runtime C. La `CString` classe fournit des fonctions membres et des opérateurs pour la gestion simplifiée des chaînes, similaires à celles trouvées dans Basic. La classe fournit également des constructeurs et des opérateurs pour construire, assigner et comparer des `CString` types de données de chaînes C++ standard et. Étant donné que `CString` n’est pas dérivé de `CObject` , vous pouvez utiliser des `CString` objets indépendamment de la plupart des bibliothèque MFC (Microsoft Foundation Class) (MFC).

`CString` les objets suivent « sémantique des valeurs ». Un `CString` objet représente une valeur unique. Imaginez un `CString` comme une chaîne réelle, et non comme un pointeur vers une chaîne.

Un `CString` objet représente une séquence d’un nombre variable de caractères. `CString` les objets peuvent être considérés comme des tableaux de caractères.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode et MBCS offrent une portabilité

Avec MFC version 3,0 et versions ultérieures, MFC, y compris `CString` , est activé pour Unicode et les jeux de caractères multioctets (MBCS). Cette prise en charge facilite l’écriture d’applications portables que vous pouvez créer pour les caractères Unicode ou ANSI. Pour activer cette portabilité, chaque caractère d’un `CString` objet est de type TCHAR, qui est défini comme **`wchar_t`** si vous définissiez le symbole _UNICODE lorsque vous générez votre application, ou comme **`char`** si ce n’est pas le cas. Un **`wchar_t`** caractère a une largeur de 16 bits. MBCS est activé si vous générez avec le symbole _MBCS défini. MFC est créée avec soit le symbole _MBCS (pour les bibliothèques NAFX), soit le symbole _UNICODE (pour les bibliothèques UAFX) défini.

> [!NOTE]
> Les `CString` exemples de cette et les Articles connexes sur les chaînes affichent des chaînes littérales correctement mises en forme pour la portabilité Unicode, à l’aide de la macro _T, qui convertit la chaîne littérale au format suivant :

`L"literal string"`

> [!NOTE]
> que le compilateur traite comme une chaîne Unicode. Par exemple, le code suivant :

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> est traduit comme une chaîne Unicode si _UNICODE est défini ou comme une chaîne ANSI dans le cas contraire. Pour plus d’informations, consultez l’article [prise en charge d’Unicode et du jeu de caractères multioctets (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

Un `CString` objet peut stocker jusqu’à INT_MAX (2 147 483 647) caractères. Le type de données TCHAR est utilisé pour obtenir ou définir des caractères individuels à l’intérieur d’un `CString` objet. Contrairement aux tableaux de caractères, la `CString` classe a une fonctionnalité d’allocation de mémoire intégrée. Cela permet `CString` aux objets de croître automatiquement en fonction des besoins (autrement dit, vous n’avez pas à vous soucier de la croissance `CString` d’un objet pour qu’il contienne des chaînes plus longues).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a> CStrings et pointeurs const char

Un `CString` objet peut également agir comme une chaîne de style C littérale (un `PCXSTR` , qui est le même que **const char** <strong>\*</strong> s’il n’est pas sous Unicode). L’opérateur de conversion [CSimpleStringT :: Operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) permet `CString` aux objets d’être substitués librement aux pointeurs de caractère dans les appels de fonction. Le constructeur **CString (LPCWSTR** `pszSrc` **)** permet aux pointeurs de caractère de se substituer aux `CString` objets.

Aucune tentative n’est faite pour plier les `CString` objets. Si vous créez deux `CString` objets contenant `Chicago` , par exemple, les caractères de `Chicago` sont stockés à deux emplacements. (Cela peut ne pas être vrai pour les futures versions de MFC, donc vous ne devez pas en dépendre.)

> [!NOTE]
> Utilisez les fonctions membres [CSimpleStringT :: GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [CSimpleStringT :: ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) lorsque vous avez besoin d’accéder directement `CString` à un comme pointeur non constant vers un caractère.

> [!NOTE]
> Utilisez les fonctions membres [CStringT :: AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) et [CStringT :: SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) pour allouer et définir des objets BSTR utilisés dans Automation (anciennement appelé OLE Automation).

> [!NOTE]
> Dans la mesure du possible, allouez `CString` des objets sur le frame plutôt que sur le tas. Cela permet d’économiser de la mémoire et de simplifier le passage des paramètres.

La `CString` classe n’est pas implémentée en tant que classe de collection bibliothèque MFC (Microsoft Foundation Class), bien que les `CString` objets puissent certainement être stockés en tant qu’éléments dans des collections.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a> Comptage de références CString

À partir de la version 4,0 de MFC, lorsque les objets de [classe CStringT](../atl-mfc-shared/reference/cstringt-class.md) sont copiés, MFC incrémente un décompte de références au lieu de copier les données. Cela permet de passer des paramètres par valeur et de retourner des `CString` objets par valeur plus efficacement. Ces opérations entraînent l’appel du constructeur de copie, parfois plusieurs fois. L’incrémentation d’un décompte de références réduit la surcharge liée à ces opérations courantes et utilise `CString` une option plus attrayante.

À mesure que chaque copie est détruite, le nombre de références dans l’objet d’origine est décrémenté. L’objet d’origine `CString` n’est pas détruit tant que son décompte de références n’est pas réduit à zéro.

Vous pouvez utiliser les `CString` fonctions membres [CSimpleStringT :: LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [CSimpleStringT :: UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) pour désactiver ou activer le décompte de références.

## <a name="see-also"></a>Voir aussi

[Rubriques générales sur MFC](../mfc/general-mfc-topics.md)
