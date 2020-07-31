---
title: CComCurrency, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
ms.openlocfilehash: 2b3c260f250fdb198c8317355628fa2fe62c44eb
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470782"
---
# <a name="ccomcurrency-class"></a>CComCurrency, classe

`CComCurrency` a des méthodes et des opérateurs pour créer et gérer un objet CURRENCY.

## <a name="syntax"></a>Syntax

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
|[CComCurrency :: Operator-](#operator_-)|Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency`.|
|[CComCurrency::operator !=](#operator_neq)|Compare deux objets `CComCurrency` pour déterminer s'ils sont différents.|
|[CComCurrency :: Operator *](#operator_star)|Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency`.|
|[CComCurrency :: Operator * =](#operator_star_eq)|Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency` et de lui assigner le résultat.|
|[CComCurrency :: Operator/](#operator_div)|Cet opérateur permet d'effectuer une division sur un objet `CComCurrency`.|
|[CComCurrency :: Operator/=](#operator_div_eq)|Cet opérateur permet d'effectuer une division sur un objet `CComCurrency` et de lui assigner le résultat.|
|[CComCurrency :: Operator +](#operator_add)|Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency`.|
|[CComCurrency :: Operator + =](#operator_add_eq)|Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency` et d'assigner le résultat à l'objet actuel.|
|[CComCurrency :: Operator <](#operator_lt)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit.|
|[CComCurrency :: Operator <=](#operator_lt_eq)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit ou leur égalité.|
|[CComCurrency :: Operator =](#operator_eq)|Cet opérateur assigne l'objet `CComCurrency` à une nouvelle valeur.|
|[CComCurrency :: Operator-=](#operator_-_eq)|Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency` et de lui assigner le résultat.|
|[CComCurrency :: Operator = =](#operator_eq_eq)|Cet opérateur compare deux objets `CComCurrency` pour déterminer leur égalité.|
|[CComCurrency :: Operator >](#operator_gt)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand.|
|[CComCurrency :: Operator >=](#operator_gt_eq)|Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand ou leur égalité.|
|[CComCurrency :: devise de l’opérateur](#operator_currency)|Effectue un cast d’un objet CURRENCY.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Variable monétaire créée par votre instance de classe.|

## <a name="remarks"></a>Remarques

`CComCurrency` est un wrapper pour le type de données CURRENCY. Le type CURRENCY est implémenté en tant qu'entier de 8 octets en complément à deux, multiplié par 10 000. Ceci fournit un nombre à virgule fixe avec 15 chiffres à gauche du séparateur décimal et 4 chiffres à droite. Le type de données CURRENCY est extrêmement utile pour les calculs impliquant des valeurs monétaires ou pour les calculs à virgule fixe où la précision est importante.

Le `CComCurrency` Wrapper implémente des opérations arithmétiques, d’assignation et de comparaison pour ce type à virgule fixe. Les applications prises en charge ont été sélectionnées pour contrôler les erreurs d'arrondi qui peuvent se produire lors de calculs à virgule fixe.

L'objet `CComCurrency` permet d'accéder aux nombres figurant de chaque côté du séparateur décimal sous la forme de deux composantes : une partie entière correspondant à la valeur à gauche du séparateur décimal et une partie fractionnaire correspondant à la valeur à droite du séparateur décimal. La partie fractionnaire est stockée en interne en tant que valeur entière comprise entre -9999 (CY_MIN_FRACTION) et +9999 (CY_MAX_FRACTION). La méthode [CComCurrency :: GetFraction](#getfraction) retourne une valeur mise à l’échelle par un facteur de 10000 (CY_SCALE).

Lorsque vous spécifiez les composants de type entier et fractionnaire d’un `CComCurrency` objet, n’oubliez pas que le composant fractionnaire est un nombre compris entre 0 et 9999. Ceci est important dans le cas d'une devise telle que le dollar américain, où les sommes sont exprimées avec seulement deux chiffres significatifs après le séparateur décimal. Bien que les deux derniers chiffres ne soient pas affichés, ils doivent être pris en compte.

|Valeur|Affectations CComCurrency possibles|
|-----------|---------------------------------------|
|$10.50|CComCurrency (10, 5000) *ou* CComCurrency (10,50)|
|$10.05|CComCurrency (10500) *ou* CComCurrency (10.05)|

Les valeurs CY_MIN_FRACTION, CY_MAX_FRACTION et CY_SCALE sont définies dans atlcur.h.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcur. h

## <a name="ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CComCurrency :: CComCurrency

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

*curSrc*<br/>
Objet `CComCurrency` existant.

*cySrc*<br/>
Variable de type CURRENCY.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
Valeur initiale donnée à la variable membre `m_currency` .

*cSrc*<br/>
Caractère contenant la valeur initiale donnée à la variable membre `m_currency` .

*nInteger*, *nFraction*<br/>
Parties entières et fractionnaires de la valeur monétaire initiale. Pour plus d’informations, consultez la vue d’ensemble de [CComCurrency](../../atl/reference/ccomcurrency-class.md) .

*pDispSrc*<br/>
`IDispatch`Pointeur.

*varSrc*<br/>
Variable de type VARIANT. Les paramètres régionaux du thread actuel sont utilisés pour effectuer la conversion.

*szSrc*<br/>
Chaîne Unicode ou ANSI contenant la valeur initiale. Les paramètres régionaux du thread actuel sont utilisés pour effectuer la conversion.

### <a name="remarks"></a>Remarques

Le constructeur définit la valeur initiale de [CComCurrency :: m_currency](#m_currency)et accepte un large éventail de types de données, notamment des entiers, des chaînes, des nombres à virgule flottante, des variables monétaires et d’autres `CComCurrency` objets. Si aucune valeur n’est fournie, a la valeur `m_currency` 0.

En cas d’erreur, telle qu’un dépassement de capacité, les constructeurs ne disposant pas d’un appel de spécification d’exception vide (**Throw ()**) `AtlThrow` avec un HRESULT décrivant l’erreur.

Lorsque vous utilisez des valeurs à virgule flottante ou double pour assigner une valeur, Notez que `CComCurrency(10.50)` est équivalent à `CComCurrency(10,5000)` et non `CComCurrency(10,50)` .

## <a name="ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CComCurrency :: GetCurrencyPtr

Retourne l'adresse d'un membre de données `m_currency`.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’adresse d’un `m_currency` membre de données

## <a name="ccomcurrencygetfraction"></a><a name="getfraction"></a>CComCurrency :: GetFraction

Appelez cette méthode pour retourner le composant fractionnaire de l' `CComCurrency` objet.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le composant fractionnaire du membre de `m_currency` données.

### <a name="remarks"></a>Remarques

Le composant fractionnaire est une valeur entière de 4 chiffres comprise entre-9999 (CY_MIN_FRACTION) et + 9999 (CY_MAX_FRACTION). `GetFraction`retourne cette valeur mise à l’échelle par 10000 (CY_SCALE). Les valeurs de CY_MIN_FRACTION, CY_MAX_FRACTION et CY_SCALE sont définies dans atlcur. h.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

## <a name="ccomcurrencygetinteger"></a><a name="getinteger"></a>CComCurrency :: GetInteger

Appelez cette méthode pour obtenir le composant entier d’un `CComCurrency` objet.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le composant entier du `m_currency` membre de données.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

## <a name="ccomcurrencym_currency"></a><a name="m_currency"></a>CComCurrency :: m_currency

Membre de données de devise.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Remarques

Ce membre contient la devise accessible et manipulée par les méthodes de cette classe.

## <a name="ccomcurrencyoperator--"></a><a name="operator_-"></a>CComCurrency :: Operator-

Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency`.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency`.

### <a name="return-value"></a>Valeur renvoyée

Retourne un `CComCurrency` objet représentant le résultat de la soustraction. En cas d’erreur, telle qu’un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_neq"></a>CComCurrency :: Operator ! =

Cet opérateur compare l’inégalité de deux objets.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency` à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’élément en cours de comparaison n’est pas égal à l' `CComCurrency` objet ; sinon, false.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star"></a>CComCurrency :: Operator *

Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency`.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*nOperand*<br/>
Multiplicateur.

*Tabs*<br/>
`CComCurrency`Objet utilisé comme multiplicateur.

### <a name="return-value"></a>Valeur renvoyée

Retourne un `CComCurrency` objet représentant le résultat de la multiplication. En cas d’erreur, telle qu’un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CComCurrency ::, opérateur\*=

Cet opérateur permet d'effectuer une multiplication sur un objet `CComCurrency` et de lui assigner le résultat.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Paramètres

*nOperand*<br/>
Multiplicateur.

*Tabs*<br/>
`CComCurrency`Objet utilisé comme multiplicateur.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CComCurrency` . En cas d’erreur, telle qu’un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div"></a>CComCurrency :: Operator/

Cet opérateur permet d'effectuer une division sur un objet `CComCurrency`.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Paramètres

*nOperand*<br/>
Diviseur.

### <a name="return-value"></a>Valeur renvoyée

Retourne un `CComCurrency` objet représentant le résultat de la Division. Si le diviseur est égal à 0, un échec d’assertion se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CComCurrency :: Operator/=

Cet opérateur permet d'effectuer une division sur un objet `CComCurrency` et de lui assigner le résultat.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Paramètres

*nOperand*<br/>
Diviseur.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CComCurrency` . Si le diviseur est égal à 0, un échec d’assertion se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add"></a>CComCurrency :: Operator +

Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency`.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
`CComCurrency`Objet à ajouter à l’objet d’origine.

### <a name="return-value"></a>Valeur renvoyée

Retourne un `CComCurrency` objet représentant le résultat de l’addition. En cas d’erreur, telle qu’un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CComCurrency :: Operator + =

Cet opérateur permet d'effectuer une addition sur un objet `CComCurrency` et d'assigner le résultat à l'objet actuel.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency`.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CComCurrency` . En cas d’erreur, telle qu’un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CComCurrency ::, opérateur&lt;

Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency`.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le premier objet est inférieur au second, FALSe dans le cas contraire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CComCurrency ::, opérateur&lt;=

Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus petit ou leur égalité.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency`.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le premier objet est inférieur ou égal au second, FALSe dans le cas contraire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq"></a>CComCurrency :: Operator =

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

*curSrc*<br/>
Objet `CComCurrency`.

*cySrc*<br/>
Variable de type CURRENCY.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *CSRC*, *ulSrc*, *dSrc*<br/>
Valeur numérique à assigner à l' `CComCurrency` objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CComCurrency` . En cas d’erreur, telle qu’un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

## <a name="ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CComCurrency :: Operator-=

Cet opérateur permet d'effectuer une soustraction sur un objet `CComCurrency` et de lui assigner le résultat.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency`.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CComCurrency` . En cas d’erreur, telle qu’un dépassement de capacité, cet opérateur appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CComCurrency :: Operator = =

Cet opérateur compare deux objets `CComCurrency` pour déterminer leur égalité.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency` à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si les objets sont égaux (autrement dit, les `m_currency` données membres, Integer et fractionnaires, dans les deux objets ont la même valeur); sinon, false.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CComCurrency ::, opérateur&gt;

Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency`.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le premier objet est supérieur au second, FALSe dans le cas contraire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CComCurrency ::, opérateur&gt;=

Cet opérateur compare deux objets `CComCurrency` pour déterminer le plus grand ou leur égalité.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Paramètres

*Tabs*<br/>
Objet `CComCurrency`.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le premier objet est supérieur ou égal au second, FALSe dans le cas contraire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

## <a name="ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CComCurrency :: devise de l’opérateur

Ces opérateurs sont utilisés pour effectuer un cast d’un `CComCurrency` objet en un type de données Currency.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à un objet CURRENCY.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

## <a name="ccomcurrencyround"></a><a name="round"></a>CComCurrency :: Round

Appelez cette méthode pour arrondir la devise à un nombre spécifié de décimales.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Paramètres

*nDecimals*<br/>
Nombre de chiffres à utiliser pour l' `m_currency` arrondi, compris entre 0 et 4.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

## <a name="ccomcurrencysetfraction"></a><a name="setfraction"></a>CComCurrency :: SetFraction

Appelez cette méthode pour définir la partie fractionnaire d'un objet `CComCurrency`.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Paramètres

*nFraction*<br/>
Valeur à assigner au composant fractionnaire du `m_currency` membre de données. Le signe du composant fractionnaire doit être le même que le composant entier, et la valeur doit être comprise entre-9999 (CY_MIN_FRACTION) et + 9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

## <a name="ccomcurrencysetinteger"></a><a name="setinteger"></a>CComCurrency :: SetInteger

Appelez cette méthode pour définir la partie entière d'un objet `CComCurrency`.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Paramètres

*nInteger*<br/>
Valeur à assigner au composant entier du membre de `m_currency` données. Le signe du composant entier doit correspondre au signe du composant fractionnaire existant.

*nInteger* doit se trouver dans la plage CY_MIN_INTEGER pour CY_MAX_INTEGER inclus. Ces valeurs sont définies dans atlcur. h.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Voir aussi

[COleCurrency, classe](../../mfc/reference/colecurrency-class.md)<br/>
[ACCÈS](/windows/win32/api/wtypes/ns-wtypes-cy-r1)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
