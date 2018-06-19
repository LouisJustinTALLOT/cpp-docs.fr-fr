---
title: Classe CComBSTR | Documents Microsoft
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
ms.openlocfilehash: 7a9130dec2de7d22cfec8a76cdeb31e11388a205
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366443"
---
# <a name="ccombstr-class"></a>Classe CComBSTR
Cette classe est un wrapper pour `BSTR`s.  
  
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
|[CComBSTR::AppendBSTR](#appendbstr)|Ajoute un `BSTR` à `m_str`.|  
|[CComBSTR::AppendBytes](#appendbytes)|Ajoute un nombre spécifié d’octets à `m_str`.|  
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crée un `BSTR` entre le premier caractère de chaque élément de tableau safearray et l’attache à le `CComBSTR` objet.|  
|[CComBSTR::AssignBSTR](#assignbstr)|Affecte un `BSTR` à `m_str`.|  
|[CComBSTR::Attach](#attach)|Attache un `BSTR` à la `CComBSTR` objet.|  
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crée un safearray unidimensionnel base zéro, où chaque élément du tableau est un caractère à partir de la `CComBSTR` objet.|  
|[CComBSTR::ByteLength](#bytelength)|Retourne la longueur de `m_str` en octets.|  
|[CComBSTR::Copy](#copy)|Retourne une copie de `m_str`.|  
|[CComBSTR::CopyTo](#copyto)|Retourne une copie de `m_str` via un **[out]** paramètre|  
|[CComBSTR::Detach](#detach)|Détache `m_str` à partir de la `CComBSTR` objet.|  
|[CComBSTR::Empty](#empty)|Libère `m_str`.|  
|[CComBSTR::Length](#length)|Retourne la longueur de `m_str`.|  
|[CComBSTR::LoadString](#loadstring)|Charge une ressource de chaîne.|  
|[CComBSTR::ReadFromStream](#readfromstream)|Charge un `BSTR` objet à partir d’un flux de données.|  
|[CComBSTR::ToLower](#tolower)|Convertit la chaîne en minuscules.|  
|[CComBSTR::ToUpper](#toupper)|Convertit la chaîne en majuscules.|  
|[CComBSTR::WriteToStream](#writetostream)|Enregistre `m_str` dans un flux.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](#operator_bstr)|Les casts un `CComBSTR` de l’objet à un `BSTR`.|  
|[CComBSTR::operator !](#operator_not)|Retourne `true` ou `false`, selon que `m_str`est `NULL`.|  
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
|[CComBSTR::m_str](#m_str)|Contient le `BSTR` associé à la `CComBSTR` objet.|  
  
## <a name="remarks"></a>Notes  
 Le `CComBSTR` classe est un wrapper pour `BSTR`s, qui sont des chaînes de longueur de préfixe. La longueur est stockée comme un entier à l’emplacement de mémoire qui précède les données dans la chaîne.  
  
 A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) est terminée après le dernier comptabilisées caractère mais peut également contenir des caractères null incorporés dans la chaîne. La longueur de chaîne est déterminée par le nombre de caractères, pas au premier caractère null.  
  
> [!NOTE]
>  La `CComBSTR` classe fournit un nombre de membres (constructeurs, les opérateurs d’assignation et les opérateurs de comparaison) qui prennent des chaînes ANSI ou Unicode en tant qu’arguments. Les versions ANSI de ces fonctions sont moins efficaces que leurs équivalents Unicode, car les chaînes Unicode temporaires sont souvent créées en interne. Pour plus d’efficacité, utilisez les versions Unicode lorsque cela est possible.  
  
> [!NOTE]
>  En raison du comportement de recherche améliorée implémenté dans Visual Studio .NET, un code tel que `bstr = L"String2" + bstr;`, qui peut avoir compilées dans les versions précédentes, devrait plutôt être implémentée en tant que `bstr = CStringW(L"String2") + bstr`.  
  
 Pour obtenir la liste des avertissements lors de l’utilisation `CComBSTR`, consultez [programmation avec CComBSTR](../../atl/programming-with-ccombstr-atl.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
##  <a name="append"></a>  CComBSTR::Append  
 Ajoute une `lpsz` ou `BSTR` membre `bstrSrc` à [m_str](#m_str).  
  
```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrSrc`  
 [in] A `CComBSTR` objet à ajouter.  
  
 *ch*  
 [in] Un caractère à ajouter.  
  
 `lpsz`  
 [in] Une chaîne de caractères terminée par zéro à ajouter. Vous pouvez passer une chaîne Unicode via la **LPCOLESTR** surcharge ou une chaîne ANSI via la `LPCSTR` version.  
  
 `nLen`  
 [in] Le nombre de caractères à partir de `lpsz` à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` sur la réussite ou norme `HRESULT` valeur d’erreur.  
  
### <a name="remarks"></a>Notes  
 Une chaîne ANSI sera convertie au format Unicode avant d’être ajouté.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]  
  
##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR  
 Ajoute le texte spécifié `BSTR` à [m_str](#m_str).  
  
```
HRESULT AppendBSTR(BSTR p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 [in] A `BSTR` à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` sur la réussite ou norme `HRESULT` valeur d’erreur.  
  
### <a name="remarks"></a>Notes  
 Ne passez pas une chaîne à caractères larges ordinaire à cette méthode. Le compilateur ne peut pas intercepter l’erreur et l’exécution des erreurs se produiront.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]  
  
##  <a name="appendbytes"></a>  CComBSTR::AppendBytes  
 Ajoute le nombre spécifié d’octets à [m_str](#m_str) sans conversion.  
  
```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpsz`  
 [in] Pointeur vers un tableau d’octets à ajouter.  
  
 `p`  
 [in] Le nombre d’octets à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` sur la réussite ou norme `HRESULT` valeur d’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]  
  
##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR  
 Libère toute chaîne existante dans le `CComBSTR` de l’objet, puis crée un `BSTR` entre le premier caractère de chaque élément de tableau safearray et l’attache à la `CComBSTR` objet.  
  
```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pSrc`  
 [in] Safearray contenant les éléments utilisés pour créer la chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` sur la réussite ou norme `HRESULT` valeur d’erreur.  
  
##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR  
 Affecte un `BSTR` à [m_str](#m_str).  
  
```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrSrc`  
 [in] A `BSTR` à affecter au actuel `CComBSTR` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` sur la réussite ou norme `HRESULT` valeur d’erreur.  
  
##  <a name="attach"></a>  CComBSTR::Attach  
 Attache un `BSTR` à la `CComBSTR` objet en définissant le [m_str](#m_str) membre *src*.  
  
```
void Attach(BSTR src) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *src*  
 [in] Le `BSTR` à attacher à l’objet.  
  
### <a name="remarks"></a>Notes  
 Ne passez pas une chaîne à caractères larges ordinaire à cette méthode. Le compilateur ne peut pas intercepter l’erreur et l’exécution des erreurs se produiront.  
  
> [!NOTE]
>  Cette méthode vérifie si `m_str` est non - **NULL**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="bstrtoarray"></a>  CComBSTR::BSTRToArray  
 Crée un safearray unidimensionnel base zéro, où chaque élément du tableau est un caractère à partir de la `CComBSTR` objet.  
  
```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `ppArray`  
 [out] Pointeur vers un safearray utilisé pour stocker les résultats de la fonction.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` sur la réussite ou norme `HRESULT` valeur d’erreur.  
  
##  <a name="bytelength"></a>  CComBSTR::ByteLength  
 Retourne le nombre d’octets dans `m_str`, à l’exclusion du caractère null de fin.  
  
```
unsigned int ByteLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La longueur de la [m_str](#m_str) membre en octets.  
  
### <a name="remarks"></a>Notes  
 Retourne 0 si `m_str` est **NULL**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]  
  
##  <a name="ccombstr"></a>  CComBSTR::CComBSTR  
 Constructeur. Le constructeur par défaut affecte la [m_str](#m_str) membre **NULL**.  
  
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
 `nSize`  
 [in] Nombre de caractères à copier à partir de `sz` ou taille initiale en caractères pour `CComBSTR`.  
  
 `sz`  
 [in] Chaîne à copier. La version Unicode spécifie un **LPCOLESTR**; la version ANSI spécifie un `LPCSTR`.  
  
 `pSrc`  
 [in] Chaîne à copier. La version Unicode spécifie un **LPCOLESTR**; la version ANSI spécifie un `LPCSTR`.  
  
 *src*  
 [in] Objet `CComBSTR`  
  
 `guid`  
 [in] Une référence à un **GUID** structure.  
  
### <a name="remarks"></a>Notes  
 Le constructeur de copie affecte `m_str` vers une copie de la `BSTR` membre *src*. Le **REFGUID** constructeur convertit le **GUID** à une chaîne à l’aide de **StringFromGUID2** et stocke le résultat.  
  
 Les autres constructeurs affectent à `m_str` une copie de la chaîne spécifiée. Si vous transmettez une valeur pour `nSize`, seuls `nSize` caractères sont copiés, suivis d'un caractère null de fin.  
  
 `CComBSTR` prend en charge la sémantique de déplacement. Vous pouvez utiliser le constructeur de déplacement (constructeur qui accepte une référence rvalue ( `&&`) pour créer un nouvel objet qui utilise les mêmes données sous-jacentes que l’ancien objet que vous transmettez comme argument, sans surcharge pour la copie de l’objet.  
  
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
 Une copie de la [m_str](#m_str) membre. Si `m_str` est **NULL**, retourne **NULL**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]  
  
##  <a name="copyto"></a>  CComBSTR::CopyTo  
 Alloue et retourne une copie de [m_str](#m_str) via le paramètre.  
  
```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *pbstr*  
 [out] L’adresse d’un `BSTR` dans lequel retourner la chaîne allouée par cette méthode.  
  
 `pvarDest`  
 [out] L’adresse d’un **VARIANT** dans lequel retourner la chaîne allouée par cette méthode.  
  
### <a name="return-value"></a>Valeur de retour  
 Une norme `HRESULT` indiquant la réussite ou l’échec de la copie.  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé cette méthode, le **VARIANT** vers lequel pointe `pvarDest` sera de type `VT_BSTR`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]  
  
##  <a name="detach"></a>  CComBSTR::Detach  
 Détache [m_str](#m_str) à partir de la `CComBSTR` objet et les jeux `m_str` à **NULL**.  
  
```
BSTR Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le `BSTR` associé à la `CComBSTR` objet.  
  
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
 Charge une ressource de chaîne spécifiée par `nID` et le stocke dans cet objet.  
  
```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 Consultez [LoadString](http://msdn.microsoft.com/library/windows/desktop/ms647486) dans le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si la chaîne est correctement chargé ; sinon, retourne **false**.  
  
### <a name="remarks"></a>Notes  
 La première fonction charge la ressource à partir du module identifié par vous via le `hInst` paramètre. La deuxième fonction charge la ressource à partir du module de ressources associé à la [CComModule](../../atl/reference/ccommodule-class.md)-objet utilisé dans ce projet dérivé.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]  
  
##  <a name="m_str"></a>  CComBSTR::m_str  
 Contient le `BSTR` associé à la `CComBSTR` objet.  
  
```
BSTR m_str;
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]  
  
##  <a name="operator_bstr"></a>  CComBSTR::operator BSTR  
 Les casts un `CComBSTR` de l’objet à un `BSTR`.  
  
```  
operator BSTR() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Vous pouvez ainsi passer `CComBSTR` objets à des fonctions qui ont **[in] BSTR** paramètres.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CComBSTR::m_str](#m_str).  
  
##  <a name="operator_not"></a>  CComBSTR::operator !  
 Vérifie si `BSTR` chaîne a la valeur NULL.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le [m_str](#m_str) membre est **NULL**; sinon, **false**.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur vérifie uniquement une valeur NULL, pas pour une chaîne vide.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="operator_neq"></a>  CComBSTR::operator ! =  
 Retourne l’inverse logique de [opérateur ==](#operator_eq_eq).  
  
```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrSrc`  
 [in] Objet `CComBSTR`  
  
 `pszSrc`  
 [in] Chaîne terminée par zéro.  
  
 `nNull`  
 [in] Doit être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’élément en cours de comparaison n’est pas égale à la `CComBSTR` de l’objet ; sinon, retourne **false**.  
  
### <a name="remarks"></a>Notes  
 `CComBSTR`s sont comparées textuellement dans le contexte des paramètres régionaux par défaut de l’utilisateur. L’opérateur de comparaison finale compare simplement la chaîne de relation contenant-contenue contre **NULL**.  
  
##  <a name="operator_amp"></a>  CComBSTR::operator &amp;  
 Retourne l’adresse de la `BSTR` stockés dans le [m_str](#m_str) membre.  
  
```
BSTR* operator&() throw();
```  
  
### <a name="remarks"></a>Notes  
 `CComBstr operator &` est une assertion spéciale associé pour aider à identifier les fuites de mémoire. Le programme sera évaluée lorsque le `m_str` membre est initialisé. Cette assertion a été créée pour identifier les situations où un programmeur utilise le `& operator` pour attribuer une nouvelle valeur à `m_str` membre sans la libération de la première allocation de `m_str`. Si `m_str` est égal à NULL, le programme suppose que m_str n’a pas été encore affectés. Dans ce cas, le programme ne sera pas évaluée.  
  
 Cette assertion n’est pas activée par défaut. Définir `ATL_CCOMBSTR_ADDRESS_OF_ASSERT` pour activer cette assertion.  
  
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
 `bstrSrc`  
 [in] A `CComBSTR` objet à ajouter.  
  
 `pszSrc`  
 [in] Une chaîne terminée par zéro à ajouter.  
  
### <a name="remarks"></a>Notes  
 `CComBSTR`s sont comparées textuellement dans le contexte des paramètres régionaux par défaut de l’utilisateur. Le **LPCOLESTR** comparaison est effectuée à l’aide `memcmp` sur les données brutes dans chaque chaîne. Le `LPCSTR` comparaison est effectuée de la même façon une fois qu’une valeur temporaire Unicode copie de `pszSrc` a été créé. L’opérateur de comparaison finale compare simplement la chaîne de relation contenant-contenue contre **NULL**.  
  
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
 Retourne **true** si l’élément en cours de comparaison est inférieure à la `CComBSTR` de l’objet ; sinon, retourne **false**.  
  
### <a name="remarks"></a>Notes  
 La comparaison est effectuée à l’aide des paramètres régionaux par défaut de l’utilisateur.  
  
##  <a name="operator_eq"></a>  CComBSTR::operator =  
 Définit le [m_str](#m_str) membre à une copie de `pSrc` ou à une copie de la `BSTR` membre *src*. L’opérateur d’assignation de déplacement déplace `src` sans le copier.   
  
```
CComBSTR& operator= (const CComBSTR& src);  
CComBSTR& operator= (LPCOLESTR pSrc);  
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="remarks"></a>Notes  
 Le `pSrc` paramètre spécifie un **LPCOLESTR** pour les versions Unicode ou `LPCSTR` pour les versions ANSI.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CComBSTR::Copy](#copy).  
  
##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==  
 Compare un `CComBSTR` avec une chaîne. `CComBSTR`s sont comparées textuellement dans le contexte des paramètres régionaux par défaut de l’utilisateur.  
  
```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrSrc`  
 [in] Objet `CComBSTR`  
  
 `pszSrc`  
 [in] Chaîne terminée par zéro.  
  
 `nNull`  
 [in] Doit être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’élément en cours de comparaison est égal à la `CComBSTR` de l’objet ; sinon, retourne **false**.  
  
### <a name="remarks"></a>Notes  
 L’opérateur de comparaison finale compare simplement la chaîne de relation contenant-contenue contre **NULL**.  
  
##  <a name="operator_gt"></a>  CComBSTR::operator &gt;  
 Compare un `CComBSTR` avec une chaîne.  
  
```
bool operator>(const CComBSTR& bstrSrc) const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’élément en cours de comparaison est supérieur à la `CComBSTR` de l’objet ; sinon, retourne **false**.  
  
### <a name="remarks"></a>Notes  
 La comparaison est effectuée à l’aide des paramètres régionaux par défaut de l’utilisateur.  
  
##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream  
 Définit le [m_str](#m_str) membre à la `BSTR` contenus dans le flux spécifié.  
  
```
HRESULT ReadFromStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pStream`  
 [in] Un pointeur vers le [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interface sur le flux de données contenant les données.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 **ReadToStream** requiert le contenu du flux à la position actuelle pour être compatible avec le format de données écrit par un appel à [WriteToStream](#writetostream).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]  
  
##  <a name="tolower"></a>  CComBSTR::ToLower  
 Convertit la chaîne en minuscules.  
  
```
HRESULT ToLower() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Consultez **CharLowerBuff** pour plus d’informations sur la façon dont la conversion est effectuée.  
  
##  <a name="toupper"></a>  CComBSTR::ToUpper  
 Convertit la chaîne en majuscules.  
  
```
HRESULT ToUpper() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Consultez **CharUpperBuff** pour plus d’informations sur la façon dont la conversion est effectuée.  
  
##  <a name="writetostream"></a>  CComBSTR::WriteToStream  
 Enregistre le [m_str](#m_str) membre à un flux de données.  
  
```
HRESULT WriteToStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pStream`  
 [in] Un pointeur vers le [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interface sur un flux de données.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez recréer un BSTR à partir du contenu du flux de données en utilisant la [ReadFromStream](#readfromstream) (fonction).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Macros de Conversion de chaînes MFC et ATL](string-conversion-macros.md)
