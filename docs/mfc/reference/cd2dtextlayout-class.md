---
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
ms.openlocfilehash: 9be4c1134e2f82ceb3af31cbeb1a7d55f4071777
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369024"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout, classe

Un emballage pour IDWriteTextLayout.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Construit un objet CD2DTextLayout.|
|[CD2DTextLayout: CD2DTextLayout](#_dtorcd2dtextlayout)|Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DTextLayout::Créer](#create)|Crée un CD2DTextLayout. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextLayout::Destroy](#destroy)|Détruit un objet CD2DTextLayout. (Overrides [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextLayout::Get](#get)|Retourne l’interface IDWriteTextLayout|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Copie le nom de famille de la police du texte à la position spécifiée.|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Obtient le nom local du texte à la position spécifiée.|
|[CD2DTextLayout::IsValid](#isvalid)|Vérifie la validité des ressources (Overrides [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextLayout::ReCreate](#recreate)|Re-crée un CD2DTextLayout. (Overrides [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Définit le nom de famille de police non terminé pour le texte dans une plage de texte spécifiée|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Définit le nom local du texte dans une plage de texte spécifiée|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DTextLayout::opérateur IDWriteTextLayout](#operator_idwritetextlayout_star)|Retourne l’interface IDWriteTextLayout|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Un pointeur à un IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout (en anglais)](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a>CD2DTextLayout: CD2DTextLayout

Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a>CD2DTextLayout::CD2DTextLayout

Construit un objet CD2DTextLayout.

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
Un pointeur à la cible de rendu.

*strText (en)*<br/>
Un objet CString qui contient la chaîne pour créer un nouvel objet CD2DTextLayout à partir de.

*textFormat*<br/>
Un objet CString qui contient le format à appliquer sur la chaîne.

*tailleMax*<br/>
La taille de la boîte de mise en page.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a>CD2DTextLayout::Créer

Crée un CD2DTextLayout.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a>CD2DTextLayout::Destroy

Détruit un objet CD2DTextLayout.

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a>CD2DTextLayout::Get

Retourne l’interface IDWriteTextLayout

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextLayout::GetFontFamilyName

Copie le nom de famille de la police du texte à la position spécifiée.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Paramètres

*CurrentPosition (en anglais)*<br/>
La position du texte à examiner.

*Textrange*<br/>
La gamme de texte qui a le même formatage que le texte à la position spécifiée par currentPosition. Cela signifie que l’exécution a le formatage exact comme la position spécifiée, y compris, mais non limité au nom de famille police.

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom de famille de police actuel.

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a>CD2DTextLayout::GetLocaleName

Obtient le nom local du texte à la position spécifiée.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Paramètres

*CurrentPosition (en anglais)*<br/>
La position du texte à inspecter.

*Textrange*<br/>
La gamme de texte qui a le même formatage que le texte à la position spécifiée par currentPosition. Cela signifie que l’exécution a le formatage exact comme la position spécifiée, y compris, mais non limité au nom local.

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom local actuel.

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a>CD2DTextLayout::IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a>CD2DTextLayout::m_pTextLayout

Un pointeur à un IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a>CD2DTextLayout::opérateur IDWriteTextLayout

Retourne l’interface IDWriteTextLayout

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a>CD2DTextLayout::ReCreate

Re-crée un CD2DTextLayout.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a>CD2DTextLayout::SetFontFamilyName

Définit le nom de famille de police non terminé pour le texte dans une plage de texte spécifiée

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Paramètres

*pwzFontFamilyName*<br/>
Le nom de famille de police qui s’applique à l’ensemble de la chaîne de texte dans la plage spécifiée par textRange

*Textrange*<br/>
Gamme de texte à laquelle cette modification s’applique

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a>CD2DTextLayout::SetLocaleName

Définit le nom local du texte dans une plage de texte spécifiée

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Paramètres

*pwzLocaleName*<br/>
Une chaîne de nom local annulée

*Textrange*<br/>
Gamme de texte à laquelle cette modification s’applique

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
