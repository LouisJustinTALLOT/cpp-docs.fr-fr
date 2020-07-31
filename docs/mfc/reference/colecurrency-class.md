---
title: COleCurrency, classe
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: ced4554701cef5fd6f790b9e37f4c1b41746b1ad
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470964"
---
# <a name="colecurrency-class"></a>COleCurrency, classe

Encapsule le type de données `CURRENCY` d'OLE automation.

## <a name="syntax"></a>Syntax

```
class COleCurrency
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleCurrency :: COleCurrency](#colecurrency)|Construit un objet `COleCurrency`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleCurrency :: format](#format)|Génère une représentation sous forme de chaîne mise en forme d’un `COleCurrency` objet.|
|[COleCurrency :: GetStatus](#getstatus)|Obtient l’État (validité) de cet `COleCurrency` objet.|
|[COleCurrency ::P arseCurrency](#parsecurrency)|Lit une valeur de devise à partir d’une chaîne et définit la valeur de `COleCurrency` .|
|[COleCurrency :: SetCurrency](#setcurrency)|Définit la valeur de cet `COleCurrency` objet.|
|[COleCurrency :: SetStatus](#setstatus)|Définit l’État (validité) de cet `COleCurrency` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur =](#operator_eq)|Copie une `COleCurrency` valeur.|
|[opérateur +,-](#operator_plus_minus)|Ajoute, soustrait et modifie le signe des `COleCurrency` valeurs.|
|[opérateur + =,-=](#operator_plus_minus_eq)|Ajoute et soustrait une `COleCurrency` valeur de cet `COleCurrency` objet.|
|[opérateur */](#operator_star)|Met `COleCurrency` à l’échelle une valeur avec une valeur entière.|
|[opérateur * =,/=](#operator_star_div_eq)|Met à l’échelle cette `COleCurrency` valeur d’après une valeur entière.|
|[ <<d’opérateur](#operator_stream)|Renvoie une `COleCurrency` valeur à `CArchive` ou `CDumpContext` .|
|[ >>d’opérateur](#operator_stream)|Saisit un `COleCurrency` objet à partir de `CArchive` .|
|[DEVISE de l’opérateur](#operator_currency)|Convertit une `COleCurrency` valeur en une devise.|
|[opérateur = =, <, <=, etc.](#colecurrency_relational_operators)|Compare deux `COleCurrency` valeurs.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleCurrency :: m_cur](#m_cur)|Contient la devise sous-jacente de cet `COleCurrency` objet.|
|[COleCurrency :: m_status](#m_status)|Contient l’état de cet `COleCurrency` objet.|

## <a name="remarks"></a>Remarques

`COleCurrency`n’a pas de classe de base.

La devise est implémentée sous la forme d’une valeur entière de 8 octets, à deux compléments, mise à l’échelle par 10 000. Ceci fournit un nombre à virgule fixe avec 15 chiffres à gauche du séparateur décimal et 4 chiffres à droite. Le type de données CURRENCY est extrêmement utile pour les calculs impliquant de l’argent, ou pour tout calcul à virgule fixe où la précision est importante. Il s’agit de l’un des types possibles pour le `VARIANT` type de données d’OLE Automation.

`COleCurrency`implémente également des opérations arithmétiques de base pour ce type à virgule fixe. Les opérations prises en charge ont été sélectionnées pour contrôler les erreurs d’arrondi qui se produisent pendant les calculs à virgule fixe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`COleCurrency`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency :: COleCurrency

Construit un objet `COleCurrency`.

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Paramètres

*cySrc*<br/>
Valeur monétaire à copier dans le nouvel `COleCurrency` objet.

*curSrc*<br/>
Objet existant `COleCurrency` à copier dans le nouvel `COleCurrency` objet.

*varSrc*<br/>
`VARIANT`Structure de données existante (éventuellement un `COleVariant` objet) à convertir en valeur monétaire (VT_CY) et copiée dans le nouvel `COleCurrency` objet.

*nunits*, *nFractionalUnits* indiquent les unités et la partie fractionnaire (en 1/10000) de la valeur à copier dans le nouvel `COleCurrency` objet.

### <a name="remarks"></a>Remarques

Tous ces constructeurs créent des `COleCurrency` objets initialisés à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit. Sauf indication contraire, l’état du nouvel `COleCurrency` élément est défini sur valide.

- COleCurrency () construit un `COleCurrency` objet initialisé à 0 (zéro).

- COleCurrency ( `cySrc` ) construit un `COleCurrency` objet à partir d’une valeur [monétaire](/windows/win32/api/wtypes/ns-wtypes-cy-r1) .

- COleCurrency ( `curSrc` ) construit un `COleCurrency` objet à partir d’un `COleCurrency` objet existant. Le nouvel objet a le même État que l’objet source.

- COleCurrency ( `varSrc` ) construit un `COleCurrency` objet. Tente de convertir une [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) structure ou un `COleVariant` objet variant en valeur Currency (VT_CY). Si cette conversion réussit, la valeur convertie est copiée dans le nouvel `COleCurrency` objet. Si ce n’est pas le cas, la valeur de l' `COleCurrency` objet est définie sur zéro (0) et son état sur non valide.

- COleCurrency ( `nUnits` , `nFractionalUnits` ) construit un `COleCurrency` objet à partir des composants numériques spécifiés. Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué sur les unités. Notez que les unités et la partie fractionnaire sont spécifiées par des valeurs long signées.

Pour plus d’informations, consultez les entrées [Currency](/windows/win32/api/wtypes/ns-wtypes-cy-r1) et [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) dans la SDK Windows.

### <a name="example"></a>Exemple

Les exemples suivants montrent les effets des constructeurs de paramètre zéro et à deux paramètres :

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency :: format

Appelez cette fonction membre pour créer une représentation mise en forme de la valeur monétaire.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indique des indicateurs pour les paramètres régionaux. Seul l’indicateur suivant concerne la devise :

- LOCALE_NOUSEROVERRIDE utiliser les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.

*lcid*<br/>
Indique l’ID de paramètres régionaux à utiliser pour la conversion.

### <a name="return-value"></a>Valeur renvoyée

`CString`Qui contient la valeur monétaire mise en forme.

### <a name="remarks"></a>Remarques

Il met en forme la valeur à l’aide des spécifications de langue locale (ID de paramètres régionaux). Un symbole monétaire n’est pas inclus dans la valeur retournée. Si l’état de cet `COleCurrency` objet est null, la valeur de retour est une chaîne vide. Si l’État n’est pas valide, la chaîne de retour est spécifiée par la IDS_INVALID_CURRENCY de ressource de type chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency :: GetStatus

Appelez cette fonction membre pour obtenir l’État (validité) d’un `COleCurrency` objet donné.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’état de cette `COleCurrency` valeur.

### <a name="remarks"></a>Remarques

La valeur de retour est définie par le `CurrencyStatus` type énuméré qui est défini dans la `COleCurrency` classe.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante :

- `COleCurrency::valid`Indique que cet `COleCurrency` objet est valide.

- `COleCurrency::invalid`Indique que cet `COleCurrency` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleCurrency::null`Indique que cet `COleCurrency` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « NULL » dans le sens de la base de données « n’ayant aucune valeur », par opposition à la valeur NULL C++.)

L’état d’un `COleCurrency` objet n’est pas valide dans les cas suivants :

- Si sa valeur est définie à partir d’une variante ou d’une `COleVariant` valeur qui n’a pas pu être convertie en valeur monétaire.

- Si cet objet a rencontré un dépassement de capacité positif ou négatif au cours d’une opération d’assignation arithmétique, par exemple `+=` ou **\*=** .

- Si une valeur non valide a été assignée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non valide à l’aide d' [SetStatus](#setstatus).

Pour plus d’informations sur les opérations qui peuvent affecter la valeur non valide à l’État, consultez les fonctions membres suivantes :

- [COleCurrency](#colecurrency)

- [opérateur =](#operator_eq)

- [opérateur +-](#operator_plus_minus)

- [opérateur + = et-=](#operator_plus_minus_eq)

- [opérateur */](#operator_star)

- [opérateur * = et/=](#operator_star_div_eq)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency :: m_cur

Structure [monétaire](/windows/win32/api/wtypes/ns-wtypes-cy-r1) sous-jacente de cet `COleCurrency` objet.

### <a name="remarks"></a>Remarques

> [!CAUTION]
> La modification de la valeur de la `CURRENCY` structure accessible par le pointeur retourné par cette fonction modifie la valeur de cet `COleCurrency` objet. Elle ne modifie pas l’état de cet `COleCurrency` objet.

Pour plus d’informations, consultez l’entrée [Currency](/windows/win32/api/wtypes/ns-wtypes-cy-r1) dans le SDK Windows.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency :: m_status

Le type de ce membre de données est le type énuméré `CurrencyStatus` , qui est défini dans la `COleCurrency` classe.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Remarques

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante :

- `COleCurrency::valid`Indique que cet `COleCurrency` objet est valide.

- `COleCurrency::invalid`Indique que cet `COleCurrency` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleCurrency::null`Indique que cet `COleCurrency` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « NULL » dans le sens de la base de données « n’ayant aucune valeur », par opposition à la valeur NULL C++.)

L’état d’un `COleCurrency` objet n’est pas valide dans les cas suivants :

- Si sa valeur est définie à partir d’une variante ou d’une `COleVariant` valeur qui n’a pas pu être convertie en valeur monétaire.

- Si cet objet a rencontré un dépassement de capacité positif ou négatif au cours d’une opération d’assignation arithmétique, par exemple `+=` ou **\*=** .

- Si une valeur non valide a été assignée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non valide à l’aide d' [SetStatus](#setstatus).

Pour plus d’informations sur les opérations qui peuvent affecter la valeur non valide à l’État, consultez les fonctions membres suivantes :

- [COleCurrency](#colecurrency)

- [opérateur =](#operator_eq)

- [opérateur +,-](#operator_plus_minus)

- [opérateur + =,-=](#operator_plus_minus_eq)

- [opérateur */](#operator_star)

- [opérateur * =,/=](#operator_star_div_eq)

> [!CAUTION]
> Ce membre de données est destiné à des situations de programmation avancées. Vous devez utiliser les fonctions membres inline [GetStatus](#getstatus) et [SetStatus](#setstatus). `SetStatus`Pour plus d’informations sur la définition explicite de ce membre de données, consultez.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency :: Operator =

Ces opérateurs d’assignation surchargés copient la valeur de devise source dans cet `COleCurrency` objet.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Remarques

Voici une brève description de chaque opérateur :

- **Operator = (** `cySrc` **)** la `CURRENCY` valeur est copiée dans l' `COleCurrency` objet et son état est défini sur valide.

- **Operator = (** `curSrc` **)** la valeur et l’état de l’opérande, un `COleCurrency` objet existant sont copiés dans cet `COleCurrency` objet.

- **opérateur = (** *varSrc* **)** Si la conversion de la `VARIANT` valeur (ou de l’objet [COleVariant](../../mfc/reference/colevariant-class.md) ) en devise ( `VT_CY` ) réussit, la valeur convertie est copiée dans cet `COleCurrency` objet et son état est défini sur valide. Si la conversion échoue, la valeur de l' `COleCurrency` objet est définie sur 0 et son état est non valide.

Pour plus d’informations, consultez les entrées [Currency](/windows/win32/api/wtypes/ns-wtypes-cy-r1) et [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) dans la SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency :: Operator +,-

Ces opérateurs vous permettent d’ajouter et de soustraire deux valeurs entre elles et de `COleCurrency` modifier le signe d’une `COleCurrency` valeur.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Remarques

Si l’un des opérandes est null, l’état de la valeur résultante `COleCurrency` est null.

Si l’opération arithmétique déborde, la valeur résultante `COleCurrency` n’est pas valide.

Si l’opérande n’est pas valide et que l’autre n’est pas null, l’état de la valeur résultante `COleCurrency` n’est pas valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency :: Operator + =,-=

Vous permet d’ajouter et de soustraire une `COleCurrency` valeur à et à partir de cet `COleCurrency` objet.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Remarques

Si l’un des opérandes a la valeur null, l’état de cet `COleCurrency` objet est défini sur null.

En cas de dépassement de capacité de l’opération arithmétique, l’état de cet `COleCurrency` objet est défini sur non valide.

Si l’un des opérandes n’est pas valide et que l’autre n’a pas la valeur null, l’état de cet `COleCurrency` objet est défini sur non valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency :: Operator \* et/

Vous permettent de mettre à l’échelle une `COleCurrency` valeur par valeur intégrale.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Remarques

Si l' `COleCurrency` opérande a la valeur null, l’état de la valeur résultante `COleCurrency` est null.

En cas de dépassement de capacité négatif ou négatif de l’opération arithmétique, l’état de la valeur résultante `COleCurrency` n’est pas valide.

Si l' `COleCurrency` opérande n’est pas valide, l’état de la valeur résultante `COleCurrency` n’est pas valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency :: Operator \* =,/=

Vous permettent de mettre à l’échelle cette `COleCurrency` valeur à l’aide d’une valeur intégrale.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Remarques

Si l' `COleCurrency` opérande a la valeur null, l’état de cet `COleCurrency` objet est défini sur null.

En cas de dépassement de capacité de l’opération arithmétique, l’état de cet `COleCurrency` objet est défini sur non valide.

Si l' `COleCurrency` opérande n’est pas valide, l’état de cet `COleCurrency` objet est défini sur non valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency :: Operator &lt; &lt; ,&gt;&gt;

Prend en charge le vidage et le stockage des diagnostics dans une archive.

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>Remarques

L' **>>** opérateur d’extraction () prend en charge le chargement à partir d’une archive.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency :: devise de l’opérateur

Retourne une `CURRENCY` structure dont la valeur est copiée à partir de cet `COleCurrency` objet.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Remarques

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency ::P arseCurrency

Appelez cette fonction membre pour analyser une chaîne afin de lire une valeur monétaire.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>Paramètres

*lpszCurrency*<br/>
Pointeur vers la chaîne terminée par le caractère null qui doit être analysée.

*dwFlags*<br/>
Indique des indicateurs pour les paramètres régionaux, éventuellement l’indicateur suivant :

- LOCALE_NOUSEROVERRIDE utiliser les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.

*lcid*<br/>
Indique l’ID de paramètres régionaux à utiliser pour la conversion.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la chaîne a été correctement convertie en valeur monétaire ; sinon, 0.

### <a name="remarks"></a>Remarques

Elle utilise les spécifications de langue locale (ID de paramètres régionaux) pour la signification des caractères non numériques dans la chaîne source.

Pour une description des valeurs d’ID de paramètres régionaux, consultez [prise en charge de plusieurs langues](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Si la chaîne a été correctement convertie en valeur monétaire, la valeur de cet `COleCurrency` objet est définie sur cette valeur et son état sur valide.

Si la chaîne n’a pas pu être convertie en valeur monétaire ou en cas de dépassement de capacité numérique, l’état de cet `COleCurrency` objet n’est pas valide.

Si la conversion de chaîne a échoué en raison d’erreurs d’allocation de mémoire, cette fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md). Dans tout autre État d’erreur, cette fonction lève une [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>COleCurrency, opérateurs relationnels

Compare deux valeurs monétaires et retourne une valeur différente de zéro si la condition est true ; Sinon, 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Remarques

> [!NOTE]
> La valeur de retour des opérations de classement ( **<** , **\<=**, **>** , **>=** ) n’est pas définie si l’état de l’un des opérandes est null ou non valide. Les opérateurs d’égalité ( `==` , `!=` ) considèrent l’état des opérandes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency :: SetCurrency

Appelez cette fonction membre pour définir les unités et la partie fractionnaire de cet `COleCurrency` objet.

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Paramètres

*nunits*, *nFractionalUnits* indiquent les unités et la partie fractionnaire (en 1/10000) de la valeur à copier dans cet `COleCurrency` objet.

### <a name="remarks"></a>Remarques

Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué sur les unités, comme indiqué dans la troisième des exemples suivants.

Notez que les unités et la partie fractionnaire sont spécifiées par des valeurs long signées. La quatrième des exemples suivants illustre ce qui se produit lorsque les paramètres ont des signes différents.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency :: SetStatus

Appelez cette fonction membre pour définir l’État (validité) de cet `COleCurrency` objet.

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Nouvel état de cet `COleCurrency` objet.

### <a name="remarks"></a>Remarques

La valeur du paramètre *Status* est définie par le `CurrencyStatus` type énuméré, qui est défini dans la `COleCurrency` classe.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante :

- `COleCurrency::valid`Indique que cet `COleCurrency` objet est valide.

- `COleCurrency::invalid`Indique que cet `COleCurrency` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleCurrency::null`Indique que cet `COleCurrency` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « NULL » dans le sens de la base de données « n’ayant aucune valeur », par opposition à la valeur NULL C++.)

> [!CAUTION]
> Cette fonction est destinée à des situations de programmation avancées. Cette fonction ne modifie pas les données de cet objet. Le plus souvent, il est utilisé pour définir l’État sur null ou non valide. Notez que l’opérateur d’assignation ( [Operator =](#operator_eq)) et [SetCurrency](#setcurrency) définissent l’État sur de l’objet en fonction de la ou des valeurs sources.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleVariant, classe](../../mfc/reference/colevariant-class.md)
