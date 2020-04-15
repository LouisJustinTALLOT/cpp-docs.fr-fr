---
title: Classe COleCurrency
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
ms.openlocfilehash: 3cb3217e02323f8a0afcd1639e6e24ee7b0f136e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366144"
---
# <a name="colecurrency-class"></a>Classe COleCurrency

Encapsule le type de données `CURRENCY` d'OLE automation.

## <a name="syntax"></a>Syntaxe

```
class COleCurrency
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Construit un objet `COleCurrency`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleCurrency::Format](#format)|Génère une représentation de chaîne `COleCurrency` formatée d’un objet.|
|[COleCurrency::GetStatus](#getstatus)|Obtient le statut (validité) de cet `COleCurrency` objet.|
|[COleCurrency::ParseCurrency](#parsecurrency)|Lit une valeur CURRENCY à partir `COleCurrency`d’une chaîne et définit la valeur de .|
|[COleCurrency::SetCurrency](#setcurrency)|Définit la valeur `COleCurrency` de cet objet.|
|[COleCurrency::SetStatus](#setstatus)|Définit l’état (validité) de cet `COleCurrency` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur](#operator_eq)|Copie `COleCurrency` d’une valeur.|
|[opérateur, -](#operator_plus_minus)|Ajoute, soustrait et change `COleCurrency` le signe des valeurs.|
|[opérateur , --](#operator_plus_minus_eq)|Ajoute et soustrait `COleCurrency` une `COleCurrency` valeur de cet objet.|
|[opérateur /](#operator_star)|Échelles `COleCurrency` d’une valeur par une valeur integer.|
|[opérateur, /MD](#operator_star_div_eq)|Échelles `COleCurrency` de cette valeur par une valeur integer.|
|[ <<de l’opérateur](#operator_stream)|Sorties `COleCurrency` d’une `CArchive` `CDumpContext`valeur ou .|
|[ >>de l’opérateur](#operator_stream)|Entre un `COleCurrency` objet `CArchive`de .|
|[opérateur CURRENCY](#operator_currency)|Convertit `COleCurrency` une valeur en CURRENCY.|
|[l’opérateur, <, <, etc.](#colecurrency_relational_operators)|Compare deux `COleCurrency` valeurs.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Contient le CURRENCY `COleCurrency` sous-jacent pour cet objet.|
|[COleCurrency::m_status](#m_status)|Contient l’état `COleCurrency` de cet objet.|

## <a name="remarks"></a>Notes

`COleCurrency`n’a pas de classe de base.

CURRENCY est mis en œuvre sous la forme d’un 8-byte, deux’s-complement valeur integer échelle de 10.000. Ceci fournit un nombre à virgule fixe avec 15 chiffres à gauche du séparateur décimal et 4 chiffres à droite. Le type de données CURRENCY est extrêmement utile pour les calculs impliquant de l’argent, ou pour tout calcul à points fixes où l’exactitude est importante. C’est l’un des `VARIANT` types possibles pour le type de données de l’automatisation OLE.

`COleCurrency`met également en œuvre certaines opérations arithmétiques de base pour ce type de point fixe. Les opérations prises en charge ont été sélectionnées pour contrôler les erreurs d’arrondissement qui se produisent lors des calculs à points fixes.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`COleCurrency`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::COleCurrency

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

*cySrc (en)*<br/>
Une valeur CURRENCY à copier `COleCurrency` dans le nouvel objet.

*curSrc*<br/>
Un `COleCurrency` objet existant à copier `COleCurrency` dans le nouvel objet.

*varSrc*<br/>
Une `VARIANT` structure de données `COleVariant` existante (peut-être un objet) à convertir en valeur `COleCurrency` de change (VT_CY) et copiée dans le nouvel objet.

*nUnits*, *nFractionalUnits* Indiquer les unités et la partie fractionnelle (dans 1/10,000) `COleCurrency` de la valeur à copier dans le nouvel objet.

### <a name="remarks"></a>Notes

Tous ces constructeurs `COleCurrency` créent de nouveaux objets paraspécifisés à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit. Sauf indication contraire, l’état du nouvel `COleCurrency` article est défini comme valide.

- COleCurrency() Construit `COleCurrency` un objet initialisé à 0 (zéro).

- COleCurrency(`cySrc`) Construit `COleCurrency` un objet à partir d’une valeur [CURRENCY.](/windows/win32/api/wtypes/ns-wtypes-cy~r1)

- COleCurrency(`curSrc`) Construit `COleCurrency` un objet `COleCurrency` à partir d’un objet existant. Le nouvel objet a le même statut que l’objet source.

- COleCurrency(`varSrc`) Construit `COleCurrency` un objet. Tentatives de [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) convertir `COleVariant` une structure ou un objet VARIANT en valeur de devise (VT_CY). Si cette conversion est réussie, la valeur convertie est copiée dans le nouvel `COleCurrency` objet. Si ce n’est pas `COleCurrency` le cas, la valeur de l’objet est définie à zéro (0) et son statut à invalide.

- COleCurrency(`nUnits` `nFractionalUnits`, ) `COleCurrency` Construit un objet à partir des composants numériques spécifiés. Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué aux unités. Notez que les unités et la partie fractionnaire sont spécifiées par des valeurs longues signées.

Pour plus d’informations, voir les entrées [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) et [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) dans le SDK Windows.

### <a name="example"></a>Exemple

Les exemples suivants montrent les effets des constructeurs zéro-paramètre et à deux paramètres :

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency::Format

Appelez cette fonction de membre pour créer une représentation formatée de la valeur de change.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indique les indicateurs pour les paramètres locaux. Seul le drapeau suivant est pertinent pour la monnaie :

- LOCALE_NOUSEROVERRIDE Utilisez les paramètres locaux par défaut du système, plutôt que les paramètres personnalisés de l’utilisateur.

*lcid*<br/>
Indique l’ID local à utiliser pour la conversion.

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient la valeur de change formatée.

### <a name="remarks"></a>Notes

Il formate la valeur en utilisant les spécifications de la langue locale (ID locaux). Un symbole de change n’est pas inclus dans la valeur retournée. Si l’état `COleCurrency` de cet objet est nul, la valeur de retour est une chaîne vide. Si le statut est invalide, la chaîne de retour est spécifiée par la ressource de chaîne IDS_INVALID_CURRENCY.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency::GetStatus

Appelez cette fonction de membre pour obtenir `COleCurrency` le statut (validité) d’un objet donné.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’état `COleCurrency` de cette valeur.

### <a name="remarks"></a>Notes

La valeur de rendement `CurrencyStatus` est définie par le `COleCurrency` type énuméré qui est défini au sein de la classe.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Pour une brève description de ces valeurs de statut, consultez la liste suivante :

- `COleCurrency::valid`Indique que `COleCurrency` cet objet est valide.

- `COleCurrency::invalid`Indique que `COleCurrency` cet objet est invalide; c’est-à-dire que sa valeur peut être incorrecte.

- `COleCurrency::null`Indique que `COleCurrency` cet objet est nul, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « nul » dans le sens de base de données de « n’avoir aucune valeur », par opposition au NULL DE C.)

L’état `COleCurrency` d’un objet est invalide dans les cas suivants :

- Si sa valeur est définie `COleVariant` à partir d’un VARIANT ou d’une valeur qui ne pourrait pas être converti en valeur de change.

- Si cet objet a connu un débordement ou un sous-flux `+=` lors ** \* **d’une opération d’affectation arithmétique, par exemple ou .

- Si une valeur invalide a été attribuée à cet objet.

- Si l’état de cet objet a été explicitement mis à invalider à l’aide [de SetStatus](#setstatus).

Pour plus d’informations sur les opérations qui peuvent invalider le statut, consultez les fonctions suivantes :

- [COleCurrency](#colecurrency)

- [opérateur](#operator_eq)

- [opérateur -](#operator_plus_minus)

- [opérateur et -MD](#operator_plus_minus_eq)

- [opérateur /](#operator_star)

- [opérateur et /md](#operator_star_div_eq)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency::m_cur

La structure [sous-jacente de CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) pour cet `COleCurrency` objet.

### <a name="remarks"></a>Notes

> [!CAUTION]
> Changer la valeur `CURRENCY` de la structure accessible par le pointeur `COleCurrency` retourné par cette fonction modifiera la valeur de cet objet. Il ne change pas `COleCurrency` l’état de cet objet.

Pour plus d’informations, voir l’entrée [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) dans le SDK Windows.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency::m_status

Le type de ce membre de `CurrencyStatus`données est le `COleCurrency` type énuméré , qui est défini dans la classe.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Notes

Pour une brève description de ces valeurs de statut, consultez la liste suivante :

- `COleCurrency::valid`Indique que `COleCurrency` cet objet est valide.

- `COleCurrency::invalid`Indique que `COleCurrency` cet objet est invalide; c’est-à-dire que sa valeur peut être incorrecte.

- `COleCurrency::null`Indique que `COleCurrency` cet objet est nul, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « nul » dans le sens de base de données de « n’avoir aucune valeur », par opposition au NULL DE C.)

L’état `COleCurrency` d’un objet est invalide dans les cas suivants :

- Si sa valeur est définie `COleVariant` à partir d’un VARIANT ou d’une valeur qui ne pourrait pas être converti en valeur de change.

- Si cet objet a connu un débordement ou un sous-flux `+=` lors ** \* **d’une opération d’affectation arithmétique, par exemple ou .

- Si une valeur invalide a été attribuée à cet objet.

- Si l’état de cet objet a été explicitement mis à invalider à l’aide [de SetStatus](#setstatus).

Pour plus d’informations sur les opérations qui peuvent invalider le statut, consultez les fonctions suivantes :

- [COleCurrency](#colecurrency)

- [opérateur](#operator_eq)

- [opérateur, -](#operator_plus_minus)

- [opérateur , --](#operator_plus_minus_eq)

- [opérateur /](#operator_star)

- [opérateur, /MD](#operator_star_div_eq)

> [!CAUTION]
> Ce membre des données est destiné à des situations de programmation avancées. Vous devez utiliser les fonctions de membre en ligne [GetStatus](#getstatus) et [SetStatus](#setstatus). Voir `SetStatus` pour d’autres mises en garde concernant le réglage explicite de ce membre des données.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency::opérateur

Ces opérateurs d’affectation surchargés copient `COleCurrency` la valeur de la devise source dans cet objet.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Notes

Une brève description de chaque opérateur suit :

- **opérateur** `cySrc` **()** La `CURRENCY` valeur est copiée dans l’objet `COleCurrency` et son statut est défini pour être valide.

- **opérateur** `curSrc` **()** La valeur et le statut de `COleCurrency` l’opéra, `COleCurrency` un objet existant sont copiés dans cet objet.

- **opérateur** *(varSrc)* **)** Si la conversion `VARIANT` de la valeur (ou [objet COleVariant)](../../mfc/reference/colevariant-class.md) en monnaie () `VT_CY`est `COleCurrency` réussie, la valeur convertie est copiée dans cet objet et son statut est défini comme valide. Si la conversion n’est pas `COleCurrency` réussie, la valeur de l’objet est réglée à 0 et son statut à invalide.

Pour plus d’informations, voir les entrées [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) et [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency::opérateur, -

Ces opérateurs vous permettent d’ajouter et de soustraire deux valeurs les unes `COleCurrency` aux autres et de modifier le signe d’une `COleCurrency` valeur.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Notes

Si l’un ou l’autre des opérandes est nul, l’état de la valeur résultante `COleCurrency` est nul.

Si l’opération arithmétique déborde, la valeur résultante est invalide. `COleCurrency`

Si l’opéra est invalide et que l’autre `COleCurrency` n’est pas nul, le statut de la valeur résultante est invalide.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency::opérateur ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '

Vous permettre d’ajouter `COleCurrency` et de soustraire une valeur à et à partir de cet `COleCurrency` objet.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Notes

Si l’un ou l’autre des `COleCurrency` opérandes est nul, l’état de cet objet est mis à null.

Si l’opération arithmétique déborde, `COleCurrency` l’état de cet objet est mis à invalider.

Si l’un ou l’autre des opérandes est `COleCurrency` invalide et que l’autre n’est pas nul, le statut de cet objet est mis à l’invalide.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency::opérateur \* et /

Vous permettre d’établir une `COleCurrency` valeur à valeur intégrale.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Notes

Si `COleCurrency` l’opérande est nulle, `COleCurrency` l’état de la valeur résultante est nul.

Si l’opération arithmétique déborde ou sous-débit, `COleCurrency` l’état de la valeur résultante est invalide.

Si `COleCurrency` l’opérande est invalide, le statut de la valeur résultante `COleCurrency` est invalide.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency::opérateur, \*/md

Vous permettre d’établir cette `COleCurrency` valeur par une valeur intégrale.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Notes

Si `COleCurrency` l’opéra est nul, `COleCurrency` l’état de cet objet est mis à nul.

Si l’opération arithmétique déborde, `COleCurrency` l’état de cet objet est mis à invalider.

Si `COleCurrency` l’opéra est invalide, `COleCurrency` le statut de cet objet est mis à invalider.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency::opérateur &lt; &lt;,&gt;&gt;

Soutient le dumping diagnostique et le stockage à une archive.

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

### <a name="remarks"></a>Notes

L’opérateur **>>** d’extraction () prend en charge le chargement à partir d’une archive.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency::opérateur CURRENCY

Retourne `CURRENCY` une structure dont la `COleCurrency` valeur est copiée à partir de cet objet.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Notes

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::ParseCurrency

Appelez cette fonction de membre pour analyser une chaîne pour lire une valeur de change.

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
Un pointeur à la corde non terminée qui doit être analysé.

*dwFlags*<br/>
Indique les indicateurs pour les paramètres locaux, peut-être le drapeau suivant:

- LOCALE_NOUSEROVERRIDE Utilisez les paramètres locaux par défaut du système, plutôt que les paramètres personnalisés de l’utilisateur.

*lcid*<br/>
Indique l’ID local à utiliser pour la conversion.

### <a name="return-value"></a>Valeur de retour

Nonzero si la chaîne a été convertie avec succès en une valeur de change, autrement 0.

### <a name="remarks"></a>Notes

Il utilise des spécifications de langue locale (ID locales) pour le sens des caractères nonnumériques dans la chaîne source.

Pour une discussion sur les valeurs d’identification locale, voir [Supporting Multiple Languages](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Si la chaîne a été convertie avec succès `COleCurrency` en valeur de change, la valeur de cet objet est définie à cette valeur et son statut en valide.

Si la chaîne ne pouvait pas être convertie en valeur de change `COleCurrency` ou s’il y avait un débordement numérique, l’état de cet objet est invalide.

Si la conversion de la chaîne a échoué en raison d’erreurs d’allocation de mémoire, cette fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md). Dans tout autre état d’erreur, cette fonction jette un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Opérateurs relationnels COleCurrency

Comparez deux valeurs monétaires et retournez non zéro si la condition est vraie; sinon 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> La valeur de retour des **<** ** \< **opérations **>** de commande ( , , , **>=**) n’est pas définie si le statut de l’opéra est nul ou invalide. Les opérateurs `==`d’égalité ( , `!=`) considèrent le statut des opérands.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency::SetCurrency

Appelez cette fonction de membre pour définir `COleCurrency` les unités et la partie fractionnelle de cet objet.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Paramètres

*nUnits*, *nFractionalUnits* Indiquer les unités et la partie fractionnelle (dans 1/10,000) de la valeur à copier dans cet `COleCurrency` objet.

### <a name="remarks"></a>Notes

Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué aux unités, comme le montre le troisième des exemples suivants.

Notez que les unités et la partie fractionnaire sont spécifiées par des valeurs longues signées. Le quatrième des exemples suivants montre ce qui se passe lorsque les paramètres ont des signes différents.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency::SetStatus

Appelez cette fonction de membre pour définir `COleCurrency` le statut (validité) de cet objet.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Le nouveau statut `COleCurrency` pour cet objet.

### <a name="remarks"></a>Notes

La valeur du paramètre *de statut* est définie par le `CurrencyStatus` type énuméré, qui est défini au sein de la `COleCurrency` classe.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Pour une brève description de ces valeurs de statut, consultez la liste suivante :

- `COleCurrency::valid`Indique que `COleCurrency` cet objet est valide.

- `COleCurrency::invalid`Indique que `COleCurrency` cet objet est invalide; c’est-à-dire que sa valeur peut être incorrecte.

- `COleCurrency::null`Indique que `COleCurrency` cet objet est nul, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « nul » dans le sens de base de données de « n’avoir aucune valeur », par opposition au NULL DE C.)

> [!CAUTION]
> Cette fonction est pour les situations de programmation avancées. Cette fonction ne modifie pas les données de cet objet. Il sera le plus souvent utilisé pour définir le statut à nul ou invalide. Notez que l’opérateur [d’affectation (opérateur](#operator_eq)) et [SetCurrency](#setcurrency) fixent l’état de l’objet en fonction de la valeur source(s).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleVariant, classe](../../mfc/reference/colevariant-class.md)
