---
title: Classe CStringT
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
ms.openlocfilehash: 90f63b474f509b4d1a15ad6fe11bda61c343f483
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317589"
---
# <a name="cstringt-class"></a>Classe CStringT

Cette classe `CStringT` représente un objet.

## <a name="syntax"></a>Syntaxe

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Paramètres

*BaseType*<br/>
Le type de personnage de la classe de cordes. Il peut s'agir d'une des méthodes suivantes :

- **char** (pour les cordes de caractère ANSI).

- **wchar_t** (pour les chaînes de caractères Unicode).

- TCHAR (pour les chaînes de caractères ANSI et Unicode).

*StringTraits (en)*<br/>
Détermine si la classe de cordes a besoin du support de la bibliothèque C Run-Time (CRT) et de l’endroit où se trouvent les ressources en chaîne. Il peut s'agir d'une des méthodes suivantes :

- **StrTraitATL< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** &#124; **char** &#124; **TCHAR > >**

   La classe nécessite un support CRT et recherche `m_hInstResource` des chaînes de ressources dans le module spécifié par (un membre de la classe de module de l’application).

- **StrTraitATL< wchar_t &#124;** **char** &#124; **TCHAR, ChTraitsOS< wchar_t** &#124; **char** &#124; **TCHAR > >**

   La classe n’a pas besoin de support CRT `m_hInstResource` et recherche des chaînes de ressources dans le module spécifié par (un membre de la classe de module de l’application).

- **StrTraitMFC< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** &#124; **char** &#124; **TCHAR > >**

   La classe nécessite un support CRT et recherche des chaînes de ressources à l’aide de l’algorithme de recherche MFC standard.

- **StrTraitMFC< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS< wchar_t** &#124; **char** &#124; **TCHAR > >**

   La classe n’a pas besoin de support CRT et recherche des chaînes de ressources à l’aide de l’algorithme de recherche MFC standard.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStringT::CStringt](#cstringt)|Construit un `CStringT` objet de différentes façons.|
|[CStringT: :CStringT](#_dtorcstringt)|Détruit un objet `CStringT` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Alloue un `CStringT` BSTR à partir de données.|
|[CStringT::AnsiTooem](#ansitooem)|Effectue une conversion en place du personnage ANSI mis à l’ensemble de caractères OEM.|
|[CStringT::AppendFormat](#appendformat)|Annexes données formatées à `CStringT` un objet existant.|
|[CStringT::Collate](#collate)|Compare deux chaînes (sensibles aux cas, utilise des informations locales).|
|[CStringT::CollateNoCase](#collatenocase)|Compare deux chaînes (insensibles aux cas, utilise des informations locales).|
|[CStringT::Comparez](#compare)|Compare deux cordes (sensibles au boîtier).|
|[CStringT::CompareNoCase](#comparenocase)|Compare deux cordes (insensibles aux cas).|
|[CStringT::Delete](#delete)|Supprime un personnage ou des caractères d’une chaîne.|
|[CStringT::Trouver](#find)|Trouve un personnage ou une sous-corde à l’intérieur d’une plus grande chaîne.|
|[CStringT::FindOneOf](#findoneof)|Trouve le premier personnage correspondant à partir d’un ensemble.|
|[CStringT::Format](#format)|Formats la `sprintf` chaîne comme le fait.|
|[CStringT::FormatMessage](#formatmessage)|Formate une chaîne de messages.|
|[CStringT::FormatMessageV](#formatmessagev)|Formats une chaîne de message à l’aide d’une liste d’arguments variables.|
|[CStringT::FormatV](#formatv)|Formats la chaîne à l’aide d’une liste variable d’arguments.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Définit la chaîne à la valeur de la variable d’environnement spécifiée.|
|[CStringT::Insert](#insert)|Insère un seul caractère ou un sous-cordon à l’index donné dans la chaîne.|
|[CStringT::Gauche](#left)|Extrait la partie gauche d’une ficelle.|
|[CStringT::LoadString](#loadstring)|Charge un `CStringT` objet existant à partir d’une ressource Windows.|
|[CStringT::MakeLower](#makelower)|Convertit tous les personnages de cette chaîne en caractères minuscules.|
|[CStringT::MakeReverse](#makereverse)|Renverse la ficelle.|
|[CStringT::MakeUpper](#makeupper)|Convertit tous les personnages de cette chaîne en personnages majuscules.|
|[CStringT::Mid](#mid)|Extrait la partie centrale d’une ficelle.|
|[CStringT::OemToAnsi](#oemtoansi)|Effectue une conversion en place du personnage OEM mis à l’ensemble de caractères ANSI.|
|[CStringT::Supprimer](#remove)|Supprime les caractères indiqués d’une chaîne.|
|[CStringT::Remplacer](#replace)|Remplace les caractères indiqués par d’autres caractères.|
|[CStringT::ReverseFind](#reversefind)|Trouve un personnage à l’intérieur d’une plus grande chaîne; commence à partir de la fin.|
|[CStringT::Droite](#right)|Extrait la bonne partie d’une chaîne.|
|[CStringT::SetSysString](#setsysstring)|Définit un objet BSTR existant `CStringT` avec les données d’un objet.|
|[CStringT::SpanExcluding](#spanexcluding)|Extrait des personnages de la chaîne, à commencer par le premier `pszCharSet`personnage, qui ne sont pas dans l’ensemble des personnages identifiés par .|
|[CStringT::SpanIncluding](#spanincluding)|Extrait un sous-cordon qui ne contient que les caractères d’un ensemble.|
|[CStringT::Tokenize](#tokenize)|Extraits de jetons spécifiés dans une chaîne cible.|
|[CStringT::Trim](#trim)|Coupe tous les personnages de l’espace blanc de tête et de fuite de la chaîne.|
|[CStringT::TrimLeft](#trimleft)|Coupe les personnages de l’espace blanc de la chaîne.|
|[CStringT::TrimRight](#trimright)|Trims trailing caractères d’espace blanc de la chaîne.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[CStringT::opérateur](#operator_eq)|Attribue une nouvelle valeur `CStringT` à un objet.|
|[CStringT::opérateur](#operator_add)|Concatenates deux cordes ou un personnage et une corde.|
|[CStringT::opérateur](#operator_add_eq)|Concatenates une nouvelle chaîne à la fin d’une chaîne existante.|
|[CStringT::opérateur](#operator_eq_eq)|Détermine si deux cordes sont logiquement égales.|
|[CStringT::opérateur !](#operator_neq)|Détermine si deux cordes ne sont logiquement pas égales.|
|[CStringT::opérateur&lt;](#operator_lt)|Détermine si la ficelle du côté gauche de l’opérateur est inférieure à celle de la corde sur le côté droit.|
|[CStringT::opérateur&gt;](#operator_gt)|Détermine si la ficelle du côté gauche de l’opérateur est supérieure à la corde sur le côté droit.|
|[CStringT::opérateur&lt;=](#operator_lt_eq)|Détermine si la ficelle du côté gauche de l’opérateur est inférieure ou égale à la corde sur le côté droit.|
|[CStringT::opérateur&gt;=](#operator_gt_eq)|Détermine si la ficelle du côté gauche de l’opérateur est supérieure ou égale à la corde sur le côté droit.|

## <a name="remarks"></a>Notes

`CStringT`hérite de [CSimpleStringT Class](../../atl-mfc-shared/reference/csimplestringt-class.md). Les fonctionnalités avancées, telles que la manipulation de `CStringT`caractère, la commande et la recherche, sont implémentées par .

> [!NOTE]
> `CStringT`les objets sont capables de jeter des exceptions. Cela se `CStringT` produit quand un objet manque de mémoire pour n’importe quelle raison.

Un `CStringT` objet se compose d’une séquence variable de caractères. `CStringT`fournit des fonctions et des opérateurs utilisant la syntaxe similaire à celle de Base. Les opérateurs de concatenation et de `CStringT` comparaison, ainsi que la gestion simplifiée de la mémoire, rendent les objets plus faciles à utiliser que les tableaux de caractères ordinaires.

> [!NOTE]
> Bien qu’il `CStringT` soit possible de créer des instances qui contiennent des caractères nuls intégrés, nous recommandons contre elle. Les méthodes d’appel et les opérateurs sur `CStringT` les objets qui contiennent des caractères nuls intégrés peuvent produire des résultats imprévus.

En utilisant différentes combinaisons `StringTraits` de `CStringT` la et des paramètres, les `BaseType` objets peuvent venir dans les types suivants, qui sont ont été prédéfinis par les bibliothèques ATL.

Si vous utilisez dans une application ATL :

`CString`, `CStringA`et `CStringW` sont exportés à partir du MFC DLL (MFC90. DLL), jamais de l’utilisateur DLLs. Ceci est fait `CStringT` pour éviter d’être multiplié défini.

> [!NOTE]
> Si votre code contient la solution de contournement pour les erreurs de liaison qui est décrite dans [les classes de chaîne d’exportation à l’aide de CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), vous devez supprimer ce code. Ce n'est plus nécessaire.

Les types de chaînes suivants sont disponibles dans les applications basées sur MFC :

|Type CStringT|Déclaration|
|-------------------|-----------------|
|`CStringA`|Une chaîne de type caractère ANSI avec support CRT.|
|`CStringW`|Une chaîne de type caractère Unicode avec support CRT.|
|`CString`|Les types de caractères ANSI et Unicode avec support CRT.|

Les types de chaînes suivants sont disponibles dans les projets où ATL_CSTRING_NO_CRT est définie :

|Type CStringT|Déclaration|
|-------------------|-----------------|
|`CAtlStringA`|Une chaîne de type caractère ANSI sans support CRT.|
|`CAtlStringW`|Une chaîne de type de caractère Unicode sans support CRT.|
|`CAtlString`|Les types de caractères ANSI et Unicode sans support CRT.|

Les types de chaînes suivants sont disponibles dans les projets où ATL_CSTRING_NO_CRT n’est pas définie :

|Type CStringT|Déclaration|
|-------------------|-----------------|
|`CAtlStringA`|Une chaîne de type caractère ANSI avec support CRT.|
|`CAtlStringW`|Une chaîne de type caractère Unicode avec support CRT.|
|`CAtlString`|Les types de caractères ANSI et Unicode avec support CRT.|

`CString`les objets ont également les caractéristiques suivantes :

- `CStringT`les objets peuvent se développer à la suite d’opérations de concatenation.

- `CStringT`les objets suivent la « sémantique de valeur ». Considérez `CStringT` un objet comme une chaîne réelle, pas comme un pointeur d’une chaîne.

- Vous pouvez `CStringT` substituer librement des objets à `PCXSTR` des arguments de fonction.

- Gestion personnalisée de la mémoire pour les tampons de chaîne. Pour plus d’informations, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Types prédéfinis CStringT

Parce `CStringT` que utilise un argument de modèle pour définir le type de caractère [(wchar_t](../../c-runtime-library/standard-types.md) ou [char](../../c-runtime-library/standard-types.md)) pris en charge, les types de paramètres de méthode peuvent être compliqués à certains moments. Pour simplifier ce problème, un ensemble de types prédéfinis est défini et utilisé dans toute la `CStringT` classe. Le tableau suivant énumère les différents types :

|Nom|Description|
|----------|-----------------|
|`XCHAR`|Un seul personnage **(wchar_t** ou **char)** avec le `CStringT` même type de caractère que l’objet.|
|`YCHAR`|Un seul personnage **(wchar_t** ou **char)** avec le type `CStringT` de personnage opposé comme objet.|
|`PXSTR`|Un pointeur à une chaîne de caractère **(wchar_t** ou **char)** avec le même type de caractère que l’objet. `CStringT`|
|`PYSTR`|Un pointeur à une chaîne de caractère **(wchar_t** ou **char)** avec le type de caractère opposé comme l’objet. `CStringT`|
|`PCXSTR`|Pointeur d’une chaîne de caractère **const** **(wchar_t** ou **char)** avec le même type de caractère que l’objet. `CStringT`|
|`PCYSTR`|Pointeur d’une chaîne de caractère **const** **(wchar_t** ou **char)** `CStringT` avec le type de caractère opposé comme objet.|

> [!NOTE]
> Le code qui a `CString` déjà utilisé `AssignCopy`des méthodes non documentées de (comme ) doit être remplacé par du code qui utilise les méthodes documentées suivantes de `CStringT` (tels que `GetBuffer` ou `ReleaseBuffer`). Ces méthodes sont `CSimpleStringT`héritées de .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Spécifications

|En-tête|Utilisée pour|
|------------|-------------|
|cstringt.h|Objets à cordes MFC uniquement|
|atlstr.h (en anglais)|Objets à cordes non MFC|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT::AllocSysString

Alloue une chaîne compatible avec l’automatisation du `CStringT` type BSTR et y copie le contenu de l’objet, y compris le caractère null de fin.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Valeur de retour

La chaîne nouvellement allouée.

### <a name="remarks"></a>Notes

Dans les programmes MFC, une [classe CMemoryException](../../mfc/reference/cmemoryexception-class.md) est lancée si la mémoire n’existe pas. Dans les programmes ATL, un [CAtlException](../../atl/reference/catlexception-class.md) est jeté. Cette fonction est normalement utilisée pour retourner les cordes pour Automation.

Généralement, si cette chaîne est passée à une fonction COM comme un paramètre [dans], alors cela nécessite l’appelant pour libérer la chaîne. Cela peut être fait en utilisant [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), tel que décrit dans le SDK Windows. Pour plus d’informations, voir [Allouer et libérer la mémoire pour un BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Pour plus d’informations sur les fonctions d’allocation OLE dans Windows, voir [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a>CStringT::AnsiTooem

Convertit tous les `CStringT` personnages de cet objet à partir du personnage ANSI mis à l’ensemble de caractères OEM.

```
void AnsiToOem();
```

### <a name="remarks"></a>Notes

La fonction n’est pas disponible si _UNICODE est définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a>CStringT::AppendFormat

Annexes données formatées à `CStringT` un objet existant.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Une chaîne de contrôle de format.

*nFormatID (en)*<br/>
L’identifiant de ressources de chaîne qui contient la chaîne de contrôle de format.

*Argument*<br/>
Arguments facultatifs.

### <a name="remarks"></a>Notes

Cette fonction formate et joint une série de `CStringT`caractères et de valeurs dans le . Chaque argument facultatif (le cas échéant) est converti et annexé selon les spécifications de format correspondantes dans *pszFormat* ou à partir de la ressource de chaîne identifiée par *nFormatID*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a>CStringT::Collate

Compare deux chaînes à l’aide `_tcscoll`de la fonction de texte générique .

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
L’autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les cordes sont identiques, < `CStringT` 0 si cet objet est inférieur *à psz*, ou > 0 si cet `CStringT` objet est plus grand que *psz*.

### <a name="remarks"></a>Notes

La fonction `_tcscoll`de texte générique , qui est définie dans TCHAR. H, cartes `strcoll`à `wcscoll`l’un ou l’autre , , ou `_mbscoll`, en fonction de l’ensemble de caractères qui est défini au moment de compilation. Chaque fonction effectue une comparaison sensible aux cas des chaînes selon la page de code actuellement utilisée. Pour plus d’informations, voir [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::CollateNoCase

Compare deux chaînes à l’aide `_tcscoll`de la fonction de texte générique .

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
L’autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les cordes sont identiques (ignorant le cas), < 0 `CStringT` si cet objet est inférieur à *psz* (cas ignorant), ou > 0 si cet `CStringT` objet est plus grand que *psz* (sans tenir compte du cas).

### <a name="remarks"></a>Notes

La fonction `_tcscoll`de texte générique , qui est définie dans TCHAR. H, cartes `stricoll`à `wcsicoll`l’un ou l’autre , , ou `_mbsicoll`, en fonction de l’ensemble de caractères qui est défini au moment de compilation. Chaque fonction effectue une comparaison insensible des chaînes, selon la page de code actuellement en service. Pour plus d’informations, voir [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a>CStringT::Comparez

Compare deux cordes (sensibles au boîtier).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
L’autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les cordes sont identiques, < `CStringT` 0 si cet objet est inférieur *à psz*, ou > 0 si cet `CStringT` objet est plus grand que *psz*.

### <a name="remarks"></a>Notes

La fonction `_tcscmp`de texte générique , qui est définie dans TCHAR. H, cartes `strcmp`à `wcscmp`l’un ou l’autre , , ou `_mbscmp`, en fonction de l’ensemble de caractères qui est défini au moment de compilation. Chaque fonction effectue une comparaison sensible aux cas des cordes et n’est pas affectée par le local. Pour plus d’informations, voir [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Si la chaîne contient des nulls intégrés, aux fins de comparaison, la chaîne est considérée comme tronquée au premier caractère indactif.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT::CompareNoCase

Compare deux cordes (insensibles aux cas).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
L’autre chaîne utilisée pour la comparaison.

### <a name="return-value"></a>Valeur de retour

Zéro si les cordes sont identiques (ignorant le cas), <0 si cet `CStringT` objet est inférieur à `CStringT` *psz* (cas ignorant), ou >0 si cet objet est plus grand que *psz* (sans tenir compte de cas).

### <a name="remarks"></a>Notes

La fonction `_tcsicmp`de texte générique , qui est définie dans TCHAR. H, cartes `_stricmp`à `_wcsicmp` `_mbsicmp`l’un ou l’autre, ou , en fonction de l’ensemble de caractères qui est défini au moment de compilation. Chaque fonction effectue une comparaison insensible des cordes. La comparaison dépend de l’aspect LC_CTYPE du lieu mais pas LC_COLLATE. Pour plus d’informations, voir [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a>CStringT::CStringt

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

*Pch*<br/>
Un pointeur à un tableau de caractères de longueur *nLength*, pas non non terminé.

*nLength (en)*<br/>
Un compte du nombre de caractères en *pch*.

*Ch*<br/>
Un seul personnage.

*pszSrc*<br/>
Une corde à résilier `CStringT` nulle à copier dans cet objet.

*pStringMgr*<br/>
Un pointeur pour le `CStringT` gestionnaire de mémoire pour l’objet. Pour plus `IAtlStringMgr` d’informations `CStringT`sur et la gestion de la mémoire pour , voir [Memory Management avec CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc (strSrc)*<br/>
Un `CStringT` objet existant à copier `CStringT` dans cet objet. Pour plus `CThisString` d’informations sur et `CThisSimpleString`, voir la section Remarques.

*varSrc*<br/>
Un objet de variante à `CStringT` copier dans cet objet.

*BaseType*<br/>
Le type de personnage de la classe de cordes. Il peut s'agir d'une des méthodes suivantes :

**char** (pour les cordes de caractère ANSI).

**wchar_t** (pour les chaînes de caractères Unicode).

TCHAR (pour les chaînes de caractères ANSI et Unicode).

*bMFCDLL (en)*<br/>
Boolean qui précise si le projet est un MFC DLL (TRUE) ou non (FALSE).

*SystemString (en)*<br/>
Doit `System::String`être, et le projet doit être compilé avec /clr.

*pString*<br/>
Une poignée `CStringT` pour un objet.

### <a name="remarks"></a>Notes

Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, vous devez être conscient que des exceptions de mémoire peuvent en résulter. Notez que certains de ces constructeurs agissent comme fonctions de conversion. Cela vous permet de remplacer, par exemple, `CStringT` un LPTSTR où un objet est attendu.

- `CStringT`( `LPCSTR` `lpsz` ): Construit un `CStringT` Unicode à partir d’une chaîne ANSI. Vous pouvez également utiliser ce constructeur pour charger une ressource de chaîne comme indiqué dans l’exemple ci-dessous.

- `CStringT(`): Construit `CStringT` un à partir d’une chaîne Unicode. `LPCWSTR` `lpsz`

- `CStringT`( `const unsigned char*` `psz` ): Vous permet `CStringT` de construire un pointeur à **char non signé**.

> [!NOTE]
> Définissez la macro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION pour désactiver la conversion implicite des chaînes entre les chaînes ANSI et Unicode. La macro exclut des constructeurs de compilation qui prennent en charge la conversion.

Notez que le paramètre *strSrc* peut être soit un ou `CStringT` `CThisSimpleString` un objet. Pour `CStringT`, utilisez l’une de`CString`ses `CStringA`instantanéisations par défaut ( , , ou `CStringW`); pour `CThisSimpleString`, utiliser un **ce** pointeur. `CThisSimpleString`déclare un exemple de la [classe CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), qui est une classe de `CStringT` cordes plus petite avec moins de fonctionnalité intégrée que la classe.

L’opérateur `CSimpleStringT<>&()` de surcharge `CStringT` construit `CSimpleStringT` un objet à partir d’une déclaration.

> [!NOTE]
> Bien qu’il `CStringT` soit possible de créer des instances qui contiennent des caractères nuls intégrés, nous recommandons contre elle. Les méthodes d’appel et les opérateurs sur `CStringT` les objets qui contiennent des caractères nuls intégrés peuvent produire des résultats imprévus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a>CStringT: :CStringT

Détruit l’objet. `CStringT`

```
~CStringT() throw();
```

### <a name="remarks"></a>Notes

Détruit l’objet. `CStringT`

## <a name="cstringtdelete"></a><a name="delete"></a>CStringT::Delete

Supprime un personnage ou des caractères d’une chaîne à partir du personnage à l’index donné.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
L’index zéro du premier personnage `CStringT` de l’objet à supprimer.

*nCompte*<br/>
Le nombre de caractères à supprimer.

### <a name="return-value"></a>Valeur de retour

La longueur de la corde changée.

### <a name="remarks"></a>Notes

Si *nCount* est plus long que la ficelle, le reste de la chaîne sera enlevé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a>CStringT::Trouver

Recherche cette chaîne pour le premier match d’un personnage ou d’un sous-corde.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Paramètres

*pszSub*<br/>
Un sous-cordon à rechercher.

*iStart (en)*<br/>
L’index du personnage dans la chaîne pour commencer la recherche avec, ou 0 pour commencer par le début.

*Ch*<br/>
Un seul personnage à rechercher.

### <a name="return-value"></a>Valeur de retour

L’index zéro du premier personnage `CStringT` de cet objet qui correspond au sous-corde demandé ou aux caractères; -1 si le sous-corde ou le caractère n’est pas trouvé.

### <a name="remarks"></a>Notes

La fonction est surchargée pour accepter à la fois `strchr`les caractères simples `strstr`(semblable à la fonction de run-time ) et les cordes (semblable à ).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a>CStringT::FindOneOf

Recherche cette chaîne pour le premier personnage qui correspond à tout personnage contenu dans *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Paramètres

*pszCharSet (en)*<br/>
Chaîne contenant des caractères pour correspondre.

### <a name="return-value"></a>Valeur de retour

L’index zéro du premier personnage de cette chaîne qui est également dans *pszCharSet*; -1 s’il n’y a pas de correspondance.

### <a name="remarks"></a>Notes

Trouve la première occurrence de l’un des personnages dans *pszCharSet*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a>CStringT::Format

Écrit des données `CStringT` formatées de la même manière que [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formate les données dans un tableau de caractères de type C.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Paramètres

*nFormatID (en)*<br/>
L’identifiant de ressources de chaîne qui contient la chaîne de contrôle de format.

*pszFormat*<br/>
Une chaîne de contrôle de format.

*Argument*<br/>
Arguments facultatifs.

### <a name="remarks"></a>Notes

Cette fonction formate et stocke une `CStringT`série de caractères et de valeurs dans le . Chaque argument facultatif (le cas échéant) est converti et la sortie selon les spécifications de format correspondantes dans *pszFormat* ou à partir de la ressource de chaîne identifiée par *nFormatID*.

L’appel échouera si l’objet de `Format`chaîne lui-même est offert comme paramètre pour . Par exemple, le code suivant donnera des résultats imprévisibles :

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Pour plus d’informations, consultez [Syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::FormatMessage

Formate une chaîne de messages.

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Paramètres

*nFormatID (en)*<br/>
L’identifiant de ressources de chaîne qui contient le texte de message non formé.

*pszFormat*<br/>
Points à la chaîne de format-contrôle. Il sera numérisé pour les inserts et formaté en conséquence. La chaîne de format est similaire aux chaînes de format de format de format de type *printf*de fonction en temps d’exécution, sauf qu’elle permet d’insérer les paramètres dans un ordre arbitraire.

*Argument*<br/>
Arguments facultatifs.

### <a name="remarks"></a>Notes

La fonction nécessite une définition de message comme entrée. La définition du message est déterminée par *pszFormat* ou à partir de la ressource de chaîne identifiée par *nFormatID*. La fonction copie le texte `CStringT` de message formaté à l’objet, traitant toutes les séquences d’insertion intégrées si demandé.

> [!NOTE]
> `FormatMessage`tente d’allouer la mémoire du système pour la chaîne nouvellement formatée. Si cette tentative échoue, une exception de mémoire est automatiquement lancée.

Chaque insert doit avoir un paramètre correspondant suivant le *paramètre pszFormat* ou *nFormatID.* Dans le texte du message, plusieurs séquences d’évacuation sont prises en charge pour formater dynamiquement le message. Pour plus d’informations, consultez la fonction [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) Windows dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::FormatMessageV

Formats une chaîne de message à l’aide d’une liste d’arguments variables.

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Points à la chaîne de format-contrôle. Il sera numérisé pour les inserts et formaté en conséquence. La chaîne de format est `printf`similaire aux chaînes de format de format de fonction-style run-time, sauf qu’elle permet d’insérer les paramètres dans un ordre arbitraire.

*pArgList (en)*<br/>
Pointeur à une liste d’arguments.

### <a name="remarks"></a>Notes

La fonction nécessite une définition de message comme entrée, déterminée par *pszFormat*. La fonction copie le texte de message formaté `CStringT` et une liste variable d’arguments à l’objet, le traitement des séquences d’insertion intégrées si demandé.

> [!NOTE]
> `FormatMessageV`appelle [CStringT::FormatMessage](#formatmessage), qui tente d’allouer la mémoire du système pour la chaîne nouvellement formatée. Si cette tentative échoue, une exception de mémoire est automatiquement lancée.

Pour plus d’informations, consultez la fonction [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) Windows dans le SDK Windows.

## <a name="cstringtformatv"></a><a name="formatv"></a>CStringT::FormatV

Formats une chaîne de message à l’aide d’une liste d’arguments variables.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Points à la chaîne de format-contrôle. Il sera numérisé pour les inserts et formaté en conséquence. La chaîne de format est `printf`similaire aux chaînes de format de format de fonction-style run-time, sauf qu’elle permet d’insérer les paramètres dans un ordre arbitraire.

*Args*<br/>
Pointeur à une liste d’arguments.

### <a name="remarks"></a>Notes

Écrit une chaîne formatée et une `CStringT` liste variable d’arguments à une chaîne de la même manière que `vsprintf_s` les formats de données dans un tableau de caractères de style C.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable

Définit la chaîne à la valeur de la variable d’environnement spécifiée.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Paramètres

*pszVar*<br/>
Pointeur vers une chaîne non terminée qui spécifie la variable de l’environnement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Récupère la valeur de la variable spécifiée à partir du bloc environnement du processus d’appel. La valeur est sous la forme d’une chaîne de caractères non terminés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a>CStringT::Insert

Insère un seul caractère ou un sous-cordon à l’index donné dans la chaîne.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
L’index du personnage devant lequel l’insertion aura lieu.

*Zsp*<br/>
Un pointeur à la sous-corde à insérer.

*Ch*<br/>
Le personnage à insérer.

### <a name="return-value"></a>Valeur de retour

La longueur de la corde changée.

### <a name="remarks"></a>Notes

Le *paramètre iIndex* identifie le premier personnage qui sera déplacé pour faire de la place pour le personnage ou le sous-corde. Si *nIndex* est nul, l’insertion se produira avant la chaîne entière. Si *nIndex* est plus élevé que la longueur de la chaîne, la fonction concatenate la chaîne actuelle et le nouveau matériau fourni par *ch* ou *psz*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a>CStringT::Gauche

Extrait les caractères *nCount* `CStringT` les plus à gauche de cet objet et renvoie une copie du sous-corde extrait.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Paramètres

*nCompte*<br/>
Nombre de caractères à extraire de cet objet `CStringT`.

### <a name="return-value"></a>Valeur de retour

Objet `CStringT` qui contient une copie de la plage spécifiée des caractères. L'objet retourné par `CStringT` peut être vide.

### <a name="remarks"></a>Notes

Si *nCount* dépasse la longueur de la chaîne, la chaîne entière est extraite. `Left` est similaire à la fonction de base `Left`.

Pour les ensembles de caractères multi-byte (MBCS), *nCount* traite chaque séquence 8 bits comme un personnage, de sorte que *nCount* retourne le nombre de caractères multi-byte multiplié par deux.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a>CStringT::LoadString

Lit une ressource de chaîne Windows, identifiée `CStringT` par *nID*, dans un objet existant.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
Une poignée à l’instance du module.

*nID*<br/>
Un id de ressource de chaîne Windows.

*wLanguageID (en)*<br/>
La langue de la ressource à cordes.

### <a name="return-value"></a>Valeur de retour

Nonzero si la charge de ressources a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Charge la ressource de chaîne (*nID*) du module spécifié (*hInstance*) en utilisant la langue spécifiée (*wLanguage*).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a>CStringT::MakeLower

Convertit `CStringT` l’objet en une chaîne minuscule.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Valeur de retour

La chaîne inférieure résultante.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a>CStringT::MakeReverse

Inverse l’ordre des caractères de l’objet. `CStringT`

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Valeur de retour

La chaîne inversée qui en résulte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a>CStringT::MakeUpper

Convertit `CStringT` l’objet en une corde supérieure.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Valeur de retour

La chaîne supérieure résultante.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a>CStringT::Mid

Extrait un sous-cordon de la longueur `CStringT` *nCount* caractères de cet objet, à partir de la position *iFirst* (zéro-basé).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Paramètres

*iFirst*<br/>
L’index zéro du premier personnage `CStringT` de cet objet qui doit être inclus dans le sous-corde extrait.

*nCompte*<br/>
Nombre de caractères à extraire de cet objet `CStringT`. Si ce paramètre n’est pas fourni, le reste de la chaîne est extrait.

### <a name="return-value"></a>Valeur de retour

Objet `CStringT` qui contient une copie de la plage spécifiée des caractères. Notez que `CStringT` l’objet retourné peut être vide.

### <a name="remarks"></a>Notes

La fonction renvoie une copie du sous-corde extrait. `Mid`est similaire à la fonction Basic Mid (sauf que les index de Base sont basés sur un).

Pour les ensembles de caractères multioctets (MBCS), *nCount* se réfère à chaque personnage 8 bits; c’est-à-dire qu’un fil et un byte de sentier dans un personnage multioctet sont comptés comme deux caractères.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a>CStringT::OemToAnsi

Convertit tous les `CStringT` personnages de cet objet à partir du personnage OEM mis à l’ensemble de caractères ANSI.

```
void OemToAnsi();
```

### <a name="remarks"></a>Notes

Cette fonction n’est pas disponible si _UNICODE est définie.

### <a name="example"></a>Exemple

Voir l’exemple pour [CStringT:AnsiTooem](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a>CStringT::opérateur

Attribue une nouvelle valeur à la chaîne.

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

*strSrc (strSrc)*<br/>
A `CStringT` à attribuer à cette chaîne.

*Str*<br/>
Référence à un objet `CThisSimpleString`.

*bMFCDLL (en)*<br/>
Un boolean précisant si le projet est un DLL MFC ou non.

*BaseType*<br/>
Le type de base de chaîne.

*Var*<br/>
Un objet de variante à attribuer à cette chaîne.

*Ch*<br/>
Un caractère ANSI ou Unicode à attribuer à la chaîne.

*pszSrc*<br/>
Un pointeur à la corde d’origine assignée.

### <a name="remarks"></a>Notes

L’opérateur d’affectation accepte un autre `CStringT` objet, un pointeur de caractère ou un seul caractère. Vous devez être conscient que des exceptions de mémoire peuvent se produire chaque fois que vous utilisez cet opérateur parce que le nouveau stockage peut être alloué.

Pour plus `CThisSimpleString`d’informations sur , voir la section Remarques de [CStringT::CStringT](#cstringt).

> [!NOTE]
> Bien qu’il `CStringT` soit possible de créer des instances qui contiennent des caractères nuls intégrés, nous recommandons contre elle. Les méthodes d’appel et les opérateurs sur `CStringT` les objets qui contiennent des caractères nuls intégrés peuvent produire des résultats imprévus.

## <a name="cstringtoperator-"></a><a name="operator_add"></a>CStringT::opérateur

Concatenates deux cordes ou un personnage et une corde.

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

*ch1 (en)*<br/>
Un caractère ANSI ou Unicode pour concatenate avec une chaîne.

*ch2*<br/>
Un caractère ANSI ou Unicode pour concatenate avec une chaîne.

*str1*<br/>
A `CStringT` pour concatenate avec une ficelle ou un caractère.

*str2*<br/>
A `CStringT` pour concatenate avec une ficelle ou un caractère.

*psz1 (psz1)*<br/>
Un pointeur à une corde non terminée pour concatenate avec une ficelle ou un caractère.

*psz2*<br/>
Un pointeur à une corde pour concatenate avec une corde ou un caractère.

### <a name="remarks"></a>Notes

Il existe sept formes `CStringT::operator+` de surcharge de la fonction. La première version concatenates deux objets existants. `CStringT` Les deux suivants concatenent un `CStringT` objet et une corde non terminée. Les deux suivants concatenent un `CStringT` objet et un caractère ANSI. Les deux derniers concatenent un `CStringT` objet et un personnage Unicode.

> [!NOTE]
> Bien qu’il `CStringT` soit possible de créer des instances qui contiennent des caractères nuls intégrés, nous recommandons contre elle. Les méthodes d’appel et les opérateurs sur `CStringT` les objets qui contiennent des caractères nuls intégrés peuvent produire des résultats imprévus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::opérateur

Concatenates caractères à la fin de la chaîne.

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

*Str*<br/>
Référence à un objet `CThisSimpleString`.

*bMFCDLL (en)*<br/>
Un boolean précisant si le projet est un DLL MFC ou non.

*BaseType*<br/>
Le type de base de chaîne.

*Var*<br/>
Un objet variante à concatenate à cette chaîne.

*Ch*<br/>
Un caractère ANSI ou Unicode pour concatenate avec une chaîne.

*pszSrc*<br/>
Un pointeur à la corde d’origine étant concatenated.

*strSrc (strSrc)*<br/>
A `CStringT` pour concatenate à cette chaîne.

### <a name="remarks"></a>Notes

L’opérateur accepte `CStringT` un autre objet, un pointeur de caractère ou un seul personnage. Vous devez être conscient que des exceptions de mémoire peuvent se produire chaque fois que `CStringT` vous utilisez cet opérateur de concatenation parce que le nouveau stockage peut être alloué pour les caractères ajoutés à cet objet.

Pour plus `CThisSimpleString`d’informations sur , voir la section Remarques de [CStringT::CStringT](#cstringt).

> [!NOTE]
> Bien qu’il `CStringT` soit possible de créer des instances qui contiennent des caractères nuls intégrés, nous recommandons contre elle. Les méthodes d’appel et les opérateurs sur `CStringT` les objets qui contiennent des caractères nuls intégrés peuvent produire des résultats imprévus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::opérateur

Détermine si deux cordes sont logiquement égales.

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

*ch1 (en)*<br/>
Un caractère ANSI ou Unicode à titre de comparaison.

*ch2*<br/>
Un caractère ANSI ou Unicode à titre de comparaison.

*str1*<br/>
A `CStringT` à comparer.

*str2*<br/>
A `CStringT` à comparer.

*psz1 (psz1)*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

*psz2*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

### <a name="remarks"></a>Notes

Teste si une chaîne ou un personnage sur le côté gauche est égal à une chaîne ou un personnage sur le côté droit, et retourne TRUE ou FALSE en conséquence.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a>CStringT::opérateur !

Détermine si deux cordes ne sont logiquement pas égales.

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

*ch1 (en)*<br/>
Un caractère ANSI ou Unicode pour concatenate avec une chaîne.

*ch2*<br/>
Un caractère ANSI ou Unicode pour concatenate avec une chaîne.

*str1*<br/>
A `CStringT` à comparer.

*str2*<br/>
A `CStringT` à comparer.

*psz1 (psz1)*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

*psz2*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

### <a name="remarks"></a>Notes

Test si une chaîne ou un personnage sur le côté gauche n’est pas égal à une chaîne ou un personnage sur le côté droit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::opérateur&lt;

Détermine si la ficelle du côté gauche de l’opérateur est inférieure à la corde sur le côté droit.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
A `CStringT` à comparer.

*str2*<br/>
A `CStringT` à comparer.

*psz1 (psz1)*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

*psz2*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre les cordes, caractère par personnage jusqu’à :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::opérateur&gt;

Détermine si la ficelle du côté gauche de l’opérateur est supérieure à la corde sur le côté droit.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
A `CStringT` à comparer.

*str2*<br/>
A `CStringT` à comparer.

*psz1 (psz1)*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

*psz2*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre les cordes, caractère par personnage jusqu’à :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::opérateur&lt;=

Détermine si la corde du côté gauche de l’opérateur est inférieure ou égale à la corde sur le côté droit.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
A `CStringT` à comparer.

*str2*<br/>
A `CStringT` à comparer.

*psz1 (psz1)*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

*psz2*<br/>
Un pointeur à une chaîne annulée pour la comparaison.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre les cordes, caractère par personnage jusqu’à :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::opérateur&gt;=

Détermine si la ficelle du côté gauche de l’opérateur est supérieure ou égale à la corde sur le côté droit.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
A `CStringT` à comparer.

*str2*<br/>
A `CStringT` à comparer.

*psz1 (psz1)*<br/>
Un pointeur à une chaîne pour la comparaison.

*psz2*<br/>
Un pointeur à une chaîne pour la comparaison.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre les cordes, caractère par personnage jusqu’à :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a>CStringT::Supprimer

Supprime tous les cas du caractère spécifié de la chaîne.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Paramètres

*chRemove chRemove*<br/>
Le personnage à retirer d’une chaîne.

### <a name="return-value"></a>Valeur de retour

Le nombre de caractères retirés de la corde. Zéro si la chaîne n’est pas changée.

### <a name="remarks"></a>Notes

Les comparaisons pour le personnage sont sensibles aux cas.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a>CStringT::Remplacer

Il existe deux `Replace`versions de . La première version remplace une ou plusieurs copies d’un sous-corde en utilisant un autre sous-corde. Les deux sous-cordes sont non terminées. La deuxième version remplace une ou plusieurs copies d’un personnage en utilisant un autre personnage. Les deux versions fonctionnent sur `CStringT`les données de caractère stockées dans .

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Paramètres

*pszOld*<br/>
Un pointeur à une corde non terminée pour être remplacé par *pszNew*.

*pszNouvelle*<br/>
Un pointeur à une corde non terminée qui remplace *pszOld*.

*chOld chOld*<br/>
Le personnage à remplacer par *chNew*.

*chNouvelle*<br/>
Le personnage remplaçant *chOld*.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’instances remplacées du personnage ou du sous-corde, ou zéro si la chaîne n’est pas modifiée.

### <a name="remarks"></a>Notes

`Replace`peut changer la longueur de la chaîne parce que *pszNew* et *pszOld* n’ont pas à être de la même longueur, et plusieurs copies de l’ancien sous-corde peut être changé pour le nouveau. La fonction effectue un match sensible aux cas.

Exemples `CStringT` d’exemples sont `CString`, `CStringA`, et `CStringW`.

Pour `CStringA` `Replace` , travaille avec ANSI ou multioctets (MBCS) caractères. Pour `CStringW` `Replace` , fonctionne avec de larges personnages.

Pour `CString`, le type de données de caractère est sélectionné au moment de la compilation, en fonction de la définition des constantes dans le tableau suivant.

|Constant défini|Type de données de caractère|
|----------------------|-------------------------|
|_UNICODE|Caractères larges|
|_MBCS|Personnages multi-byte|
|Aucun|Personnages uni-byte|
|Les deux|Indéfini|

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a>CStringT::ReverseFind

Recherche `CStringT` cet objet pour le dernier match d’un personnage.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Paramètres

*Ch*<br/>
Le personnage à rechercher.

### <a name="return-value"></a>Valeur de retour

L’index à base zéro du `CStringT` dernier personnage de cet objet qui correspond au caractère demandé, ou -1 si le personnage n’est pas trouvé.

### <a name="remarks"></a>Notes

La fonction est similaire à `strrchr`la fonction de temps d’exécution.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a>CStringT::Droite

Extrait le dernier (c’est-à-dire, `CStringT` *c’est-à-dire* le plus) des caractères nCount de cet objet et renvoie une copie du sous-corde extrait.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Paramètres

*nCompte*<br/>
Nombre de caractères à extraire de cet objet `CStringT`.

### <a name="return-value"></a>Valeur de retour

Objet `CStringT` qui contient une copie de la plage spécifiée des caractères. Notez que `CStringT` l’objet retourné peut être vide.

### <a name="remarks"></a>Notes

Si *nCount* dépasse la longueur de la chaîne, la chaîne entière est extraite. `Right`est similaire à `Right` la fonction de base (sauf que les index de Base sont basés à zéro).

Pour les ensembles de caractères multioctets (MBCS), *nCount* se réfère à chaque personnage 8 bits; c’est-à-dire qu’un fil et un byte de sentier dans un personnage multioctet sont comptés comme deux caractères.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString

Réaffecte le BSTR pointé par *pbstr* et copie le contenu de l’objet `CStringT` en elle, y compris le caractère NULL.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Paramètres

*pbstr pbstr*<br/>
Un pointeur à une chaîne de caractère.

### <a name="return-value"></a>Valeur de retour

La nouvelle chaîne.

### <a name="remarks"></a>Notes

Selon le contenu `CStringT` de l’objet, la valeur du BSTR référencé par *pbstr* peut changer. La fonction jette `CMemoryException` une mémoire si insuffisante existe.

Cette fonction est normalement utilisée pour modifier la valeur des chaînes transmises par référence pour Automation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::SpanExcluding

Extrait des personnages de la chaîne, à commencer par le premier personnage, qui ne sont pas dans l’ensemble des personnages identifiés par *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Paramètres

*pszCharSet (en)*<br/>
Une chaîne interprétée comme un ensemble de personnages.

### <a name="return-value"></a>Valeur de retour

Un sous-corde qui contient des caractères dans la chaîne qui ne sont pas dans *pszCharSet*, en commençant par le premier personnage de la chaîne et se terminant par le premier personnage trouvé dans la chaîne qui est également dans *pszCharSet* (c’est-à-dire, à commencer par le premier personnage dans la chaîne et jusqu’à mais à l’exclusion du premier personnage de la chaîne qui se trouve *pszCharSet*). Il renvoie la chaîne entière si aucun personnage dans *pszCharSet* se trouve dans la chaîne.

### <a name="remarks"></a>Notes

`SpanExcluding`extraits et renvois tous les personnages précédant la première occurrence d’un personnage de *pszCharSet* (en d’autres termes, le personnage de *pszCharSet* et tous les personnages qui le suivent dans la chaîne, ne sont pas retournés). Si aucun personnage de *pszCharSet* n’est trouvé dans la chaîne, retourne alors `SpanExcluding` la chaîne entière.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::SpanIncluding

Extrait des personnages de la chaîne, à commencer par le premier personnage, qui sont dans l’ensemble des personnages identifiés par *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Paramètres

*pszCharSet (en)*<br/>
Une chaîne interprétée comme un ensemble de personnages.

### <a name="return-value"></a>Valeur de retour

Un sous-cordon qui contient des caractères dans la chaîne qui sont dans *pszCharSet*, en commençant par le premier personnage dans la chaîne et se terminant quand un personnage se trouve dans la chaîne qui n’est pas dans *pszCharSet*. `SpanIncluding`retourne une sous-corde vide si le premier personnage de la chaîne n’est pas dans l’ensemble spécifié.

### <a name="remarks"></a>Notes

Si le premier personnage de la corde n’est pas dans l’ensemble de caractères, retourne alors `SpanIncluding` une chaîne vide. Sinon, il renvoie une séquence de personnages consécutifs qui sont dans l’ensemble.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a>CStringT::Tokenize

Trouve le prochain jeton dans une chaîne cible

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Paramètres

*pszTokens*<br/>
Une chaîne contenant des délimitants symboliques. L’ordre de ces délimitants n’est pas important.

*iStart (en)*<br/>
L’index zéro pour commencer la recherche.

### <a name="return-value"></a>Valeur de retour

Un `CStringT` objet contenant la valeur symbolique actuelle.

### <a name="remarks"></a>Notes

La `Tokenize` fonction trouve le jeton suivant dans la chaîne cible. L’ensemble de caractères dans *pszTokens* spécifie délimitations possibles du jeton à trouver. Sur chaque `Tokenize` appel à la fonction commence à *iStart*, saute `CStringT` les délimitations de premier plan, et retourne un objet contenant le jeton actuel, qui est la chaîne de caractères jusqu’au caractère délimital suivant. La valeur *d’iStart* est mise à jour pour être la position suivant le caractère de délimital de fin, ou -1 si la fin de la chaîne a été atteinte. Plus de jetons peuvent être brisés du reste de la `Tokenize`chaîne cible par une série d’appels à , en utilisant *iStart* pour garder une trace de l’endroit dans la chaîne le jeton suivant doit être lu. Quand il n’y a plus de jetons, la fonction retournera une chaîne vide et *iStart* sera réglé à -1.

Contrairement aux fonctions de jetonisation CRT comme [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` ne modifie pas la chaîne cible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Notes

La sortie de cet exemple est la suivante :

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a>CStringT::Trim

Coupe des personnages de premier plan et de fuite de la corde.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Paramètres

*chTarget chTarget*<br/>
Le caractère cible à couper.

*pszTargets*<br/>
Un pointeur à une chaîne contenant les caractères cibles à couper. Tous les événements de tête et de fuite des caractères `CStringT` dans *pszTarget* seront coupés de l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la ficelle taillée.

### <a name="remarks"></a>Notes

Supprime tous les événements de premier plan et de fuite de l’un des éléments suivants :

- Le caractère spécifié par *chTarget*.

- Tous les caractères trouvés dans la chaîne spécifiée par *pszTargets*.

- Espaces.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Notes

La sortie de cet exemple est la suivante :

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a>CStringT::TrimLeft

Coupe les personnages principaux de la chaîne.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Paramètres

*chTarget chTarget*<br/>
Le caractère cible à couper.

*pszTargets*<br/>
Un pointeur à une chaîne contenant les caractères cibles à couper. Toutes les occurrences principales des caractères dans *pszTarget* seront taillées à partir de l’objet. `CStringT`

### <a name="return-value"></a>Valeur de retour

La ficelle taillée qui en résulte.

### <a name="remarks"></a>Notes

Supprime tous les événements de premier plan et de fuite de l’un des éléments suivants :

- Le caractère spécifié par *chTarget*.

- Tous les caractères trouvés dans la chaîne spécifiée par *pszTargets*.

- Espaces.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a>CStringT::TrimRight

Trims trailing personnages de la chaîne.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Paramètres

*chTarget chTarget*<br/>
Le caractère cible à couper.

*pszTargets*<br/>
Un pointeur à une chaîne contenant les caractères cibles à couper. Tous les événements de fuite des caractères dans *pszTarget* seront coupés de l’objet. `CStringT`

### <a name="return-value"></a>Valeur de retour

Retourne `CStringT` l’objet qui contient la ficelle taillée.

### <a name="remarks"></a>Notes

Supprime les événements de fuite de l’un des éléments suivants :

- Le caractère spécifié par *chTarget*.

- Tous les caractères trouvés dans la chaîne spécifiée par *pszTargets*.

- Espaces.

La `CStringT& TrimRight(XCHAR chTarget)` version accepte un paramètre de caractère et supprime `CStringT` toutes les copies de ce personnage de la fin des données de chaîne. Il commence à partir de la fin de la corde et fonctionne vers l’avant. Il s’arrête quand il `CSTringT` trouve un caractère différent ou quand il est à court de données de caractère.

La `CStringT& TrimRight(PCXSTR pszTargets)` version accepte une chaîne non terminée qui contient tous les différents caractères à rechercher. Il supprime toutes les copies `CStringT` de ces caractères dans l’objet. Il commence à la fin de la corde et fonctionne vers l’avant. Il s’arrête lorsqu’il trouve un personnage qui `CStringT` n’est pas dans la chaîne cible, ou lorsqu’il est à court de données de caractère. Il n’essaie pas d’égaler l’ensemble de la `CStringT`chaîne cible à un sous-corde à la fin de .

La `CStringT& TrimRight()` version ne nécessite aucun paramètre. Il coupe tous les personnages de l’espace blanc de fuite de la fin de la `CStringT` chaîne. Les caractères Whitespace peuvent être des sauts de ligne, des espaces ou des onglets.

-

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[Classe CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)
