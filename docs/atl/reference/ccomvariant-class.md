---
title: Classe CComVariant
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
ms.openlocfilehash: 9a84d91e20242fb206d1d3f71fcb3dd207561f62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327226"
---
# <a name="ccomvariant-class"></a>Classe CComVariant

Cette classe enveloppe le type VARIANT, fournissant un membre indiquant le type de données stockées.

## <a name="syntax"></a>Syntaxe

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|Constructeur.|
|[CComVariant: :CComVariant](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComVariant::Attach](#attach)|Attache un VARIANT `CComVariant` à l’objet.|
|[CComVariant::ChangeType](#changetype)|Convertit `CComVariant` l’objet en un nouveau type.|
|[CComVariant::Clair](#clear)|Dégage l' `CComVariant` objet.|
|[CComVariant::Copie](#copy)|Copie d’un `CComVariant` VARIANT à l’objet.|
|[CComVariant::CopyTo](#copyto)|Copie le contenu `CComVariant` de l’objet.|
|[CComVariant::Detach](#detach)|Détache le VARIANT sous-jacent de l’objet. `CComVariant`|
|[CComVariant::GetSize](#getsize)|Retourne la taille en nombre d’octets du contenu de l’objet. `CComVariant`|
|[CComVariant::LireDestream](#readfromstream)|Charge un VARIANT à partir d’un flux.|
|[CComVariant::SetByRef](#setbyref)|Initialise l’objet `CComVariant` et `vt` met le membre à VT_BYREF.|
|[CComVariant::WriteToStream](#writetostream)|Enregistre le VARIANT sous-jacent dans un flux.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|||
|-|-|
|[CComVariant::opérateur <](#operator_lt)|Indique si `CComVariant` l’objet est inférieur à la VARIANT spécifiée.|
|[CComVariant::opérateur >](#operator_gt)|Indique si `CComVariant` l’objet est plus grand que le VARIANT spécifié.|
|[opérateur !](#operator_neq)|Indique si `CComVariant` l’objet n’est pas égal à la VARIANT spécifiée.|
|[opérateur](#operator_eq)|Attribue une valeur `CComVariant` à l’objet.|
|[opérateur](#operator_eq_eq)|Indique si `CComVariant` l’objet est égal à la VARIANT spécifiée.|

## <a name="remarks"></a>Notes

`CComVariant`enveloppe le type VARIANT et VARIANTARG, qui consiste en un syndicat et un membre indiquant le type de données stockées dans le syndicat. Les VARIANT sont généralement utilisés dans Automation.

`CComVariant`dérive du type VARIANT afin qu’il puisse être utilisé partout où un VARIANT peut être utilisé. Vous pouvez, par exemple, utiliser la macro V_VT pour `CComVariant` extraire le `vt` type de a ou vous pouvez accéder au membre directement comme vous le pouvez avec un VARIANT.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcomcli.h

## <a name="ccomvariantattach"></a><a name="attach"></a>CComVariant::Attach

Efface en toute sécurité le `CComVariant` contenu actuel de l’objet, copie le contenu du *pSrc* dans cet objet, puis définit le type de variante de *pSrc* à VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Paramètres

*pSrc (en)*<br/>
[dans] Points à la [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) à attacher à l’objet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La propriété des données détenues par `CComVariant` *pSrc* est transférée à l’objet.

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CComVariant::CComVariant

Chaque constructeur gère l’initialisation `CComVariant` sûre de `VariantInit` l’objet en appelant la fonction Win32 ou en définissant la valeur et le type de l’objet en fonction des paramètres passés.

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
[dans] Le `CComVariant` variante ou variable `CComVariant` utilisé pour initialiser l’objet. Le contenu de la variante source est copié à la destination sans conversion.

*lpszSrc (en)*<br/>
[dans] La chaîne de caractère `CComVariant` utilisée pour initialiser l’objet. Vous pouvez passer une chaîne de caractères large (Unicode) à zéro fin (Unicode) à la version LPCOLESTR du constructeur ou à une chaîne ANSI à la version LPCSTR. Dans les deux cas, la chaîne est convertie `SysAllocString`en un BSTR Unicode alloué à l’aide de . Le type `CComVariant` de l’objet sera VT_BSTR.

*bSrc (en)*<br/>
[dans] Le **bool** utilisé pour `CComVariant` initialiser l’objet. **L’argument bool** est converti en un VARIANT_BOOL avant d’être stocké. Le type `CComVariant` de l’objet sera VT_BOOL.

*nSrc (en)*<br/>
[dans] **L’int**, **BYTE**, **court**, **long**, LONGLONG, ULONGLONG, non **signé court**, non **signé long**, ou **int non signé** utilisé pour initialiser l’objet. `CComVariant` Le type `CComVariant` d’objet sera VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 ou VT_UI4, respectivement.

*vtSrc*<br/>
[dans] Le type de la variante. Lorsque le premier paramètre est **int,** les types valides sont VT_I4 et VT_INT. Lorsque le premier paramètre est **long,** les types valides sont VT_I4 et VT_ERROR. Lorsque le premier paramètre est **double,** les types valides sont VT_R8 et VT_DATE. Lorsque le premier paramètre **n’est pas signé int**, les types valides sont VT_UI4 et VT_UINT.

*fltSrc*<br/>
[dans] Le **flotteur** utilisé `CComVariant` pour initialiser l’objet. Le type `CComVariant` de l’objet sera VT_R4.

*dblSrc*<br/>
[dans] Le **double** utilisé pour `CComVariant` initialiser l’objet. Le type `CComVariant` de l’objet sera VT_R8.

*cySrc (en)*<br/>
[dans] L’utilisé `CY` pour `CComVariant` initialiser l’objet. Le type `CComVariant` de l’objet sera VT_CY.

*pSrc (en)*<br/>
[dans] Le `IDispatch` `IUnknown` pointeur ou le `CComVariant` pointeur utilisé pour initialiser l’objet. `AddRef`sera appelé sur le pointeur d’interface. Le type `CComVariant` de l’objet sera VT_DISPATCH ou VT_UNKNOWN, respectivement.

Ou, le pointeur SAFERRAY `CComVariant` utilisé pour initialiser l’objet. Une copie du SAFEARRAY est `CComVariant` stockée dans l’objet. Le type `CComVariant` d’objet sera une combinaison du type original de la SAFEARRAY et VT_ARRAY.

*Csrc*<br/>
[dans] **L’omble utilisé** `CComVariant` pour initialiser l’objet. Le type `CComVariant` de l’objet sera VT_I1.

*bstrSrc (en)*<br/>
[dans] Le BSTR avait l’habitude d’initialiser l’objet. `CComVariant` Le type `CComVariant` de l’objet sera VT_BSTR.

### <a name="remarks"></a>Notes

Le destructeur gère le nettoyage en appelant [CComVariant::Clear](#clear).

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CComVariant: :CComVariant

Destructeur.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Notes

Cette méthode gère le nettoyage en appelant [CComVariant::Clear](#clear).

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CComVariant::ChangeType

Convertit `CComVariant` l’objet en un nouveau type.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Paramètres

*vtNouvelle*<br/>
[dans] Le nouveau type `CComVariant` pour l’objet.

*pSrc (en)*<br/>
[dans] Un pointeur pour le VARIANT dont la valeur sera convertie en nouveau type. La valeur par défaut `CComVariant` est NULL, ce qui signifie que l’objet sera converti en place.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si vous passez une valeur pour `ChangeType` *pSrc*, utilisera ce VARIANT comme source de conversion. Sinon, `CComVariant` l’objet sera la source.

## <a name="ccomvariantclear"></a><a name="clear"></a>CComVariant::Clair

Efface l’objet `CComVariant` en `VariantClear` appelant la fonction Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le destructeur `Clear`appelle automatiquement .

## <a name="ccomvariantcopy"></a><a name="copy"></a>CComVariant::Copie

Libère l’objet `CComVariant` et lui attribue ensuite une copie du VARIANT spécifié.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Paramètres

*pSrc (en)*<br/>
[dans] Un pointeur à la [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) à copier.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>CComVariant::CopyTo

Copie le contenu `CComVariant` de l’objet.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Paramètres

*pstrDest*<br/>
Indique un BSTR qui recevra une copie `CComVariant` du contenu de l’objet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet `CComVariant` doit être de type VT_BSTR.

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant::Detach

Détache le VARIANT sous-jacent de l’objet `CComVariant` et définit le type de l’objet pour VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
[out] Retourne la valeur sous-jacente de l’objet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Notez que le contenu du VARIANT référencé par *pDest* sera automatiquement `CComVariant` effacé avant d’être attribué la valeur et le type de l’objet d’appel.

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CComVariant::GetSize

Pour les VARIANT de taille simple, cette méthode retourne la **taille du** type de données sous-jacent plus la taille **de (VARTYPE)**.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille dans les octets `CComVariant` du contenu actuel de l’objet.

### <a name="remarks"></a>Notes

Si le VARIANT contient `GetSize` un pointeur d’interface, des requêtes pour `IPersistStream` ou `IPersistStreamInit`. En cas de succès, la valeur de rendement est la `GetSizeMax` commande basse 32 bits de la valeur retournée par plus la **taille d’un** CLSID et **tailleof (VARTYPE)**. Si le pointeur `GetSize` d’interface est NULL, retourne la **taille d’un** CLSID plus **sizeof (VARTYPE)**. Si la taille totale est plus `GetSize` grande que ULONG_MAX, retourne **la taille de (VARTYPE)** qui indique une erreur.

Dans tous les autres cas, un variant temporaire de type VT_BSTR est contraint du variant actuel. La longueur de ce BSTR est calculée comme la taille de la longueur de la chaîne plus la longueur de la chaîne elle-même plus la taille du caractère nul plus **la taille de (VARTYPE)**. Si le VARIANT ne peut pas être contraint à `GetSize` une VARIANTE de type VT_BSTR, retourne **la taille de (VARTYPE)**.

La taille retournée par cette méthode correspond au nombre d’octets utilisés par [CComVariant::WriteToStream](#writetostream) dans des conditions réussies.

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant::opérateur

Assigne une valeur et `CComVariant` un type correspondant à l’objet.

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
[dans] Le `CComVariant` [variante](/windows/win32/api/oaidl/ns-oaidl-variant) ou à `CComVariant` attribuer à l’objet. Le contenu de la variante source est copié à la destination sans conversion.

*bstrSrc (en)*<br/>
[dans] Le BSTR à attribuer `CComVariant` à l’objet. Le type `CComVariant` de l’objet sera VT_BSTR.

*lpszSrc (en)*<br/>
[dans] La chaîne de caractère `CComVariant` à attribuer à l’objet. Vous pouvez passer une chaîne de caractères large (Unicode) à zéro fin (Unicode) à la version LPCOLESTR de l’opérateur ou une chaîne ANSI à la version LPCSTR. Dans les deux cas, la chaîne est convertie `SysAllocString`en un BSTR Unicode alloué à l’aide de . Le type `CComVariant` de l’objet sera VT_BSTR.

*bSrc (en)*<br/>
[dans] Le **bool** à attribuer `CComVariant` à l’objet. **L’argument bool** est converti en un VARIANT_BOOL avant d’être stocké. Le type `CComVariant` de l’objet sera VT_BOOL.

*nSrc (en)*<br/>
[dans] **L’int**, BYTE, **court**, **long**, LONGLONG, ULONGLONG, non **signé court**, non **signé long**, ou **int non signé** à attribuer à l’objet. `CComVariant` Le type `CComVariant` d’objet sera VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 ou VT_UI4, respectivement.

*fltSrc*<br/>
[dans] Le **flotteur** à `CComVariant` attribuer à l’objet. Le type `CComVariant` de l’objet sera VT_R4.

*dblSrc*<br/>
[dans] Le **double** à attribuer `CComVariant` à l’objet. Le type `CComVariant` de l’objet sera VT_R8.

*cySrc (en)*<br/>
[dans] Le `CY` à assigner `CComVariant` à l’objet. Le type `CComVariant` de l’objet sera VT_CY.

*pSrc (en)*<br/>
[dans] Le `IDispatch` `IUnknown` pointeur ou pointeur à attribuer à l’objet. `CComVariant` `AddRef`sera appelé sur le pointeur d’interface. Le type `CComVariant` de l’objet sera VT_DISPATCH ou VT_UNKNOWN, respectivement.

Ou, un pointeur SAFEARRAY `CComVariant` à attribuer à l’objet. Une copie du SAFEARRAY est `CComVariant` stockée dans l’objet. Le type `CComVariant` d’objet sera une combinaison du type original de la SAFEARRAY et VT_ARRAY.

*Csrc*<br/>
[dans] L’omble à `CComVariant` attribuer à l’objet. Le type `CComVariant` de l’objet sera VT_I1.

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant::opérateur

Indique si `CComVariant` l’objet est égal à la VARIANT spécifiée.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne VRAI si la valeur et le type de *varSrc* sont `CComVariant` égaux à la valeur et le type, respectivement, de l’objet. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise le lieu par défaut de l’utilisateur pour effectuer la comparaison.

L’opérateur ne compare que la valeur des types de variantes. Il compare les cordes, les intégrages et les points flottants, mais pas les tableaux ou les enregistrements.

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant::opérateur !

Indique si `CComVariant` l’objet n’est pas égal à la VARIANT spécifiée.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne VRAI si la valeur ou le type de *varSrc* n’est `CComVariant` pas égal à la valeur ou au type, respectivement, de l’objet. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise le lieu par défaut de l’utilisateur pour effectuer la comparaison.

L’opérateur ne compare que la valeur des types de variantes. Il compare les cordes, les intégrages et les points flottants, mais pas les tableaux ou les enregistrements.

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CComVariant::opérateur&lt;

Indique si `CComVariant` l’objet est inférieur à la VARIANT spécifiée.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne VRAI si la `CComVariant` valeur de l’objet est inférieure à la valeur de *varSrc*. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise le lieu par défaut de l’utilisateur pour effectuer la comparaison.

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CComVariant::opérateur&gt;

Indique si `CComVariant` l’objet est plus grand que le VARIANT spécifié.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne VRAI si la `CComVariant` valeur de l’objet est supérieure à la valeur de *varSrc*. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise le lieu par défaut de l’utilisateur pour effectuer la comparaison.

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>CComVariant::LireDestream

Définit le VARIANT sous-jacent au VARIANT contenu dans le flux spécifié.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[dans] Un pointeur à l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur le flux contenant les données.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`ReadToStream`nécessite un appel précédent pour [WriteToStream](#writetostream).

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>CComVariant::SetByRef

Initialise l’objet `CComVariant` et `vt` met le membre à VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de VARIANT, par exemple, BSTR, **int**, ou **char**.

*Pt*<br/>
Le pointeur utilisé `CComVariant` pour initialiser l’objet.

### <a name="remarks"></a>Notes

`SetByRef`est un modèle de fonction `CComVariant` qui initialise l’objet `vt` au *pointeur pT* et définit le membre à VT_BYREF. Par exemple :

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>CComVariant::WriteToStream

Enregistre le VARIANT sous-jacent dans un flux.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[dans] Un pointeur à l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur un flux.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
