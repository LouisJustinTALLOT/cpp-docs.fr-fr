---
title: Cfontholder, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
dev_langs:
- C++
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 344e2e39e52aa80624e4959daada5038506bb4c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433169"
---
# <a name="cfontholder-class"></a>Cfontholder, classe

Implémente la propriété stock Font et encapsule les fonctionnalités d'un objet police Windows et de l'interface `IFont` .

## <a name="syntax"></a>Syntaxe

```
class CFontHolder
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Construit un objet `CFontHolder`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Récupère la chaîne affichée dans l’Explorateur de propriétés d’un conteneur.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Retourne la police `IDispatch` interface.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Retourne un handle vers une police Windows.|
|[CFontHolder::InitializeFont](#initializefont)|Initialise un `CFontHolder` objet.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Récupère des informations connexes avec la police.|
|[CFontHolder::ReleaseFont](#releasefont)|Déconnecte le `CFontHolder` de l’objet à partir de la `IFont` et `IFontNotification` interfaces.|
|[CFontHolder::Select](#select)|Sélectionne une ressource de police dans un contexte de périphérique.|
|[CFontHolder::SetFont](#setfont)|Se connecte le `CFontHolder` de l’objet à un `IFont` interface.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Un pointeur vers le `CFontHolder` l’objet `IFont` interface.|

## <a name="remarks"></a>Notes

`CFontHolder` n’a pas d’une classe de base.

Utilisez cette classe pour implémenter les propriétés de police personnalisée pour votre contrôle. Pour plus d’informations sur la création de ces propriétés, consultez l’article [contrôles ActiveX : utilisation des polices](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CFontHolder`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxctl.h

##  <a name="cfontholder"></a>  CFontHolder::CFontHolder

Construit un objet `CFontHolder`.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Paramètres

*pNotify*<br/>
Pointeur vers la police `IPropertyNotifySink` interface.

### <a name="remarks"></a>Notes

Vous devez appeler `InitializeFont` pour initialiser l’objet qui en résulte avant de l’utiliser.

##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString

Récupère une chaîne qui peut être affichée dans l’Explorateur de propriétés d’un conteneur.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Paramètres

*strValue*<br/>
Référence à la [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui doit contenir la chaîne d’affichage.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la chaîne est correctement récupérée ; sinon 0.

##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch

Appelez cette fonction pour récupérer un pointeur vers l’interface de dispatch de la police.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `CFontHolder` l’objet `IFontDisp` interface. Notez que la fonction qui appelle `GetFontDispatch` doit appeler `IUnknown::Release` sur ce pointeur d’interface lorsque vous avez terminé avec lui.

### <a name="remarks"></a>Notes

Appelez `InitializeFont` avant d’appeler `GetFontDispatch`.

##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle

Appelez cette fonction pour obtenir un handle à une police Windows.

```
HFONT GetFontHandle();


HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Paramètres

*cyLogical*<br/>
Hauteur, en unités logiques, du rectangle dans lequel le contrôle est dessiné.

*cyHimetric*<br/>
Hauteur, en unités MM_HIMETRIC, du contrôle.

### <a name="return-value"></a>Valeur de retour

Un handle vers l’objet de police ; Sinon, NULL.

### <a name="remarks"></a>Notes

Le rapport entre *cyLogical* et *cyHimetric* est utilisée pour calculer la taille d’affichage approprié, en unités logiques, de la taille de police point exprimé en unités MM_HIMETRIC :

Taille d’affichage = ( *cyLogical* / *cyHimetric*) X taille de police

La version sans paramètres retourne un handle vers une police dimensionnée correctement pour l’écran.

##  <a name="initializefont"></a>  CFontHolder::InitializeFont

Initialise un `CFontHolder` objet.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Paramètres

*pFontDesc*<br/>
Pointeur vers une structure de description de police ( [FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc)) qui spécifie les caractéristiques de la police.

*pFontDispAmbient*<br/>
Pointeur vers la propriété de police ambiante du conteneur.

### <a name="remarks"></a>Notes

Si *pFontDispAmbient* n’est pas NULL, le `CFontHolder` objet est connecté à un clone de le `IFont` interface utilisée par la propriété de police ambiante du conteneur.

Si *pFontDispAmbient* est NULL, une nouvelle police de l’objet est créé à partir de la description de police vers lequel pointe *pFontDesc* ou, si *pFontDesc* est NULL, une valeur par défaut Description.

Appelez cette fonction après avoir construit un `CFontHolder` objet.

##  <a name="m_pfont"></a>  CFontHolder::m_pFont

Un pointeur vers le `CFontHolder` l’objet `IFont` interface.

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics

Récupère des informations sur la police physique représentée par le `CFontHolder` objet.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Paramètres

*lptm*<br/>
Un pointeur vers un [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) structure qui recevra les informations.

##  <a name="releasefont"></a>  CFontHolder::ReleaseFont

Cette fonction se déconnecte le `CFontHolder` de l’objet à partir de son `IFont` interface.

```
void ReleaseFont();
```

##  <a name="select"></a>  CFontHolder::Select

Appelez cette fonction pour sélectionner la police de votre contrôle dans le contexte de périphérique spécifié.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Contexte de périphérique dans lequel la police est sélectionnée.

*cyLogical*<br/>
Hauteur, en unités logiques, du rectangle dans lequel le contrôle est dessiné.

*cyHimetric*<br/>
Hauteur, en unités MM_HIMETRIC, du contrôle.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la police qui est remplacé.

### <a name="remarks"></a>Notes

Consultez [GetFontHandle](#getfonthandle) pour une présentation de la *cyLogical* et *cyHimetric* paramètres.

##  <a name="setfont"></a>  CFontHolder::SetFont

Libère toutes les polices et se connecte le `CFontHolder` de l’objet à un `IFont` interface.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Paramètres

*pNewFont*<br/>
Pointeur vers le nouveau `IFont` interface.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange, classe](../../mfc/reference/cpropexchange-class.md)
