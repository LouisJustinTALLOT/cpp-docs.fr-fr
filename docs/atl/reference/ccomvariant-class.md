---
description: 'En savoir plus sur : CComVariant, classe'
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
ms.openlocfilehash: e618e7e68704d2fd8b69aecd58cbf986bb704c53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142127"
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
|[CComVariant :: CComVariant](#ccomvariant)|Constructeur.|
|[CComVariant :: ~ CComVariant](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComVariant :: Attach](#attach)|Joint un VARIANT à l' `CComVariant` objet.|
|[CComVariant :: ChangeType](#changetype)|Convertit l' `CComVariant` objet en un nouveau type.|
|[CComVariant :: Clear](#clear)|Efface l' `CComVariant` objet.|
|[CComVariant :: Copy](#copy)|Copie un VARIANT vers l' `CComVariant` objet.|
|[CComVariant :: CopyTo](#copyto)|Copie le contenu de l' `CComVariant` objet.|
|[CComVariant ::D Etach](#detach)|Détache la variante sous-jacente de l' `CComVariant` objet.|
|[CComVariant :: dela](#getsize)|Retourne la taille en nombre d’octets du contenu de l' `CComVariant` objet.|
|[CComVariant :: ReadFromStream](#readfromstream)|Charge un VARIANT à partir d’un flux.|
|[CComVariant :: SetByRef](#setbyref)|Initialise l' `CComVariant` objet et définit le `vt` membre à VT_BYREF.|
|[CComVariant :: WriteToStream](#writetostream)|Enregistre la variante sous-jacente dans un flux.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Opérateur|Description|
|-|-|
|[CComVariant :: Operator <](#operator_lt)|Indique si l' `CComVariant` objet est inférieur à la variante spécifiée.|
|[CComVariant :: Operator >](#operator_gt)|Indique si l' `CComVariant` objet est supérieur à la variante spécifiée.|
|[opérateur ! =](#operator_neq)|Indique si l' `CComVariant` objet n’est pas égal au variant spécifié.|
|[opérateur =](#operator_eq)|Assigne une valeur à l' `CComVariant` objet.|
|[opérateur = =](#operator_eq_eq)|Indique si l' `CComVariant` objet est égal à la variante spécifiée.|

## <a name="remarks"></a>Notes

`CComVariant` encapsule le type VARIANT et VARIANTARG, qui se compose d’une Union et d’un membre indiquant le type des données stockées dans l’Union. Les VARIANTEs sont généralement utilisées dans Automation.

`CComVariant` dérive du type VARIANT afin qu’il puisse être utilisé partout où un VARIANT peut être utilisé. Vous pouvez, par exemple, utiliser la macro V_VT pour extraire le type d’un `CComVariant` ou vous pouvez accéder au `vt` membre directement comme vous le feriez avec un variant.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcomcli. h

## <a name="ccomvariantattach"></a><a name="attach"></a> CComVariant :: Attach

Efface en toute sécurité le contenu actuel de l' `CComVariant` objet, copie le contenu de *pSrc* dans cet objet, puis définit le type variant de *pSrc* sur VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Paramètres

*pSrc*<br/>
dans Pointe vers le [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) à attacher à l’objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

La propriété des données détenues par *pSrc* est transférée à l' `CComVariant` objet.

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a> CComVariant :: CComVariant

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
dans `CComVariant` Variant ou utilisé pour initialiser l' `CComVariant` objet. Le contenu du variant source est copié vers la destination sans conversion.

*lpszSrc*<br/>
dans Chaîne de caractères utilisée pour initialiser l' `CComVariant` objet. Vous pouvez passer une chaîne de caractères de largeur nulle (Unicode) à la version LPCOLESTR du constructeur ou une chaîne ANSI à la version LPCSTR. Dans les deux cas, la chaîne est convertie en un BSTR Unicode alloué à l’aide de `SysAllocString` . Le type de l' `CComVariant` objet sera VT_BSTR.

*bSrc*<br/>
dans **`bool`** Utilisé pour initialiser l' `CComVariant` objet. L' **`bool`** argument est converti en VARIANT_BOOL avant d’être stocké. Le type de l' `CComVariant` objet sera VT_BOOL.

*nSrc*<br/>
dans **`int`**, **Byte**, **`short`** ,, **`long`** LongLong, ULONGLONG,, **`unsigned short`** **`unsigned long`** ou **`unsigned int`** utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 ou VT_UI4, respectivement.

*vtSrc*<br/>
dans Type de la variante. Lorsque le premier paramètre est **`int`** , les types valides sont VT_I4 et VT_INT. Lorsque le premier paramètre est **`long`** , les types valides sont VT_I4 et VT_ERROR. Lorsque le premier paramètre est **`double`** , les types valides sont VT_R8 et VT_DATE. Lorsque le premier paramètre est **`unsigned int`** , les types valides sont VT_UI4 et VT_UINT.

*fltSrc*<br/>
dans **`float`** Utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_R4.

*dblSrc*<br/>
dans **`double`** Utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_R8.

*cySrc*<br/>
dans `CY` Utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_CY.

*pSrc*<br/>
dans `IDispatch` Pointeur ou `IUnknown` utilisé pour initialiser l' `CComVariant` objet. `AddRef` est appelé sur le pointeur d’interface. Le type de l' `CComVariant` objet sera VT_DISPATCH ou VT_UNKNOWN, respectivement.

Ou le pointeur SAFERRAY utilisé pour initialiser l' `CComVariant` objet. Une copie du SAFEARRAY est stockée dans l' `CComVariant` objet. Le type de l' `CComVariant` objet est une combinaison du type d’origine du SAFEARRAY et VT_ARRAY.

*cSrc*<br/>
dans **`char`** Utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I1.

*bstrSrc*<br/>
dans BSTR utilisé pour initialiser l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_BSTR.

### <a name="remarks"></a>Notes

Le destructeur gère le nettoyage en appelant [CComVariant :: Clear](#clear).

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a> CComVariant :: ~ CComVariant

Destructeur.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Notes

Cette méthode gère le nettoyage en appelant [CComVariant :: Clear](#clear).

## <a name="ccomvariantchangetype"></a><a name="changetype"></a> CComVariant :: ChangeType

Convertit l' `CComVariant` objet en un nouveau type.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Paramètres

*vtNew*<br/>
dans Nouveau type de l' `CComVariant` objet.

*pSrc*<br/>
dans Pointeur vers le VARIANT dont la valeur sera convertie vers le nouveau type. La valeur par défaut est NULL, ce qui signifie que l' `CComVariant` objet sera converti sur place.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si vous transmettez une valeur pour *pSrc*, `ChangeType` utilise cette variante comme source pour la conversion. Dans le cas contraire, l' `CComVariant` objet sera la source.

## <a name="ccomvariantclear"></a><a name="clear"></a> CComVariant :: Clear

Efface l' `CComVariant` objet en appelant la `VariantClear` fonction Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le destructeur appelle automatiquement `Clear` .

## <a name="ccomvariantcopy"></a><a name="copy"></a> CComVariant :: Copy

Libère l' `CComVariant` objet, puis lui assigne une copie de la variante spécifiée.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Paramètres

*pSrc*<br/>
dans Pointeur vers le [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) à copier.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="ccomvariantcopyto"></a><a name="copyto"></a> CComVariant :: CopyTo

Copie le contenu de l' `CComVariant` objet.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Paramètres

*pstrDest*<br/>
Pointe vers un BSTR qui recevra une copie du contenu de l' `CComVariant` objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L' `CComVariant` objet doit être de type VT_BSTR.

## <a name="ccomvariantdetach"></a><a name="detach"></a> CComVariant ::D Etach

Détache la variante sous-jacente de l' `CComVariant` objet et définit le type de l’objet sur VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
à Retourne la valeur de type VARIANT sous-jacent de l’objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Notez que le contenu de la variante référencée par *pDEST* sera automatiquement effacé avant d’être affecté à la valeur et au type de l' `CComVariant` objet appelant.

## <a name="ccomvariantgetsize"></a><a name="getsize"></a> CComVariant :: dela

Pour les VARIANTEs de taille fixe simples, cette méthode retourne la **`sizeof`** valeur pour le type de données sous-jacent plus **sizeof (VarType)**.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille en octets du contenu actuel de l' `CComVariant` objet.

### <a name="remarks"></a>Notes

Si le VARIANT contient un pointeur d’interface, `GetSize` interroge pour `IPersistStream` ou `IPersistStreamInit` . En cas de réussite, la valeur de retour est l’ordre de 32 bits de poids faible de la valeur retournée par `GetSizeMax` plus `sizeof(CLSID)` et `sizeof(VARTYPE)` . Si le pointeur d’interface est NULL, `GetSize` retourne `sizeof(CLSID)` plus `sizeof(VARTYPE)` . Si la taille totale est supérieure à ULONG_MAX, `GetSize` retourne `sizeof(VARTYPE)` qui indique une erreur.

Dans tous les autres cas, une variante temporaire de type VT_BSTR est convertie à partir de la variante actuelle. La longueur de ce BSTR est calculée en fonction de la taille de la chaîne plus la longueur de la chaîne elle-même, plus la taille du caractère null plus **sizeof (VarType)**. Si la variante ne peut pas être forcée à un VARIANT de type VT_BSTR, `GetSize` retourne **sizeof (VarType)**.

La taille retournée par cette méthode correspond au nombre d’octets utilisés par [CComVariant :: WriteToStream](#writetostream) en cas de réussite.

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a> CComVariant :: Operator =

Assigne une valeur et un type correspondant à l' `CComVariant` objet.

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
dans `CComVariant` [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) ou à assigner à l' `CComVariant` objet. Le contenu du variant source est copié vers la destination sans conversion.

*bstrSrc*<br/>
dans BSTR à assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_BSTR.

*lpszSrc*<br/>
dans Chaîne de caractères à assigner à l' `CComVariant` objet. Vous pouvez transmettre une chaîne de caractères de largeur nulle (Unicode) à la version LPCOLESTR de l’opérateur ou une chaîne ANSI à la version LPCSTR. Dans les deux cas, la chaîne est convertie en un BSTR Unicode alloué à l’aide de `SysAllocString` . Le type de l' `CComVariant` objet sera VT_BSTR.

*bSrc*<br/>
dans **`bool`** À assigner à l' `CComVariant` objet. L' **`bool`** argument est converti en VARIANT_BOOL avant d’être stocké. Le type de l' `CComVariant` objet sera VT_BOOL.

*nSrc*<br/>
dans **`int`**, Byte, **`short`** , **`long`** , LongLong, ULONGLONG,, **`unsigned short`** **`unsigned long`** ou **`unsigned int`** à assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 ou VT_UI4, respectivement.

*fltSrc*<br/>
dans **`float`** À assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_R4.

*dblSrc*<br/>
dans **`double`** À assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_R8.

*cySrc*<br/>
dans `CY` À assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_CY.

*pSrc*<br/>
dans `IDispatch` Pointeur ou `IUnknown` à assigner à l' `CComVariant` objet. `AddRef` est appelé sur le pointeur d’interface. Le type de l' `CComVariant` objet sera VT_DISPATCH ou VT_UNKNOWN, respectivement.

Ou un pointeur SAFEARRAY à assigner à l' `CComVariant` objet. Une copie du SAFEARRAY est stockée dans l' `CComVariant` objet. Le type de l' `CComVariant` objet est une combinaison du type d’origine du SAFEARRAY et VT_ARRAY.

*cSrc*<br/>
dans Caractère à assigner à l' `CComVariant` objet. Le type de l' `CComVariant` objet sera VT_I1.

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a> CComVariant :: Operator = =

Indique si l' `CComVariant` objet est égal à la variante spécifiée.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si la valeur et le type de *varSrc* sont égaux à la valeur et au type, respectivement, de l' `CComVariant` objet. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

L’opérateur ne compare que la valeur des types variant. Elle compare des chaînes, des entiers et des points flottants, mais pas des tableaux ou des enregistrements.

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a> CComVariant :: Operator ! =

Indique si l' `CComVariant` objet n’est pas égal au variant spécifié.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si la valeur ou le type de *varSrc* n’est pas égal à la valeur ou au type, respectivement, de l' `CComVariant` objet. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

L’opérateur ne compare que la valeur des types variant. Elle compare des chaînes, des entiers et des points flottants, mais pas des tableaux ou des enregistrements.

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a> CComVariant :: Operator &lt;

Indique si l' `CComVariant` objet est inférieur à la variante spécifiée.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si la valeur de l' `CComVariant` objet est inférieure à la valeur de *varSrc*. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a> CComVariant :: Operator &gt;

Indique si l' `CComVariant` objet est supérieur à la variante spécifiée.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si la valeur de l' `CComVariant` objet est supérieure à la valeur de *varSrc*. Dans le cas contraire, la valeur est FALSE. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a> CComVariant :: ReadFromStream

Définit le VARIANT sous-jacent sur la variante contenue dans le flux spécifié.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur le flux contenant les données.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

`ReadToStream` requiert un appel précédent à [WriteToStream](#writetostream).

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a> CComVariant :: SetByRef

Initialise l' `CComVariant` objet et définit le `vt` membre à VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de VARIANT, par exemple, BSTR, **`int`** ou **`char`** .

*Unis*<br/>
Pointeur utilisé pour initialiser l' `CComVariant` objet.

### <a name="remarks"></a>Notes

`SetByRef` est un modèle de fonction qui initialise l' `CComVariant` objet sur le pointeur *PT* et définit le `vt` membre sur VT_BYREF. Par exemple :

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a> CComVariant :: WriteToStream

Enregistre la variante sous-jacente dans un flux.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) sur un flux.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
