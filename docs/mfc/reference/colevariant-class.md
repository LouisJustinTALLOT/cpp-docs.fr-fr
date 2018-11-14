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
ms.openlocfilehash: b37105cf1afdcf966176a2e2615f9c141022088d
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520516"
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
|[COleVariant::Attach](#attach)|Attache un VARIANT vers un `COleVariant`.|
|[COleVariant::ChangeType](#changetype)|Change le type variant de ce `COleVariant` objet.|
|[COleVariant::Clear](#clear)|Cela efface `COleVariant` objet.|
|[COleVariant::Detach](#detach)|Détache une variante à partir d’un `COleVariant` et retourne la variante.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Récupère un tableau d’octets à partir d’un tableau de variant existant.|
|[COleVariant::SetString](#setstring)|Définit la chaîne à un type particulier, généralement ANSI.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Convertit un `COleVariant` valeur dans un `LPCVARIANT`.|
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Convertit un `COleVariant` de l’objet dans un `LPVARIANT`.|
|[COleVariant::operator =](#operator_eq)|Copie un `COleVariant` valeur.|
|[COleVariant::operator ==](#operator_eq_eq)|Compare deux `COleVariant` valeurs.|
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Sorties un `COleVariant` valeur `CArchive` ou `CDumpContext` et entrées un `COleVariant` à partir de l’objet `CArchive`.|

## <a name="remarks"></a>Notes

Ce type de données est utilisé dans OLE automation. Plus précisément, le [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams) structure contient un pointeur vers un tableau de structures VARIANT. Un `DISPPARAMS` structure est utilisée pour passer des paramètres à [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Cette classe est dérivée de la `VARIANT` structure. Cela signifie que vous pouvez passer un `COleVariant` dans un paramètre qui demande un `VARIANT` et que les membres de données de la `VARIANT` structure sont membres de données accessibles de `COleVariant`.

Les deux associés des classes MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) et [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsuler les types de données variant devise ( `VT_CY`) et la DATE ( `VT_DATE`). Le `COleVariant` classe est largement utilisée dans les classes DAO ; consultez ces classes pour une utilisation typique de cette classe, par exemple [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Pour plus d’informations, consultez le [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [devise](/windows/desktop/api/wtypes/ns-wtypes-tagcy), [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams), et [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) entrées dans le SDK Windows.

Pour plus d’informations sur la `COleVariant` classe et son utilisation dans OLE automation, consultez « En passant les paramètres dans OLE Automation » dans l’article [Automation](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="attach"></a>  COleVariant::Attach

Appelez cette fonction pour attacher la donnée [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) objet actuel `COleVariant` objet.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Un existant `VARIANT` objet à attacher à actuel `COleVariant` objet.

### <a name="remarks"></a>Notes

Cette fonction affecte VARTYPE de *varSrc* avec la valeur VT_EMPTY.

Pour plus d’informations, consultez le [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) et [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) entrées dans le SDK Windows.

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
Un existant `COleVariant` ou `VARIANT` objet doit être copié dans le nouveau `COleVariant` objet.

*pSrc*<br/>
Un pointeur vers un `VARIANT` objet qui sera copié dans le nouveau `COleVariant` objet.

*lpszSrc*<br/>
Une chaîne se terminant par null doit être copié dans le nouveau `COleVariant` objet.

*vtSrc*<br/>
Le `VARTYPE` pour le nouveau `COleVariant` objet.

*strSrc*<br/>
Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet doit être copié dans le nouveau `COleVariant` objet.

*nSrc*, *lSrc* une valeur numérique doit être copié dans le nouveau `COleVariant` objet.

*vtSrc*<br/>
Le `VARTYPE` pour le nouveau `COleVariant` objet.

*curSrc*<br/>
Un [COleCurrency](../../mfc/reference/colecurrency-class.md) objet doit être copié dans le nouveau `COleVariant` objet.

*fltSrc*, *dblSrc*<br/>
Valeur numérique à copier dans le nouvel objet `COleVariant`.

*timeSrc*<br/>
Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet doit être copié dans le nouveau `COleVariant` objet.

*arrSrc*<br/>
Un [CByteArray](../../mfc/reference/cbytearray-class.md) objet doit être copié dans le nouveau `COleVariant` objet.

*lbSrc*<br/>
Un [CLongBinary](../../mfc/reference/clongbinary-class.md) objet doit être copié dans le nouveau `COleVariant` objet.

*PIDL*<br/>
Un pointeur vers un [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-_itemidlist) structure doit être copié dans le nouveau `COleVariant` objet.

### <a name="remarks"></a>Notes

Créent tous ces constructeurs `COleVariant` objets initialisés à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit.

- **() COleVariant** crée vide `COleVariant` objet, VT_EMPTY.

- **COleVariant (** *varSrc* **)** copie existante `VARIANT` ou `COleVariant` objet. Le type variant est conservé.

- **COleVariant (** *pSrc* **)** copie existante `VARIANT` ou `COleVariant` objet. Le type variant est conservé.

- **COleVariant (** *lpszSrc* **)** copie une chaîne dans le nouvel objet, VT_BSTR (UNICODE).

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** copie une chaîne dans le nouvel objet. Le paramètre *vtSrc* doit être VT_BSTR (UNICODE) ou VT_BSTRT (ANSI).

- **COleVariant (** *strSrc* **)** copie une chaîne dans le nouvel objet, VT_BSTR (UNICODE).

- **COleVariant (** *nSrc* **)** copie d’un entier 8 bits dans le nouvel objet, VT_UI1.

- **COleVariant (** *nSrc* **,** *vtSrc* **)** copie d’un entier 16 bits (ou une valeur booléenne) dans le nouvel objet. Le paramètre *vtSrc* doit être VT_I2 ou VT_BOOL.

- **COleVariant (** *lSrc* **,** *vtSrc* **)** copie d’un entier 32 bits (ou valeur SCODE) dans le nouvel objet. Le paramètre *vtSrc* doit être VT_I4, VT_ERROR ou VT_BOOL.

- **COleVariant (** *curSrc* **)** Copies un `COleCurrency` valeur dans le nouvel objet, VT_CY.

- **COleVariant (** *fltSrc* **)** copie une valeur à virgule flottante 32 bits dans le nouvel objet, VT_R4.

- **COleVariant (** *dblSrc* **)** copie une valeur à virgule flottante 64 bits dans le nouvel objet, VT_R8.

- **COleVariant (** *timeSrc* **)** Copies un `COleDateTime` valeur dans le nouvel objet, VT_DATE.

- **COleVariant (** *arrSrc* **)** Copies un `CByteArray` objet dans le nouvel objet, VT_EMPTY.

- **COleVariant (** *lbSrc* **)** Copies un `CLongBinary` objet dans le nouvel objet, VT_EMPTY.

Pour plus d’informations sur SCODE, consultez [Structure of COM Error Codes](/windows/desktop/com/structure-of-com-error-codes) dans le SDK Windows.

##  <a name="changetype"></a>  COleVariant::ChangeType

Convertit le type de valeur de type variant dans ce `COleVariant` objet.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Paramètres

*VarType*<br/>
VARTYPE pour ce `COleVariant` objet.

*pSrc*<br/>
Un pointeur vers le [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) objet à convertir. Si cette valeur est NULL, cela `COleVariant` objet est utilisé comme source pour la conversion.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum), et [VariantChangeType](/windows/desktop/api/oleauto/nf-oleauto-variantchangetype) entrées dans le SDK Windows.

##  <a name="clear"></a>  COleVariant::Clear

Efface le `VARIANT`.

```
void Clear();
```

### <a name="remarks"></a>Notes

Cela définit le VARTYPE pour cet objet avec la valeur VT_EMPTY. Le `COleVariant` destructeur appelle cette fonction.

Pour plus d’informations, consultez le `VARIANT`, VARTYPE, et `VariantClear` entrées dans le SDK Windows.

##  <a name="detach"></a>  COleVariant::Detach

Détache sous-jacent [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) objet à partir de ce `COleVariant` objet.

```
VARIANT Detach();
```

### <a name="remarks"></a>Notes

Cette fonction définit VARTYPE pour cet `COleVariant` objet avec la valeur VT_EMPTY.

> [!NOTE]
>  Après avoir appelé `Detach`, il est responsable de l’appelant d’appeler `VariantClear` sur résultant `VARIANT` structure.

Pour plus d’informations, consultez le [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum), et [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) entrées dans le SDK Windows.

##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray

Récupère un tableau d’octets à partir d’un tableau de variant existant

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Paramètres

*Octets*<br/>
Une référence à un existant [CByteArray](../../mfc/reference/cbytearray-class.md) objet.

##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT

Cet opérateur de conversion retourne un `VARIANT` structure dont la valeur est copiée à partir de ce `COleVariant` objet.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Notes

##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT

Appeler cet opérateur de cast pour accéder à sous-jacent `VARIANT` structure pour ce `COleVariant` objet.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Notes

> [!CAUTION]
> Modification de la valeur dans le `VARIANT` structure accédé par le pointeur retourné par cette fonction modifie la valeur de ce `COleVariant` objet.

##  <a name="operator_eq"></a>  COleVariant::operator =

Ces opérateurs d’assignation surchargés copier la valeur source dans cette `COleVariant` objet.

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

Une brève description de chaque opérateur suit :

- **opérateur = (** *varSrc* **)** copie une variante existante ou `COleVariant` objet dans cet objet.

- **opérateur = (** *pSrc* **)** copie l’objet de type VARIANT accédé par *pSrc* dans cet objet.

- **opérateur = (** *lpszSrc* **)** copie une chaîne se terminant par null dans cet objet et affecte le VARTYPE VT_BSTR.

- **opérateur = (** *strSrc* **)** Copies un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet dans cet objet et les jeux VARTYPE sur VT_BSTR.

- **opérateur = (** *nSrc* **)** copie une valeur entière de 8 ou 16 bits dans cet objet. Si *nSrc* est une valeur 8 bits, VARTYPE de cela est défini sur VT_UI1. Si *nSrc* est une valeur 16 bits et VARTYPE de ceci est VT_BOOL, il est conservé ; sinon, elle est définie sur VT_I2.

- **opérateur = (** *lSrc* **)** copie une valeur d’entier 32 bits dans cet objet. Si le VARTYPE de ce est VT_ERROR, il est conservé ; Sinon, il est défini sur VT_I4.

- **opérateur = (** *curSrc* **)** Copies un [COleCurrency](../../mfc/reference/colecurrency-class.md) objet dans cet objet et les jeux VARTYPE à VT_CY.

- **opérateur = (** *fltSrc* **)** copie une valeur à virgule flottante 32 bits dans cet objet et affecte le VARTYPE VT_R4.

- **opérateur = (** *dblSrc* **)** copie une valeur à virgule flottante 64 bits dans cet objet et affecte le VARTYPE VT_R8.

- **opérateur = (** *dateSrc* **)** Copies un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet dans cet objet et les jeux VARTYPE à VT_DATE.

- **opérateur = (** *arrSrc* **)** Copies un [CByteArray](../../mfc/reference/cbytearray-class.md) objet dans ce `COleVariant` objet.

- **opérateur = (** *lbSrc* **)** Copies un [CLongBinary](../../mfc/reference/clongbinary-class.md) objet dans ce `COleVariant` objet.

Pour plus d’informations, consultez le [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) et [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) entrées dans le SDK Windows.

##  <a name="operator_eq_eq"></a>  COleVariant::operator ==

Cet opérateur compare deux valeurs de type variants et retourne zéro si elles sont égales ; sinon 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;

Sorties un `COleVariant` valeur `CArchive` ou `CdumpContext` et entrées un `COleVariant` à partir de l’objet `CArchive`.

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

Le `COleVariant` insertion (**\<\<**) prend en charge l’opérateur vidage de diagnostic et le stockage dans une archive. L’extraction (**>>**) opérateur prend en charge le chargement à partir d’une archive.

##  <a name="setstring"></a>  COleVariant::SetString

Définit la chaîne à un type particulier.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Paramètres

*lpszSrc*<br/>
Une chaîne se terminant par null doit être copié dans le nouveau `COleVariant` objet.

*vtSrc*<br/>
VARTYPE pour le nouveau `COleVariant` objet.

### <a name="remarks"></a>Notes

Le paramètre *vtSrc* doit être VT_BSTR (UNICODE) ou VT_BSTRT (ANSI). `SetString` est généralement utilisé pour définir des chaînes au format ANSI, depuis la valeur par défaut pour le [COleVariant::COleVariant](#colevariant) constructeur avec une chaîne ou le paramètre de pointeur de chaîne et aucun VARTYPE est UNICODE.

Un objet DAO recordset dans une build non-UNICODE attend des chaînes sont ANSI. Par conséquent, pour DAO les fonctions qui utilisent `COleVariant` objets, si vous ne créez pas un jeu d’enregistrements UNICODE, vous devez utiliser le **COleVariant::COleVariant (** *lpszSrc* **,** *vtSrc* **)** formulaire du constructeur avec *vtSrc* définir VT_BSTRT (ANSI) ou utiliser `SetString` avec *vtSrc* valeur VT _BSTRT pour rendre les chaînes ANSI. Par exemple, le `CDaoRecordset` fonctions [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) et [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) utiliser `COleVariant` objets en tant que paramètres. Ces objets doivent être ANSI si le jeu d’enregistrements DAO n’est pas UNICODE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
