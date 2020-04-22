---
title: Classe CComBSTR
ms.date: 11/04/2016
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: c1448a5638b263a87403edf0baca170f0f952e26
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748139"
---
# <a name="ccombstr-class"></a>Classe CComBSTR

Cette classe est un emballage pour [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Syntaxe

```
class CComBSTR
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|Constructeur.|
|[CComBSTR: CComBSTR](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComBSTR::Annexe](#append)|Annexe une corde `m_str`à .|
|[CComBSTR::AppendBSTR](#appendbstr)|Annexe d’un BSTR à `m_str`.|
|[CComBSTR::AppendBytes](#appendbytes)|Annexe un nombre spécifié d’octets à `m_str`.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crée un BSTR à partir du premier caractère de chaque élément `CComBSTR` dans le safearray et le fixe à l’objet.|
|[CComBSTR::AssignBSTR](#assignbstr)|Assigne un BSTR à `m_str`.|
|[CComBSTR::Attach](#attach)|Attache un BSTR `CComBSTR` à l’objet.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crée une mise en sécurité unidimensionnelle à base zéro, où `CComBSTR` chaque élément du tableau est un personnage de l’objet.|
|[CComBSTR::ByteLength](#bytelength)|Retourne la `m_str` longueur des octets.|
|[CComBSTR::Copie](#copy)|Retourne une `m_str`copie de .|
|[CComBSTR::CopyTo](#copyto)|Retourne une `m_str` copie de l’intermédiaire d’un paramètre **[out]**|
|[CComBSTR::Detach](#detach)|Se `m_str` détache de `CComBSTR` l’objet.|
|[CComBSTR::Vide](#empty)|Frees `m_str`.|
|[CComBSTR::Longueur](#length)|Retourne la `m_str`longueur de .|
|[CComBSTR::LoadString](#loadstring)|Charge une ressource de chaîne.|
|[CComBSTR::LireDestream](#readfromstream)|Charge un objet BSTR à partir d’un flux.|
|[CComBSTR::ToLower](#tolower)|Convertit la ficelle en minuscule.|
|[CComBSTR::ToUpper](#toupper)|Convertit la ficelle en uppercase.|
|[CComBSTR::WriteToStream](#writetostream)|Enregistre `m_str` à un flux.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR::opérateur BSTR](#operator_bstr)|Jette un `CComBSTR` objet à un BSTR.|
|[CComBSTR::opérateur !](#operator_not)|Retourne TRUE ou FALSE, `m_str`selon qu’il s’agisse de NULL.|
|[CComBSTR::opérateur !](#operator_neq)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR::opérateur &](#operator_amp)|Retourne l’adresse de `m_str`.|
|[CComBSTR::opérateur](#operator_add_eq)|Annexe à `CComBSTR` l’objet.|
|[CComBSTR::opérateur <](#operator_lt)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR::opérateur](#operator_eq)|Assigne une `m_str`valeur à .|
|[CComBSTR::opérateur](#operator_eq_eq)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR::opérateur >](#operator_gt)|Compare un `CComBSTR` avec une chaîne.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR:m_str](#m_str)|Contient le BSTR `CComBSTR` associé à l’objet.|

## <a name="remarks"></a>Notes

La `CComBSTR` classe est un emballage pour les BSTRs, qui sont des cordes préfixées sur la longueur. La longueur est stockée comme un intégrant à l’emplacement de mémoire précédant les données dans la chaîne.

Un [BSTR](/previous-versions/windows/desktop/automat/bstr) est annulé après le dernier caractère compté, mais peut également contenir des caractères nuls intégrés dans la chaîne. La longueur de la chaîne est déterminée par le nombre de personnages, et non par le premier caractère nul.

> [!NOTE]
> La `CComBSTR` classe fournit un certain nombre de membres (constructeurs, opérateurs d’affectation, et les opérateurs de comparaison) qui prennent soit ansI ou Unicode chaînes comme arguments. Les versions ANSI de ces fonctions sont moins efficaces que leurs homologues Unicode car les chaînes Unicode temporaires sont souvent créées en interne. Pour plus d’efficacité, utilisez les versions Unicode dans la mesure du possible.

> [!NOTE]
> En raison de l’amélioration du comportement de recherche `bstr = L"String2" + bstr;`mis en œuvre dans Visual Studio `bstr = CStringW(L"String2") + bstr`.NET, code tel que , qui peut avoir compilé dans les versions précédentes, devrait plutôt être mis en œuvre comme .

Pour une liste de `CComBSTR`mises en garde lors de l’utilisation , voir [Programmation avec CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccombstrappend"></a><a name="append"></a>CComBSTR::Annexe

Annexes *lpsz* ou le membre BSTR de *bstrSrc* à [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc (en)*<br/>
[dans] Un `CComBSTR` objet à appendice.

*Ch*<br/>
[dans] Un personnage à appendice.

*lpsz lpsz*<br/>
[dans] Une chaîne de caractère à zéro fin à l’annexe. Vous pouvez passer une chaîne Unicode via la surcharge LPCOLESTR ou une chaîne ANSI via la version LPCSTR.

*nLen (en)*<br/>
[dans] Le nombre de caractères de *lpsz* à l’annexe.

### <a name="return-value"></a>Valeur de retour

S_OK sur le succès, ou toute valeur d’erreur HRESULT standard.

### <a name="remarks"></a>Notes

Une chaîne ANSI sera convertie en Unicode avant d’être jointe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::AppendBSTR

Annexes du BSTR spécifié à [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Un BSTR à annexer.

### <a name="return-value"></a>Valeur de retour

S_OK sur le succès, ou toute valeur d’erreur HRESULT standard.

### <a name="remarks"></a>Notes

Ne passez pas une corde ordinaire à caractère large à cette méthode. Le compilateur ne peut pas attraper l’erreur et des erreurs de temps d’exécution se produiront.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::AppendBytes

Annexe le nombre spécifié d’octets à [m_str](#m_str) sans conversion.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Paramètres

*lpsz lpsz*<br/>
[dans] Un pointeur à un tableau d’octets à l’annexe.

*P*<br/>
[dans] Le nombre d’octets à ajouter.

### <a name="return-value"></a>Valeur de retour

S_OK sur le succès, ou toute valeur d’erreur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArrayToBSTR

Libère toute chaîne existante `CComBSTR` tenue dans l’objet, puis crée un BSTR à partir du premier `CComBSTR` caractère de chaque élément dans le safearray et l’attache à l’objet.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Paramètres

*pSrc (en)*<br/>
[dans] Le safearray contenant les éléments utilisés pour créer la chaîne.

### <a name="return-value"></a>Valeur de retour

S_OK sur le succès, ou toute valeur d’erreur HRESULT standard.

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::AssignBSTR

Assigne un BSTR à [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc (en)*<br/>
[dans] Un BSTR à attribuer `CComBSTR` à l’objet actuel.

### <a name="return-value"></a>Valeur de retour

S_OK sur le succès, ou toute valeur d’erreur HRESULT standard.

## <a name="ccombstrattach"></a><a name="attach"></a>CComBSTR::Attach

Attache un BSTR `CComBSTR` à l’objet en plaçant le [membre m_str](#m_str) à *src*.

```cpp
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] Le BSTR à attacher à l’objet.

### <a name="remarks"></a>Notes

Ne passez pas une corde ordinaire à caractère large à cette méthode. Le compilateur ne peut pas attraper l’erreur et des erreurs de temps d’exécution se produiront.

> [!NOTE]
> Cette méthode s’affirmera si elle `m_str` n’est pas NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR::BSTRToArray

Crée une mise en sécurité unidimensionnelle à base zéro, où `CComBSTR` chaque élément du tableau est un personnage de l’objet.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
[out] Le pointeur de la safearray utilisé pour tenir les résultats de la fonction.

### <a name="return-value"></a>Valeur de retour

S_OK sur le succès, ou toute valeur d’erreur HRESULT standard.

## <a name="ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR::ByteLength

Retourne le nombre d’octets dans , à `m_str`l’exclusion du caractère nul de fin.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

La longueur du [m_str](#m_str) membre dans les octets.

### <a name="remarks"></a>Notes

Retours 0 s’il `m_str` est NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR::CComBSTR

Constructeur. Le constructeur par défaut définit le [m_str](#m_str) membre à NULL.

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
[dans] Le nombre de caractères à copier à partir `CComBSTR` *de sz* ou la taille initiale dans les caractères pour le .

*Sz*<br/>
[in] Chaîne à copier. La version Unicode spécifie un LPCOLESTR; la version ANSI spécifie un LPCSTR.

*pSrc (en)*<br/>
[in] Chaîne à copier. La version Unicode spécifie un LPCOLESTR; la version ANSI spécifie un LPCSTR.

*src*<br/>
[in] Objet `CComBSTR`

*guid*<br/>
[dans] Une référence `GUID` à une structure.

### <a name="remarks"></a>Notes

Le constructeur de `m_str` copie s’installe à une copie du membre BSTR de *src*. Le `REFGUID` constructeur convertit le GUID `StringFromGUID2` en une chaîne à l’aide et stocke le résultat.

Les autres constructeurs affectent à `m_str` une copie de la chaîne spécifiée. Si vous passez une valeur pour *nSize*, alors seuls *les caractères nSize* seront copiés, suivis d’un caractère nul de fin.

`CComBSTR` prend en charge la sémantique de déplacement. Vous pouvez utiliser le constructeur de déplacement (constructeur qui accepte une référence rvalue (`&&`)) pour créer un nouvel objet utilisant les mêmes données sous-jacentes que l'ancien objet que vous transmettez comme argument, sans la surcharge propre à la copie de l'objet.

Le destructeur libère la chaîne pointée par `m_str`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a>CComBSTR: CComBSTR

Destructeur.

```
~CComBSTR();
```

### <a name="remarks"></a>Notes

Le destructeur libère la chaîne pointée par `m_str`.

## <a name="ccombstrcopy"></a><a name="copy"></a>CComBSTR::Copie

Alloue et renvoie une copie de `m_str`.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Valeur de retour

Une copie du [membre m_str.](#m_str) S’il `m_str` est NULL, retourne NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::CopyTo

Alloue et renvoie une copie de [m_str](#m_str) via le paramètre.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Paramètres

*pbstr pbstr*<br/>
[out] L’adresse d’un BSTR dans lequel retourner la chaîne allouée par cette méthode.

*pvarDest*<br/>
[out] L’adresse d’un VARIANT dans lequel retourner la chaîne allouée par cette méthode.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard indiquant le succès ou l’échec de la copie.

### <a name="remarks"></a>Notes

Après avoir appelé cette méthode, le VARIANT pointé par *pvarDest* sera de type VT_BSTR.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a>CComBSTR::Detach

Détache [m_str](#m_str) de l’objet `CComBSTR` et `m_str` se met en NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Le BSTR associé `CComBSTR` à l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a>CComBSTR::Vide

Libère le [m_str](#m_str) membre.

```cpp
void Empty() throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a>CComBSTR::Longueur

Retourne le nombre `m_str`de caractères dans , à l’exclusion du caractère nul de fin.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Valeur de retour

La durée du [m_str](#m_str) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::LoadString

Charge une ressource de chaîne spécifiée par *nID* et la stocke dans cet objet.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Paramètres

Voir [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) in the Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la chaîne est chargée avec succès; autrement, retourne FALSE.

### <a name="remarks"></a>Notes

La première fonction charge la ressource du module identifié par vous via le *paramètre hInst.* La deuxième fonction charge la ressource du module de ressources associé à l’objet dérivé de [CComModule](../../atl/reference/ccommodule-class.md)utilisé dans ce projet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a>CComBSTR:m_str

Contient le BSTR `CComBSTR` associé à l’objet.

```
BSTR m_str;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::opérateur BSTR

Jette un `CComBSTR` objet à un BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Notes

Vous permet de `CComBSTR` passer des objets à des fonctions qui ont [dans] les paramètres **BSTR.**

### <a name="example"></a>Exemple

Voir l’exemple pour [CComBSTR:m_str](#m_str).

## <a name="ccombstroperator-"></a><a name="operator_not"></a>CComBSTR::opérateur !

Vérifie si la chaîne BSTR est NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le [membre m_str](#m_str) est NULL; autrement, FALSE.

### <a name="remarks"></a>Notes

Cet opérateur ne vérifie qu’une valeur NULL, et non pour une chaîne vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::opérateur !

Retourne le contraire logique de [l’opérateur .](#operator_eq_eq)

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc (en)*<br/>
[in] Objet `CComBSTR`

*pszSrc*<br/>
[dans] Une ficelle à zéro.

*nNull (nNull)*<br/>
[dans] Ca doit être NULL.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément comparé `CComBSTR` n’est pas égal à l’objet; autrement, retourne FALSE.

### <a name="remarks"></a>Notes

`CComBSTR`sont comparés textuellement dans le contexte du lieu par défaut de l’utilisateur. L’opérateur de comparaison final compare simplement la chaîne contenue par rapport à NULL.

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::opérateur&amp;

Retourne l’adresse du BSTR stocké dans le [m_str](#m_str) membre.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Notes

`CComBstr operator &`a une affirmation particulière associée à elle pour aider à identifier les fuites de mémoire. Le programme s’affirmera lorsque le `m_str` membre sera parasécé. Cette affirmation a été créée pour identifier `& operator` les situations où un programmeur utilise le pour attribuer une nouvelle valeur au `m_str` membre sans libérer la première allocation de `m_str`. Si `m_str` l’on veut dire NULL, le programme suppose que m_str n’a pas encore été allouée. Dans ce cas, le programme ne fera pas d’affirmation.

Cette affirmation n’est pas activée par défaut. Définir ATL_CCOMBSTR_ADDRESS_OF_ASSERT pour permettre cette affirmation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::opérateur

Annexe une corde à `CComBSTR` l’objet.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Paramètres

*bstrSrc (en)*<br/>
[dans] Un `CComBSTR` objet à appendice.

*pszSrc*<br/>
[dans] Une ficelle à zéro fin à l’annexe.

### <a name="remarks"></a>Notes

`CComBSTR`sont comparés textuellement dans le contexte du lieu par défaut de l’utilisateur. La comparaison LPCOLESTR `memcmp` se fait à l’aide des données brutes de chaque chaîne. La comparaison LPCSTR est effectuée de la même manière une fois qu’une copie temporaire Unicode de *pszSrc* a été créée. L’opérateur de comparaison final compare simplement la chaîne contenue par rapport à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::opérateur&lt;

Compare un `CComBSTR` avec une chaîne.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément comparé `CComBSTR` est inférieur à l’objet; autrement, retourne FALSE.

### <a name="remarks"></a>Notes

La comparaison est effectuée à l’aide du lieu par défaut de l’utilisateur.

## <a name="ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::opérateur

Définit le [m_str](#m_str) membre à une copie de *pSrc* ou à une copie du membre BSTR de *src*. L’opérateur d’affectation de déménagement se déplace `src` sans le copier.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Notes

Le paramètre *pSrc* spécifie soit un LPCOLESTR pour les versions Unicode, soit un LPCSTR pour les versions ANSI.

### <a name="example"></a>Exemple

Voir l’exemple pour [CComBSTR:Copy](#copy).

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::opérateur

Compare un `CComBSTR` avec une chaîne. `CComBSTR`sont comparés textuellement dans le contexte du lieu par défaut de l’utilisateur.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc (en)*<br/>
[in] Objet `CComBSTR`

*pszSrc*<br/>
[dans] Une ficelle à zéro.

*nNull (nNull)*<br/>
[dans] Ca doit être NULL.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément comparé `CComBSTR` est égal à l’objet; autrement, retourne FALSE.

### <a name="remarks"></a>Notes

L’opérateur de comparaison final compare simplement la chaîne contenue par rapport à NULL.

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::opérateur&gt;

Compare un `CComBSTR` avec une chaîne.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément comparé `CComBSTR` est plus grand que l’objet; autrement, retourne FALSE.

### <a name="remarks"></a>Notes

La comparaison est effectuée à l’aide du lieu par défaut de l’utilisateur.

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR::LireDestream

Définit le [m_str](#m_str) membre au BSTR contenu dans le flux spécifié.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[dans] Un pointeur à l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur le flux contenant les données.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`ReadToStream`exige que le contenu du flux à la position actuelle soit compatible avec le format de données écrit par un appel à [WriteToStream](#writetostream).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a>CComBSTR::ToLower

Convertit la ficelle contenue en minuscule.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Voir `CharLowerBuff` pour plus d’informations sur la façon dont la conversion est effectuée.

## <a name="ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::ToUpper

Convertit la ficelle contenue en uppercase.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Voir `CharUpperBuff` pour plus d’informations sur la façon dont la conversion est effectuée.

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::WriteToStream

Enregistre le [m_str](#m_str) membre à un flux.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[dans] Un pointeur à l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur un flux.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez recréer un BSTR à partir du contenu du flux à l’aide de la fonction [ReadFromStream.](#readfromstream)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Macro de conversion des cordes ATL et MFC](string-conversion-macros.md)
