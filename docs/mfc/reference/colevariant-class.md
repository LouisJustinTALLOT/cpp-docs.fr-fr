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
ms.openlocfilehash: 7d8abea39a9baa3f447ca0d5f3ab1183367d531f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753711"
---
# <a name="colevariant-class"></a>COleVariant, classe

Encapsule le type de données [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) .

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
|[COleVariant::Attach](#attach)|Attache un VARIANT `COleVariant`à un .|
|[COleVariant::ChangeType](#changetype)|Modifie le type `COleVariant` de variante de cet objet.|
|[COleVariant::Clair](#clear)|Efface cet objet `COleVariant`.|
|[COleVariant::Detach](#detach)|Détache un VARIANT d’un `COleVariant` et renvoie le VARIANT.|
|[COleVariant::GetByteArrayDeVariantArray](#getbytearrayfromvariantarray)|Récupère un tableau d’en-avant d’un tableau de variantes existant.|
|[COleVariant::SetString](#setstring)|Définit la chaîne à un type particulier, généralement ANSI.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleVariant::opérateur LPCVARIANT](#operator_lpcvariant)|Convertit `COleVariant` une valeur `LPCVARIANT`en .|
|[COleVariant::opérateur LPVARIANT](#operator_lpvariant)|Convertit `COleVariant` un objet `LPVARIANT`en .|
|[COleVariant::opérateur](#operator_eq)|Copie `COleVariant` d’une valeur.|
|[COleVariant::opérateur](#operator_eq_eq)|Compare deux `COleVariant` valeurs.|
|[COleVariant::opérateur &lt; &lt;,&gt;&gt;](#operator_lt_lt__gt_gt)|Sortie `COleVariant` d’une `CArchive` `CDumpContext` valeur ou `COleVariant` d’entrées d’un objet à partir de `CArchive`.|

## <a name="remarks"></a>Notes

Ce type de données est utilisé dans l’automatisation OLE. Plus précisément, la structure [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams) contient un pointeur sur un éventail de structures VARIANT. Une `DISPPARAMS` structure est utilisée pour passer les paramètres à [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Cette classe est `VARIANT` dérivée de la structure. Cela signifie que vous `COleVariant` pouvez passer un `VARIANT` paramètre qui nécessite `VARIANT` un et que `COleVariant`les membres des données de la structure sont des membres de données accessibles de .

Les deux classes MFC connexes [COleCurrency](../../mfc/reference/colecurrency-class.md) et [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsulent les types de données variantes CURRENCY ( `VT_CY`) et DATE ( `VT_DATE`). La `COleVariant` classe est largement utilisée dans les classes DAO; voir ces classes pour l’utilisation typique de cette classe, par exemple [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Pour plus d’informations, voir le [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1), [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams), et [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) entrées dans le SDK Windows.

Pour plus d’informations sur la `COleVariant` classe et son utilisation dans l’automatisation OLE, voir "Passing Parameters in OLE Automation" dans l’article [Automation](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant::Attach

Appelez cette fonction pour attacher l’objet [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) donné à l’objet actuel. `COleVariant`

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Un `VARIANT` objet existant à attacher `COleVariant` à l’objet actuel.

### <a name="remarks"></a>Notes

Cette fonction définit le VARTYPE de *varSrc* à VT_EMPTY.

Pour plus d’informations, voir les entrées [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) et [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) dans le SDK Windows.

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant::COleVariant

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
Un `COleVariant` objet `VARIANT` existant ou à copier `COleVariant` dans le nouvel objet.

*pSrc (en)*<br/>
Un pointeur `VARIANT` à un objet qui `COleVariant` sera copié dans le nouvel objet.

*lpszSrc (en)*<br/>
Une corde à résilier nulle `COleVariant` à copier dans le nouvel objet.

*vtSrc*<br/>
Le `VARTYPE` pour `COleVariant` le nouvel objet.

*strSrc (strSrc)*<br/>
Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) à copier `COleVariant` dans le nouvel objet.

*nSrc*, *lSrc* Une valeur numérique à `COleVariant` copier dans le nouvel objet.

*vtSrc*<br/>
Le `VARTYPE` pour `COleVariant` le nouvel objet.

*curSrc*<br/>
Un objet [COleCurrency](../../mfc/reference/colecurrency-class.md) à copier `COleVariant` dans le nouvel objet.

*fltSrc*, *dblSrc*<br/>
Valeur numérique à copier dans le nouvel objet `COleVariant`.

*timeSrc*<br/>
Un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) à copier `COleVariant` dans le nouvel objet.

*arrSrc*<br/>
Un objet [CByteArray](../../mfc/reference/cbytearray-class.md) à copier `COleVariant` dans le nouvel objet.

*lbSrc*<br/>
Un objet [CLongBinary](../../mfc/reference/clongbinary-class.md) à copier `COleVariant` dans le nouvel objet.

*pidl pidl*<br/>
Un pointeur vers une structure [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) `COleVariant` à copier dans le nouvel objet.

### <a name="remarks"></a>Notes

Tous ces constructeurs `COleVariant` créent de nouveaux objets paraspécisés à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit.

- **COleVariant( )** Crée un `COleVariant` objet vide, VT_EMPTY.

- **COleVariant (** *varSrc* **)** Copie d’un objet existant `VARIANT` ou `COleVariant` existant. Le type variant est conservé.

- **COleVariant (** *pSrc* **)** Copie d’un objet existant `VARIANT` ou `COleVariant` existant. Le type variant est conservé.

- **COleVariant(** *lpszSrc* **)** Copie d’une chaîne dans le nouvel objet, VT_BSTR (UNICODE).

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** Copie d’une chaîne dans le nouvel objet. Le paramètre *vtSrc* doit être VT_BSTR (UNICODE) ou VT_BSTRT (ANSI).

- **COleVariant (** *strSrc* **)** Copie d’une chaîne dans le nouvel objet, VT_BSTR (UNICODE).

- **COleVariant(** *nSrc* **)** Copie d’un intégré 8 bits dans le nouvel objet, VT_UI1.

- **COleVariant(** *nSrc* **,** *vtSrc* **)** Copie d’un intégrisé 16 bits (ou valeur Boolean) dans le nouvel objet. Le paramètre *vtSrc* doit être VT_I2 ou VT_BOOL.

- **COleVariant(** *lSrc* **,** *vtSrc* **)** Copie d’un intégré 32 bits (ou valeur SCODE) dans le nouvel objet. Le paramètre *vtSrc* doit être VT_I4, VT_ERROR ou VT_BOOL.

- **COleVariant (** *curSrc* **)** Copie `COleCurrency` d’une valeur dans le nouvel objet, VT_CY.

- **COleVariant(** *fltSrc* **)** Copie d’une valeur de 32 bits en point flottant dans le nouvel objet, VT_R4.

- **COleVariant(** *dblSrc* **)** Copie d’une valeur flottante de 64 bits dans le nouvel objet, VT_R8.

- **COleVariant(** *timeSrc* **)** Copie `COleDateTime` d’une valeur dans le nouvel objet, VT_DATE.

- **COleVariant(** *arrSrc* **)** Copie `CByteArray` d’un objet dans le nouvel objet, VT_EMPTY.

- **COleVariant(** *lbSrc* **)** Copie `CLongBinary` d’un objet dans le nouvel objet, VT_EMPTY.

Pour plus d’informations sur SCODE, voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) in the Windows SDK.

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant::ChangeType

Convertit le type de `COleVariant` valeur de variante dans cet objet.

```cpp
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Paramètres

*vartype*<br/>
Le VARTYPE `COleVariant` pour cet objet.

*pSrc (en)*<br/>
Un pointeur vers l’objet [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) à convertir. Si cette valeur est `COleVariant` NULL, cet objet est utilisé comme source de conversion.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir les entrées [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)et [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) dans le Windows SDK.

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant::Clair

Efface la `VARIANT`.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Cela définit le VARTYPE pour cet objet à VT_EMPTY. Le `COleVariant` destructeur appelle cette fonction.

Pour plus d’informations, voir `VARIANT`le `VariantClear` , VARTYPE, et les entrées dans le SDK Windows.

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant::Detach

Détache l’objet [variant](/windows/win32/api/oaidl/ns-oaidl-variant) sous-jacent de cet `COleVariant` objet.

```
VARIANT Detach();
```

### <a name="remarks"></a>Notes

Cette fonction définit le VARTYPE pour cet `COleVariant` objet à VT_EMPTY.

> [!NOTE]
> Après `Detach`avoir appelé, il est de `VariantClear` la responsabilité `VARIANT` de l’appelant de faire appel à la structure résultante.

Pour plus d’informations, voir les entrées [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)et [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) dans le Windows SDK.

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayDeVariantArray

Récupère un tableau d’en-extraits à partir d’un tableau de variantes existant

```cpp
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Paramètres

*Octets*<br/>
Une référence à un objet [CByteArray](../../mfc/reference/cbytearray-class.md) existant.

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant::opérateur LPCVARIANT

Cet opérateur de `VARIANT` coulée renvoie une `COleVariant` structure dont la valeur est copiée à partir de cet objet.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Notes

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant::opérateur LPVARIANT

Appelez cet opérateur de `VARIANT` coulée `COleVariant` pour accéder à la structure sous-jacente de cet objet.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Notes

> [!CAUTION]
> Changer la valeur `VARIANT` de la structure accessible par le pointeur `COleVariant` retourné par cette fonction modifiera la valeur de cet objet.

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant::opérateur

Ces opérateurs d’affectation surchargés copient la valeur source dans cet `COleVariant` objet.

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

Une brève description de chaque opérateur suit :

- **opérateur** *(varSrc)* **)** Copie d’un `COleVariant` VARIANT ou d’un objet existant dans cet objet.

- **opérateur** *(pSrc)* **)** Copie de l’objet VARIANT accessible par *pSrc* dans cet objet.

- **opérateur** *(lpszSrc)* **)** Copie d’une corde à l’emploi dans cet objet et définit le VARTYPE à VT_BSTR.

- **opérateur** *(strSrc)* **)** Copie [d’un objet CString](../../atl-mfc-shared/reference/cstringt-class.md) dans cet objet et définit le VARTYPE à VT_BSTR.

- **opérateur** *(nSrc)* **)** Copie une valeur d’intégration de 8 ou 16 bits dans cet objet. Si *le NSrc* est une valeur 8 bits, le VARTYPE de ce qui est réglé pour VT_UI1. Si *le NSrc* est une valeur 16 bits et que le VARTYPE est VT_BOOL, il est conservé; sinon, il est prêt à VT_I2.

- **opérateur** *(lSrc)* **)** Copie une valeur integer 32 bits dans cet objet. Si le VARTYPE de ce n’est VT_ERROR, il est conservé; sinon, il est prêt à VT_I4.

- **opérateur** *(curSrc)* **)** Copie d’un objet [COleCurrency](../../mfc/reference/colecurrency-class.md) dans cet objet et définit le VARTYPE à VT_CY.

- **opérateur** *(fltSrc)* **)** Copie une valeur de 32 bits en point flottant dans cet objet et définit le VARTYPE à VT_R4.

- **opérateur** *(dblSrc)* **)** Copie une valeur flottante de 64 bits dans cet objet et définit le VARTYPE à VT_R8.

- **opérateur** *(dateSrc* **)** Copie [d’un objet COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) dans cet objet et définit le VARTYPE à VT_DATE.

- **opérateur** *(arrSrc* **)** Copie d’un objet [CByteArray](../../mfc/reference/cbytearray-class.md) dans cet `COleVariant` objet.

- **opérateur** *(lbSrc)* **)** Copie d’un objet [CLongBinary](../../mfc/reference/clongbinary-class.md) dans cet `COleVariant` objet.

Pour plus d’informations, voir les entrées [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) et [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) dans le SDK Windows.

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant::opérateur

Cet opérateur compare deux valeurs de variante et retourne nonzero si elles sont égales; sinon 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant::opérateur &lt; &lt;,&gt;&gt;

Sortie `COleVariant` d’une `CArchive` `CdumpContext` valeur ou `COleVariant` d’entrées d’un objet à partir de `CArchive`.

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

`COleVariant` L’opérateur**\<** d’insertion () prend en charge le dumping diagnostique et le stockage à une archive. L’opérateur**>>** d’extraction () prend en charge le chargement à partir d’une archive.

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant::SetString

Définit la chaîne à un type particulier.

```cpp
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Paramètres

*lpszSrc (en)*<br/>
Une corde à résilier nulle `COleVariant` à copier dans le nouvel objet.

*VtSrc VtSrc*<br/>
Le VARTYPE pour `COleVariant` le nouvel objet.

### <a name="remarks"></a>Notes

Le paramètre *vtSrc* doit être VT_BSTR (UNICODE) ou VT_BSTRT (ANSI). `SetString`est généralement utilisé pour régler les ficelles à ANSI, puisque la valeur par défaut pour le [COleVariant::COleVariant](#colevariant) constructeur avec une chaîne ou un paramètre pointeur de chaîne et aucun VARTYPE est UNICODE.

Un recordet DAO dans une construction non-UNICODE s’attend à ce que les cordes soient ANSI. Ainsi, pour les fonctions `COleVariant` DAO qui utilisent des objets, si vous ne créez pas un jeu d’enregistrement UNICODE, vous devez utiliser le **COleVariant::COleVariant (** *lpszSrc* **,** *vtSrc* **)** forme de constructeur avec *vtSrc* mis à VT_BSTRT (ANSI) ou utiliser `SetString` avec *vtSrc* mis à VT_BSTRT pour faire des cordes ANSI. Par exemple, `CDaoRecordset` les fonctions [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) et [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) utilisent des `COleVariant` objets comme paramètres. Ces objets doivent être ANSI si le recordet DAO n’est pas UNICODE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
