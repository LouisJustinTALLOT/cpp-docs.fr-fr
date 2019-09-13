---
title: CComVariant, classe
ms.date: 11/04/2016
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: b4c157435aaffab5f1315fd4636f55f9d4e0d5b4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496859"
---
# <a name="ccomvariant-class"></a>CComVariant, classe

Cette classe encapsule le type VARIANT, en fournissant un membre indiquant le type de données stockées.

## <a name="syntax"></a>Syntaxe

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|Constructeur.|
|[CComVariant :: ~ CComVariant](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComVariant::Attach](#attach)|Joint un variant à l' `CComVariant` objet.|
|[CComVariant::ChangeType](#changetype)|Convertit `CComVariant` l’objet en un nouveau type.|
|[CComVariant::Clear](#clear)|Efface l' `CComVariant` objet.|
|[CComVariant::Copy](#copy)|Copie un variant vers l' `CComVariant` objet.|
|[CComVariant::CopyTo](#copyto)|Copie le contenu de l' `CComVariant` objet.|
|[CComVariant::Detach](#detach)|Détache la variante sous-jacente de `CComVariant` l’objet.|
|[CComVariant::GetSize](#getsize)|Retourne la taille en nombre d’octets du contenu de l' `CComVariant` objet.|
|[CComVariant::ReadFromStream](#readfromstream)|Charge un VARIANT à partir d’un flux.|
|[CComVariant::SetByRef](#setbyref)|Initialise l' `CComVariant` objet et définit le `vt` membre à VT_BYREF.|
|[CComVariant::WriteToStream](#writetostream)|Enregistre la variante sous-jacente dans un flux.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|||
|-|-|
|[CComVariant :: Operator <](#operator_lt)|Indique si l' `CComVariant` objet est inférieur à la variante spécifiée.|
|[CComVariant :: operator >](#operator_gt)|Indique si l' `CComVariant` objet est supérieur à la variante spécifiée.|
|[opérateur ! =](#operator_neq)|Indique si l' `CComVariant` objet n’est pas égal au variant spécifié.|
|[operator =](#operator_eq)|Assigne une valeur à l' `CComVariant` objet.|
|[operator ==](#operator_eq_eq)|Indique si l' `CComVariant` objet est égal à la variante spécifiée.|

## <a name="remarks"></a>Notes

`CComVariant`encapsule le type VARIANT et VARIANTARG, qui se compose d’une Union et d’un membre indiquant le type des données stockées dans l’Union. Les VARIANTEs sont généralement utilisées dans Automation.

`CComVariant`dérive du type VARIANT afin qu’il puisse être utilisé partout où un VARIANT peut être utilisé. Vous pouvez, par exemple, utiliser la macro V_VT pour extraire le type d’un `CComVariant` ou vous pouvez accéder au `vt` membre directement comme vous le feriez avec un variant.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcomcli. h

##  <a name="attach"></a>  CComVariant::Attach

Efface en toute sécurité le contenu actuel de `CComVariant` l’objet, copie le contenu de *pSrc* dans cet objet, puis définit le type variant de *pSrc* sur VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Paramètres

*pSrc*<br/>
dans Pointe vers le [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) à attacher à l’objet.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

La propriété des données détenues par *pSrc* est transférée à l' `CComVariant` objet.

##  <a name="ccomvariant"></a>  CComVariant::CComVariant

Chaque constructeur gère l’initialisation sécurisée de l' `CComVariant` objet en appelant la `VariantInit` fonction Win32 ou en définissant la valeur et le type de l’objet en fonction des paramètres transmis.

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
dans VARIANT ou utilisé pour initialiser l' `CComVariant` objet. `CComVariant` Le contenu du variant source est copié vers la destination sans conversion.

*lpszSrc*<br/>
dans Chaîne de caractères utilisée pour initialiser l' `CComVariant` objet. Vous pouvez passer une chaîne de caractères de largeur nulle (Unicode) à la version LPCOLESTR du constructeur ou une chaîne ANSI à la version LPCSTR. Dans les deux cas, la chaîne est convertie en un `SysAllocString`BSTR Unicode alloué à l’aide de. Le type de l' `CComVariant` objet sera VT_BSTR.

*bSrc*<br/>
dans **Bool** utilisé pour initialiser l' `CComVariant` objet. L’argument **bool** est converti en VARIANT_BOOL avant d’être stocké. Le type de l' `CComVariant` objet sera VT_BOOL.

*nSrc*<br/>
dans Int **,** **Byte**, **short**, **long**, LongLong, ULONGLONG, **unsigned short**, **unsigned long**ou **unsigned int** utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 ou VT_UI4, respectivement.

*vtSrc*<br/>
dans Type de la variante. Lorsque le premier paramètre est **int**, les types valides sont VT_I4 et VT_INT. Lorsque le premier paramètre est **long**, les types valides sont VT_I4 et VT_ERROR. Lorsque le premier paramètre est **double**, les types valides sont VT_R8 et VT_DATE. Lorsque le premier paramètre est **unsigned int**, les types valides sont VT_UI4 et VT_UINT.

*fltSrc*<br/>
dans **Float** utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_R4.

*dblSrc*<br/>
dans **Double** utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_R8.

*cySrc*<br/>
dans Utilisé pour initialiser l' `CComVariant` objet. `CY` Le type de l' `CComVariant` objet sera VT_CY.

*pSrc*<br/>
dans Pointeur `IDispatch` ou `IUnknown` utilisé pour initialiser l' `CComVariant` objet. `AddRef`est appelé sur le pointeur d’interface. Le type de l' `CComVariant` objet sera VT_DISPATCH ou VT_UNKNOWN, respectivement.

Ou le pointeur SAFERRAY utilisé pour initialiser l' `CComVariant` objet. Une copie du SAFEARRAY est stockée dans l' `CComVariant` objet. Le type de l' `CComVariant` objet est une combinaison du type d’origine des SAFEARRAY et VT_ARRAY.

*cSrc*<br/>
dans **Caractère** utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I1.

*bstrSrc*<br/>
dans BSTR utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_BSTR.

### <a name="remarks"></a>Notes

Le destructeur gère le nettoyage en appelant [CComVariant :: Clear](#clear).

##  <a name="dtor"></a>  CComVariant::~CComVariant

Destructeur.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Notes

Cette méthode gère le nettoyage en appelant [CComVariant :: Clear](#clear).

##  <a name="changetype"></a>  CComVariant::ChangeType

Convertit `CComVariant` l’objet en un nouveau type.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Paramètres

*vtNew*<br/>
dans Nouveau type de l' `CComVariant` objet.

*pSrc*<br/>
dans Pointeur vers le VARIANT dont la valeur sera convertie vers le nouveau type. La valeur par défaut est null, ce `CComVariant` qui signifie que l’objet sera converti sur place.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si vous transmettez une valeurpour pSrc `ChangeType` , utilise cette variante comme source pour la conversion. Dans le cas `CComVariant` contraire, l’objet sera la source.

##  <a name="clear"></a>  CComVariant::Clear

Efface l' `CComVariant` objet en appelant la `VariantClear` fonction Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le destructeur appelle `Clear`automatiquement.

##  <a name="copy"></a>  CComVariant::Copy

Libère l' `CComVariant` objet, puis lui assigne une copie de la variante spécifiée.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Paramètres

*pSrc*<br/>
dans Pointeur vers le [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) à copier.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="copyto"></a>  CComVariant::CopyTo

Copie le contenu de l' `CComVariant` objet.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Paramètres

*pstrDest*<br/>
Pointe vers un BSTR qui recevra une copie du contenu de l' `CComVariant` objet.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L' `CComVariant` objet doit être de type VT_BSTR.

##  <a name="detach"></a>  CComVariant::Detach

Détache la variante sous-jacente de `CComVariant` l’objet et définit le type de l’objet avec la valeur VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
à Retourne la valeur de type VARIANT sous-jacent de l’objet.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Notez que le contenu de la variante référencée par *pDEST* sera automatiquement effacé avant d’être affecté à la valeur et au type de `CComVariant` l’objet appelant.

##  <a name="getsize"></a>  CComVariant::GetSize

Pour les VARIANTEs de taille fixe simples, cette méthode retourne le **sizeof** du type de données sous-jacent plus **sizeof (VarType)** .

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Taille en octets du contenu actuel de l' `CComVariant` objet.

### <a name="remarks"></a>Notes

Si le variant contient un pointeur d’interface `GetSize` , interroge `IPersistStream` pour `IPersistStreamInit`ou. En cas de réussite, la valeur de retour est l’ordre de 32 bits de poids faible `GetSizeMax` de la valeur retournée par plus le **sizeof** a CLSID et **sizeof (VarType)** . Si le pointeur d’interface est null `GetSize` , retourne le **sizeof** d’un CLSID plus **sizeof (VarType)** . Si la taille totale est supérieure à ULONG_MAX, `GetSize` retourne **sizeof (VarType)** qui indique une erreur.

Dans tous les autres cas, une variante temporaire de type VT_BSTR est convertie à partir de la variante actuelle. La longueur de ce BSTR est calculée en fonction de la taille de la chaîne plus la longueur de la chaîne elle-même, plus la taille du caractère null plus **sizeof (VarType)** . Si la variante ne peut pas être forcée à un variant de type `GetSize` VT_BSTR, retourne **sizeof (VarType)** .

La taille retournée par cette méthode correspond au nombre d’octets utilisés par [CComVariant :: WriteToStream](#writetostream) en cas de réussite.

##  <a name="operator_eq"></a>  CComVariant::operator =

Assigne une valeur et un type correspondant à `CComVariant` l’objet.

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
[in] `CComVariant` ou [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) à assigner à l’object `CComVariant`. Le contenu du variant source est copié vers la destination sans conversion.

*bstrSrc*<br/>
dans BSTR à assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_BSTR.

*lpszSrc*<br/>
dans Chaîne de caractères à assigner à `CComVariant` l’objet. Vous pouvez transmettre une chaîne de caractères de largeur nulle (Unicode) à la version LPCOLESTR de l’opérateur ou une chaîne ANSI à la version LPCSTR. Dans les deux cas, la chaîne est convertie en un BSTR `SysAllocString`Unicode alloué à l’aide de. Le type de l' `CComVariant` objet sera VT_BSTR.

*bSrc*<br/>
dans Valeur **booléenne** à assigner à `CComVariant` l’objet. L’argument **bool** est converti en VARIANT_BOOL avant d’être stocké. Le type de l' `CComVariant` objet sera VT_BOOL.

*nSrc*<br/>
dans **Int**, Byte, **short**, **long**, LongLong, ULONGLONG, **unsigned short**, **unsigned long**ou **unsigned int** à assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 ou VT_UI4, respectivement.

*fltSrc*<br/>
dans Valeur **float** à assigner à `CComVariant` l’objet. Le type de l' `CComVariant` objet sera VT_R4.

*dblSrc*<br/>
dans **Double** à assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_R8.

*cySrc*<br/>
dans À assigner à l' `CComVariant`objet. `CY` Le type de l' `CComVariant` objet sera VT_CY.

*pSrc*<br/>
dans Pointeur `IDispatch` `CComVariant` ou `IUnknown` à assigner à l’objet. `AddRef`est appelé sur le pointeur d’interface. Le type de l' `CComVariant` objet sera VT_DISPATCH ou VT_UNKNOWN, respectivement.

Ou un pointeur SAFEARRAY à assigner à l' `CComVariant` objet. Une copie du SAFEARRAY est stockée dans l' `CComVariant` objet. Le type de l' `CComVariant` objet est une combinaison du type d’origine des SAFEARRAY et VT_ARRAY.

*cSrc*<br/>
dans Caractère à assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I1.

##  <a name="operator_eq_eq"></a>  CComVariant::operator ==

Indique si l' `CComVariant` objet est égal à la variante spécifiée.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur true si la valeur et le type de *varSrc* sont égaux à la valeur et au type, `CComVariant` respectivement, de l’objet. Sinon, FALSe. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

L’opérateur ne compare que la valeur des types variant. Elle compare des chaînes, des entiers et des points flottants, mais pas des tableaux ou des enregistrements.

##  <a name="operator_neq"></a>CComVariant :: Operator ! =

Indique si l' `CComVariant` objet n’est pas égal au variant spécifié.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur true si la valeur ou le type de *varSrc* n’est pas égal à la valeur ou au type, `CComVariant` respectivement, de l’objet. Sinon, FALSe. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

L’opérateur ne compare que la valeur des types variant. Elle compare des chaînes, des entiers et des points flottants, mais pas des tableaux ou des enregistrements.

##  <a name="operator_lt"></a>CComVariant :: Operator&lt;

Indique si l' `CComVariant` objet est inférieur à la variante spécifiée.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur true si la valeur `CComVariant` de l’objet est inférieure à la valeur de *varSrc*. Sinon, FALSe. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

##  <a name="operator_gt"></a>CComVariant :: Operator&gt;

Indique si l' `CComVariant` objet est supérieur à la variante spécifiée.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur true si la valeur `CComVariant` de l’objet est supérieure à la valeur de *varSrc*. Sinon, FALSe. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

Définit le VARIANT sous-jacent sur la variante contenue dans le flux spécifié.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur le flux contenant les données.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

`ReadToStream`requiert un appel précédent à [WriteToStream](#writetostream).

##  <a name="setbyref"></a>  CComVariant::SetByRef

Initialise l' `CComVariant` objet et définit le `vt` membre à VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de VARIANT, par exemple, BSTR, **int**ou **char**.

*pT*<br/>
Pointeur utilisé pour initialiser l' `CComVariant` objet.

### <a name="remarks"></a>Notes

`SetByRef`est un modèle de fonction qui initialise l' `CComVariant` objet sur le pointeur *PT* et définit le `vt` membre à VT_BYREF. Par exemple :

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>  CComVariant::WriteToStream

Enregistre la variante sous-jacente dans un flux.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur un flux.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
