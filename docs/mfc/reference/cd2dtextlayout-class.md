---
description: 'En savoir plus sur : classe Cd2dtextlayout,'
title: CD2DTextLayout, classe
ms.date: 03/27/2019
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
ms.openlocfilehash: 164c8ed5561be6e8f9ee59b07d0aecaced5f7c81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240544"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout, classe

Wrapper pour IDWriteTextLayout.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dtextlayout, :: Cd2dtextlayout,](#cd2dtextlayout)|Construit un objet Cd2dtextlayout,.|
|[Cd2dtextlayout, :: ~ Cd2dtextlayout,](#_dtorcd2dtextlayout)|Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dtextlayout, :: Create](#create)|Crée un Cd2dtextlayout,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dtextlayout, ::D estroy](#destroy)|Détruit un objet Cd2dtextlayout,. (Substitue [CD2DResource, ::D estroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[Cd2dtextlayout, :: obtient](#get)|Retourne l’interface IDWriteTextLayout|
|[Cd2dtextlayout, :: GetFontFamilyName](#getfontfamilyname)|Copie le nom de famille de polices du texte à la position spécifiée.|
|[Cd2dtextlayout, :: GetLocaleName](#getlocalename)|Obtient le nom des paramètres régionaux du texte à la position spécifiée.|
|[Cd2dtextlayout, :: IsValid](#isvalid)|Vérifie la validité des ressources (Substitue [CD2DResource, :: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[Cd2dtextlayout, :: recréer](#recreate)|Recrée un Cd2dtextlayout,. (Substitue [CD2DResource, :: recreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[Cd2dtextlayout, :: SetFontFamilyName](#setfontfamilyname)|Définit le nom de famille de polices se terminant par un caractère null pour le texte dans une plage de texte spécifiée|
|[Cd2dtextlayout, :: SetLocaleName](#setlocalename)|Définit le nom des paramètres régionaux pour le texte dans une plage de texte spécifiée|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dtextlayout, :: Operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Retourne l’interface IDWriteTextLayout|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dtextlayout, :: m_pTextLayout](#m_ptextlayout)|Pointeur vers un IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dtextlayout,](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a> Cd2dtextlayout, :: ~ Cd2dtextlayout,

Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a> Cd2dtextlayout, :: Cd2dtextlayout,

Construit un objet Cd2dtextlayout,.

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*strText*<br/>
Objet CString qui contient la chaîne à partir de laquelle créer un nouvel objet Cd2dtextlayout,.

*textFormat*<br/>
Objet CString qui contient le format à appliquer à la chaîne.

*sizeMax*<br/>
Taille de la zone de disposition.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a> Cd2dtextlayout, :: Create

Crée un Cd2dtextlayout,.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a> Cd2dtextlayout, ::D estroy

Détruit un objet Cd2dtextlayout,.

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a> Cd2dtextlayout, :: obtient

Retourne l’interface IDWriteTextLayout

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a> Cd2dtextlayout, :: GetFontFamilyName

Copie le nom de famille de polices du texte à la position spécifiée.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Paramètres

*currentPosition*<br/>
Position du texte à examiner.

*textRange*<br/>
Plage de texte qui a la même mise en forme que le texte à la position spécifiée par currentPosition. Cela signifie que l’exécution a la mise en forme exacte comme position spécifiée, y compris mais sans s’y limiter, le nom de famille de polices.

### <a name="return-value"></a>Valeur renvoyée

Objet CString qui contient le nom de famille de polices actuel.

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a> Cd2dtextlayout, :: GetLocaleName

Obtient le nom des paramètres régionaux du texte à la position spécifiée.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Paramètres

*currentPosition*<br/>
Position du texte à inspecter.

*textRange*<br/>
Plage de texte qui a la même mise en forme que le texte à la position spécifiée par currentPosition. Cela signifie que l’exécution a la mise en forme exacte comme position spécifiée, y compris mais sans s’y limiter, le nom des paramètres régionaux.

### <a name="return-value"></a>Valeur renvoyée

Objet CString qui contient le nom des paramètres régionaux actuels.

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a> Cd2dtextlayout, :: IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a> Cd2dtextlayout, :: m_pTextLayout

Pointeur vers un IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a> Cd2dtextlayout, :: Operator IDWriteTextLayout *

Retourne l’interface IDWriteTextLayout

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a> Cd2dtextlayout, :: recréer

Recrée un Cd2dtextlayout,.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a> Cd2dtextlayout, :: SetFontFamilyName

Définit le nom de famille de polices se terminant par un caractère null pour le texte dans une plage de texte spécifiée

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Paramètres

*pwzFontFamilyName*<br/>
Nom de famille de polices qui s’applique à la chaîne de texte entière dans la plage spécifiée par textRange

*textRange*<br/>
Plage de texte à laquelle cette modification s’applique

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a> Cd2dtextlayout, :: SetLocaleName

Définit le nom des paramètres régionaux pour le texte dans une plage de texte spécifiée

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Paramètres

*pwzLocaleName*<br/>
Chaîne de nom de paramètres régionaux se terminant par un caractère null

*textRange*<br/>
Plage de texte à laquelle cette modification s’applique

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
