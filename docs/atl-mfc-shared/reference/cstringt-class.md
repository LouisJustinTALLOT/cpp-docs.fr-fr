---
title: '**`CStringT`** Type'
description: Informations de référence sur l’API pour la classe Microsoft ATL **`CStringT`**
ms.date: 12/06/2020
f1_keywords:
- CStringT
- CSTRINGT/ATL::CStringT
- CSTRINGT/ATL::CStringT::CStringT
- CSTRINGT/ATL::CStringT::AllocSysString
- CSTRINGT/ATL::CStringT::AnsiToOem
- CSTRINGT/ATL::CStringT::AppendFormat
- CSTRINGT/ATL::CStringT::Collate
- CSTRINGT/ATL::CStringT::CollateNoCase
- CSTRINGT/ATL::CStringT::Compare
- CSTRINGT/ATL::CStringT::CompareNoCase
- CSTRINGT/ATL::CStringT::Delete
- CSTRINGT/ATL::CStringT::Find
- CSTRINGT/ATL::CStringT::FindOneOf
- CSTRINGT/ATL::CStringT::Format
- CSTRINGT/ATL::CStringT::FormatMessage
- CSTRINGT/ATL::CStringT::FormatMessageV
- CSTRINGT/ATL::CStringT::FormatV
- CSTRINGT/ATL::CStringT::GetEnvironmentVariable
- CSTRINGT/ATL::CStringT::Insert
- CSTRINGT/ATL::CStringT::Left
- CSTRINGT/ATL::CStringT::LoadString
- CSTRINGT/ATL::CStringT::MakeLower
- CSTRINGT/ATL::CStringT::MakeReverse
- CSTRINGT/ATL::CStringT::MakeUpper
- CSTRINGT/ATL::CStringT::Mid
- CSTRINGT/ATL::CStringT::OemToAnsi
- CSTRINGT/ATL::CStringT::Remove
- CSTRINGT/ATL::CStringT::Replace
- CSTRINGT/ATL::CStringT::ReverseFind
- CSTRINGT/ATL::CStringT::Right
- CSTRINGT/ATL::CStringT::SetSysString
- CSTRINGT/ATL::CStringT::SpanExcluding
- CSTRINGT/ATL::CStringT::SpanIncluding
- CSTRINGT/ATL::CStringT::Tokenize
- CSTRINGT/ATL::CStringT::Trim
- CSTRINGT/ATL::CStringT::TrimLeft
- CSTRINGT/ATL::CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.openlocfilehash: f9ec5c02aa1ed9377a38d30d9a4152af5e164d58
ms.sourcegitcommit: 7b131db4ed39bddb4a456ebea402f47c5cbd69d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96776542"
---
# <a name="cstringt-class"></a>La classe `CStringT`

Cette classe représente un **`CStringT`** objet.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Paramètres

*`BaseType`*\
Type de caractère de la classe String. Il peut s'agir d'une des méthodes suivantes :

- **`char`** (pour les chaînes de caractères ANSI).

- **`wchar_t`** (pour les chaînes de caractères Unicode).

- **`TCHAR`** (pour les chaînes de caractères ANSI et Unicode).

*`StringTraits`*\
Détermine si la classe de chaîne requiert la prise en charge de la bibliothèque C Run-Time (CRT) et où les ressources de type chaîne sont situées. Il peut s'agir d'une des méthodes suivantes :

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   La classe requiert la prise en charge de CRT et recherche des chaînes de ressource dans le module spécifié par `m_hInstResource` (un membre de la classe de module de l’application).

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char |TCHAR>>`**

   La classe ne requiert pas la prise en charge de CRT et recherche des chaînes de ressource dans le module spécifié par `m_hInstResource` (un membre de la classe de module de l’application).

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   La classe requiert la prise en charge de CRT et recherche des chaînes de ressources à l’aide de l’algorithme de recherche MFC standard.

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char | TCHAR>>`**

   La classe ne requiert pas la prise en charge de CRT et recherche des chaînes de ressources à l’aide de l’algorithme de recherche MFC standard.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[`CStringT::CStringT`](#cstringt)|Construit un **`CStringT`** objet de différentes façons.|
|[`CStringT::~CStringT`](#_dtorcstringt)|Détruit un **`CStringT`** objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[`CStringT::AllocSysString`](#allocsysstring)|Alloue un `BSTR` à partir de **`CStringT`** données.|
|[`CStringT::AnsiToOem`](#ansitooem)|Effectue une conversion sur place du jeu de caractères ANSI en jeu de caractères OEM.|
|[`CStringT::AppendFormat`](#appendformat)|Ajoute des données mises en forme à un **`CStringT`** objet existant.|
|[`CStringT::Collate`](#collate)|Compare deux chaînes (respecte la casse, utilise des informations spécifiques aux paramètres régionaux).|
|[`CStringT::CollateNoCase`](#collatenocase)|Compare deux chaînes (non-respect de la casse, utilise des informations spécifiques aux paramètres régionaux).|
|[`CStringT::Compare`](#compare)|Compare deux chaînes (respect de la casse).|
|[`CStringT::CompareNoCase`](#comparenocase)|Compare deux chaînes (non-respect de la casse).|
|[`CStringT::Delete`](#delete)|Supprime un ou des caractères d’une chaîne.|
|[`CStringT::Find`](#find)|Recherche un caractère ou une sous-chaîne à l’intérieur d’une chaîne plus grande.|
|[`CStringT::FindOneOf`](#findoneof)|Recherche le premier caractère correspondant dans un ensemble.|
|[`CStringT::Format`](#format)|Met en forme la chaîne comme `sprintf` c’est le cas.|
|[`CStringT::FormatMessage`](#formatmessage)|Met en forme une chaîne de message.|
|[`CStringT::FormatMessageV`](#formatmessagev)|Met en forme une chaîne de message à l’aide d’une liste d’arguments de variables.|
|[`CStringT::FormatV`](#formatv)|Met en forme la chaîne à l’aide d’une liste variable d’arguments.|
|[`CStringT::GetEnvironmentVariable`](#getenvironmentvariable)|Affecte à la chaîne la valeur de la variable d’environnement spécifiée.|
|[`CStringT::Insert`](#insert)|Insère un caractère unique ou une sous-chaîne à l’index donné dans la chaîne.|
|[`CStringT::Left`](#left)|Extrait la partie gauche d’une chaîne.|
|[`CStringT::LoadString`](#loadstring)|Charge un **`CStringT`** objet existant à partir d’une ressource Windows.|
|[`CStringT::MakeLower`](#makelower)|Convertit tous les caractères de cette chaîne en caractères minuscules.|
|[`CStringT::MakeReverse`](#makereverse)|Inverse la chaîne.|
|[`CStringT::MakeUpper`](#makeupper)|Convertit tous les caractères de cette chaîne en caractères majuscules.|
|[`CStringT::Mid`](#mid)|Extrait la partie centrale d’une chaîne.|
|[`CStringT::OemToAnsi`](#oemtoansi)|Effectue une conversion sur place du jeu de caractères OEM en jeu de caractères ANSI.|
|[`CStringT::Remove`](#remove)|Supprime les caractères indiqués d’une chaîne.|
|[`CStringT::Replace`](#replace)|Remplace les caractères indiqués par d’autres caractères.|
|[`CStringT::ReverseFind`](#reversefind)|Recherche un caractère dans une chaîne plus grande ; démarre à partir de la fin.|
|[`CStringT::Right`](#right)|Extrait la partie droite d’une chaîne.|
|[`CStringT::SetSysString`](#setsysstring)|Définit un `BSTR` objet existant avec les données d’un **`CStringT`** objet.|
|[`CStringT::SpanExcluding`](#spanexcluding)|Extrait des caractères de la chaîne, en commençant par le premier caractère, qui ne se trouvent pas dans le jeu de caractères identifié par `pszCharSet` .|
|[`CStringT::SpanIncluding`](#spanincluding)|Extrait une sous-chaîne qui contient uniquement les caractères d’un jeu.|
|[`CStringT::Tokenize`](#tokenize)|Extrait les jetons spécifiés dans une chaîne cible.|
|[`CStringT::Trim`](#trim)|Supprime tous les caractères d’espace blanc de début et de fin de la chaîne.|
|[`CStringT::TrimLeft`](#trimleft)|Supprime les caractères d’espace blanc de début de la chaîne.|
|[`CStringT::TrimRight`](#trimright)|Supprime les caractères d’espace blanc de fin de la chaîne.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[`CStringT::operator =`](#operator_eq)|Assigne une nouvelle valeur à un **`CStringT`** objet.|
|[`CStringT::operator +`](#operator_add)|Concatène deux chaînes, ou un caractère et une chaîne.|
|[`CStringT::operator +=`](#operator_add_eq)|Concatène une nouvelle chaîne à la fin d’une chaîne existante.|
|[`CStringT::operator ==`](#operator_eq_eq)|Détermine si deux chaînes sont logiquement égales.|
|[`CStringT::operator !=`](#operator_neq)|Détermine si deux chaînes ne sont pas égales logiquement.|
|[`CStringT::operator <`](#operator_lt)|Détermine si la chaîne située à gauche de l’opérateur est inférieure à la chaîne sur le côté droit.|
|[`CStringT::operator >`](#operator_gt)|Détermine si la chaîne située à gauche de l’opérateur est supérieure à la chaîne sur le côté droit.|
|[`CStringT::operator <=`](#operator_lt_eq)|Détermine si la chaîne située à gauche de l’opérateur est inférieure ou égale à la chaîne située à droite.|
|[`CStringT::operator >=`](#operator_gt_eq)|Détermine si la chaîne située à gauche de l’opérateur est supérieure ou égale à la chaîne située à droite.|

## <a name="remarks"></a>Remarques

**`CStringT`** hérite de la [classe CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md). Les fonctionnalités avancées, telles que la manipulation de caractères, le classement et la recherche, sont implémentées par **`CStringT`** .

> [!NOTE]
> **`CStringT`** les objets peuvent lever des exceptions. Cela se produit lorsqu’un **`CStringT`** objet manque de mémoire pour une raison quelconque.

Un **`CStringT`** objet se compose d’une séquence de caractères de longueur variable. **`CStringT`** fournit des fonctions et des opérateurs à l’aide d’une syntaxe similaire à celle de Basic. Les opérateurs de concaténation et de comparaison, ainsi que la gestion simplifiée de la mémoire, rendent les **`CStringT`** objets plus faciles à utiliser que les tableaux de caractères ordinaires.

> [!NOTE]
> Bien qu’il soit possible de créer **`CStringT`** des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et d’opérateurs sur des **`CStringT`** objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

En utilisant différentes combinaisons des `BaseType` paramètres et `StringTraits` , les **`CStringT`** objets peuvent être dans les types suivants, qui ont été prédéfinis par les bibliothèques ATL.

Si vous utilisez dans une application ATL :

`CString`, `CStringA` et `CStringW` sont exportés à partir de la DLL MFC (MFC90.DLL), jamais à partir des dll utilisateur. Cette opération est effectuée pour empêcher la **`CStringT`** définition de plusieurs fois.

> [!NOTE]
> Si votre code contient la solution de contournement pour les erreurs de l’éditeur de liens qui est décrite dans [exportation de classes de chaînes à l’aide de CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), vous devez supprimer ce code. Ce n'est plus nécessaire.

Les types de chaîne suivants sont disponibles dans les applications basées sur MFC :

|CStringT, type|Déclaration|
|-------------------|-----------------|
|`CStringA`|Chaîne de type caractère ANSI avec prise en charge de CRT.|
|`CStringW`|Chaîne de type caractère Unicode avec prise en charge de CRT.|
|`CString`|Types de caractères ANSI et Unicode avec prise en charge de CRT.|

Les types de chaîne suivants sont disponibles dans les projets où `ATL_CSTRING_NO_CRT` est défini :

|CStringT, type|Déclaration|
|-------------------|-----------------|
|`CAtlStringA`|Chaîne de type caractère ANSI sans prise en charge CRT.|
|`CAtlStringW`|Chaîne de type caractère Unicode sans prise en charge CRT.|
|`CAtlString`|Types de caractères ANSI et Unicode sans prise en charge de CRT.|

Les types de chaîne suivants sont disponibles dans les projets où `ATL_CSTRING_NO_CRT` n’est pas défini :

|CStringT, type|Déclaration|
|-------------------|-----------------|
|`CAtlStringA`|Chaîne de type caractère ANSI avec prise en charge de CRT.|
|`CAtlStringW`|Chaîne de type caractère Unicode avec prise en charge de CRT.|
|`CAtlString`|Types de caractères ANSI et Unicode avec prise en charge de CRT.|

`CString` les objets présentent également les caractéristiques suivantes :

- **`CStringT`** les objets peuvent croître en raison d’opérations de concaténation.

- **`CStringT`** les objets suivent « sémantique des valeurs ». Imaginez un **`CStringT`** objet comme une chaîne réelle, et non comme un pointeur vers une chaîne.

- Vous pouvez substituer librement **`CStringT`** des objets pour des `PCXSTR` arguments de fonction.

- Gestion de la mémoire personnalisée pour les mémoires tampons de chaîne. Pour plus d’informations, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Types prédéfinis de CStringT

Étant donné que **`CStringT`** utilise un argument template pour définir le type de caractère ( [wchar_t](../../c-runtime-library/standard-types.md) ou [char](../../c-runtime-library/standard-types.md)) pris en charge, les types de paramètres de méthode peuvent être compliqués à des moments. Pour simplifier ce problème, un ensemble de types prédéfinis est défini et utilisé dans l’ensemble de la **`CStringT`** classe. Le tableau suivant répertorie les différents types :

|Nom|Description|
|----------|-----------------|
|`XCHAR`|Caractère unique ( **`wchar_t`** ou **`char`** ) avec le même type de caractère que l' **`CStringT`** objet.|
|`YCHAR`|Caractère unique ( **`wchar_t`** ou **`char`** ) avec le type de caractère opposé comme **`CStringT`** objet.|
|`PXSTR`|Pointeur vers une chaîne de caractères ( **`wchar_t`** ou **`char`** ) avec le même type de caractère que l’objet * * * * * * * * `CStringT` .|
|`PYSTR`|Pointeur vers une chaîne de caractères ( **`wchar_t`** ou **`char`** ) avec le type de caractère opposé comme **`CStringT`** objet.|
|`PCXSTR`|Pointeur vers une **`const`** chaîne de caractères ( **`wchar_t`** ou **`char`** ) avec le même type de caractère que l' **`CStringT`** objet.|
|`PCYSTR`|Pointeur vers une **`const`** chaîne de caractères ( **`wchar_t`** ou **`char`** ) avec le type de caractère opposé comme **`CStringT`** objet.|

> [!NOTE]
> Le code qui utilisait précédemment des méthodes non documentées de `CString` (telles que `AssignCopy` ) doit être remplacé par du code qui utilise les méthodes documentées suivantes de **`CStringT`** (telles que `GetBuffer` ou `ReleaseBuffer` ). Ces méthodes sont héritées de `CSimpleStringT` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

**`CStringT`**

## <a name="requirements"></a>Spécifications

|En-tête|Utilisée pour|
|------------|-------------|
|CStringT. h|Objets String MFC uniquement|
|atlstr. h|Objets String non MFC|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a> `CStringT::AllocSysString`

Alloue une chaîne compatible Automation du type `BSTR` et y copie le contenu de l' **`CStringT`** objet, y compris le caractère null de fin.

```cpp
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne qui vient d’être allouée.

### <a name="remarks"></a>Remarques

Dans les programmes MFC, une [classe CMemoryException](../../mfc/reference/cmemoryexception-class.md) est levée si la mémoire disponible est insuffisante. Dans les programmes ATL, une [CAtlException](../../atl/reference/catlexception-class.md) est levée. Cette fonction est généralement utilisée pour retourner des chaînes pour l’automatisation.

En règle générale, si cette chaîne est passée à une fonction COM en tant que `[in]` paramètre, l’appelant doit libérer la chaîne. Pour ce faire, vous pouvez utiliser [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), comme décrit dans la SDK Windows. Pour plus d’informations, consultez [allocation et libération de mémoire pour un BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Pour plus d’informations sur les fonctions d’allocation OLE dans Windows, consultez [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) dans la SDK Windows.

### <a name="example"></a> Exemple

L'exemple suivant montre l'utilisation de `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a> `CStringT::AnsiToOem`

Convertit tous les caractères de cet **`CStringT`** objet du jeu de caractères ANSI en jeu de caractères OEM.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Remarques

La fonction n’est pas disponible si `_UNICODE` est défini.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a> `CStringT::AppendFormat`

Ajoute des données mises en forme à un **`CStringT`** objet existant.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Paramètres

*`pszFormat`*\
Chaîne de contrôle de format.

*`nFormatID`*\
Identificateur de ressource de chaîne qui contient la chaîne de contrôle de format.

*`argument`*\
Arguments facultatifs.

### <a name="remarks"></a>Remarques

Cette fonction met en forme et ajoute une série de caractères et de valeurs dans le **`CStringT`** . Chaque argument facultatif (le cas échéant) est converti et ajouté conformément à la spécification de format correspondante dans *`pszFormat`* ou à partir de la ressource de chaîne identifiée par *`nFormatID`* .

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a> `CStringT::Collate`

Compare deux chaînes à l’aide de la fonction de texte générique `_tcscoll` .

```cpp
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*`psz`*\
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur renvoyée

Zéro si les chaînes sont identiques, < 0 si cet **`CStringT`** objet est inférieur à *`psz`* , ou > 0 si cet **`CStringT`** objet est supérieur à *`psz`* .

### <a name="remarks"></a>Remarques

La fonction de texte générique `_tcscoll` , qui est définie dans Tchar. H, est mappé à `strcoll` , `wcscoll` ou `_mbscoll` , selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison sensible à la casse des chaînes en fonction de la page de codes en cours d’utilisation. Pour plus d’informations, consultez [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a> `CStringT::CollateNoCase`

Compare deux chaînes à l’aide de la fonction de texte générique `_tcscoll` .

```cpp
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*`psz`*\
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur renvoyée

Zéro si les chaînes sont identiques (casse ignorée), < 0 si cet **`CStringT`** objet est inférieur à *`psz`* (casse ignorée), ou > 0 si cet **`CStringT`** objet est supérieur à *`psz`* (casse ignorée).

### <a name="remarks"></a>Remarques

La fonction de texte générique `_tcscoll` , qui est définie dans Tchar. H, est mappé à `stricoll` , `wcsicoll` ou `_mbsicoll` , selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison ne respectant pas la casse des chaînes, en fonction de la page de codes en cours d’utilisation. Pour plus d’informations, consultez [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a> `CStringT::Compare`

Compare deux chaînes (respect de la casse).

```cpp
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Paramètres

*`psz`*\
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur renvoyée

Zéro si les chaînes sont identiques, < 0 si cet **`CStringT`** objet est inférieur à *`psz`* , ou > 0 si cet **`CStringT`** objet est supérieur à *`psz`* .

### <a name="remarks"></a>Remarques

La fonction de texte générique `_tcscmp` , qui est définie dans Tchar. H, est mappé à `strcmp` , `wcscmp` ou `_mbscmp` , selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison sensible à la casse des chaînes et n’est pas affectée par les paramètres régionaux. Pour plus d’informations, consultez [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Si la chaîne contient des valeurs NULL incorporées, à des fins de comparaison, la chaîne est considérée comme tronquée au premier caractère null incorporé.

### <a name="example"></a> Exemple

L'exemple suivant montre l'utilisation de `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a> `CStringT::CompareNoCase`

Compare deux chaînes (non-respect de la casse).

```cpp
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*`psz`*\
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur renvoyée

Zéro si les chaînes sont identiques (casse ignorée), <0 si cet **`CStringT`** objet est inférieur à *`psz`* (casse ignorée), ou >0 si cet **`CStringT`** objet est supérieur à *`psz`* (casse ignorée).

### <a name="remarks"></a>Remarques

La fonction de texte générique `_tcsicmp` , qui est définie dans Tchar. H, correspond à `_stricmp` , `_wcsicmp` ou `_mbsicmp` , selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison ne respectant pas la casse des chaînes. La comparaison dépend de l’aspect LC_CTYPE des paramètres régionaux, mais pas LC_COLLATE. Pour plus d’informations, consultez [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a> `CStringT::CStringT`

Construit un **`CStringT`** objet.

```cpp
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>Paramètres

*`pch`*\
Pointeur vers un tableau de caractères de longueur *nLength*, non terminé par le caractère null.

*`nLength`*\
Nombre de caractères dans *PCH*.

*`ch`*\
Caractère unique.

*`pszSrc`*\
Chaîne terminée par le caractère null à copier dans cet **`CStringT`** objet.

*`pStringMgr`*\
Pointeur vers le gestionnaire de mémoire de l' **`CStringT`** objet. Pour plus d’informations sur et sur la `IAtlStringMgr` gestion de la mémoire pour **`CStringT`** , consultez Gestion de la [mémoire avec CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*`strSrc`*\
Objet existant **`CStringT`** à copier dans cet **`CStringT`** objet. Pour plus d’informations sur `CThisString` et `CThisSimpleString` , consultez la section Notes.

*`varSrc`*\
Objet variant à copier dans cet **`CStringT`** objet.

*`BaseType`*\
Type de caractère de la classe String. Il peut s'agir d'une des méthodes suivantes :

**`char`** (pour les chaînes de caractères ANSI).

**`wchar_t`** (pour les chaînes de caractères Unicode).

`TCHAR` (pour les chaînes de caractères ANSI et Unicode).

*`bMFCDLL`*\
Valeur booléenne qui spécifie si le projet est une DLL MFC ( `TRUE` ) ou non ( `FALSE` ).

*`SystemString`*\
Doit être `System::String` , et le projet doit être compilé avec `/clr` .

*`pString`*\
Handle pour un **`CStringT`** objet.

### <a name="remarks"></a>Remarques

Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, des exceptions de mémoire peuvent se produire. Certains de ces constructeurs agissent comme des fonctions de conversion. Cela vous permet de substituer, par exemple, un **`LPTSTR`** où un **`CStringT`** objet est attendu.

- **`CStringT`**( `LPCSTR` `lpsz` ) : Construit un Unicode **`CStringT`** à partir d’une chaîne ANSI. Vous pouvez également utiliser ce constructeur pour charger une ressource de type chaîne comme indiqué dans l’exemple ci-dessous.

- `CStringT(``LPCWSTR` `lpsz` ) : Construit un **`CStringT`** à partir d’une chaîne Unicode.

- **`CStringT`**( `const unsigned char*` `psz` ) : Vous permet de construire un **`CStringT`** à partir d’un pointeur vers **`unsigned char`** .

> [!NOTE]
> Définissez la `_CSTRING_DISABLE_NARROW_WIDE_CONVERSION` macro pour désactiver la conversion de chaînes implicite entre les chaînes ANSI et Unicode. La macro exclut des constructeurs de compilation qui prennent en charge la conversion.

Le *`strSrc`* paramètre peut être un **`CStringT`** objet ou `CThisSimpleString` . Pour **`CStringT`** , utilisez l’une de ses instanciations par défaut ( `CString` , `CStringA` ou `CStringW` ); pour `CThisSimpleString` , utilisez un **`this`** pointeur. `CThisSimpleString` déclare une instance de la [classe CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), qui est une classe de chaîne plus petite avec des fonctionnalités moins intégrées que la **`CStringT`** classe.

L’opérateur `CSimpleStringT<>&()` de surcharge construit un **`CStringT`** objet à partir d’une `CSimpleStringT` déclaration.

> [!NOTE]
> Bien qu’il soit possible de créer **`CStringT`** des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et d’opérateurs sur des **`CStringT`** objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a> `CStringT::~CStringT`

Détruit l' **`CStringT`** objet.

```cpp
~CStringT() throw();
```

### <a name="remarks"></a>Remarques

Détruit l' **`CStringT`** objet.

## <a name="cstringtdelete"></a><a name="delete"></a> `CStringT::Delete`

Supprime un ou des caractères d’une chaîne commençant par le caractère à l’index donné.

```cpp
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Paramètres

*`iIndex`*\
Index de base zéro du premier caractère de l' **`CStringT`** objet à supprimer.

*`nCount`*\
Nombre de caractères à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Longueur de la chaîne modifiée.

### <a name="remarks"></a>Remarques

Si *`nCount`* est plus long que la chaîne, le reste de la chaîne sera supprimé.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a> `CStringT::Find`

Recherche la première correspondance d’un caractère ou d’une sous-chaîne dans cette chaîne.

```cpp
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Paramètres

*`pszSub`*\
Sous-chaîne à rechercher.

*`iStart`*\
Index du caractère dans la chaîne à partir duquel commencer la recherche, ou 0 pour démarrer à partir du début.

*`ch`*\
Caractère unique à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro du premier caractère de cet **`CStringT`** objet qui correspond à la sous-chaîne ou aux caractères demandés ;-1 si la sous-chaîne ou le caractère est introuvable.

### <a name="remarks"></a>Remarques

La fonction est surchargée pour accepter les deux caractères uniques (similaires à la fonction runtime `strchr` ) et les chaînes (similaires à `strstr` ).

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a> `CStringT::FindOneOf`

Recherche dans cette chaîne le premier caractère qui correspond à n’importe quel caractère contenu dans *`pszCharSet`* .

```cpp
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Paramètres

*`pszCharSet`*\
Chaîne contenant des caractères pour la correspondance.

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro du premier caractère de cette chaîne qui se trouve également dans *`pszCharSet`* ;-1 s’il n’y a aucune correspondance.

### <a name="remarks"></a>Remarques

Recherche la première occurrence de l’un des caractères de *`pszCharSet`* .

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a> `CStringT::Format`

Écrit des données mises en forme dans un **`CStringT`** de la même façon que [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) met en forme les données dans un tableau de caractères de style C.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Paramètres

*`nFormatID`*\
Identificateur de ressource de chaîne qui contient la chaîne de contrôle de format.

*`pszFormat`*\
Chaîne de contrôle de format.

*`argument`*\
Arguments facultatifs.

### <a name="remarks"></a>Remarques

Cette fonction met en forme et stocke une série de caractères et de valeurs dans le **`CStringT`** . Chaque argument facultatif (le cas échéant) est converti et sorti selon la spécification de format correspondante dans *`pszFormat`* ou à partir de la ressource de chaîne identifiée par *`nFormatID`* .

L’appel échoue si l’objet String lui-même est proposé en tant que paramètre à `Format` . Par exemple, le code suivant génère des résultats imprévisibles :

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Pour plus d’informations, consultez [Syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a> `CStringT::FormatMessage`

Met en forme une chaîne de message.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Paramètres

*`nFormatID`*\
Identificateur de ressource de chaîne qui contient le texte de message sans mise en forme.

*`pszFormat`*\
Pointe vers la chaîne de contrôle de format. Les insertions et les mises en forme sont analysées en conséquence. La chaîne de format est semblable aux chaînes de format de style *printf* de la fonction runtime, sauf qu’elle permet l’insertion des paramètres dans un ordre arbitraire.

*`argument`*\
Arguments facultatifs.

### <a name="remarks"></a>Remarques

La fonction requiert une définition de message comme entrée. La définition du message est déterminée par *`pszFormat`* ou à partir de la ressource de type chaîne identifiée par *`nFormatID`* . La fonction copie le texte du message mis en forme dans l' **`CStringT`** objet, en traitant toutes les séquences d’insertion incorporées si nécessaire.

> [!NOTE]
> `FormatMessage` tente d’allouer de la mémoire système pour la chaîne mise en forme récemment. Si cette tentative échoue, une exception de mémoire est automatiquement levée.

Chaque instruction INSERT doit avoir un paramètre correspondant à la suite du *`pszFormat`* *`nFormatID`* paramètre ou. Dans le texte du message, plusieurs séquences d’échappement sont prises en charge pour la mise en forme dynamique du message. Pour plus d’informations, consultez la fonction [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows dans le SDK Windows.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a> `CStringT::FormatMessageV`

Met en forme une chaîne de message à l’aide d’une liste d’arguments de variables.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Paramètres

*`pszFormat`*\
Pointe vers la chaîne de contrôle de format. Les insertions et les mises en forme sont analysées en conséquence. La chaîne de format est semblable aux chaînes de format de style fonction d’exécution `printf` , sauf qu’elle permet l’insertion des paramètres dans un ordre arbitraire.

*`pArgList`*\
Pointeur désignant une liste d’arguments.

### <a name="remarks"></a>Remarques

La fonction requiert une définition de message comme entrée, déterminée par *`pszFormat`* . La fonction copie le texte du message mis en forme et une liste variable d’arguments vers l' **`CStringT`** objet, en traitant toutes les séquences d’insertion incorporées, le cas échéant.

> [!NOTE]
> `FormatMessageV` appelle [CStringT :: FormatMessage](#formatmessage), qui tente d’allouer de la mémoire système pour la chaîne mise en forme récemment. Si cette tentative échoue, une exception de mémoire est automatiquement levée.

Pour plus d’informations, consultez la fonction [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows dans le SDK Windows.

## <a name="cstringtformatv"></a><a name="formatv"></a> `CStringT::FormatV`

Met en forme une chaîne de message à l’aide d’une liste d’arguments de variables.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Paramètres

*`pszFormat`*\
Pointe vers la chaîne de contrôle de format. Les insertions et les mises en forme sont analysées en conséquence. La chaîne de format est semblable aux chaînes de format de style fonction d’exécution `printf` , sauf qu’elle permet l’insertion des paramètres dans un ordre arbitraire.

*`args`*\
Pointeur désignant une liste d’arguments.

### <a name="remarks"></a>Remarques

Écrit une chaîne mise en forme et une liste variable d’arguments dans une **`CStringT`** chaîne de la même façon que `vsprintf_s` met en forme les données dans un tableau de caractères de style C.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a> `CStringT::GetEnvironmentVariable`

Affecte à la chaîne la valeur de la variable d’environnement spécifiée.

```cpp
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Paramètres

*`pszVar`*\
Pointeur vers une chaîne se terminant par un caractère null qui spécifie la variable d’environnement.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Remarques

Récupère la valeur de la variable spécifiée à partir du bloc d’environnement du processus appelant. La valeur est sous la forme d’une chaîne de caractères se terminant par un caractère null.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a> `CStringT::Insert`

Insère un caractère unique ou une sous-chaîne à l’index donné dans la chaîne.

```cpp
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Paramètres

*`iIndex`*\
Index du caractère avant lequel l’insertion doit avoir lieu.

*`psz`*\
Pointeur vers la sous-chaîne à insérer.

*`ch`*\
Caractère à insérer.

### <a name="return-value"></a>Valeur renvoyée

Longueur de la chaîne modifiée.

### <a name="remarks"></a>Remarques

Le *`iIndex`* paramètre identifie le premier caractère qui sera déplacé pour faire de la place pour le caractère ou la sous-chaîne. Si *nIndex* est égal à zéro, l’insertion se produit avant la chaîne entière. Si *nIndex* est supérieur à la longueur de la chaîne, la fonction concatène la chaîne présente et le nouveau matériel fourni par *`ch`* ou *`psz`* .

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a> `CStringT::Left`

Extrait les caractères les plus *`nCount`* à gauche de cet **`CStringT`** objet et retourne une copie de la sous-chaîne extraite.

```cpp
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Paramètres

*`nCount`*\
Nombre de caractères à extraire de cet **`CStringT`** objet.

### <a name="return-value"></a>Valeur renvoyée

**`CStringT`** Objet qui contient une copie de la plage de caractères spécifiée. L' **`CStringT`** objet retourné peut être vide.

### <a name="remarks"></a>Remarques

Si est *`nCount`* supérieur à la longueur de chaîne, la totalité de la chaîne est extraite. `Left` est similaire à la fonction de base `Left`.

Pour les jeux de caractères multioctets (MBCS), *`nCount`* traite chaque séquence de 8 bits comme un caractère, de sorte que *`nCount`* retourne le nombre de caractères multioctets multiplié par deux.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a> `CStringT::LoadString`

Lit une ressource de chaîne Windows, identifiée par *nid*, dans un **`CStringT`** objet existant.

```cpp
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Paramètres

*`hInstance`*\
Handle de l’instance du module.

*`nID`*\
ID de ressource de chaîne Windows.

*`wLanguageID`*\
Langage de la ressource de type chaîne.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le chargement de la ressource a réussi ; Sinon, 0.

### <a name="remarks"></a>Remarques

Charge la ressource de chaîne (*nid*) à partir du module spécifié (*HINSTANCE*) à l’aide du langage spécifié (*wLanguage*).

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a> `CStringT::MakeLower`

Convertit l' **`CStringT`** objet en chaîne minuscule.

```cpp
CStringT& MakeLower();
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne en minuscules résultante.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a> `CStringT::MakeReverse`

Inverse l’ordre des caractères dans l' **`CStringT`** objet.

```cpp
CStringT& MakeReverse();
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne inversée résultante.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a> `CStringT::MakeUpper`

Convertit l' **`CStringT`** objet en une chaîne en majuscules.

```cpp
CStringT& MakeUpper();
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne en majuscules résultante.

### <a name="remarks"></a>Remarques

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a> `CStringT::Mid`

Extrait une sous-chaîne de caractères de longueur *`nCount`* à partir de cet **`CStringT`** objet, en commençant à la position *`iFirst`* (de base zéro).

```cpp
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Paramètres

*`iFirst`*\
Index de base zéro du premier caractère de cet **`CStringT`** objet à inclure dans la sous-chaîne extraite.

*`nCount`*\
Nombre de caractères à extraire de cet **`CStringT`** objet. Si ce paramètre n’est pas fourni, le reste de la chaîne est extrait.

### <a name="return-value"></a>Valeur renvoyée

**`CStringT`** Objet qui contient une copie de la plage de caractères spécifiée. L' **`CStringT`** objet retourné peut être vide.

### <a name="remarks"></a>Remarques

La fonction retourne une copie de la sous-chaîne extraite. `Mid` est similaire à la fonction Mid de base (à ceci près que les index de base sont de base un).

Pour les jeux de caractères multioctets (MBCS), *`nCount`* fait référence à chaque caractère 8 bits ; autrement dit, un octet de tête et de fin dans un caractère multioctet est compté comme deux caractères.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a> `CStringT::OemToAnsi`

Convertit tous les caractères de cet **`CStringT`** objet du jeu de caractères OEM en jeu de caractères ANSI.

```cppcpp
void OemToAnsi();
```

### <a name="remarks"></a>Remarques

Cette fonction n’est pas disponible si `_UNICODE` est défini.

### <a name="example"></a> Exemple

Consultez l’exemple pour [CStringT :: AnsiToOem](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a> `CStringT::operator =`

Assigne une nouvelle valeur à la chaîne.

```cpp
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);
CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>Paramètres

*`strSrc`*\
**`CStringT`** À assigner à cette chaîne.

*`str`*\
Référence à un objet `CThisSimpleString`.

*`bMFCDLL`*\
Valeur booléenne qui spécifie si le projet est une DLL MFC ou non.

*`BaseType`*\
Type de base de la chaîne.

*`var`*\
Objet variant à assigner à cette chaîne.

*`ch`*\
Caractère ANSI ou Unicode à assigner à la chaîne.

*`pszSrc`*\
Pointeur vers la chaîne d’origine qui est assignée.

### <a name="remarks"></a>Remarques

L’opérateur d’assignation accepte un autre **`CStringT`** objet, un pointeur de caractère ou un caractère unique. Des exceptions de mémoire peuvent se produire chaque fois que vous utilisez cet opérateur, car un nouveau stockage peut être alloué.

Pour plus d’informations sur `CThisSimpleString` , consultez la section Notes de [CStringT :: CStringT](#cstringt).

> [!NOTE]
> Bien qu’il soit possible de créer **`CStringT`** des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et d’opérateurs sur des **`CStringT`** objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

## <a name="cstringtoperator-"></a><a name="operator_add"></a> `CStringT::operator +`

Concatène deux chaînes ou un caractère et une chaîne.

```cpp
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>Paramètres

*`ch1`*\
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*`ch2`*\
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*`str1`*\
**`CStringT`** À concaténer avec une chaîne ou un caractère.

*`str2`*\
**`CStringT`** À concaténer avec une chaîne ou un caractère.

*`psz1`*\
Pointeur vers une chaîne se terminant par null à concaténer avec une chaîne ou un caractère.

*`psz2`*\
Pointeur vers une chaîne à concaténer avec une chaîne ou un caractère.

### <a name="remarks"></a>Remarques

Il existe sept formes surchargées de la `CStringT::operator+` fonction. La première version concatène deux objets existants **`CStringT`** . Les deux suivants concatènent un **`CStringT`** objet et une chaîne terminée par le caractère null. Les deux suivants concatènent un **`CStringT`** objet et un caractère ANSI. Les deux derniers concatènent un **`CStringT`** objet et un caractère Unicode.

> [!NOTE]
> Bien qu’il soit possible de créer **`CStringT`** des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et d’opérateurs sur des **`CStringT`** objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a> `CStringT::operator +=`

Concatène les caractères à la fin de la chaîne.

```cpp
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>Paramètres

*`str`*\
Référence à un objet `CThisSimpleString`.

*`bMFCDLL`*\
Valeur booléenne qui spécifie si le projet est une DLL MFC ou non.

*`BaseType`*\
Type de base de la chaîne.

*`var`*\
Objet variant à concaténer à cette chaîne.

*`ch`*\
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*`pszSrc`*\
Pointeur vers la chaîne d’origine qui est concaténée.

*`strSrc`*\
**`CStringT`** À concaténer à cette chaîne.

### <a name="remarks"></a>Remarques

L’opérateur accepte un autre **`CStringT`** objet, un pointeur de caractère ou un caractère unique. Des exceptions de mémoire peuvent se produire chaque fois que vous utilisez cet opérateur de concaténation, car un nouveau stockage peut être alloué pour les caractères ajoutés à cet **`CStringT`** objet.

Pour plus d’informations sur `CThisSimpleString` , consultez la section Notes de [CStringT :: CStringT](#cstringt).

> [!NOTE]
> Bien qu’il soit possible de créer **`CStringT`** des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et d’opérateurs sur des **`CStringT`** objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a> `CStringT::operator ==`

Détermine si deux chaînes sont logiquement égales.

```cpp
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Paramètres

*`ch1`*\
Caractère ANSI ou Unicode pour la comparaison.

*`ch2`*\
Caractère ANSI ou Unicode pour la comparaison.

*`str1`*\
**`CStringT`** À des fins de comparaison.

*`str2`*\
**`CStringT`** À des fins de comparaison.

*`psz1`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

*`psz2`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Remarques

Teste si une chaîne ou un caractère sur le côté gauche est égal à une chaîne ou un caractère situé à droite, et retourne `TRUE` ou en `FALSE` conséquence.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a> `CStringT::operator !=`

Détermine si deux chaînes sont logiquement inégales.

```cpp
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Paramètres

*`ch1`*\
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*`ch2`*\
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*`str1`*\
**`CStringT`** À des fins de comparaison.

*`str2`*\
**`CStringT`** À des fins de comparaison.

*`psz1`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

*`psz2`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Remarques

Teste si une chaîne ou un caractère situé à gauche n’est pas égal à une chaîne ou un caractère situé à droite.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt"></a> `CStringT::operator <`

Détermine si la chaîne située à gauche de l’opérateur est inférieure à la chaîne sur le côté droit.

```cpp
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*`str1`*\
**`CStringT`** À des fins de comparaison.

*`str2`*\
**`CStringT`** À des fins de comparaison.

*`psz1`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

*`psz2`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Remarques

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt"></a> `CStringT::operator >`

Détermine si la chaîne située à gauche de l’opérateur est supérieure à la chaîne située à droite.

```cpp
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*`str1`*\
**`CStringT`** À des fins de comparaison.

*`str2`*\
**`CStringT`** À des fins de comparaison.

*`psz1`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

*`psz2`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Remarques

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt_eq"></a> `CStringT::operator <=`

Détermine si la chaîne située à gauche de l’opérateur est inférieure ou égale à la chaîne située à droite.

```cpp
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*`str1`*\
**`CStringT`** À des fins de comparaison.

*`str2`*\
**`CStringT`** À des fins de comparaison.

*`psz1`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

*`psz2`*\
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Remarques

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt_eq"></a> `CStringT::operator >=`

Détermine si la chaîne située à gauche de l’opérateur est supérieure ou égale à la chaîne située à droite.

```cpp
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*`str1`*\
**`CStringT`** À des fins de comparaison.

*`str2`*\
**`CStringT`** À des fins de comparaison.

*`psz1`*\
Pointeur vers une chaîne à comparer.

*`psz2`*\
Pointeur vers une chaîne à comparer.

### <a name="remarks"></a>Remarques

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a> `CStringT::Remove`

Supprime toutes les instances du caractère spécifié de la chaîne.

```cpp
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Paramètres

*`chRemove`*\
Caractère à supprimer d’une chaîne.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères supprimés de la chaîne. Zéro si la chaîne n’est pas modifiée.

### <a name="remarks"></a>Remarques

Les comparaisons pour le caractère respectent la casse.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a> `CStringT::Replace`

Il existe deux versions de `Replace` . La première version remplace une ou plusieurs copies d’une sous-chaîne à l’aide d’une autre sous-chaîne. Les deux sous-chaînes se terminent par un caractère null. La deuxième version remplace une ou plusieurs copies d’un caractère à l’aide d’un autre caractère. Les deux versions fonctionnent sur les données caractères stockées dans **`CStringT`** .

```cpp
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Paramètres

*`pszOld`*\
Pointeur vers une chaîne se terminant par null à remplacer par *`pszNew`* .

*`pszNew`*\
Pointeur vers une chaîne terminée par le caractère null qui remplace *`pszOld`* .

*`chOld`*\
Caractère à remplacer par *`chNew`* .

*`chNew`*\
Caractère qui remplace *`chOld`* .

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’instances remplacées du caractère ou de la sous-chaîne, ou zéro si la chaîne n’est pas modifiée.

### <a name="remarks"></a>Remarques

`Replace` peut modifier la longueur de chaîne car *`pszNew`* et *`pszOld`* n’a pas besoin d’être de la même longueur, et plusieurs copies de l’ancienne sous-chaîne peuvent être remplacées par la nouvelle. La fonction effectue une correspondance respectant la casse.

, Et sont des exemples d' **`CStringT`** instances `CString` `CStringA` `CStringW` .

Pour `CStringA` , `Replace` fonctionne avec des caractères ANSI ou multioctets (MBCS). Pour `CStringW` , `Replace` fonctionne avec des caractères larges.

Pour `CString` , le type de données character est sélectionné au moment de la compilation, selon que les constantes dans le tableau suivant sont définies ou non.

|Constante définie|Type de données character|
|----------------------|-------------------------|
|`_UNICODE`|Caractères larges|
|`_MBCS`|Caractères multioctets|
|Aucun|Caractères codés sur un octet|
|Les deux|Indéfini|

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a> `CStringT::ReverseFind`

Recherche **`CStringT`** la dernière correspondance d’un caractère dans cet objet.

```cpp
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Paramètres

*`ch`*\
Caractère à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro du dernier caractère de cet **`CStringT`** objet qui correspond au caractère demandé, ou-1 si le caractère est introuvable.

### <a name="remarks"></a>Remarques

La fonction est similaire à la fonction runtime `strrchr` .

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a> `CStringT::Right`

Extrait les derniers caractères (c’est-à-dire, les plus à droite) *`nCount`* à partir de cet **`CStringT`** objet et retourne une copie de la sous-chaîne extraite.

```cpp
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Paramètres

*`nCount`*\
Nombre de caractères à extraire de cet **`CStringT`** objet.

### <a name="return-value"></a>Valeur renvoyée

**`CStringT`** Objet qui contient une copie de la plage de caractères spécifiée. L' **`CStringT`** objet retourné peut être vide.

### <a name="remarks"></a>Remarques

Si est *`nCount`* supérieur à la longueur de chaîne, la totalité de la chaîne est extraite. `Right` est similaire à la fonction de base `Right` (à ceci près que les index de base sont de base zéro).

Pour les jeux de caractères multioctets (MBCS), *`nCount`* fait référence à chaque caractère 8 bits ; autrement dit, un octet de tête et de fin dans un caractère multioctet est compté comme deux caractères.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a> `CStringT::SetSysString`

Réalloue le **`BSTR`** pointé vers *`pbstr`* et y copie le contenu de l' **`CStringT`** objet, y compris le caractère null.

```cpp
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Paramètres

*`pbstr`*\
Pointeur vers une chaîne de caractères.

### <a name="return-value"></a>Valeur renvoyée

La nouvelle chaîne.

### <a name="remarks"></a>Remarques

En fonction du contenu de l' **`CStringT`** objet, la valeur de l’objet **`BSTR`** référencé par *`pbstr`* peut changer. La fonction lève une si la mémoire disponible est `CMemoryException` insuffisante.

Cette fonction est généralement utilisée pour modifier la valeur des chaînes passées par référence pour Automation.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a> `CStringT::SpanExcluding`

Extrait des caractères de la chaîne, en commençant par le premier caractère, qui ne se trouvent pas dans le jeu de caractères identifié par *`pszCharSet`* .

```cpp
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Paramètres

*`pszCharSet`*\
Chaîne interprétée comme un jeu de caractères.

### <a name="return-value"></a>Valeur renvoyée

Sous-chaîne qui contient les caractères de la chaîne qui ne se trouvent pas dans *`pszCharSet`* , commençant par le premier caractère de la chaîne et se terminant par le premier caractère trouvé dans la chaîne qui se trouve également dans *`pszCharSet`* (autrement dit, en commençant par le premier caractère de la chaîne et en excluant le premier caractère de la chaîne trouvée *`pszCharSet`* ). Elle retourne la chaîne entière si aucun caractère dans *`pszCharSet`* n’est trouvé dans la chaîne.

### <a name="remarks"></a>Remarques

`SpanExcluding` extrait et retourne tous les caractères qui précèdent la première occurrence d’un caractère de *`pszCharSet`* (en d’autres termes, le caractère de *`pszCharSet`* et tous les caractères qui le suivent dans la chaîne ne sont pas retournés). Si aucun caractère de *`pszCharSet`* n’est trouvé dans la chaîne, `SpanExcluding` retourne la chaîne entière.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a> `CStringT::SpanIncluding`

Extrait des caractères de la chaîne, en commençant par le premier caractère, qui se trouvent dans le jeu de caractères identifié par *`pszCharSet`* .

```cpp
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Paramètres

*`pszCharSet`*\
Chaîne interprétée comme un jeu de caractères.

### <a name="return-value"></a>Valeur renvoyée

Sous-chaîne qui contient les caractères de la chaîne qui se trouvent dans *`pszCharSet`* , commençant par le premier caractère de la chaîne et se terminant lorsqu’un caractère se trouve dans la chaîne qui n’est pas dans *`pszCharSet`* . `SpanIncluding` retourne une sous-chaîne vide si le premier caractère de la chaîne ne figure pas dans le jeu spécifié.

### <a name="remarks"></a>Remarques

Si le premier caractère de la chaîne ne figure pas dans le jeu de caractères, `SpanIncluding` retourne une chaîne vide. Sinon, elle retourne une séquence de caractères consécutifs qui se trouvent dans le jeu.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a> `CStringT::Tokenize`

Recherche le jeton suivant dans une chaîne cible

```cpp
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Paramètres

*`pszTokens`*\
Chaîne contenant des délimiteurs de jetons. L’ordre de ces délimiteurs n’est pas important.

*`iStart`*\
Index de base zéro à partir duquel commencer la recherche.

### <a name="return-value"></a>Valeur renvoyée

**`CStringT`** Objet contenant la valeur de jeton actuelle.

### <a name="remarks"></a>Remarques

La `Tokenize` fonction recherche le jeton suivant dans la chaîne cible. Le jeu de caractères dans *pszTokens* spécifie les délimiteurs possibles du jeton à trouver. À chaque appel à `Tokenize` la fonction démarre à *`iStart`* , ignore les délimiteurs de début et retourne un **`CStringT`** objet contenant le jeton actuel, qui est la chaîne de caractères jusqu’au caractère délimiteur suivant. La valeur de *`iStart`* est mise à jour pour correspondre à la position qui suit le caractère délimiteur de fin, ou-1 si la fin de la chaîne a été atteinte. Un plus grand nombre de jetons peuvent être décomposés du reste de la chaîne cible par une série d’appels à `Tokenize` , à l’aide *`iStart`* de pour effectuer le suivi de l’emplacement où le jeton suivant doit être lu dans la chaîne. Lorsqu’il n’y a plus de jetons, la fonction retourne une chaîne vide et *`iStart`* prend la valeur-1.

Contrairement aux fonctions de jeton CRT [`strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l`](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md) , comme, `Tokenize` ne modifie pas la chaîne cible.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

La sortie de cet exemple est la suivante :

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a> `CStringT::Trim`

Supprime les caractères de début et de fin de la chaîne.

```cpp
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Paramètres

*`chTarget`*\
Caractère cible à tronquer.

*`pszTargets`*\
Pointeur vers une chaîne contenant les caractères cibles à tronquer. Toutes les occurrences de début et de fin des caractères dans *`pszTargets`* seront supprimées de l' **`CStringT`** objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne la chaîne tronquée.

### <a name="remarks"></a>Remarques

Supprime toutes les occurrences de début et de fin de l’un des éléments suivants :

- Caractère spécifié par *`chTarget`* .

- Tous les caractères trouvés dans la chaîne spécifiée par *`pszTargets`* .

- Situés.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

La sortie de cet exemple est la suivante :

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a> `CStringT::TrimLeft`

Supprime les caractères de début de la chaîne.

```cpp
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Paramètres

*`chTarget`*\
Caractère cible à tronquer.

*`pszTargets`*\
Pointeur vers une chaîne contenant les caractères cibles à tronquer. Toutes les occurrences de début de caractères dans *`pszTargets`* seront supprimées de l' **`CStringT`** objet.

### <a name="return-value"></a>Valeur renvoyée

Chaîne tronquée résultante.

### <a name="remarks"></a>Remarques

Supprime toutes les occurrences de début et de fin de l’un des éléments suivants :

- Caractère spécifié par *`chTarget`* .

- Tous les caractères trouvés dans la chaîne spécifiée par *`pszTargets`* .

- Situés.

### <a name="example"></a> Exemple

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a> `CStringT::TrimRight`

Supprime les caractères de fin de la chaîne.

```cpp
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Paramètres

*`chTarget`*\
Caractère cible à tronquer.

*`pszTargets`*\
Pointeur vers une chaîne contenant les caractères cibles à tronquer. Toutes les occurrences de fin de caractères dans *`pszTargets`* seront supprimées de l' **`CStringT`** objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne l' **`CStringT`** objet qui contient la chaîne tronquée.

### <a name="remarks"></a>Remarques

Supprime les occurrences de fin de l’un des éléments suivants :

- Caractère spécifié par *`chTarget`* .

- Tous les caractères trouvés dans la chaîne spécifiée par *`pszTargets`* .

- Situés.

La `CStringT& TrimRight(XCHAR chTarget)` version accepte un paramètre de caractère et supprime toutes les copies de ce caractère de la fin des **`CStringT`** données de chaîne. Elle démarre à partir de la fin de la chaîne et fonctionne vers l’avant. Il s’arrête lorsqu’il trouve un caractère différent ou lorsqu’il manque **`CStringT`** de données de caractères.

La `CStringT& TrimRight(PCXSTR pszTargets)` version accepte une chaîne se terminant par un caractère null qui contient tous les caractères différents à rechercher. Elle supprime toutes les copies de ces caractères dans l' **`CStringT`** objet. Elle commence à la fin de la chaîne et fonctionne vers l’avant. Il s’arrête lorsqu’il trouve un caractère qui n’est pas dans la chaîne cible, ou lorsque **`CStringT`** est en dehors des données de caractères. Elle n’essaie pas de faire correspondre la chaîne cible entière à une sous-chaîne à la fin de **`CStringT`** .

La `CStringT& TrimRight()` version ne nécessite aucun paramètre. Elle supprime tous les espaces blancs de fin de la **`CStringT`** chaîne. Les caractères d’espace blanc peuvent être des sauts de ligne, des espaces ou des tabulations.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)\
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)\
[CSimpleStringT, classe](../../atl-mfc-shared/reference/csimplestringt-class.md)
