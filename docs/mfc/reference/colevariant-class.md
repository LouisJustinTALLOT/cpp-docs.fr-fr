---
title: COleVariant, classe
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: 66ff3d684dba6b876ae94699209a43aaf4db5f23
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916946"
---
# <a name="colevariant-class"></a>COleVariant, classe

Encapsule le type de données [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) .

## <a name="syntax"></a>Syntaxe

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleVariant::COleVariant](#colevariant)|Construit un objet `COleVariant`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleVariant::Attach](#attach)|Joint un VARIANT à un `COleVariant`.|
|[COleVariant::ChangeType](#changetype)|Modifie le type variant de cet `COleVariant` objet.|
|[COleVariant::Clear](#clear)|Efface cet `COleVariant` objet.|
|[COleVariant::Detach](#detach)|Détache un variant d’un `COleVariant` et retourne le variant.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Récupère un tableau d’octets d’un tableau variant existant.|
|[COleVariant::SetString](#setstring)|Affecte à la chaîne un type particulier, généralement ANSI.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleVariant:: Operator LPCVARIANT](#operator_lpcvariant)|Convertit `COleVariant` une valeur `LPCVARIANT`en.|
|[COleVariant:: Operator LPVARIANT](#operator_lpvariant)|Convertit `COleVariant` un objet `LPVARIANT`en.|
|[COleVariant:: Operator =](#operator_eq)|Copie une `COleVariant` valeur.|
|[COleVariant::operator ==](#operator_eq_eq)|Compare deux `COleVariant` valeurs.|
|[COleVariant:: Operator &lt;, &lt;&gt;&gt;](#operator_lt_lt__gt_gt)|Renvoie une `COleVariant` valeur à `CArchive` ou `CDumpContext` et les entrées `COleVariant` d’un `CArchive`objet à partir de.|

## <a name="remarks"></a>Notes

Ce type de données est utilisé dans OLE Automation. Plus précisément, la structure [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams) contient un pointeur vers un tableau de structures de type Variant. Une `DISPPARAMS` structure est utilisée pour passer des paramètres à [IDispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Cette classe est dérivée de `VARIANT` la structure. Cela signifie que vous pouvez passer `COleVariant` un dans un paramètre qui appelle pour `VARIANT` un et que les données membres de `VARIANT` la structure sont des membres de `COleVariant`données accessibles de.

Les deux classes MFC associées [COleCurrency](../../mfc/reference/colecurrency-class.md) et [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsulent les types de données Variant `VT_CY`Currency () et `VT_DATE`Date (). La `COleVariant` classe est largement utilisée dans les classes DAO; consultez ces classes pour une utilisation classique de cette classe, par exemple [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Pour plus d’informations, consultez les entrées [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [Currency](/windows/desktop/api/wtypes/ns-wtypes-tagcy), [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams)et [IDispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) dans le SDK Windows.

Pour plus d’informations sur `COleVariant` la classe et son utilisation dans OLE Automation, consultez «passage de paramètres dans OLE Automation» dans l’article [automatisation](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="attach"></a>  COleVariant::Attach

Appelez cette fonction pour attacher l’objet [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) donné à l’objet `COleVariant` actuel.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet existant `VARIANT` à attacher à l’objet actuel `COleVariant` .

### <a name="remarks"></a>Notes

Cette fonction définit le VARTYPE de *varSrc* sur VT_EMPTY.

Pour plus d’informations, consultez les entrées [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) et [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) dans le SDK Windows.

##  <a name="colevariant"></a>  COleVariant::COleVariant

Construit un objet `COleVariant`.

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet ou `COleVariant` `VARIANT` existant à copier dans le nouvel `COleVariant` objet.

*pSrc*<br/>
Pointeur vers un `VARIANT` objet qui sera copié dans le nouvel `COleVariant` objet.

*lpszSrc*<br/>
Chaîne terminée par le caractère null à copier dans le nouvel `COleVariant` objet.

*vtSrc*<br/>
Pour le nouvel `COleVariant`objet. `VARTYPE`

*strSrc*<br/>
Objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) à copier dans le nouvel `COleVariant` objet.

*nSrc*, *lSrc* une valeur numérique à copier dans le nouvel `COleVariant` objet.

*vtSrc*<br/>
Pour le nouvel `COleVariant`objet. `VARTYPE`

*curSrc*<br/>
Objet [COleCurrency](../../mfc/reference/colecurrency-class.md) à copier dans le nouvel `COleVariant` objet.

*fltSrc*, *dblSrc*<br/>
Valeur numérique à copier dans le nouvel objet `COleVariant`.

*timeSrc*<br/>
Objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) à copier dans le nouvel `COleVariant` objet.

*arrSrc*<br/>
Objet [CByteArray](../../mfc/reference/cbytearray-class.md) à copier dans le nouvel `COleVariant` objet.

*lbSrc*<br/>
Objet [CLongBinary](../../mfc/reference/clongbinary-class.md) à copier dans le nouvel `COleVariant` objet.

*pidl*<br/>
Pointeur vers une structure [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-itemidlist) à copier dans le nouvel `COleVariant` objet.

### <a name="remarks"></a>Notes

Tous ces constructeurs créent des `COleVariant` objets initialisés à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit.

- **COleVariant ()** Crée un objet `COleVariant` vide, VT_EMPTY.

- **COleVariant (** *varSrc* **)** Copie un objet `VARIANT` ou `COleVariant` existant. Le type variant est conservé.

- **COleVariant (** *pSrc* **)** Copie un objet `VARIANT` ou `COleVariant` existant. Le type variant est conservé.

- **COleVariant (** *lpszSrc* **)** Copie une chaîne dans le nouvel objet, VT_BSTR (UNICODE).

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** Copie une chaîne dans le nouvel objet. Le paramètre *vtSrc* doit être VT_BSTR (Unicode) ou VT_BSTRT (ANSI).

- **COleVariant (** *strSrc* **)** Copie une chaîne dans le nouvel objet, VT_BSTR (UNICODE).

- **COleVariant (** *nSrc* **)** Copie un entier 8 bits dans le nouvel objet, VT_UI1.

- **COleVariant (** *nSrc* **,** *vtSrc* **)** Copie un entier 16 bits (ou une valeur booléenne) dans le nouvel objet. Le paramètre *vtSrc* doit être VT_I2 ou VT_BOOL.

- **COleVariant (** *lSrc* **,** *vtSrc* **)** Copie un entier 32 bits (ou une valeur SCODE) dans le nouvel objet. Le paramètre *vtSrc* doit être VT_I4, VT_ERROR ou VT_BOOL.

- **COleVariant (** *curSrc* **)** Copie une `COleCurrency` valeur dans le nouvel objet, VT_CY.

- **COleVariant (** *fltSrc* **)** Copie une valeur à virgule flottante 32 bits dans le nouvel objet, VT_R4.

- **COleVariant (** *dblSrc* **)** Copie une valeur à virgule flottante 64 bits dans le nouvel objet, VT_R8.

- **COleVariant (** *timeSrc* **)** Copie une `COleDateTime` valeur dans le nouvel objet, VT_DATE.

- **COleVariant (** *arrSrc* **)** Copie un `CByteArray` objet dans le nouvel objet, VT_EMPTY.

- **COleVariant (** *lbSrc* **)** Copie un `CLongBinary` objet dans le nouvel objet, VT_EMPTY.

Pour plus d’informations sur SCODE, consultez [structure of com Error Codes](/windows/desktop/com/structure-of-com-error-codes) in the SDK Windows.

##  <a name="changetype"></a>  COleVariant::ChangeType

Convertit le type de valeur variant dans `COleVariant` cet objet.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Paramètres

*vartype*<br/>
VarType de cet `COleVariant` objet.

*pSrc*<br/>
Pointeur vers l’objet [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) à convertir. Si cette valeur est null, cet `COleVariant` objet est utilisé comme source pour la conversion.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez les entrées [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum)et [VariantChangeType](/windows/desktop/api/oleauto/nf-oleauto-variantchangetype) dans la SDK Windows.

##  <a name="clear"></a>  COleVariant::Clear

Efface `VARIANT`.

```
void Clear();
```

### <a name="remarks"></a>Notes

Cela définit le VARTYPE de cet objet avec la valeur VT_EMPTY. Le `COleVariant` destructeur appelle cette fonction.

Pour plus d’informations, consultez `VARIANT`les entrées, VarType `VariantClear` et dans le SDK Windows.

##  <a name="detach"></a>  COleVariant::Detach

Détache l’objet [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) sous-jacent de `COleVariant` cet objet.

```
VARIANT Detach();
```

### <a name="remarks"></a>Notes

Cette fonction définit le VarType de cet `COleVariant` objet avec la valeur VT_EMPTY.

> [!NOTE]
>  Après l' `Detach`appel de, l’appelant est responsable de l' `VariantClear` appel sur la `VARIANT` structure résultante.

Pour plus d’informations, consultez les entrées [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum)et [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) dans la SDK Windows.

##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray

Récupère un tableau d’octets d’un tableau variant existant

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Paramètres

*bytes*<br/>
Référence à un objet [CByteArray](../../mfc/reference/cbytearray-class.md) existant.

##  <a name="operator_lpcvariant"></a>COleVariant:: Operator LPCVARIANT

Cet opérateur de cast retourne `VARIANT` une structure dont la valeur est copiée à partir de cet `COleVariant` objet.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Notes

##  <a name="operator_lpvariant"></a>COleVariant:: Operator LPVARIANT

Appelez cet opérateur de cast pour accéder à `VARIANT` la structure sous `COleVariant` -jacente de cet objet.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Notes

> [!CAUTION]
> La modification de la valeur `VARIANT` de la structure accessible par le pointeur retourné par cette fonction modifie la valeur de `COleVariant` cet objet.

##  <a name="operator_eq"></a>  COleVariant::operator =

Ces opérateurs d’assignation surchargés copient la valeur source `COleVariant` dans cet objet.

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>Notes

Voici une brève description de chaque opérateur:

- **opérateur = (** *varSrc* **)** Copie une variante ou `COleVariant` un objet existant dans cet objet.

- **opérateur = (** *pSrc* **)** Copie l’objet VARIANT auquel accède *pSrc* dans cet objet.

- **opérateur = (** *lpszSrc* **)** Copie une chaîne se terminant par un caractère NULL dans cet objet et définit le VARTYPE sur VT_BSTR.

- **opérateur = (** *strSrc* **)** Copie un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) dans cet objet et définit le VarType sur VT_BSTR.

- **opérateur = (** *nSrc* **)** Copie une valeur entière de 8 ou 16 bits dans cet objet. Si *nSrc* est une valeur de 8 bits, le VarType de ce est défini sur VT_UI1. Si *nSrc* est une valeur de 16 bits et que le VarType de ce est VT_BOOL, il est conservé. dans le cas contraire, elle est définie sur VT_I2.

- **opérateur = (** *lSrc* **)** Copie une valeur entière 32 bits dans cet objet. Si le VARTYPE de ce est VT_ERROR, il est conservé; dans le cas contraire, elle est définie sur VT_I4.

- **opérateur = (** *curSrc* **)** Copie un objet [COleCurrency](../../mfc/reference/colecurrency-class.md) dans cet objet et définit le VarType sur VT_CY.

- **opérateur = (** *fltSrc* **)** Copie une valeur à virgule flottante 32 bits dans cet objet et définit le VARTYPE sur VT_R4.

- **opérateur = (** *dblSrc* **)** Copie une valeur à virgule flottante 64 bits dans cet objet et définit le VARTYPE sur VT_R8.

- **opérateur = (** *dateSrc* **)** Copie un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) dans cet objet et définit le VarType sur VT_DATE.

- **opérateur = (** *arrSrc* **)** Copie un objet [CByteArray](../../mfc/reference/cbytearray-class.md) dans cet `COleVariant` objet.

- **opérateur = (** *lbSrc* **)** Copie un objet [CLongBinary](../../mfc/reference/clongbinary-class.md) dans cet `COleVariant` objet.

Pour plus d’informations, consultez les entrées [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) et [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) dans le SDK Windows.

##  <a name="operator_eq_eq"></a>  COleVariant::operator ==

Cet opérateur compare deux valeurs de type Variant et retourne une valeur différente de zéro si elles sont égales; Sinon, 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>COleVariant:: Operator &lt;, &lt;&gt;&gt;

Renvoie une `COleVariant` valeur à `CArchive` ou `CdumpContext` et les entrées `COleVariant` d’un `CArchive`objet à partir de.

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>Notes

L' `COleVariant` opérateur d' **\<insertion(\<** ) prend en charge le vidage et le stockage des diagnostics dans une archive. L’opérateur d' **>>** extraction () prend en charge le chargement à partir d’une archive.

##  <a name="setstring"></a>  COleVariant::SetString

Définit la chaîne sur un type particulier.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Paramètres

*lpszSrc*<br/>
Chaîne terminée par le caractère null à copier dans le nouvel `COleVariant` objet.

*VtSrc*<br/>
VarType du nouvel `COleVariant` objet.

### <a name="remarks"></a>Notes

Le paramètre *vtSrc* doit être VT_BSTR (Unicode) ou VT_BSTRT (ANSI). `SetString`est généralement utilisé pour définir des chaînes ANSI, car la valeur par défaut pour le constructeur [COleVariant:: COleVariant](#colevariant) avec un paramètre de pointeur de chaîne ou de chaîne et sans VarType est Unicode.

Un jeu d’enregistrements DAO dans une génération non UNICODE s’attend à ce que les chaînes soient au format ANSI. Ainsi, pour les fonctions DAO qui `COleVariant` utilisent des objets, si vous n’êtes pas en train de créer un jeu d’enregistrements Unicode, vous devez utiliser la forme **COleVariant:: COleVariant (** *lpszSrc* **,** *vtSrc* **)** du constructeur avec *vtSrc* défini sur VT. _BSTRT (ANSI) ou utilisez `SetString` avec *vtSrc* défini sur VT_BSTRT pour créer des chaînes ANSI. Par exemple, les `CDaoRecordset` fonctions [CDaoRecordset:: Seek](../../mfc/reference/cdaorecordset-class.md#seek) et [CDaoRecordset:: SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) utilisent `COleVariant` des objets en tant que paramètres. Ces objets doivent être ANSI si le jeu d’enregistrements DAO n’est pas UNICODE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
