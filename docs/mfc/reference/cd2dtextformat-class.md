---
description: 'En savoir plus sur : classe Cd2dtextformat,'
title: CD2DTextFormat, classe
ms.date: 03/27/2019
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
ms.openlocfilehash: fc87aec6acb0e1eae0211555f1bdc943079081f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338334"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat, classe

Wrapper pour IDWriteTextFormat.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dtextformat, :: Cd2dtextformat,](#cd2dtextformat)|Construit un objet Cd2dtextformat,.|
|[Cd2dtextformat, :: ~ Cd2dtextformat,](#_dtorcd2dtextformat)|Destructeur. Appelé lorsqu’un objet de format de texte D2D est en cours de destruction.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dtextformat, :: Create](#create)|Crée un Cd2dtextformat,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dtextformat, ::D estroy](#destroy)|Détruit un objet Cd2dtextformat,. (Substitue [CD2DResource, ::D estroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[Cd2dtextformat, :: obtient](#get)|Retourne l’interface IDWriteTextFormat|
|[Cd2dtextformat, :: GetFontFamilyName](#getfontfamilyname)|Obtient une copie du nom de famille de polices.|
|[Cd2dtextformat, :: GetLocaleName](#getlocalename)|Obtient une copie du nom de paramètres régionaux.|
|[Cd2dtextformat, :: IsValid](#isvalid)|Vérifie la validité des ressources (Substitue [CD2DResource, :: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[Cd2dtextformat, :: recréer](#recreate)|Recrée un Cd2dtextformat,. (Substitue [CD2DResource, :: recreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dtextformat, :: Operator IDWriteTextFormat *](#operator_idwritetextformat_star)|Retourne l’interface IDWriteTextFormat|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dtextformat, :: m_pTextFormat](#m_ptextformat)|Pointeur vers un IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dtextformat,](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a> Cd2dtextformat, :: ~ Cd2dtextformat,

Destructeur. Appelé lorsqu’un objet de format de texte D2D est en cours de destruction.

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a> Cd2dtextformat, :: Cd2dtextformat,

Construit un objet Cd2dtextformat,.

```
CD2DTextFormat(
    CRenderTarget* pParentTarget,
    const CString& strFontFamilyName,
    FLOAT fontSize,
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,
    const CString& strFontLocale = _T(""),
    IDWriteFontCollection* pFontCollection = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*strFontFamilyName*<br/>
Objet CString qui contient le nom de la famille de polices.

*fontSize*<br/>
Taille logique de la police en unités DIP (« pixel indépendant du périphérique »). DIPequals 1/96 pouces.

*fontWeight*<br/>
Valeur qui indique l’épaisseur de police de l’objet texte.

*fontStyle*<br/>
Valeur qui indique le style de police pour l’objet texte.

*fontStretch*<br/>
Valeur qui indique l’étirement de la police pour l’objet texte.

*strFontLocale*<br/>
Objet CString qui contient le nom des paramètres régionaux.

*pFontCollection*<br/>
Pointeur vers un objet de collection de polices. Lorsque la valeur est NULL, indique la collection de polices système.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dtextformatcreate"></a><a name="create"></a> Cd2dtextformat, :: Create

Crée un Cd2dtextformat,.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a> Cd2dtextformat, ::D estroy

Détruit un objet Cd2dtextformat,.

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a> Cd2dtextformat, :: obtient

Retourne l’interface IDWriteTextFormat

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a> Cd2dtextformat, :: GetFontFamilyName

Obtient une copie du nom de famille de polices.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet CString qui contient le nom de famille de polices actuel.

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a> Cd2dtextformat, :: GetLocaleName

Obtient une copie du nom de paramètres régionaux.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet CString qui contient le nom des paramètres régionaux actuels.

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a> Cd2dtextformat, :: IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a> Cd2dtextformat, :: m_pTextFormat

Pointeur vers un IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a> Cd2dtextformat, :: Operator IDWriteTextFormat *

Retourne l’interface IDWriteTextFormat

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a> Cd2dtextformat, :: recréer

Recrée un Cd2dtextformat,.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
