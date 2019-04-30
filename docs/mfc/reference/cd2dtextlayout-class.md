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
ms.openlocfilehash: ca89d12c6aeed33be740aa9f999e7c11d6c32056
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396182"
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
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Construit un objet CD2DTextLayout.|
|[CD2DTextLayout::~CD2DTextLayout](#_dtorcd2dtextlayout)|Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DTextLayout::Create](#create)|Crée un CD2DTextLayout. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextLayout::Destroy](#destroy)|Détruit un objet CD2DTextLayout. (Substitue [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextLayout::Get](#get)|Renvoie l’interface IDWriteTextLayout|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Copie le nom de famille de polices du texte à la position spécifiée.|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Obtient le nom des paramètres régionaux du texte à la position spécifiée.|
|[CD2DTextLayout::IsValid](#isvalid)|Vérifie la validité des ressources (remplace [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextLayout::ReCreate](#recreate)|Recrée un CD2DTextLayout. (Substitue [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Nom de famille de polices se terminant par null de jeux pour du texte dans une plage de texte spécifiée|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Définit le nom de paramètres régionaux pour le texte dans une plage de texte spécifié|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Renvoie l’interface IDWriteTextLayout|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Pointeur vers un IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="_dtorcd2dtextlayout"></a>  CD2DTextLayout::~CD2DTextLayout

Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.

```
virtual ~CD2DTextLayout();
```

##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout

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
Pointeur vers la cible de rendu.

*strText*<br/>
Un objet CString qui contient la chaîne pour créer un nouvel objet CD2DTextLayout à partir de.

*textFormat*<br/>
Un objet CString qui contient le format à appliquer à la chaîne.

*sizeMax*<br/>
La taille de la zone de disposition.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

##  <a name="create"></a>  CD2DTextLayout::Create

Crée un CD2DTextLayout.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="destroy"></a>  CD2DTextLayout::Destroy

Détruit un objet CD2DTextLayout.

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextLayout::Get

Renvoie l’interface IDWriteTextLayout

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.

##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName

Copie le nom de famille de polices du texte à la position spécifiée.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Paramètres

*currentPosition*<br/>
La position du texte à examiner.

*textRange*<br/>
La plage de texte qui a la même mise en forme en tant que le texte à la position spécifiée par la position actuelle. Cela signifie que l’exécution de la mise en forme exacte que la position spécifiée, y compris de manière non limitative, le nom de famille de polices.

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom de famille de polices actuel.

##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName

Obtient le nom des paramètres régionaux du texte à la position spécifiée.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Paramètres

*currentPosition*<br/>
La position du texte à inspecter.

*textRange*<br/>
La plage de texte qui a la même mise en forme en tant que le texte à la position spécifiée par la position actuelle. Cela signifie que l’exécution de la mise en forme exacte que la position spécifiée, y compris de manière non limitative, le nom des paramètres régionaux.

### <a name="return-value"></a>Valeur de retour

Objet CString qui contient le nom des paramètres régionaux en cours.

##  <a name="isvalid"></a>  CD2DTextLayout::IsValid

Vérifications de validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la ressource est valide ; Sinon, FALSE.

##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout

Pointeur vers un IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::operator IDWriteTextLayout*

Renvoie l’interface IDWriteTextLayout

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.

##  <a name="recreate"></a>  CD2DTextLayout::ReCreate

Recrée un CD2DTextLayout.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName

Nom de famille de polices se terminant par null de jeux pour du texte dans une plage de texte spécifiée

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Paramètres

*pwzFontFamilyName*<br/>
Le nom de famille de polices qui s’applique à la chaîne de caractères dans la plage spécifiée par textRange

*textRange*<br/>
Plage de texte à laquelle cette modification s’applique.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE

##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName

Définit le nom de paramètres régionaux pour le texte dans une plage de texte spécifié

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Paramètres

*pwzLocaleName*<br/>
Une chaîne de nom se terminant par null de paramètres régionaux

*textRange*<br/>
Plage de texte à laquelle cette modification s’applique.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
