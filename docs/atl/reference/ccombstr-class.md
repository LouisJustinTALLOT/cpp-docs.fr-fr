---
title: CComBSTR, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2045a6c14a37d270d895a5eeb4fa455711e7354
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097677"
---
# <a name="ccombstr-class"></a>CComBSTR, classe

Cette classe est un wrapper de BSTR.

## <a name="syntax"></a>Syntaxe

```
class CComBSTR
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|Constructeur.|
|[CComBSTR :: ~ CComBSTR](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComBSTR::Append](#append)|Ajoute une chaîne à `m_str`.|
|[CComBSTR::AppendBSTR](#appendbstr)|Ajoute un BSTR à `m_str`.|
|[CComBSTR::AppendBytes](#appendbytes)|Ajoute un nombre spécifié d’octets à `m_str`.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crée un BSTR au premier caractère de chaque élément dans le safearray et l’attache à la `CComBSTR` objet.|
|[CComBSTR::AssignBSTR](#assignbstr)|Assigne un BSTR à `m_str`.|
|[CComBSTR::Attach](#attach)|Attache un BSTR à la `CComBSTR` objet.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crée de base zéro unidimensionnel safearray, où chaque élément du tableau est un caractère à partir de la `CComBSTR` objet.|
|[CComBSTR::ByteLength](#bytelength)|Retourne la longueur de `m_str` en octets.|
|[CComBSTR::Copy](#copy)|Retourne une copie de `m_str`.|
|[CComBSTR::CopyTo](#copyto)|Retourne une copie de `m_str` via un **[out]** paramètre|
|[CComBSTR::Detach](#detach)|Détache `m_str` à partir de la `CComBSTR` objet.|
|[CComBSTR::Empty](#empty)|Libère `m_str`.|
|[CComBSTR::Length](#length)|Retourne la longueur de `m_str`.|
|[CComBSTR::LoadString](#loadstring)|Charge une ressource de chaîne.|
|[CComBSTR::ReadFromStream](#readfromstream)|Charge un objet BSTR à partir d’un flux de données.|
|[CComBSTR::ToLower](#tolower)|Convertit la chaîne en minuscules.|
|[CComBSTR::ToUpper](#toupper)|Convertit la chaîne en majuscules.|
|[CComBSTR::WriteToStream](#writetostream)|Enregistre `m_str` dans un flux.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR::operator BSTR](#operator_bstr)|Les casts un `CComBSTR` objet vers un BSTR.|
|[CComBSTR::operator !](#operator_not)|Retourne TRUE ou FALSE selon que `m_str`a la valeur NULL.|
|[CComBSTR::operator ! =](#operator_neq)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR::operator &](#operator_amp)|Retourne l’adresse de `m_str`.|
|[CComBSTR::operator +=](#operator_add_eq)|Ajoute un `CComBSTR` à l’objet.|
|[CComBSTR::operator <](#operator_lt)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR::operator =](#operator_eq)|Affecte une valeur à `m_str`.|
|[CComBSTR::operator ==](#operator_eq_eq)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR::operator >](#operator_gt)|Compare un `CComBSTR` avec une chaîne.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Contient le BSTR associé à la `CComBSTR` objet.|

## <a name="remarks"></a>Notes

Le `CComBSTR` classe est un wrapper de BSTR, qui sont des chaînes préfixée par sa longueur. La longueur est stockée en tant qu’entier à l’emplacement de mémoire qui précède les données dans la chaîne.

Un [BSTR](/previous-versions/windows/desktop/automat/bstr) est nul après le dernier comptés caractère, mais peut également contenir des caractères null incorporés dans la chaîne. La longueur de chaîne est déterminée par le nombre de caractères, pas au premier caractère null.

> [!NOTE]
>  Le `CComBSTR` classe fournit un nombre de membres (constructeurs, opérateurs d’assignation et les opérateurs de comparaison) qui acceptent des chaînes ANSI ou Unicode en tant qu’arguments. Les versions ANSI de ces fonctions sont moins efficaces que leurs équivalents Unicode, car les chaînes Unicode temporaires sont souvent créées en interne. Pour plus d’efficacité, utilisez les versions Unicode lorsque cela est possible.

> [!NOTE]
>  En raison du comportement de recherche améliorée implémenté dans Visual Studio .NET, un code tel que `bstr = L"String2" + bstr;`, qui peut avoir compilées dans les versions précédentes, devrait plutôt être implémentée en tant que `bstr = CStringW(L"String2") + bstr`.

Pour obtenir la liste des précautions à prendre lorsque vous utilisez `CComBSTR`, consultez [programmation avec CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="append"></a>  CComBSTR::Append

Ajoute une *lpsz* ou le membre BSTR de *bstrSrc* à [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc*<br/>
[in] Un `CComBSTR` objet à ajouter.

*ch*<br/>
[in] Un caractère à ajouter.

*lpsz*<br/>
[in] Une chaîne de caractères se terminant par zéro à ajouter. Vous pouvez passer une chaîne Unicode via la surcharge LPCOLESTR ou une chaîne ANSI via la version LPCSTR.

*nLen*<br/>
[in] Le nombre de caractères à partir de *lpsz* à ajouter.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

### <a name="remarks"></a>Notes

Une chaîne ANSI sera convertie au format Unicode avant d’être ajouté.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR

Ajoute le BSTR spécifié à [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Un BSTR à ajouter.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

### <a name="remarks"></a>Notes

Ne passez pas une chaîne de caractères larges ordinaire à cette méthode. Le compilateur ne peut pas intercepter l’erreur et l’exécution erreurs se produisent.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>  CComBSTR::AppendBytes

Ajoute le nombre spécifié d’octets à [m_str](#m_str) sans conversion.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
[in] Pointeur vers un tableau d’octets à ajouter.

*p*<br/>
[in] Le nombre d’octets à ajouter.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR

Libère toute chaîne existante dans le `CComBSTR` de l’objet, puis crée un BSTR au premier caractère de chaque élément dans le safearray et l’attache à la `CComBSTR` objet.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Paramètres

*pSrc*<br/>
[in] Safearray qui contient les éléments utilisés pour créer la chaîne.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR

Assigne un BSTR à [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc*<br/>
[in] Un BSTR à affecter à l’actuel `CComBSTR` objet.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

##  <a name="attach"></a>  CComBSTR::Attach

Attache un BSTR à la `CComBSTR` objet en définissant le [m_str](#m_str) membre à *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[in] BSTR à attacher à l’objet.

### <a name="remarks"></a>Notes

Ne passez pas une chaîne de caractères larges ordinaire à cette méthode. Le compilateur ne peut pas intercepter l’erreur et l’exécution erreurs se produisent.

> [!NOTE]
>  Cette méthode vérifie si `m_str` n’est pas NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>  CComBSTR::BSTRToArray

Crée de base zéro unidimensionnel safearray, où chaque élément du tableau est un caractère à partir de la `CComBSTR` objet.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
[out] Pointeur vers un safearray utilisé pour stocker les résultats de la fonction.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

##  <a name="bytelength"></a>  CComBSTR::ByteLength

Retourne le nombre d’octets dans `m_str`, à l’exclusion du caractère null de fin.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

La longueur de la [m_str](#m_str) membre en octets.

### <a name="remarks"></a>Notes

Retourne 0 si `m_str` a la valeur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>  CComBSTR::CComBSTR

Constructeur. Le constructeur par défaut affecte la [m_str](#m_str) membre avec la valeur NULL.

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

*nSize*<br/>
[in] Le nombre de caractères à copier à partir de *sz* ou la taille initiale en caractères pour le `CComBSTR`.

*sz*<br/>
[in] Chaîne à copier. La version Unicode spécifie un LPCOLESTR ; la version ANSI spécifie un LPCSTR.

*pSrc*<br/>
[in] Chaîne à copier. La version Unicode spécifie un LPCOLESTR ; la version ANSI spécifie un LPCSTR.

*src*<br/>
[in] Objet `CComBSTR`

*guid*<br/>
[in] Une référence à un `GUID` structure.

### <a name="remarks"></a>Notes

Le constructeur de copie affecte `m_str` vers une copie du membre de BSTR *src*. Le `REFGUID` constructeur convertit le GUID en une chaîne à l’aide `StringFromGUID2` et stocke le résultat.

Les autres constructeurs affectent à `m_str` une copie de la chaîne spécifiée. Si vous transmettez une valeur pour *nSize*, seule *nSize* les caractères sont copiés, suivie d’un caractère null de fin.

`CComBSTR` prend en charge la sémantique de déplacement. Vous pouvez utiliser le constructeur de déplacement (constructeur qui accepte une référence rvalue (`&&`)) pour créer un nouvel objet utilisant les mêmes données sous-jacentes que l'ancien objet que vous transmettez comme argument, sans la surcharge propre à la copie de l'objet.

Le destructeur libère la chaîne pointée par `m_str`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>  CComBSTR :: ~ CComBSTR

Destructeur.

```
~CComBSTR();
```

### <a name="remarks"></a>Notes

Le destructeur libère la chaîne pointée par `m_str`.

##  <a name="copy"></a>  CComBSTR::Copy

Alloue et retourne une copie de `m_str`.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Valeur de retour

Une copie de la [m_str](#m_str) membre. Si `m_str` a la valeur NULL, retourne NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>  CComBSTR::CopyTo

Alloue et retourne une copie de [m_str](#m_str) via le paramètre.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Paramètres

*pbstr*<br/>
[out] Adresse du BSTR dans lequel retourner la chaîne allouée par cette méthode.

*pvarDest*<br/>
[out] L’adresse d’un VARIANT dans lequel retourner la chaîne allouée par cette méthode.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard indiquant la réussite ou l’échec de la copie.

### <a name="remarks"></a>Notes

Après avoir appelé cette méthode, la variante vers lequel pointe *pvarDest* sera de type VT_BSTR.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>  CComBSTR::Detach

Détache [m_str](#m_str) à partir de la `CComBSTR` objet et jeux `m_str` avec la valeur NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Le BSTR associé le `CComBSTR` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>  CComBSTR::Empty

Libère le [m_str](#m_str) membre.

```
void Empty() throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>  CComBSTR::Length

Retourne le nombre de caractères dans `m_str`, à l’exclusion du caractère null de fin.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Valeur de retour

La longueur de la [m_str](#m_str) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>  CComBSTR::LoadString

Charge une ressource de chaîne spécifiée par *nID* et le stocke dans cet objet.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Paramètres

Consultez [LoadString](/windows/desktop/api/winuser/nf-winuser-loadstringa) dans le Kit de développement logiciel Windows.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la chaîne est correctement chargée ; Sinon, retourne FALSE.

### <a name="remarks"></a>Notes

La première fonction charge la ressource à partir du module identifié par vous via le *hInst* paramètre. La deuxième fonction charge la ressource à partir du module de ressources associé à la [CComModule](../../atl/reference/ccommodule-class.md)-objet utilisé dans ce projet dérivé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

Contient le BSTR associé à la `CComBSTR` objet.

```
BSTR m_str;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>  CComBSTR::operator BSTR

Les casts un `CComBSTR` objet vers un BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Notes

Vous pouvez ainsi passer `CComBSTR` objets aux fonctions qui ont **[in] BSTR** paramètres.

### <a name="example"></a>Exemple

Consultez l’exemple de [CComBSTR::m_str](#m_str).

##  <a name="operator_not"></a>  CComBSTR::operator !

Vérifie si chaîne BSTR est NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le [m_str](#m_str) membre est NULL ; sinon, FALSE.

### <a name="remarks"></a>Notes

Cet opérateur vérifie uniquement une valeur NULL, pas pour une chaîne vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>  CComBSTR::operator ! =

Retourne le contraire logique de [opérateur ==](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc*<br/>
[in] Objet `CComBSTR`

*pszSrc*<br/>
[in] Chaîne se terminant par zéro.

*nNull*<br/>
[in] Doit être NULL.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément en cours de comparaison n’est pas égale à la `CComBSTR` de l’objet ; sinon, retourne FALSE.

### <a name="remarks"></a>Notes

`CComBSTR`s sont comparées textuellement dans le contexte de paramètres régionaux par défaut de l’utilisateur. L’opérateur de comparaison finale compare simplement la chaîne de relation contenant-contenue par rapport à NULL.

##  <a name="operator_amp"></a>  CComBSTR::operator &amp;

Retourne l’adresse du BSTR stocké dans le [m_str](#m_str) membre.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Notes

`CComBstr operator &` est une assertion spéciale associé pour aider à identifier les fuites de mémoire. Le programme déclarera lorsque le `m_str` membre est initialisé. Cette assertion a été créée pour identifier les situations où un programmeur utilise le `& operator` pour attribuer une nouvelle valeur à `m_str` membre sans la libérer la première allocation de `m_str`. Si `m_str` est égal à NULL, le programme suppose que m_str n’a pas été encore affectés. Dans ce cas, le programme ne déclarera pas.

Cette assertion n’est pas activée par défaut. Définir ATL_CCOMBSTR_ADDRESS_OF_ASSERT pour activer cette assertion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>  CComBSTR::operator +=

Ajoute une chaîne à la `CComBSTR` objet.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Paramètres

*bstrSrc*<br/>
[in] Un `CComBSTR` objet à ajouter.

*pszSrc*<br/>
[in] Chaîne se terminant par zéro à ajouter.

### <a name="remarks"></a>Notes

`CComBSTR`s sont comparées textuellement dans le contexte de paramètres régionaux par défaut de l’utilisateur. La comparaison LPCOLESTR est effectuée à l’aide `memcmp` sur les données brutes dans chaque chaîne. La comparaison LPCSTR est effectuée de la même façon une fois Unicode temporaire copier de *pszSrc* a été créé. L’opérateur de comparaison finale compare simplement la chaîne de relation contenant-contenue par rapport à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>  CComBSTR::operator &lt;

Compare un `CComBSTR` avec une chaîne.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément en cours de comparaison est inférieur au `CComBSTR` de l’objet ; sinon, retourne FALSE.

### <a name="remarks"></a>Notes

La comparaison est effectuée à l’aide des paramètres régionaux par défaut de l’utilisateur.

##  <a name="operator_eq"></a>  CComBSTR::operator =

Définit le [m_str](#m_str) membre vers une copie de *pSrc* ou à une copie du membre de BSTR *src*. Déplace l’opérateur d’assignation de déplacement `src` sans le copier.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Notes

Le *pSrc* paramètre spécifie un LPCOLESTR pour les versions Unicode ou LPCSTR pour les versions ANSI.

### <a name="example"></a>Exemple

Consultez l’exemple de [CComBSTR::Copy](#copy).

##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==

Compare un `CComBSTR` avec une chaîne. `CComBSTR`s sont comparées textuellement dans le contexte de paramètres régionaux par défaut de l’utilisateur.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc*<br/>
[in] Objet `CComBSTR`

*pszSrc*<br/>
[in] Chaîne se terminant par zéro.

*nNull*<br/>
[in] Doit être NULL.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément en cours de comparaison est égal à la `CComBSTR` de l’objet ; sinon, retourne FALSE.

### <a name="remarks"></a>Notes

L’opérateur de comparaison finale compare simplement la chaîne de relation contenant-contenue par rapport à NULL.

##  <a name="operator_gt"></a>  CComBSTR::operator &gt;

Compare un `CComBSTR` avec une chaîne.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément en cours de comparaison est supérieur à la `CComBSTR` de l’objet ; sinon, retourne FALSE.

### <a name="remarks"></a>Notes

La comparaison est effectuée à l’aide des paramètres régionaux par défaut de l’utilisateur.

##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream

Définit le [m_str](#m_str) membre vers le BSTR contenu dans le flux spécifié.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[in] Un pointeur vers le [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interface sur le flux contenant les données.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`ReadToStream` nécessite le contenu du flux à la position actuelle pour être compatible avec le format de données écrit par un appel à [WriteToStream](#writetostream).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>  CComBSTR::ToLower

Convertit la chaîne de relation contenant-contenue en minuscules.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Consultez `CharLowerBuff` pour plus d’informations sur la façon dont la conversion est effectuée.

##  <a name="toupper"></a>  CComBSTR::ToUpper

Convertit la chaîne de relation contenant-contenue en majuscules.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Consultez `CharUpperBuff` pour plus d’informations sur la façon dont la conversion est effectuée.

##  <a name="writetostream"></a>  CComBSTR::WriteToStream

Enregistre le [m_str](#m_str) membre à un flux de données.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[in] Un pointeur vers le [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interface sur un flux de données.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez recréer un BSTR à partir du contenu du flux de données en utilisant le [ReadFromStream](#readfromstream) (fonction).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Macros de Conversion de chaîne MFC et ATL](string-conversion-macros.md)
