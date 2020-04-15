---
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
ms.openlocfilehash: f7310fd3ca2ac34df7cc1a99cd5527ea8ba709c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369044"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat, classe

Un emballage pour IDWriteTextFormat.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Construit un objet CD2DTextFormat.|
|[CD2DTextFormat: CD2DTextFormat](#_dtorcd2dtextformat)|Destructeur. Appelé lorsqu’un objet de format de texte D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DTextFormat::Créer](#create)|Crée un CD2DTextFormat. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormat::Destroy](#destroy)|Détruit un objet CD2DTextFormat. (Overrides [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextFormat::Get](#get)|Retourne l’interface IDWriteTextFormat|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Obtient une copie du nom de famille de police.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Obtient une copie du nom local.|
|[CD2DTextFormat::IsValid](#isvalid)|Vérifie la validité des ressources (Overrides [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::ReCreate](#recreate)|Re-crée un CD2DTextFormat. (Overrides [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DTextFormat::opérateur IDWriteTextFormat](#operator_idwritetextformat_star)|Retourne l’interface IDWriteTextFormat|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Un pointeur à un IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DTextFormat (en anglais)](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2DTextFormat: CD2DTextFormat

Destructeur. Appelé lorsqu’un objet de format de texte D2D est détruit.

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2DTextFormat::CD2DTextFormat

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
Un pointeur à la cible de rendu.

*strFontFamilyName (en)*<br/>
Un objet CString qui contient le nom de la famille de police.

*Fontsize*<br/>
La taille logique de la police dans les unités DIP (« pixel indépendant de l’appareil »). Un DIPequals 1/96 pouce.

*Fontweight*<br/>
Une valeur qui indique le poids de police pour l’objet de texte.

*Fontstyle*<br/>
Une valeur qui indique le style de police pour l’objet de texte.

*Fontstretch*<br/>
Une valeur qui indique l’étirement de police pour l’objet de texte.

*strFontLocale*<br/>
Un objet CString qui contient le nom local.

*pFontCollection*<br/>
Pointeur d’un objet de collecte de polices. Lorsque c’est NULL, indique la collecte de police système.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dtextformatcreate"></a><a name="create"></a>CD2DTextFormat::Créer

Crée un CD2DTextFormat.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a>CD2DTextFormat::Destroy

Détruit un objet CD2DTextFormat.

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a>CD2DTextFormat::Get

Retourne l’interface IDWriteTextFormat

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextFormat::GetFontFamilyName

Obtient une copie du nom de famille de police.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom de famille de police actuel.

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2DTextFormat::GetLocaleName

Obtient une copie du nom local.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom local actuel.

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2DTextFormat::IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a>CD2DTextFormat::m_pTextFormat

Un pointeur à un IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2DTextFormat::opérateur IDWriteTextFormat

Retourne l’interface IDWriteTextFormat

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a>CD2DTextFormat::ReCreate

Re-crée un CD2DTextFormat.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
