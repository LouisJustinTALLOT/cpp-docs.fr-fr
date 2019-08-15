---
title: CStringT (classe)
ms.date: 03/27/2019
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: a411ed54a73a0dee49ebbd9ccacbd7c6f8e69ca5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491639"
---
# <a name="cstringt-class"></a>CStringT (classe)

Cette classe représente un `CStringT` objet.

## <a name="syntax"></a>Syntaxe

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Paramètres

*BaseType*<br/>
Type de caractère de la classe String. Il peut s'agir d'une des valeurs suivantes :

- **caractère** (pour les chaînes de caractères ANSI).

- **wchar_t** (pour les chaînes de caractères Unicode).

- TCHAR (pour les chaînes de caractères ANSI et Unicode).

*StringTraits*<br/>
Détermine si la classe de chaîne a besoin de la prise en charge de la bibliothèque Runtime C (CRT) et de l’emplacement des ressources de type chaîne. Il peut s'agir d'une des valeurs suivantes :

- **StrTraitATL < wchar_t** &#124; **char** &#124; &#124; TCHAR, ChTraitsCRT < wchar_t char TCHAR > > &#124;

   La classe requiert la prise en charge de CRT et recherche des chaînes de ressource `m_hInstResource` dans le module spécifié par (un membre de la classe de module de l’application).

- **StrTraitATL < wchar_t** &#124; **char** &#124; &#124; TCHAR, ChTraitsOS < wchar_t char TCHAR > > &#124;

   La classe ne requiert pas la prise en charge de CRT et recherche des chaînes de ressource `m_hInstResource` dans le module spécifié par (un membre de la classe de module de l’application).

- **StrTraitMFC < wchar_t** &#124; **char** &#124; &#124; TCHAR, ChTraitsCRT < wchar_t char TCHAR > > &#124;

   La classe requiert la prise en charge de CRT et recherche des chaînes de ressources à l’aide de l’algorithme de recherche MFC standard.

- **StrTraitMFC < wchar_t** &#124; **char** &#124; &#124; TCHAR, ChTraitsOS < wchar_t char TCHAR > > &#124;

   La classe ne requiert pas la prise en charge de CRT et recherche des chaînes de ressources à l’aide de l’algorithme de recherche MFC standard.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|Construit un `CStringT` objet de différentes façons.|
|[CStringT::~CStringT](#_dtorcstringt)|Détruit un objet `CStringT`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Alloue un BSTR à partir `CStringT` de données.|
|[CStringT::AnsiToOem](#ansitooem)|Effectue une conversion sur place du jeu de caractères ANSI en jeu de caractères OEM.|
|[CStringT::AppendFormat](#appendformat)|Ajoute des données mises en forme à `CStringT` un objet existant.|
|[CStringT::Collate](#collate)|Compare deux chaînes (respecte la casse, utilise des informations spécifiques aux paramètres régionaux).|
|[CStringT::CollateNoCase](#collatenocase)|Compare deux chaînes (non-respect de la casse, utilise des informations spécifiques aux paramètres régionaux).|
|[CStringT::Compare](#compare)|Compare deux chaînes (respect de la casse).|
|[CStringT::CompareNoCase](#comparenocase)|Compare deux chaînes (non-respect de la casse).|
|[CStringT::Delete](#delete)|Supprime un ou des caractères d’une chaîne.|
|[CStringT::Find](#find)|Recherche un caractère ou une sous-chaîne à l’intérieur d’une chaîne plus grande.|
|[CStringT::FindOneOf](#findoneof)|Recherche le premier caractère correspondant dans un ensemble.|
|[CStringT::Format](#format)|Met en forme la `sprintf` chaîne comme c’est le cas.|
|[CStringT::FormatMessage](#formatmessage)|Met en forme une chaîne de message.|
|[CStringT::FormatMessageV](#formatmessagev)|Met en forme une chaîne de message à l’aide d’une liste d’arguments de variables.|
|[CStringT::FormatV](#formatv)|Met en forme la chaîne à l’aide d’une liste variable d’arguments.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Affecte à la chaîne la valeur de la variable d’environnement spécifiée.|
|[CStringT::Insert](#insert)|Insère un caractère unique ou une sous-chaîne à l’index donné dans la chaîne.|
|[CStringT::Left](#left)|Extrait la partie gauche d’une chaîne.|
|[CStringT::LoadString](#loadstring)|Charge un objet `CStringT` existant à partir d’une ressource Windows.|
|[CStringT::MakeLower](#makelower)|Convertit tous les caractères de cette chaîne en caractères minuscules.|
|[CStringT::MakeReverse](#makereverse)|Inverse la chaîne.|
|[CStringT::MakeUpper](#makeupper)|Convertit tous les caractères de cette chaîne en caractères majuscules.|
|[CStringT::Mid](#mid)|Extrait la partie centrale d’une chaîne.|
|[CStringT::OemToAnsi](#oemtoansi)|Effectue une conversion sur place du jeu de caractères OEM en jeu de caractères ANSI.|
|[CStringT::Remove](#remove)|Supprime les caractères indiqués d’une chaîne.|
|[CStringT::Replace](#replace)|Remplace les caractères indiqués par d’autres caractères.|
|[CStringT::ReverseFind](#reversefind)|Recherche un caractère dans une chaîne plus grande; démarre à partir de la fin.|
|[CStringT::Right](#right)|Extrait la partie droite d’une chaîne.|
|[CStringT::SetSysString](#setsysstring)|Définit un objet BSTR existant avec les données d' `CStringT` un objet.|
|[CStringT:: SpanExcluding](#spanexcluding)|Extrait des caractères de la chaîne, en commençant par le premier caractère, qui ne figurent pas dans le jeu de caractères `pszCharSet`identifié par.|
|[CStringT::SpanIncluding](#spanincluding)|Extrait une sous-chaîne qui contient uniquement les caractères d’un jeu.|
|[CStringT::Tokenize](#tokenize)|Extrait les jetons spécifiés dans une chaîne cible.|
|[CStringT::Trim](#trim)|Supprime tous les caractères d’espace blanc de début et de fin de la chaîne.|
|[CStringT::TrimLeft](#trimleft)|Supprime les caractères d’espace blanc de début de la chaîne.|
|[CStringT::TrimRight](#trimright)|Supprime les caractères d’espace blanc de fin de la chaîne.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[CStringT::operator =](#operator_eq)|Assigne une nouvelle valeur à un `CStringT` objet.|
|[CStringT:: Operator +](#operator_add)|Concatène deux chaînes ou un caractère et une chaîne.|
|[CStringT:: Operator + =](#operator_add_eq)|Concatène une nouvelle chaîne à la fin d’une chaîne existante.|
|[CStringT::operator ==](#operator_eq_eq)|Détermine si deux chaînes sont logiquement égales.|
|[CStringT:: Operator! =](#operator_neq)|Détermine si deux chaînes sont logiquement inégales.|
|[CStringT:: Operator&lt;](#operator_lt)|Détermine si la chaîne située à gauche de l’opérateur est inférieure à la chaîne sur le côté droit.|
|[CStringT:: Operator&gt;](#operator_gt)|Détermine si la chaîne située à gauche de l’opérateur est supérieure à la chaîne sur le côté droit.|
|[CStringT:: Operator&lt;=](#operator_lt_eq)|Détermine si la chaîne située à gauche de l’opérateur est inférieure ou égale à la chaîne située à droite.|
|[CStringT:: Operator&gt;=](#operator_gt_eq)|Détermine si la chaîne située à gauche de l’opérateur est supérieure ou égale à la chaîne située à droite.|

## <a name="remarks"></a>Notes

`CStringT`hérite de la [classe CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md). Les fonctionnalités avancées, telles que la manipulation de caractères, le classement et la recherche `CStringT`, sont implémentées par.

> [!NOTE]
> `CStringT`les objets peuvent lever des exceptions. Cela se produit lorsqu' `CStringT` un objet manque de mémoire pour une raison quelconque.

Un `CStringT` objet se compose d’une séquence de caractères de longueur variable. `CStringT`fournit des fonctions et des opérateurs à l’aide d’une syntaxe similaire à celle de Basic. Les opérateurs de concaténation et de comparaison, ainsi que la gestion `CStringT` simplifiée de la mémoire, rendent les objets plus faciles à utiliser que les tableaux de caractères ordinaires.

> [!NOTE]
>  Bien qu’il soit possible de `CStringT` créer des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et `CStringT` d’opérateurs sur des objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

En utilisant différentes combinaisons des `BaseType` paramètres et `StringTraits` , `CStringT` les objets peuvent être dans les types suivants, qui ont été prédéfinis par les bibliothèques ATL.

Si vous utilisez dans une application ATL:

`CString`, `CStringA` et`CStringW` sont exportés à partir de la DLL MFC (MFC90. DLL), jamais à partir de DLL utilisateur. Cette opération est effectuée pour `CStringT` empêcher la multiplication de la valeur définie.

> [!NOTE]
>  Si votre code contient la solution de contournement pour les erreurs de l’éditeur de liens qui est décrite dans [exportation de classes de chaînes à l’aide de CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), vous devez supprimer ce code. Il n’est plus nécessaire.

Les types de chaîne suivants sont disponibles dans les applications basées sur MFC:

|CStringT, type|Déclaration|
|-------------------|-----------------|
|`CStringA`|Chaîne de type caractère ANSI avec prise en charge de CRT.|
|`CStringW`|Chaîne de type caractère Unicode avec prise en charge de CRT.|
|`CString`|Types de caractères ANSI et Unicode avec prise en charge de CRT.|

Les types de chaîne suivants sont disponibles dans les projets où ATL_CSTRING_NO_CRT est défini:

|CStringT, type|Déclaration|
|-------------------|-----------------|
|`CAtlStringA`|Chaîne de type caractère ANSI sans prise en charge CRT.|
|`CAtlStringW`|Chaîne de type caractère Unicode sans prise en charge CRT.|
|`CAtlString`|Types de caractères ANSI et Unicode sans prise en charge de CRT.|

Les types de chaîne suivants sont disponibles dans les projets où ATL_CSTRING_NO_CRT n’est pas défini:

|CStringT, type|Déclaration|
|-------------------|-----------------|
|`CAtlStringA`|Chaîne de type caractère ANSI avec prise en charge de CRT.|
|`CAtlStringW`|Chaîne de type caractère Unicode avec prise en charge de CRT.|
|`CAtlString`|Types de caractères ANSI et Unicode avec prise en charge de CRT.|

`CString`les objets présentent également les caractéristiques suivantes:

- `CStringT`les objets peuvent croître à la suite d’opérations de concaténation.

- `CStringT`les objets suivent «sémantique des valeurs». Imaginez un `CStringT` objet comme une chaîne réelle, et non comme un pointeur vers une chaîne.

- Vous pouvez substituer `CStringT` librement des `PCXSTR` objets pour des arguments de fonction.

- Gestion de la mémoire personnalisée pour les mémoires tampons de chaîne. Pour plus d’informations, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Types prédéfinis de CStringT

Étant `CStringT` donné que utilise un argument template pour définir le type de caractère ( [wchar_t](../../c-runtime-library/standard-types.md) ou [char](../../c-runtime-library/standard-types.md)) pris en charge, les types de paramètres de méthode peuvent être compliqués à des moments. Pour simplifier ce problème, un ensemble de types prédéfinis est défini et utilisé dans l' `CStringT` ensemble de la classe. Le tableau suivant répertorie les différents types:

|Nom|Description|
|----------|-----------------|
|`XCHAR`|Caractère unique ( **wchar_t** ou **char**) avec le même type de caractère que l' `CStringT` objet.|
|`YCHAR`|Caractère unique ( **wchar_t** ou **char**) avec le `CStringT` type de caractère opposé comme objet.|
|`PXSTR`|Pointeur vers une chaîne de caractères ( **wchar_t** ou **char**) avec le même type de caractère que l' `CStringT` objet.|
|`PYSTR`|Pointeur vers une chaîne de caractères ( **wchar_t** ou **char**) avec le `CStringT` type de caractère opposé comme objet.|
|`PCXSTR`|Pointeur vers une chaîne de caractères const ( **wchar_t** ou **char**) avec le même type de caractère que l' `CStringT` objet.|
|`PCYSTR`|Pointeur vers une chaîne de caractères const ( **wchar_t** ou **char**) avec le type de caractère `CStringT` opposé comme objet.|

> [!NOTE]
>  Le code qui utilisait précédemment des méthodes non `CString` documentées de `AssignCopy`(telles que) doit être remplacé par du code qui utilise les `CStringT` méthodes documentées suivantes `ReleaseBuffer`de (telles que `GetBuffer` ou). Ces méthodes sont héritées `CSimpleStringT`de.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Configuration requise

|Header|Utilisez pour|
|------------|-------------|
|CStringT. h|Objets String MFC uniquement|
|atlstr.h|Objets String non MFC|

##  <a name="allocsysstring"></a>  CStringT::AllocSysString

Alloue une chaîne compatible Automation du type BSTR et y copie le contenu de l' `CStringT` objet, y compris le caractère null de fin.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne qui vient d’être allouée.

### <a name="remarks"></a>Notes

Dans les programmes MFC, une [classe CMemoryException](../../mfc/reference/cmemoryexception-class.md) est levée si la mémoire disponible est insuffisante. Dans les programmes ATL, une [CAtlException](../../atl/reference/catlexception-class.md) est levée. Cette fonction est généralement utilisée pour retourner des chaînes pour l’automatisation.

En règle générale, si cette chaîne est passée à une fonction COM en tant que paramètre [in], l’appelant doit libérer la chaîne. Pour ce faire, vous pouvez utiliser [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), comme décrit dans la SDK Windows. Pour plus d’informations, consultez [allocation et libération de mémoire pour un BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Pour plus d’informations sur les fonctions d’allocation OLE dans Windows, consultez [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) dans la SDK Windows.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

##  <a name="ansitooem"></a>  CStringT::AnsiToOem

Convertit tous les caractères de `CStringT` cet objet du jeu de caractères ANSI en jeu de caractères OEM.

```
void AnsiToOem();
```

### <a name="remarks"></a>Notes

La fonction n’est pas disponible si _ Unicode est défini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>  CStringT::AppendFormat

Ajoute des données mises en forme à `CStringT` un objet existant.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Chaîne de contrôle de format.

*nFormatID*<br/>
Identificateur de ressource de chaîne qui contient la chaîne de contrôle de format.

*argument*<br/>
Arguments facultatifs.

### <a name="remarks"></a>Notes

Cette fonction met en forme et ajoute une série de caractères et de valeurs `CStringT`dans le. Chaque argument facultatif (le cas échéant) est converti et ajouté conformément à la spécification de format correspondante dans *pszFormat* ou à partir de la ressource de type chaîne identifiée par *nFormatID*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>  CStringT::Collate

Compare deux chaînes à l’aide de la fonction `_tcscoll`de texte générique.

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les chaînes sont identiques, < 0 si cet `CStringT` objet est inférieur à *PSZ*, ou > 0 si cet `CStringT` objet est supérieur à *PSZ*.

### <a name="remarks"></a>Notes

La fonction `_tcscoll`de texte générique, qui est définie dans Tchar. H, est mappé à `strcoll`, `wcscoll`ou `_mbscoll`, selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison qui respecte la casse des chaînes en fonction de la page de codes en cours d’utilisation. Pour plus d’informations, consultez [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

##  <a name="collatenocase"></a>  CStringT::CollateNoCase

Compare deux chaînes à l’aide de la fonction `_tcscoll`de texte générique.

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les chaînes sont identiques (casse ignorée), < 0 si cet `CStringT` objet est inférieur à *PSZ* (casse ignorée), ou > 0 si cet `CStringT` objet est supérieur à *PSZ* (casse ignorée).

### <a name="remarks"></a>Notes

La fonction `_tcscoll`de texte générique, qui est définie dans Tchar. H, est mappé à `stricoll`, `wcsicoll`ou `_mbsicoll`, selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison qui ne respecte pas la casse des chaînes, en fonction de la page de codes en cours d’utilisation. Pour plus d’informations, consultez [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

##  <a name="compare"></a>  CStringT::Compare

Compare deux chaînes (respect de la casse).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les chaînes sont identiques, < 0 si cet `CStringT` objet est inférieur à *PSZ*, ou > 0 si cet `CStringT` objet est supérieur à *PSZ*.

### <a name="remarks"></a>Notes

La fonction `_tcscmp`de texte générique, qui est définie dans Tchar. H, est mappé à `strcmp`, `wcscmp`ou `_mbscmp`, selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison de chaînes respectant la casse et n’est pas affectée par les paramètres régionaux. Pour plus d’informations, consultez [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Si la chaîne contient des valeurs NULL incorporées, à des fins de comparaison, la chaîne est considérée comme tronquée au premier caractère null incorporé.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

##  <a name="comparenocase"></a>  CStringT::CompareNoCase

Compare deux chaînes (non-respect de la casse).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les chaînes sont identiques (casse ignorée), < 0 si cet `CStringT` objet est inférieur à *PSZ* (casse ignorée), ou > 0 si cet `CStringT` objet est supérieur à *PSZ* (casse ignorée).

### <a name="remarks"></a>Notes

La fonction `_tcsicmp`de texte générique, qui est définie dans Tchar. H, correspond à `_stricmp`, `_wcsicmp` ou `_mbsicmp`, selon le jeu de caractères défini au moment de la compilation. Chaque fonction effectue une comparaison qui ne respecte pas la casse des chaînes. La comparaison dépend de l’aspect LC_CTYPE des paramètres régionaux, mais pas de LC_COLLATE. Pour plus d’informations, consultez [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

##  <a name="cstringt"></a>  CStringT::CStringT

Construit un objet `CStringT`.

```
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

*pch*<br/>
Pointeur vers un tableau de caractères de longueur *nLength*, non terminé par le caractère null.

*nLength*<br/>
Nombre de caractères dans *PCH*.

*ch*<br/>
Caractère unique.

*pszSrc*<br/>
Chaîne terminée par le caractère null à copier dans cet `CStringT` objet.

*pStringMgr*<br/>
Pointeur vers le gestionnaire de mémoire de l' `CStringT` objet. Pour plus d’informations `IAtlStringMgr` sur et sur la `CStringT`gestion de la mémoire pour, consultez Gestion de la [mémoire avec CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Objet existant `CStringT` à copier dans cet `CStringT` objet. Pour plus d’informations `CThisString` sur `CThisSimpleString`et, consultez la section Notes.

*varSrc*<br/>
Objet variant à copier dans cet `CStringT` objet.

*BaseType*<br/>
Type de caractère de la classe String. Il peut s'agir d'une des valeurs suivantes :

**caractère** (pour les chaînes de caractères ANSI).

**wchar_t** (pour les chaînes de caractères Unicode).

TCHAR (pour les chaînes de caractères ANSI et Unicode).

*bMFCDLL*<br/>
Valeur booléenne qui spécifie si le projet est une DLL MFC (TRUE) ou non (FALSe).

*SystemString*<br/>
Doit être `System::String`, et le projet doit être compilé avec/CLR.

*pString*<br/>
Handle pour un `CStringT` objet.

### <a name="remarks"></a>Notes

Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, vous devez savoir que des exceptions de mémoire peuvent se produire. Notez que certains de ces constructeurs agissent comme des fonctions de conversion. Cela vous permet de substituer, par exemple, un LPTStr où `CStringT` un objet est attendu.

- `CStringT`( `LPCSTR` `lpsz` ): Construit un Unicode `CStringT` à partir d’une chaîne ANSI. Vous pouvez également utiliser ce constructeur pour charger une ressource de type chaîne comme indiqué dans l’exemple ci-dessous.

- `CStringT(` `LPCWSTR` `lpsz` ): Construit un `CStringT` à partir d’une chaîne Unicode.

- `CStringT`( `const unsigned char*` `psz` ): Vous permet de construire un `CStringT` à partir d’un pointeur vers un **type non signé**.

> [!NOTE]
>  Définissez la macro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION pour désactiver la conversion de chaînes implicite entre les chaînes ANSI et Unicode. La macro exclut des constructeurs de compilation qui prennent en charge la conversion.

Notez que le paramètre *strSrc* peut être un `CStringT` objet ou. `CThisSimpleString` Pour `CStringT`, utilisez l’une de ses instanciations`CString`par `CStringA`défaut ( `CStringW`, ou) `CThisSimpleString`; pour, utilisez un pointeur **This** . `CThisSimpleString`déclare une instance de la [classe CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), qui est une classe de chaîne plus petite avec des fonctionnalités moins intégrées que la `CStringT` classe.

L’opérateur `CSimpleStringT<>&()` de surcharge construit un `CStringT` objet à partir `CSimpleStringT` d’une déclaration.

> [!NOTE]
>  Bien qu’il soit possible de `CStringT` créer des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et `CStringT` d’opérateurs sur des objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>  CStringT::~CStringT

Détruit l' `CStringT` objet.

```
~CStringT() throw();
```

### <a name="remarks"></a>Notes

Détruit l' `CStringT` objet.

##  <a name="delete"></a>  CStringT::Delete

Supprime un ou des caractères d’une chaîne commençant par le caractère à l’index donné.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
Index de base zéro du premier caractère de l' `CStringT` objet à supprimer.

*nCount*<br/>
Nombre de caractères à supprimer.

### <a name="return-value"></a>Valeur de retour

Longueur de la chaîne modifiée.

### <a name="remarks"></a>Notes

Si *nCount* est plus long que la chaîne, le reste de la chaîne sera supprimé.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

##  <a name="find"></a>  CStringT::Find

Recherche la première correspondance d’un caractère ou d’une sous-chaîne dans cette chaîne.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Paramètres

*pszSub*<br/>
Sous-chaîne à rechercher.

*iStart*<br/>
Index du caractère dans la chaîne à partir duquel commencer la recherche, ou 0 pour démarrer à partir du début.

*ch*<br/>
Caractère unique à rechercher.

### <a name="return-value"></a>Valeur de retour

Index de base zéro du premier caractère de cet `CStringT` objet qui correspond à la sous-chaîne ou aux caractères demandés;-1 si la sous-chaîne ou le caractère est introuvable.

### <a name="remarks"></a>Notes

La fonction est surchargée pour accepter les deux caractères uniques (similaires à la fonction `strchr`Runtime) et les chaînes (similaires à `strstr`).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

##  <a name="findoneof"></a>  CStringT::FindOneOf

Recherche dans cette chaîne le premier caractère qui correspond à n’importe quel caractère contenu dans *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Paramètres

*pszCharSet*<br/>
Chaîne contenant des caractères pour la correspondance.

### <a name="return-value"></a>Valeur de retour

Index de base zéro du premier caractère de cette chaîne qui se trouve également dans *pszCharSet*; -1 s’il n’y a aucune correspondance.

### <a name="remarks"></a>Notes

Recherche la première occurrence de l’un des caractères dans *pszCharSet*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

##  <a name="format"></a>  CStringT::Format

Écrit des données mises en `CStringT` forme dans un de la même façon que [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) met en forme les données dans un tableau de caractères de style C.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Paramètres

*nFormatID*<br/>
Identificateur de ressource de chaîne qui contient la chaîne de contrôle de format.

*pszFormat*<br/>
Chaîne de contrôle de format.

*argument*<br/>
Arguments facultatifs.

### <a name="remarks"></a>Notes

Cette fonction met en forme et stocke une série de caractères et `CStringT`de valeurs dans le. Chaque argument facultatif (le cas échéant) est converti et sorti selon la spécification de format correspondante dans *pszFormat* ou à partir de la ressource de type chaîne identifiée par *nFormatID*.

L’appel échoue si l’objet String lui-même est proposé en tant que `Format`paramètre à. Par exemple, le code suivant génère des résultats imprévisibles:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Pour plus d’informations, consultez [Syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

##  <a name="formatmessage"></a>  CStringT::FormatMessage

Met en forme une chaîne de message.

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Paramètres

*nFormatID*<br/>
Identificateur de ressource de chaîne qui contient le texte de message sans mise en forme.

*pszFormat*<br/>
Pointe vers la chaîne de contrôle de format. Les insertions et les mises en forme sont analysées en conséquence. La chaîne de format est semblable aux chaînes de format de style *printf*de la fonction runtime, sauf qu’elle permet l’insertion des paramètres dans un ordre arbitraire.

*argument*<br/>
Arguments facultatifs.

### <a name="remarks"></a>Notes

La fonction requiert une définition de message comme entrée. La définition du message est déterminée par *pszFormat* ou à partir de la ressource de type chaîne identifiée par *nFormatID*. La fonction copie le texte du message mis en `CStringT` forme dans l’objet, en traitant toutes les séquences d’insertion incorporées si nécessaire.

> [!NOTE]
> `FormatMessage`tente d’allouer de la mémoire système pour la chaîne mise en forme récemment. Si cette tentative échoue, une exception de mémoire est automatiquement levée.

Chaque instruction INSERT doit avoir un paramètre correspondant à la suite du paramètre *pszFormat* ou *nFormatID* . Dans le texte du message, plusieurs séquences d’échappement sont prises en charge pour la mise en forme dynamique du message. Pour plus d’informations, consultez la fonction [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

##  <a name="formatmessagev"></a>  CStringT::FormatMessageV

Met en forme une chaîne de message à l’aide d’une liste d’arguments de variables.

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Pointe vers la chaîne de contrôle de format. Les insertions et les mises en forme sont analysées en conséquence. La chaîne de format est semblable aux chaînes de format `printf`de style fonction d’exécution, sauf qu’elle permet l’insertion des paramètres dans un ordre arbitraire.

*pArgList*<br/>
Pointeur désignant une liste d’arguments.

### <a name="remarks"></a>Notes

La fonction requiert une définition de message comme entrée, déterminée par *pszFormat*. La fonction copie le texte du message mis en forme et une liste variable d' `CStringT` arguments vers l’objet, en traitant toutes les séquences d’insertion incorporées, le cas échéant.

> [!NOTE]
> `FormatMessageV`appelle [CStringT:: FormatMessage](#formatmessage), qui tente d’allouer de la mémoire système pour la chaîne mise en forme récemment. Si cette tentative échoue, une exception de mémoire est automatiquement levée.

Pour plus d’informations, consultez la fonction [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows dans le SDK Windows.

##  <a name="formatv"></a>  CStringT::FormatV

Met en forme une chaîne de message à l’aide d’une liste d’arguments de variables.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Pointe vers la chaîne de contrôle de format. Les insertions et les mises en forme sont analysées en conséquence. La chaîne de format est semblable aux chaînes de format `printf`de style fonction d’exécution, sauf qu’elle permet l’insertion des paramètres dans un ordre arbitraire.

*args*<br/>
Pointeur désignant une liste d’arguments.

### <a name="remarks"></a>Notes

Écrit une chaîne mise en forme et une liste variable d’arguments `CStringT` dans une chaîne de la même `vsprintf_s` façon que met en forme les données dans un tableau de caractères de style C.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

##  <a name="getenvironmentvariable"></a>  CStringT::GetEnvironmentVariable

Affecte à la chaîne la valeur de la variable d’environnement spécifiée.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Paramètres

*pszVar*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie la variable d’environnement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Récupère la valeur de la variable spécifiée à partir du bloc d’environnement du processus appelant. La valeur est sous la forme d’une chaîne de caractères se terminant par un caractère null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

##  <a name="insert"></a>  CStringT::Insert

Insère un caractère unique ou une sous-chaîne à l’index donné dans la chaîne.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
Index du caractère avant lequel l’insertion doit avoir lieu.

*psz*<br/>
Pointeur vers la sous-chaîne à insérer.

*ch*<br/>
Caractère à insérer.

### <a name="return-value"></a>Valeur de retour

Longueur de la chaîne modifiée.

### <a name="remarks"></a>Notes

Le paramètre *iIndex* identifie le premier caractère qui sera déplacé pour faire de la place pour le caractère ou la sous-chaîne. Si *nIndex* est égal à zéro, l’insertion se produit avant la chaîne entière. Si *nIndex* est supérieur à la longueur de la chaîne, la fonction concatène la chaîne présente et le nouveau matériel fourni par *ch* ou *PSZ*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>  CStringT::Left

Extrait les caractères *nCount* les plus à gauche `CStringT` de cet objet et retourne une copie de la sous-chaîne extraite.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Paramètres

*nCount*<br/>
Nombre de caractères à extraire de cet objet `CStringT`.

### <a name="return-value"></a>Valeur de retour

Objet `CStringT` qui contient une copie de la plage spécifiée des caractères. L'objet retourné par `CStringT` peut être vide.

### <a name="remarks"></a>Notes

Si *nCount* dépasse la longueur de chaîne, la totalité de la chaîne est extraite. `Left` est similaire à la fonction de base `Left`.

Pour les jeux de caractères multioctets (MBCS), *nCount* traite chaque séquence de 8 bits comme un caractère, de sorte que *nCount* retourne le nombre de caractères multioctets multiplié par deux.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>  CStringT::LoadString

Lit une ressource de chaîne Windows, identifiée par *nid*, dans `CStringT` un objet existant.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
Handle de l’instance du module.

*nID*<br/>
ID de ressource de chaîne Windows.

*wLanguageID*<br/>
Langage de la ressource de type chaîne.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le chargement de la ressource a réussi; Sinon, 0.

### <a name="remarks"></a>Notes

Charge la ressource de chaîne (*nid*) à partir du module spécifié (*HINSTANCE*) à l’aide du langage spécifié (*wLanguage*).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

##  <a name="makelower"></a>  CStringT::MakeLower

Convertit `CStringT` l’objet en chaîne minuscule.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Valeur de retour

Chaîne en minuscules résultante.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>  CStringT::MakeReverse

Inverse l’ordre des caractères dans l' `CStringT` objet.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Valeur de retour

Chaîne inversée résultante.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>  CStringT::MakeUpper

Convertit `CStringT` l’objet en une chaîne en majuscules.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Valeur de retour

Chaîne en majuscules résultante.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>  CStringT::Mid

Extrait une sous-chaîne de longueur *nCount* caractères à partir `CStringT` de cet objet, en commençant à la position *iFirst* (de base zéro).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Paramètres

*iFirst*<br/>
Index de base zéro du premier caractère de cet `CStringT` objet à inclure dans la sous-chaîne extraite.

*nCount*<br/>
Nombre de caractères à extraire de cet objet `CStringT`. Si ce paramètre n’est pas fourni, le reste de la chaîne est extrait.

### <a name="return-value"></a>Valeur de retour

Objet `CStringT` qui contient une copie de la plage spécifiée des caractères. Notez que l’objet `CStringT` retourné peut être vide.

### <a name="remarks"></a>Notes

La fonction retourne une copie de la sous-chaîne extraite. `Mid`est similaire à la fonction Mid de base (à ceci près que les index de base sont de base un).

Pour les jeux de caractères multioctets (MBCS), *nCount* fait référence à chaque caractère 8 bits; autrement dit, un octet de tête et de fin dans un caractère multioctet est compté comme deux caractères.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>  CStringT::OemToAnsi

Convertit tous les caractères de `CStringT` cet objet du jeu de caractères OEM en jeu de caractères ANSI.

```
void OemToAnsi();
```

### <a name="remarks"></a>Notes

Cette fonction n’est pas disponible si _ Unicode est défini.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CStringT:: AnsiToOem](#ansitooem).

##  <a name="operator_eq"></a>  CStringT::operator =

Assigne une nouvelle valeur à la chaîne.

```
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

*strSrc*<br/>
`CStringT` À assigner à cette chaîne.

*str*<br/>
Référence à un objet `CThisSimpleString`.

*bMFCDLL*<br/>
Valeur booléenne qui spécifie si le projet est une DLL MFC ou non.

*BaseType*<br/>
Type de base de la chaîne.

*var*<br/>
Objet variant à assigner à cette chaîne.

*ch*<br/>
Caractère ANSI ou Unicode à assigner à la chaîne.

*pszSrc*<br/>
Pointeur vers la chaîne d’origine qui est assignée.

### <a name="remarks"></a>Notes

L’opérateur d’assignation accepte `CStringT` un autre objet, un pointeur de caractère ou un caractère unique. Sachez que les exceptions de mémoire peuvent se produire chaque fois que vous utilisez cet opérateur, car un nouveau stockage peut être alloué.

Pour plus d' `CThisSimpleString`informations sur, consultez la section Notes de [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Bien qu’il soit possible de `CStringT` créer des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et `CStringT` d’opérateurs sur des objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

##  <a name="operator_add"></a>  CStringT::operator +

Concatène deux chaînes ou un caractère et une chaîne.

```
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>Paramètres

*ch1*<br/>
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*ch2*<br/>
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*str1*<br/>
`CStringT` À concaténer avec une chaîne ou un caractère.

*str2*<br/>
`CStringT` À concaténer avec une chaîne ou un caractère.

*psz1*<br/>
Pointeur vers une chaîne se terminant par null à concaténer avec une chaîne ou un caractère.

*psz2*<br/>
Pointeur vers une chaîne à concaténer avec une chaîne ou un caractère.

### <a name="remarks"></a>Notes

Il existe sept formes surchargées `CStringT::operator+` de la fonction. La première version concatène deux objets existants `CStringT` . Les deux suivants concatènent un `CStringT` objet et une chaîne terminée par le caractère null. Les deux suivants concatènent un `CStringT` objet et un caractère ANSI. Les deux derniers concatènent un `CStringT` objet et un caractère Unicode.

> [!NOTE]
>  Bien qu’il soit possible de `CStringT` créer des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et `CStringT` d’opérateurs sur des objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

##  <a name="operator_add_eq"></a>  CStringT::operator +=

Concatène les caractères à la fin de la chaîne.

```
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

*str*<br/>
Référence à un objet `CThisSimpleString`.

*bMFCDLL*<br/>
Valeur booléenne qui spécifie si le projet est une DLL MFC ou non.

*BaseType*<br/>
Type de base de la chaîne.

*var*<br/>
Objet variant à concaténer à cette chaîne.

*ch*<br/>
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*pszSrc*<br/>
Pointeur vers la chaîne d’origine qui est concaténée.

*strSrc*<br/>
`CStringT` À concaténer à cette chaîne.

### <a name="remarks"></a>Notes

L’opérateur accepte un `CStringT` autre objet, un pointeur de caractère ou un caractère unique. Vous devez savoir que des exceptions de mémoire peuvent se produire chaque fois que vous utilisez cet opérateur de concaténation, car un nouveau stockage peut `CStringT` être alloué pour les caractères ajoutés à cet objet.

Pour plus d' `CThisSimpleString`informations sur, consultez la section Notes de [CStringT:: CStringT](#cstringt).

> [!NOTE]
>  Bien qu’il soit possible de `CStringT` créer des instances qui contiennent des caractères null incorporés, nous vous le déconseillons. L’appel de méthodes et `CStringT` d’opérateurs sur des objets qui contiennent des caractères null incorporés peut produire des résultats inattendus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

##  <a name="operator_eq_eq"></a>  CStringT::operator ==

Détermine si deux chaînes sont logiquement égales.

```
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Paramètres

*ch1*<br/>
Caractère ANSI ou Unicode pour la comparaison.

*ch2*<br/>
Caractère ANSI ou Unicode pour la comparaison.

*str1*<br/>
`CStringT` À des fins de comparaison.

*str2*<br/>
`CStringT` À des fins de comparaison.

*psz1*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

*psz2*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Notes

Teste si une chaîne ou un caractère sur le côté gauche est égal à une chaîne ou un caractère situé à droite, et retourne TRUE ou FALSe en conséquence.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

##  <a name="operator_neq"></a>CStringT:: Operator! =

Détermine si deux chaînes sont logiquement inégales.

```
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Paramètres

*ch1*<br/>
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*ch2*<br/>
Caractère ANSI ou Unicode à concaténer avec une chaîne.

*str1*<br/>
`CStringT` À des fins de comparaison.

*str2*<br/>
`CStringT` À des fins de comparaison.

*psz1*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

*psz2*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Notes

Teste si une chaîne ou un caractère situé sur le côté gauche n’est pas égal à une chaîne ou un caractère situé à droite.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

##  <a name="operator_lt"></a>CStringT:: Operator&lt;

Détermine si la chaîne située à gauche de l’opérateur est inférieure à la chaîne sur le côté droit.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
`CStringT` À des fins de comparaison.

*str2*<br/>
`CStringT` À des fins de comparaison.

*psz1*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

*psz2*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Notes

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que:

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

##  <a name="operator_gt"></a>CStringT:: Operator&gt;

Détermine si la chaîne située à gauche de l’opérateur est supérieure à la chaîne située à droite.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
`CStringT` À des fins de comparaison.

*str2*<br/>
`CStringT` À des fins de comparaison.

*psz1*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

*psz2*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Notes

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que:

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

##  <a name="operator_lt_eq"></a>CStringT:: Operator&lt;=

Détermine si la chaîne située à gauche de l’opérateur est inférieure ou égale à la chaîne située à droite.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
`CStringT` À des fins de comparaison.

*str2*<br/>
`CStringT` À des fins de comparaison.

*psz1*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

*psz2*<br/>
Pointeur vers une chaîne se terminant par null pour la comparaison.

### <a name="remarks"></a>Notes

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que:

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

##  <a name="operator_gt_eq"></a>CStringT:: Operator&gt;=

Détermine si la chaîne située à gauche de l’opérateur est supérieure ou égale à la chaîne située à droite.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
`CStringT` À des fins de comparaison.

*str2*<br/>
`CStringT` À des fins de comparaison.

*psz1*<br/>
Pointeur vers une chaîne à comparer.

*psz2*<br/>
Pointeur vers une chaîne à comparer.

### <a name="remarks"></a>Notes

Comparaison lexicographique entre les chaînes, caractère par caractère jusqu’à ce que:

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

##  <a name="remove"></a>  CStringT::Remove

Supprime toutes les instances du caractère spécifié de la chaîne.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Paramètres

*chRemove*<br/>
Caractère à supprimer d’une chaîne.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères supprimés de la chaîne. Zéro si la chaîne n’est pas modifiée.

### <a name="remarks"></a>Notes

Les comparaisons pour le caractère respectent la casse.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

##  <a name="replace"></a>  CStringT::Replace

Il existe deux versions de `Replace`. La première version remplace une ou plusieurs copies d’une sous-chaîne à l’aide d’une autre sous-chaîne. Les deux sous-chaînes se terminent par un caractère null. La deuxième version remplace une ou plusieurs copies d’un caractère à l’aide d’un autre caractère. Les deux versions fonctionnent sur les données caractères stockées `CStringT`dans.

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Paramètres

*pszOld*<br/>
Pointeur vers une chaîne se terminant par un caractère null à remplacer par *pszNew*.

*pszNew*<br/>
Pointeur vers une chaîne terminée par le caractère null qui remplace *pszOld*.

*chOld*<br/>
Caractère à remplacer par *chNew*.

*chNew*<br/>
Caractère qui remplace *chOld*.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’instances remplacées du caractère ou de la sous-chaîne, ou zéro si la chaîne n’est pas modifiée.

### <a name="remarks"></a>Notes

`Replace`peut modifier la longueur de chaîne, car *pszNew* et *pszOld* n’ont pas besoin d’être de la même longueur, et plusieurs copies de l’ancienne sous-chaîne peuvent être remplacées par la nouvelle. La fonction effectue une correspondance respectant la casse.

, Et `CStringT` `CString` sontdes`CStringA`exemplesd’instances. `CStringW`

Pour `CStringA` ,`Replace` fonctionne avec des caractères ANSI ou multioctets (MBCS). Pour `CStringW` ,`Replace` fonctionne avec des caractères larges.

Pour `CString`, le type de données character est sélectionné au moment de la compilation, selon que les constantes dans le tableau suivant sont définies ou non.

|Constante définie|Type de données character|
|----------------------|-------------------------|
|_UNICODE|Caractères larges|
|_MBCS|Caractères multioctets|
|SP5|Caractères codés sur un octet|
|Les deux|Undefined|

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>  CStringT::ReverseFind

Recherche la `CStringT` dernière correspondance d’un caractère dans cet objet.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Paramètres

*ch*<br/>
Caractère à rechercher.

### <a name="return-value"></a>Valeur de retour

Index de base zéro du dernier caractère de cet `CStringT` objet qui correspond au caractère demandé, ou-1 si le caractère est introuvable.

### <a name="remarks"></a>Notes

La fonction est similaire à la fonction `strrchr`Runtime.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>  CStringT::Right

Extrait les derniers caractères *nCount* (autrement dit, les plus à droite) `CStringT` à partir de cet objet et retourne une copie de la sous-chaîne extraite.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Paramètres

*nCount*<br/>
Nombre de caractères à extraire de cet objet `CStringT`.

### <a name="return-value"></a>Valeur de retour

Objet `CStringT` qui contient une copie de la plage spécifiée des caractères. Notez que l’objet `CStringT` retourné peut être vide.

### <a name="remarks"></a>Notes

Si *nCount* dépasse la longueur de chaîne, la totalité de la chaîne est extraite. `Right`est similaire à la fonction `Right` de base (à ceci près que les index de base sont de base zéro).

Pour les jeux de caractères multioctets (MBCS), *nCount* fait référence à chaque caractère 8 bits; autrement dit, un octet de tête et de fin dans un caractère multioctet est compté comme deux caractères.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>  CStringT::SetSysString

Réalloue le BSTR pointé par *pbstr* et y copie le contenu de l' `CStringT` objet, y compris le caractère null.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Paramètres

*pbstr*<br/>
Pointeur vers une chaîne de caractères.

### <a name="return-value"></a>Valeur de retour

La nouvelle chaîne.

### <a name="remarks"></a>Notes

En fonction du contenu de l' `CStringT` objet, la valeur du BSTR référencé par *pbstr* peut changer. La fonction lève une `CMemoryException` si la mémoire disponible est insuffisante.

Cette fonction est généralement utilisée pour modifier la valeur des chaînes passées par référence pour Automation.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

##  <a name="spanexcluding"></a>  CStringT::SpanExcluding

Extrait des caractères de la chaîne, en commençant par le premier caractère, qui ne figurent pas dans le jeu de caractères identifié par *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Paramètres

*pszCharSet*<br/>
Chaîne interprétée comme un jeu de caractères.

### <a name="return-value"></a>Valeur de retour

Sous-chaîne qui contient les caractères de la chaîne qui ne sont pas dans *pszCharSet*, en commençant par le premier caractère de la chaîne et en terminant par le premier caractère trouvé dans la chaîne qui se trouve également dans *pszCharSet* (autrement dit, en commençant par la première caractère dans la chaîne et jusqu’au premier caractère de la chaîne trouvée *pszCharSet*). Elle retourne la chaîne entière si aucun caractère dans *pszCharSet* n’est trouvé dans la chaîne.

### <a name="remarks"></a>Notes

`SpanExcluding`extrait et retourne tous les caractères précédant la première occurrence d’un caractère de *pszCharSet* (en d’autres termes, le caractère de *pszCharSet* et tous les caractères qui le suivent dans la chaîne ne sont pas retournés). Si aucun caractère de *pszCharSet* n’est trouvé dans la chaîne, `SpanExcluding` retourne la chaîne entière.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

##  <a name="spanincluding"></a>  CStringT::SpanIncluding

Extrait des caractères de la chaîne, en commençant par le premier caractère, qui se trouvent dans le jeu de caractères identifié par *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Paramètres

*pszCharSet*<br/>
Chaîne interprétée comme un jeu de caractères.

### <a name="return-value"></a>Valeur de retour

Sous-chaîne qui contient les caractères de la chaîne qui sont dans *pszCharSet*, en commençant par le premier caractère de la chaîne et en finissant lorsqu’un caractère est trouvé dans la chaîne qui n’est pas dans *pszCharSet*. `SpanIncluding`retourne une sous-chaîne vide si le premier caractère de la chaîne n’est pas dans le jeu spécifié.

### <a name="remarks"></a>Notes

Si le premier caractère de la chaîne n’est pas dans le jeu de caractères `SpanIncluding` , retourne une chaîne vide. Sinon, elle retourne une séquence de caractères consécutifs qui se trouvent dans le jeu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

##  <a name="tokenize"></a>  CStringT::Tokenize

Recherche le jeton suivant dans une chaîne cible

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Paramètres

*pszTokens*<br/>
Chaîne contenant des délimiteurs de jetons. L’ordre de ces délimiteurs n’est pas important.

*iStart*<br/>
Index de base zéro à partir duquel commencer la recherche.

### <a name="return-value"></a>Valeur de retour

`CStringT` Objet contenant la valeur de jeton actuelle.

### <a name="remarks"></a>Notes

La `Tokenize` fonction recherche le jeton suivant dans la chaîne cible. Le jeu de caractères dans *pszTokens* spécifie les délimiteurs possibles du jeton à trouver. À chaque appel à `Tokenize` la fonction commence à *iStart*, ignore les délimiteurs de début et retourne `CStringT` un objet contenant le jeton actuel, qui est la chaîne de caractères jusqu’au caractère délimiteur suivant. La valeur de *iStart* est mise à jour pour correspondre à la position qui suit le caractère délimiteur de fin, ou-1 si la fin de la chaîne a été atteinte. Un plus grand nombre de jetons peuvent être décomposés du reste de la chaîne cible par une série `Tokenize`d’appels à, à l’aide de *iStart* pour effectuer le suivi de l’emplacement où le jeton suivant doit être lu dans la chaîne. Lorsqu’il n’y a plus de jetons, la fonction retourne une chaîne vide et *iStart* prend la valeur-1.

Contrairement aux fonctions de jeton CRT, telles que [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` ne modifie pas la chaîne cible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Notes

La sortie de cet exemple est la suivante:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

##  <a name="trim"></a>  CStringT::Trim

Supprime les caractères de début et de fin de la chaîne.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Paramètres

*chTarget*<br/>
Caractère cible à tronquer.

*pszTargets*<br/>
Pointeur vers une chaîne contenant les caractères cibles à tronquer. Toutes les occurrences de caractères de début et de fin de caractères dans *pszTarget* seront `CStringT` supprimées de l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne tronquée.

### <a name="remarks"></a>Notes

Supprime toutes les occurrences de début et de fin de l’un des éléments suivants:

- Caractère spécifié par *chTarget*.

- Tous les caractères trouvés dans la chaîne spécifiée par *pszTargets*.

- Situés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Notes

La sortie de cet exemple est la suivante:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

##  <a name="trimleft"></a>  CStringT::TrimLeft

Supprime les caractères de début de la chaîne.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Paramètres

*chTarget*<br/>
Caractère cible à tronquer.

*pszTargets*<br/>
Pointeur vers une chaîne contenant les caractères cibles à tronquer. Toutes les occurrences de caractères de début de *pszTarget* seront supprimées `CStringT` de l’objet.

### <a name="return-value"></a>Valeur de retour

Chaîne tronquée résultante.

### <a name="remarks"></a>Notes

Supprime toutes les occurrences de début et de fin de l’un des éléments suivants:

- Caractère spécifié par *chTarget*.

- Tous les caractères trouvés dans la chaîne spécifiée par *pszTargets*.

- Situés.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

##  <a name="trimright"></a>  CStringT::TrimRight

Supprime les caractères de fin de la chaîne.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Paramètres

*chTarget*<br/>
Caractère cible à tronquer.

*pszTargets*<br/>
Pointeur vers une chaîne contenant les caractères cibles à tronquer. Toutes les occurrences de caractère de fin de caractères dans *pszTarget* seront supprimées de l' `CStringT` objet.

### <a name="return-value"></a>Valeur de retour

Retourne l' `CStringT` objet qui contient la chaîne tronquée.

### <a name="remarks"></a>Notes

Supprime les occurrences de fin de l’un des éléments suivants:

- Caractère spécifié par *chTarget*.

- Tous les caractères trouvés dans la chaîne spécifiée par *pszTargets*.

- Situés.

La `CStringT& TrimRight(XCHAR chTarget)` version accepte un paramètre de caractère et supprime toutes les copies de ce caractère de la `CStringT` fin des données de chaîne. Elle démarre à partir de la fin de la chaîne et fonctionne vers l’avant. Il s’arrête lorsqu’il trouve un caractère différent ou `CSTringT` lorsqu’il manque de données de caractères.

La `CStringT& TrimRight(PCXSTR pszTargets)` version accepte une chaîne se terminant par un caractère null qui contient tous les caractères différents à rechercher. Elle supprime toutes les copies de ces caractères dans `CStringT` l’objet. Elle commence à la fin de la chaîne et fonctionne vers l’avant. Il s’arrête lorsqu’il trouve un caractère qui n’est pas dans la chaîne cible, `CStringT` ou lorsqu’il manque de données de caractères. Elle n’essaie pas de faire correspondre la chaîne cible entière à une sous-chaîne à la `CStringT`fin de.

La `CStringT& TrimRight()` version ne nécessite aucun paramètre. Elle supprime tous les espaces blancs de fin de `CStringT` la chaîne. Les caractères d’espace blanc peuvent être des sauts de ligne, des espaces ou des tabulations.

-

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT, classe](../../atl-mfc-shared/reference/csimplestringt-class.md)
