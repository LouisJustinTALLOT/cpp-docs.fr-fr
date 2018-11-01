---
title: CD2DTextFormat, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 092ffff91113b42cd106fe7079b06b9482400c63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557155"
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
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Construit un objet CD2DTextFormat.|
|[CD2DTextFormat :: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|Destructeur. Appelé lorsqu’un objet de format de texte D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DTextFormat::Create](#create)|Crée un CD2DTextFormat. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormat::Destroy](#destroy)|Détruit un objet CD2DTextFormat. (Substitue [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextFormat::Get](#get)|Renvoie l’interface IDWriteTextFormat|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Obtient une copie du nom de famille de polices.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Obtient une copie du nom des paramètres régionaux.|
|[CD2DTextFormat::IsValid](#isvalid)|Vérifie la validité des ressources (remplace [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::ReCreate](#recreate)|Recrée un CD2DTextFormat. (Substitue [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DTextFormat::operator IDWriteTextFormat *](#operator_idwritetextformat_star)|Renvoie l’interface IDWriteTextFormat|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Pointeur vers un IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="_dtorcd2dtextformat"></a>  CD2DTextFormat :: ~ CD2DTextFormat

Destructeur. Appelé lorsqu’un objet de format de texte D2D est détruit.

```
virtual ~CD2DTextFormat();
```

##  <a name="cd2dtextformat"></a>  CD2DTextFormat::CD2DTextFormat

Construit un objet CD2DTextFormat.

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
Un objet CString qui contient le nom de la famille de polices.

*fontSize*<br/>
La taille logique de la police en unités DIP (« pixels indépendants du périphérique »). Une DIP est égal à 1/96ème de pouce.

*fontWeight*<br/>
Une valeur qui indique l’épaisseur de police pour l’élément textuel.

*fontStyle*<br/>
Une valeur qui indique le style de police pour l’élément textuel.

*fontStretch*<br/>
Une valeur qui indique l’étirement de police pour l’élément textuel.

*strFontLocale*<br/>
Un objet CString qui contient le nom des paramètres régionaux.

*pFontCollection*<br/>
Pointeur vers un objet de collection de polices. Lorsque ce paramètre est NULL, indique la collection de polices système.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

##  <a name="create"></a>  CD2DTextFormat::Create

Crée un CD2DTextFormat.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="destroy"></a>  CD2DTextFormat::Destroy

Détruit un objet CD2DTextFormat.

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextFormat::Get

Renvoie l’interface IDWriteTextFormat

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.

##  <a name="getfontfamilyname"></a>  CD2DTextFormat::GetFontFamilyName

Obtient une copie du nom de famille de polices.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom de famille de polices actuel.

##  <a name="getlocalename"></a>  CD2DTextFormat::GetLocaleName

Obtient une copie du nom des paramètres régionaux.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom des paramètres régionaux en cours.

##  <a name="isvalid"></a>  CD2DTextFormat::IsValid

Vérifications de validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la ressource est valide ; Sinon, FALSE.

##  <a name="m_ptextformat"></a>  CD2DTextFormat::m_pTextFormat

Pointeur vers un IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

##  <a name="operator_idwritetextformat_star"></a>  CD2DTextFormat::operator IDWriteTextFormat *

Renvoie l’interface IDWriteTextFormat

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.

##  <a name="recreate"></a>  CD2DTextFormat::ReCreate

Recrée un CD2DTextFormat.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
