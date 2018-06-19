---
title: Classe de CComCurrency | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
dev_langs:
- C++
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 847cbe230e14975e883c42f52538ba3863d505c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366245"
---
# <a name="ccomcurrency-class"></a>Classe de CComCurrency
`CComCurrency` a des méthodes et des opérateurs pour créer et gérer un objet CURRENCY.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComCurrency
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](#ccomcurrency)|Constructeur d'un objet `CComCurrency`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Retourne l'adresse d'un membre de données `m_currency`.|  
|[CComCurrency::GetFraction](#getfraction)|Appelez cette méthode pour retourner la partie fractionnaire d'un objet `CComCurrency`.|  
|[CComCurrency::GetInteger](#getinteger)|Appelez cette méthode pour retourner la partie entière d'un objet `CComCurrency`.|  
|[CComCurrency::Round](#round)|Appelez cette méthode pour arrondir un objet `CComCurrency` à l'entier le plus proche.|  
|[CComCurrency::SetFraction](#setfraction)|Appelez cette méthode pour définir la partie fractionnaire d'un objet `CComCurrency`.|  
|[CComCurrency::SetInteger](#setinteger)|Appelez cette méthode pour définir la partie entière d'un objet `CComCurrency`.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCurrency::operator-](#operator_-)|Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency`.|  
|[CComCurrency::operator ! =](#operator_neq)|Compare deux objets `CComCurrency` pour déterminer s'ils sont différents.|  
|[CComCurrency::operator *](#operator_star)|Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency`.|  
|[CComCurrency::operator * =](#operator_star_eq)|Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency` et de lui assigner le résultat.|  
|[CComCurrency::operator /](#operator_div)|Cet opérateur permet d'effectuer une division sur un objet `CComCurrency`.|  
|[CComCurrency::operator / =](#operator_div_eq)|Cet opérateur permet d'effectuer une division sur un objet `CComCurrency` et de lui assigner le résultat.|  
|[CComCurrency::operator +](#operator_add)|Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency`.|  
|[CComCurrency::operator +=](#operator_add_eq)|Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency` et d'assigner le résultat à l'objet actuel.|  
|[CComCurrency::operator <](#operator_lt)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit.|  
|[CComCurrency::operator < =](#operator_lt_eq)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit ou leur égalité.|  
|[CComCurrency::operator =](#operator_eq)|Cet opérateur assigne l'objet `CComCurrency` à une nouvelle valeur.|  
|[CComCurrency::operator =](#operator_-_eq)|Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency` et de lui assigner le résultat.|  
|[CComCurrency::operator ==](#operator_eq_eq)|Cet opérateur compare deux objets `CComCurrency` pour déterminer leur égalité.|  
|[CComCurrency::operator >](#operator_gt)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand.|  
|[CComCurrency::operator > =](#operator_gt_eq)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand ou leur égalité.|  
|[CComCurrency::operator devise](#operator_currency)|Effectue un cast d'un objet `CURRENCY`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|Variable `CURRENCY` créée par votre instance de classe.|  
  
## <a name="remarks"></a>Notes  
 `CComCurrency` est un wrapper pour le **devise** type de données. **DEVISE** est implémenté comme un entier de 8 octets de complément à 2 multiplié par 10 000. Ceci fournit un nombre à virgule fixe avec 15 chiffres à gauche du séparateur décimal et 4 chiffres à droite. Le **devise** type de données est très utile pour les calculs impliquant des valeurs monétaires, ou pour les calculs à virgule fixe où la précision est importante.  
  
 Le **CComCurrency** wrapper implémente des opérations arithmétiques, de comparaison et assignation de ce type à virgule fixe. Les applications prises en charge ont été sélectionnées pour contrôler les erreurs d'arrondi qui peuvent se produire lors de calculs à virgule fixe.  
  
 L'objet `CComCurrency` permet d'accéder aux nombres figurant de chaque côté du séparateur décimal sous la forme de deux composantes : une partie entière correspondant à la valeur à gauche du séparateur décimal et une partie fractionnaire correspondant à la valeur à droite du séparateur décimal. La partie fractionnaire est stockée en interne comme une valeur entière comprise entre -9999 ( **CY_MIN_FRACTION**) et + 9999 ( **CY_MAX_FRACTION**). La méthode [CComCurrency::GetFraction](#getfraction) retourne une valeur d’un facteur de 10 000 ( **CY_SCALE**).  
  
 Lorsque vous spécifiez les composantes entière et fractionnaire d’un **CComCurrency** d’objet, n’oubliez pas que la partie fractionnaire est un nombre dans la plage comprise entre 0 et 9999. Ceci est important dans le cas d'une devise telle que le dollar américain, où les sommes sont exprimées avec seulement deux chiffres significatifs après le séparateur décimal. Bien que les deux derniers chiffres ne soient pas affichés, ils doivent être pris en compte.  
  
|Value|Affectations CComCurrency possibles|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency (10,5000) *ou* CComCurrency (10.50)|  
|$10.05|CComCurrency (10,500) *ou* CComCurrency (10.05)|  
  
 Les valeurs **CY_MIN_FRACTION**, **CY_MAX_FRACTION**, et **CY_SCALE** sont définies dans atlcur.h.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcur.h  
  
##  <a name="ccomcurrency"></a>  CComCurrency::CComCurrency  
 Constructeur.  
  
```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);  
CComCurrency(USHORT usSrc);  
CComCurrency(CHAR cSrc);  
CComCurrency(DOUBLE dSrc);  
CComCurrency(FLOAT fSrc);  
CComCurrency(LONG lSrc);  
CComCurrency(SHORT sSrc);  
CComCurrency(BYTE bSrc);  
CComCurrency(LONGLONG nInteger, SHORT nFraction);  
explicit CComCurrency(LPDISPATCH pDispSrc);  
explicit CComCurrency(const VARIANT& varSrc);  
explicit CComCurrency(LPCWSTR szSrc);  
explicit CComCurrency(LPCSTR szSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 `curSrc`  
 Objet `CComCurrency` existant.  
  
 `cySrc`  
 Une variable de type **devise**.  
  
 `bSrc`, `dSrc`, `fSrc`, `lSrc`, *sSrc*, *ulSrc, usSrc*  
 La valeur initiale donnée à la variable membre `m_currency`.  
  
 `cSrc`  
 Un caractère contenant la valeur initiale donnée à la variable membre `m_currency`.  
  
 `nInteger`, *nFraction*  
 Les composantes entière et fractionnaire de la valeur monétaire initiale. Consultez le [CComCurrency](../../atl/reference/ccomcurrency-class.md) vue d’ensemble pour plus d’informations.  
  
 `pDispSrc`  
 Un `IDispatch` pointeur.  
  
 *varSrc*  
 Une variable de type **variante**. Les paramètres régionaux du thread actuel sont utilisé pour effectuer la conversion.  
  
 `szSrc`  
 Chaîne ANSI ou Unicode contenant la valeur initiale. Les paramètres régionaux du thread actuel sont utilisé pour effectuer la conversion.  
  
### <a name="remarks"></a>Notes  
 Le constructeur définit la valeur initiale de [CComCurrency::m_currency](#m_currency)et accepte un large éventail de types de données, y compris des entiers, chaînes, nombres à virgule flottante, **devise** variables et autres `CComCurrency` objets. Si aucune valeur n’est fournie, `m_currency` est définie sur 0.  
  
 En cas d’erreur, par exemple un dépassement de capacité, les constructeurs ne dispose pas d’une spécification d’exception vide ( **throw()**) appeler `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
 Lorsque vous utilisez des valeurs à virgule flottante ou en doubles pour affecter une valeur, notez que **CComCurrency (10.50)** équivaut à **CComCurrency (10,5000)** et non **CComCurrency(10,50)**.  
  
##  <a name="getcurrencyptr"></a>  CComCurrency::GetCurrencyPtr  
 Retourne l'adresse d'un membre de données `m_currency`.  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’adresse d’un `m_currency` membre de données  
  
##  <a name="getfraction"></a>  CComCurrency::GetFraction  
 Appelez cette méthode pour retourner la partie fractionnaire de la `CComCurrency` objet.  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la partie fractionnaire de la `m_currency` membre de données.  
  
### <a name="remarks"></a>Notes  
 La partie fractionnaire est une valeur d’entier de 4 chiffres comprise entre -9999 ( **CY_MIN_FRACTION**) et + 9999 ( **CY_MAX_FRACTION**). `GetFraction` Retourne cette valeur multipliée par 10 000 ( **CY_SCALE**). Les valeurs de **CY_MIN_FRACTION**, **CY_MAX_FRACTION**, et **CY_SCALE** sont définies dans atlcur.h.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="getinteger"></a>  CComCurrency::GetInteger  
 Appelez cette méthode pour obtenir la partie entière d’un `CComCurrency` objet.  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la partie entière de la `m_currency` membre de données.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="m_currency"></a>  CComCurrency::m_currency  
 Le **devise** membre de données.  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>Notes  
 Ce membre contient la devise accessibles et manipulées par les méthodes de cette classe.  
  
##  <a name="operator_-"></a>  CComCurrency::operator-  
 Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency`.  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CComCurrency` objet représentant le résultat de la soustraction. En cas d’erreur, par exemple un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="operator_neq"></a>  CComCurrency::operator ! =  
 Cet opérateur compare deux objets sont inégaux.  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency` à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’élément en cours de comparaison n’est pas égale à la `CComCurrency` de l’objet ; sinon, **false**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="operator_star"></a>  CComCurrency::operator *  
 Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency`.  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `nOperand`  
 Multiplicateur.  
  
 `cur`  
 Le `CComCurrency` objet utilisé comme multiplicateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CComCurrency` objet représentant le résultat de la multiplication. En cas d’erreur, par exemple un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="operator_star_eq"></a>  CComCurrency::operator * =  
 Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency` et de lui assigner le résultat.  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Paramètres  
 `nOperand`  
 Multiplicateur.  
  
 `cur`  
 Le `CComCurrency` objet utilisé comme multiplicateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CComCurrency` objet. En cas d’erreur, par exemple un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="operator_div"></a>  CComCurrency::operator /  
 Cet opérateur permet d'effectuer une division sur un objet `CComCurrency`.  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `nOperand`  
 Diviseur.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CComCurrency` objet représentant le résultat de la division. Si le diviseur est 0, un échec d’assertion se produit.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="operator_div_eq"></a>  CComCurrency::operator / =  
 Cet opérateur permet d'effectuer une division sur un objet `CComCurrency` et de lui assigner le résultat.  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>Paramètres  
 `nOperand`  
 Diviseur.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CComCurrency` objet. Si le diviseur est 0, un échec d’assertion se produit.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="operator_add"></a>  CComCurrency::operator +  
 Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency`.  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Le `CComCurrency` l’objet à ajouter à l’objet d’origine.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CComCurrency` objet représentant le résultat de l’addition. En cas d’erreur, par exemple un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="operator_add_eq"></a>  CComCurrency::operator +=  
 Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency` et d'assigner le résultat à l'objet actuel.  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CComCurrency` objet. En cas d’erreur, par exemple un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="operator_lt"></a>  CComCurrency::operator &lt;  
 Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit.  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est inférieur au second, **false** dans le cas contraire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="operator_lt_eq"></a>  CComCurrency::operator &lt;=  
 Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit ou leur égalité.  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est inférieur ou égal au second, **false** dans le cas contraire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="operator_eq"></a>  CComCurrency::operator =  
 Cet opérateur assigne l'objet `CComCurrency` à une nouvelle valeur.  
  
```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 `curSrc`  
 A **CComCurrency** objet.  
  
 `cySrc`  
 Une variable de type **devise**.  
  
 *sSrc*, `fSrc`, `lSrc`, *bSrc*, *usSrc*, `dSrc`, *cSrc*, *ulSrc*, `dSrc`  
 La valeur numérique à attribuer à la `CComCurrency` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CComCurrency` objet. En cas d’erreur, par exemple un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="operator_-_eq"></a>  CComCurrency::operator =  
 Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency` et de lui assigner le résultat.  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CComCurrency` objet. En cas d’erreur, par exemple un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CComCurrency::operator ==  
 Cet opérateur compare deux objets `CComCurrency` pour déterminer leur égalité.  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Le `CComCurrency` objet à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si les objets sont égaux (autrement dit, le `m_currency` membres de données, les deux entier et fractions de seconde, dans les deux objets ont la même valeur), **false** dans le cas contraire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="operator_gt"></a>  CComCurrency::operator &gt;  
 Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand.  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est supérieur à la seconde, **false** dans le cas contraire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="operator_gt_eq"></a>  CComCurrency::operator &gt;=  
 Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand ou leur égalité.  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `cur`  
 Objet `CComCurrency`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est supérieure ou égale à la seconde, **false** dans le cas contraire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="operator_currency"></a>  CComCurrency::operator devise  
 Ces opérateurs sont utilisés pour convertir un `CComCurrency` de l’objet à un **devise** type de données.  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence à un **devise** objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="round"></a>  CComCurrency::Round  
 Appelez cette méthode pour arrondir la devise à un nombre spécifié de décimales.  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDecimals*  
 Le nombre de chiffres auquel `m_currency` arrondi, dans la plage 0 à 4.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="setfraction"></a>  CComCurrency::SetFraction  
 Appelez cette méthode pour définir la partie fractionnaire d'un objet `CComCurrency`.  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>Paramètres  
 *nFraction*  
 La valeur à affecter à la partie fractionnaire de la `m_currency` membre de données. Le signe de la partie fractionnaire doit être identique à la partie entière et la valeur doit être dans la plage de -9999 ( **CY_MIN_FRACTION**) à + 9999 ( **CY_MAX_FRACTION**).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="setinteger"></a>  CComCurrency::SetInteger  
 Appelez cette méthode pour définir la partie entière d'un objet `CComCurrency`.  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>Paramètres  
 `nInteger`  
 La valeur à affecter à la partie entière de la `m_currency` membre de données. Le signe de la partie entière doit correspondre à la connexion de la partie fractionnaire existante.  
  
 `nInteger` doit être comprise entre **CY_MIN_INTEGER** à **CY_MAX_INTEGER** inclus. Ces valeurs sont définies dans atlcur.h.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [COleCurrency, classe](../../mfc/reference/colecurrency-class.md)   
 [DEVISE](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
