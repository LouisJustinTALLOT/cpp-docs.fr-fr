---
title: CComBSTR (classe)
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
ms.openlocfilehash: dd45c2ff9b43148e0fe27ebd410a2390a4d12ce2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497553"
---
# <a name="ccombstr-class"></a>CComBSTR (classe)

Cette classe est un wrapper pour [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Syntaxe

```
class CComBSTR
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|Constructeur.|
|[CComBSTR:: ~ CComBSTR](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComBSTR:: Append](#append)|Ajoute une chaîne à `m_str`.|
|[CComBSTR:: AppendBSTR](#appendbstr)|Ajoute un BSTR à `m_str`.|
|[CComBSTR::AppendBytes](#appendbytes)|Ajoute un nombre spécifié d’octets à `m_str`.|
|[CComBSTR:: ArrayToBSTR](#arraytobstr)|Crée un BSTR à partir du premier caractère de chaque élément du SAFEARRAY et l’attache à l' `CComBSTR` objet.|
|[CComBSTR:: AssignBSTR](#assignbstr)|Affecte un BSTR à `m_str`.|
|[CComBSTR:: Attach](#attach)|Attache un BSTR à l' `CComBSTR` objet.|
|[CComBSTR:: BSTRToArray](#bstrtoarray)|Crée un SafeArray unidimensionnel de base zéro, où chaque élément du tableau est un caractère de l' `CComBSTR` objet.|
|[CComBSTR::ByteLength](#bytelength)|Retourne la longueur de `m_str` en octets.|
|[CComBSTR::Copy](#copy)|Retourne une copie de `m_str`.|
|[CComBSTR::CopyTo](#copyto)|Retourne une copie de `m_str` via un paramètre **[out]**|
|[CComBSTR::Detach](#detach)|Détache de l' `CComBSTR`objet. `m_str`|
|[CComBSTR:: Empty](#empty)|`m_str`Libère.|
|[CComBSTR::Length](#length)|Retourne la longueur de `m_str`.|
|[CComBSTR::LoadString](#loadstring)|Charge une ressource de type chaîne.|
|[CComBSTR::ReadFromStream](#readfromstream)|Charge un objet BSTR à partir d’un flux.|
|[CComBSTR:: ToLower](#tolower)|Convertit la chaîne en minuscules.|
|[CComBSTR::ToUpper](#toupper)|Convertit la chaîne en majuscules.|
|[CComBSTR::WriteToStream](#writetostream)|Enregistre `m_str` dans un flux.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR:: Operator BSTR](#operator_bstr)|Effectue un cast `CComBSTR` d’un objet en BSTR.|
|[CComBSTR:: Operator!](#operator_not)|Retourne true ou false, selon que `m_str`a la valeur null.|
|[CComBSTR:: Operator! =](#operator_neq)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR:: operator &](#operator_amp)|Retourne l’adresse de `m_str`.|
|[CComBSTR:: Operator + =](#operator_add_eq)|`CComBSTR` Ajoute à l’objet.|
|[CComBSTR:: Operator <](#operator_lt)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR:: Operator =](#operator_eq)|Assigne une valeur à `m_str`.|
|[CComBSTR:: Operator = =](#operator_eq_eq)|Compare un `CComBSTR` avec une chaîne.|
|[CComBSTR:: operator >](#operator_gt)|Compare un `CComBSTR` avec une chaîne.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComBSTR:: m_str](#m_str)|Contient le BSTR associé à l' `CComBSTR` objet.|

## <a name="remarks"></a>Notes

La `CComBSTR` classe est un wrapper pour les BSTR, qui sont des chaînes à préfixe de longueur. La longueur est stockée sous la forme d’un entier à l’emplacement de mémoire précédant les données de la chaîne.

Un [BSTR](/previous-versions/windows/desktop/automat/bstr) se termine par un caractère null après le dernier caractère compté, mais peut également contenir des caractères null incorporés dans la chaîne. La longueur de chaîne est déterminée par le nombre de caractères, et non par le premier caractère null.

> [!NOTE]
>  La `CComBSTR` classe fournit un certain nombre de membres (constructeurs, opérateurs d’assignation et opérateurs de comparaison) qui acceptent des chaînes ANSI ou Unicode comme arguments. Les versions ANSI de ces fonctions sont moins efficaces que leurs équivalents Unicode, car les chaînes Unicode temporaires sont souvent créées en interne. Pour plus d’efficacité, utilisez les versions Unicode si possible.

> [!NOTE]
>  En raison du comportement de recherche amélioré implémenté dans Visual Studio .net, le code `bstr = L"String2" + bstr;`tel que, qui peut avoir été compilé dans les versions précédentes, doit `bstr = CStringW(L"String2") + bstr`plutôt être implémenté comme.

Pour obtenir une liste des précautions à respecter `CComBSTR`lors de l’utilisation de, consultez [programmation avec CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="append"></a>  CComBSTR::Append

Ajoute *lpsz* ou le membre BSTR de *bstrSrc* à [m_str](#m_str).

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
dans `CComBSTR` Objet à ajouter.

*ch*<br/>
dans Caractère à ajouter.

*lpsz*<br/>
dans Chaîne de caractères se terminant par zéro à ajouter. Vous pouvez transmettre une chaîne Unicode via la surcharge LPCOLESTR ou une chaîne ANSI via la version LPCSTR.

*nLen*<br/>
dans Nombre de caractères de *lpsz* à ajouter.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

### <a name="remarks"></a>Notes

Une chaîne ANSI est convertie au format Unicode avant d’être ajoutée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR

Ajoute le BSTR spécifié à [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans BSTR à ajouter.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

### <a name="remarks"></a>Notes

Ne transmettez pas une chaîne de caractères larges ordinaire à cette méthode. Le compilateur ne peut pas intercepter l’erreur et des erreurs d’exécution se produisent.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>  CComBSTR::AppendBytes

Ajoute le nombre d’octets spécifié à [m_str](#m_str) sans conversion.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
dans Pointeur vers un tableau d’octets à ajouter.

*p*<br/>
dans Nombre d’octets à ajouter.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR

Libère toute chaîne existante contenue dans l' `CComBSTR` objet, puis crée un BSTR à partir du premier caractère de chaque élément du SAFEARRAY et l’attache à l' `CComBSTR` objet.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Paramètres

*pSrc*<br/>
dans SafeArray contenant les éléments utilisés pour créer la chaîne.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR

Affecte un BSTR à [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Paramètres

*bstrSrc*<br/>
dans BSTR à assigner à l' `CComBSTR` objet actuel.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

##  <a name="attach"></a>  CComBSTR::Attach

Attache un BSTR à l' `CComBSTR` objet en définissant le membre [m_str](#m_str) sur *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans BSTR à attacher à l’objet.

### <a name="remarks"></a>Notes

Ne transmettez pas une chaîne de caractères larges ordinaire à cette méthode. Le compilateur ne peut pas intercepter l’erreur et des erreurs d’exécution se produisent.

> [!NOTE]
>  Cette méthode déclare si `m_str` est non null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>CComBSTR:: BSTRToArray

Crée un SafeArray unidimensionnel de base zéro, où chaque élément du tableau est un caractère de l' `CComBSTR` objet.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
à Pointeur vers le SAFEARRAY utilisé pour stocker les résultats de la fonction.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite, ou une valeur d’erreur HRESULT standard.

##  <a name="bytelength"></a>  CComBSTR::ByteLength

Retourne le nombre d’octets dans `m_str`, à l’exclusion du caractère null de fin.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Longueur du membre [m_str](#m_str) en octets.

### <a name="remarks"></a>Notes

Retourne 0 si `m_str` a la valeur null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>  CComBSTR::CComBSTR

Constructeur. Le constructeur par défaut affecte la valeur NULL au membre [m_str](#m_str) .

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
dans Nombre de caractères à copier à partir de *SZ* ou de la taille initiale en caractères `CComBSTR`pour le.

*sz*<br/>
[in] Chaîne à copier. La version Unicode spécifie un LPCOLESTR; la version ANSI spécifie un LPCSTR.

*pSrc*<br/>
[in] Chaîne à copier. La version Unicode spécifie un LPCOLESTR; la version ANSI spécifie un LPCSTR.

*src*<br/>
[in] Objet `CComBSTR`

*guid*<br/>
dans Référence à une `GUID` structure.

### <a name="remarks"></a>Notes

Le constructeur de copie `m_str` définit sur une copie du membre BSTR de *src*. Le `REFGUID` constructeur convertit le GUID en chaîne à `StringFromGUID2` l’aide de et stocke le résultat.

Les autres constructeurs affectent à `m_str` une copie de la chaîne spécifiée. Si vous transmettez une valeur pour *nSize*, seuls les caractères *nSize* sont copiés, suivis d’un caractère null de fin.

`CComBSTR` prend en charge la sémantique de déplacement. Vous pouvez utiliser le constructeur de déplacement (constructeur qui accepte une référence rvalue (`&&`)) pour créer un nouvel objet utilisant les mêmes données sous-jacentes que l'ancien objet que vous transmettez comme argument, sans la surcharge propre à la copie de l'objet.

Le destructeur libère la chaîne pointée par `m_str`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR

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

Copie du membre [m_str](#m_str) . Si `m_str` a la valeur null, retourne la valeur null.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>  CComBSTR::CopyTo

Alloue et retourne une copie de [m_str](#m_str) via le paramètre.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Paramètres

*pbstr*<br/>
à Adresse d’un BSTR dans lequel retourner la chaîne allouée par cette méthode.

*pvarDest*<br/>
à Adresse d’un VARIANT dans lequel retourner la chaîne allouée par cette méthode.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard indiquant la réussite ou l’échec de la copie.

### <a name="remarks"></a>Notes

Après l’appel de cette méthode, la variante vers laquelle pointe *pvarDest* sera de type VT_BSTR.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>  CComBSTR::Detach

Détache [m_str](#m_str) de l’objet `CComBSTR` et affecte `m_str` à la valeur null.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

BSTR associé à l' `CComBSTR` objet.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>CComBSTR:: Empty

Libère le membre [m_str](#m_str) .

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

Longueur du membre [m_str](#m_str) .

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>  CComBSTR::LoadString

Charge une ressource de type chaîne spécifiée par *nid* et la stocke dans cet objet.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Paramètres

Consultez [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la chaîne est chargée avec succès; Sinon, retourne FALSe.

### <a name="remarks"></a>Notes

La première fonction charge la ressource à partir du module identifié par vous par le biais du paramètre *HINST* . La deuxième fonction charge la ressource à partir du module de ressource associé à l’objet dérivé de [CComModule](../../atl/reference/ccommodule-class.md)utilisé dans ce projet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

Contient le BSTR associé à l' `CComBSTR` objet.

```
BSTR m_str;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>CComBSTR:: Operator BSTR

Effectue un cast `CComBSTR` d’un objet en BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Notes

Vous permet de passer `CComBSTR` des objets à des fonctions qui ont des paramètres **de BSTR [in]** .

### <a name="example"></a>Exemples

Consultez l’exemple de [CComBSTR:: m_str](#m_str).

##  <a name="operator_not"></a>CComBSTR:: Operator!

Vérifie si BSTR chaîne a la valeur NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le membre [m_str](#m_str) a la valeur null; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cet opérateur vérifie uniquement la valeur NULL, pas une chaîne vide.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>CComBSTR:: Operator! =

Retourne l’opposé logique de l' [opérateur = =](#operator_eq_eq).

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
dans Chaîne se terminant par zéro.

*nNull*<br/>
dans Doit avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’élément en cours de comparaison n' `CComBSTR` est pas égal à l’objet; sinon, retourne false.

### <a name="remarks"></a>Notes

`CComBSTR`les s sont comparées textuellement dans le contexte des paramètres régionaux par défaut de l’utilisateur. L’opérateur de comparaison final compare simplement la chaîne contenue à la valeur NULL.

##  <a name="operator_amp"></a>CComBSTR:: Operator&amp;

Retourne l’adresse du BSTR stocké dans le membre [m_str](#m_str) .

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Notes

`CComBstr operator &`une assertion spéciale lui est associée pour aider à identifier les fuites de mémoire. Le programme déclarera quand le `m_str` membre sera initialisé. Cette assertion a été créée pour identifier les situations où un programmeur utilise le `& operator` pour assigner une nouvelle valeur à `m_str` un membre sans `m_str`libérer la première allocation de. Si `m_str` est égal à null, le programme suppose que m_str n’a pas encore été alloué. Dans ce cas, le programme n’effectuera pas d’assertion.

Cette assertion n’est pas activée par défaut. Définissez ATL_CCOMBSTR_ADDRESS_OF_ASSERT pour activer cette assertion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>CComBSTR:: Operator + =

Ajoute une chaîne à l' `CComBSTR` objet.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Paramètres

*bstrSrc*<br/>
dans `CComBSTR` Objet à ajouter.

*pszSrc*<br/>
dans Chaîne se terminant par zéro à ajouter.

### <a name="remarks"></a>Notes

`CComBSTR`les s sont comparées textuellement dans le contexte des paramètres régionaux par défaut de l’utilisateur. La comparaison LPCOLESTR est effectuée à `memcmp` l’aide de sur les données brutes de chaque chaîne. La comparaison LPCSTR est effectuée de la même manière une fois qu’une copie Unicode temporaire de *pszSrc* a été créée. L’opérateur de comparaison final compare simplement la chaîne contenue à la valeur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>CComBSTR:: Operator&lt;

Compare un `CComBSTR` avec une chaîne.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’élément en cours de comparaison `CComBSTR` est inférieur à l’objet; sinon, retourne false.

### <a name="remarks"></a>Notes

La comparaison est effectuée à l’aide des paramètres régionaux par défaut de l’utilisateur.

##  <a name="operator_eq"></a>CComBSTR:: Operator =

Définit le membre [m_str](#m_str) sur une copie de *pSrc* ou sur une copie du membre BSTR de *src*. L’opérateur d’assignation de `src` déplacement se déplace sans le copier.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Notes

Le paramètre *pSrc* spécifie un LPCOLESTR pour les versions Unicode ou LPCSTR pour les versions ANSI.

### <a name="example"></a>Exemples

Consultez l’exemple de [CComBSTR:: Copy](#copy).

##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==

Compare un `CComBSTR` avec une chaîne. `CComBSTR`les s sont comparées textuellement dans le contexte des paramètres régionaux par défaut de l’utilisateur.

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
dans Chaîne se terminant par zéro.

*nNull*<br/>
dans Doit avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’élément en cours de comparaison `CComBSTR` est égal à l’objet; sinon, retourne false.

### <a name="remarks"></a>Notes

L’opérateur de comparaison final compare simplement la chaîne contenue à la valeur NULL.

##  <a name="operator_gt"></a>CComBSTR:: Operator&gt;

Compare un `CComBSTR` avec une chaîne.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’élément en cours de comparaison `CComBSTR` est supérieur à l’objet; sinon, retourne false.

### <a name="remarks"></a>Notes

La comparaison est effectuée à l’aide des paramètres régionaux par défaut de l’utilisateur.

##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream

Définit le BSTR contenu dans le flux spécifié dans le membre [m_str](#m_str) .

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur le flux contenant les données.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

`ReadToStream`requiert que le contenu du flux à la position actuelle soit compatible avec le format de données écrit par un appel à [WriteToStream](#writetostream).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>  CComBSTR::ToLower

Convertit la chaîne contenue en minuscules.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour `CharLowerBuff` plus d’informations sur la façon dont la conversion est effectuée, consultez.

##  <a name="toupper"></a>  CComBSTR::ToUpper

Convertit la chaîne contenue en majuscules.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour `CharUpperBuff` plus d’informations sur la façon dont la conversion est effectuée, consultez.

##  <a name="writetostream"></a>  CComBSTR::WriteToStream

Enregistre le membre [m_str](#m_str) dans un flux.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur un flux.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez recréer un BSTR à partir du contenu du flux à l’aide de la fonction [readFromStream](#readfromstream) .

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Macros de conversion de chaînes ATL et MFC](string-conversion-macros.md)
