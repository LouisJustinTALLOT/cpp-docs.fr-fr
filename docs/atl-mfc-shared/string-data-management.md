---
title: Gestion des données chaînes
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 7f92b38ac659faef2dd9319b2f204ba837f0d473
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317463"
---
# <a name="string-data-management"></a>Gestion des données chaînes

Visual CMMD fournit plusieurs façons de gérer les données des chaînes :

- [Manipulation des cordes](../c-runtime-library/string-manipulation-crt.md) pour travailler avec des cordes à mi-temps nuls de style C

- Fonctions win32 API pour la gestion des cordes

- Classe [CStringT](../atl-mfc-shared/reference/cstringt-class.md)de classe de MFC , qui fournit des objets à cordes flexibles et resizables

- Classe [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md), qui fournit un objet à chaîne MFC-indépendant avec la même fonctionnalité que`CString`

Presque tous les programmes fonctionnent avec des données de chaîne. La classe `CString` de MFC est souvent la meilleure solution pour une manipulation flexible des cordes. En commençant par la version `CString` 7.0, peut être utilisé dans les programmes MFC ou MFC-indépendants. La bibliothèque de course-temps et `CString` les chaînes de support contenant des caractères multioctets (larges), comme dans unicode ou MBCS programmation.

Cet article décrit les services à usage général que la bibliothèque de classe fournit liés à la manipulation des cordes. Les sujets abordés dans cet article sont les suivants :

- [Unicode et MBCS assurent la portabilité](#_core_unicode_and_mbcs_provide_portability)

- [CStrings et const char Pointers](#_core_cstrings_and_const_char_pointers)

- [Comptage des références CString](#_core_cstring_reference_counting)

La classe [CStringT](../atl-mfc-shared/reference/cstringt-class.md) offre un soutien pour manipuler les cordes. Il est destiné à remplacer et étendre la fonctionnalité normalement fournie par le paquet de chaîne de bibliothèque C run-time. La `CString` classe fournit aux membres des fonctions et des opérateurs pour une manipulation simplifiée des cordes, semblable à celles trouvées dans Basic. La classe fournit également des constructeurs et des `CString`opérateurs pour la construction, l’attribution et la comparaison des types de données de chaîne C et standard. Parce `CString` que n’est pas `CString` dérivé de , vous pouvez utiliser des `CObject`objets indépendamment de la plupart de la Microsoft Foundation Class Library (MFC).

`CString`les objets suivent la « sémantique de valeur ». Un `CString` objet représente une valeur unique. Pensez à `CString` une chaîne réelle, pas comme un pointeur à une chaîne.

Un `CString` objet représente une séquence d’un nombre variable de caractères. `CString`objets peuvent être considérés comme des tableaux de caractères.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode et MBCS assurent la portabilité

Avec la version MFC 3.0 et `CString`plus tard, MFC, y compris, est activé pour unicode et ensembles de caractères multioctets (MBCS). Ce support vous permet d’écrire plus facilement des applications portables que vous pouvez créer pour des caractères Unicode ou ANSI. Pour activer cette portabilité, `CString` chaque personnage d’un objet `wchar_t` est de type TCHAR, qui est défini comme `char` si vous définissez le symbole _UNICODE lorsque vous construisez votre application, ou comme si ce n’était pas le cas. Un `wchar_t` personnage est de 16 bits de large. MBCS est activé si vous construisez avec le symbole _MBCS défini. MFC elle-même est construit avec le symbole _MBCS (pour les bibliothèques NAFX) ou le symbole _UNICODE (pour les bibliothèques UAFX) défini.

> [!NOTE]
> Les `CString` exemples de ceci et les articles d’accompagnement sur les cordes montrent des chaînes littérales correctement formatées pour la portabilité d’Unicode, utilisant la macro _T, qui traduit la chaîne littérale à la forme :

`L"literal string"`

> [!NOTE]
> que le compilateur traite comme une chaîne Unicode. Par exemple, le code suivant :

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> est traduit par une chaîne Unicode si _UNICODE est définie ou comme une chaîne ANSI si ce n’est pas le cas. Pour plus d’informations, voir l’article [Unicode et Multibyte Character Set (MBCS) Support](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

Un `CString` objet peut stocker jusqu’à INT_MAX (2 147 483 647) caractères. Le type de données TCHAR est utilisé `CString` pour obtenir ou définir des caractères individuels à l’intérieur d’un objet. Contrairement aux tableaux `CString` de caractères, la classe dispose d’une capacité intégrée d’allocation de mémoire. Cela `CString` permet aux objets de croître automatiquement au besoin (c’est-à-dire que vous n’avez pas à vous soucier de la croissance d’un `CString` objet pour s’adapter à des cordes plus longues).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings et const char Pointers

Un `CString` objet peut également agir comme une chaîne `PCXSTR`littérale de style C (un , qui est le même que **l’omble de** <strong>\*</strong> const si ce n’est sous Unicode). L’opérateur de conversion [PCXSTR CSimpleStringT ::opérateur permet](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) aux `CString` objets d’être librement remplacés par des pointeurs de caractères dans les appels de fonction. Le **constructeur CString (LPCWSTR** `pszSrc` **)** permet de remplacer `CString` les pointeurs de caractères par des objets.

Aucune tentative n’est faite pour plier des `CString` objets. Si vous `CString` faites `Chicago`deux objets contenant, `Chicago` par exemple, les caractères sont stockés en deux endroits. (Ce n’est peut-être pas le cas des futures versions de MFC, donc vous ne devriez pas en dépendre.)

> [!NOTE]
> Utilisez le [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) fonctions membres `CString` lorsque vous avez besoin d’accéder directement à un pointeur nonconstant à un personnage.

> [!NOTE]
> Utilisez le [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) et [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) fonctions membres pour allouer et définir les objets BSTR utilisés dans l’automatisation (anciennement connu sous le nom OLE Automation).

> [!NOTE]
> Dans la mesure `CString` du possible, répartissez les objets sur le cadre plutôt que sur le tas. Cela permet d’économiser la mémoire et de simplifier le passage des paramètres.

La `CString` classe n’est pas mise en œuvre comme une classe de collecte Microsoft Foundation Class Library, bien que les `CString` objets peuvent certainement être stockés comme des éléments dans les collections.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>Comptage des références CString

À partir de la version 4.0 de MFC, lorsque les objets [de la classe CStringT](../atl-mfc-shared/reference/cstringt-class.md) sont copiés, MFC incrémente un nombre de références plutôt que de copier les données. Cela rend le passage des `CString` paramètres par valeur et le retour des objets par valeur plus efficace. Ces opérations font appeler le constructeur de copie, parfois plus d’une fois. L’augmentation d’un nombre de références réduit les `CString` frais généraux de ces opérations courantes et rend l’utilisation d’une option plus attrayante.

Comme chaque copie est détruite, le nombre de références dans l’objet d’origine est décrète. L’objet d’origine `CString` n’est pas détruit tant que son nombre de références n’est pas réduit à zéro.

Vous pouvez `CString` utiliser les fonctions membres [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) pour désactiver ou activer le comptage des références.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)
