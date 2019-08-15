---
title: CFontHolder, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 04de8141469f82bdd1fbb6adc1bae94d6026324c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506443"
---
# <a name="cfontholder-class"></a>CFontHolder, classe

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
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Retourne l’interface de `IDispatch` la police.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Retourne un handle vers une police Windows.|
|[CFontHolder::InitializeFont](#initializefont)|Initialise un `CFontHolder` objet.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Récupère des informations pour la police associée.|
|[CFontHolder::ReleaseFont](#releasefont)|Déconnecte l' `CFontHolder` objet `IFont` des interfaces et `IFontNotification` .|
|[CFontHolder:: SELECT](#select)|Sélectionne une ressource de police dans un contexte de périphérique.|
|[CFontHolder::SetFont](#setfont)|Connecte `CFontHolder` l’objet à `IFont` une interface.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Pointeur vers l’interface `CFontHolder` de `IFont` l’objet.|

## <a name="remarks"></a>Notes

`CFontHolder`n’a pas de classe de base.

Utilisez cette classe pour implémenter des propriétés de police personnalisées pour votre contrôle. Pour plus d’informations sur la création de ces propriétés [, consultez l’article contrôles ActiveX: Utilisation des](../../mfc/mfc-activex-controls-using-fonts.md)polices.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CFontHolder`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxctl. h

##  <a name="cfontholder"></a>  CFontHolder::CFontHolder

Construit un objet `CFontHolder`.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Paramètres

*pNotify*<br/>
Pointeur vers l’interface de `IPropertyNotifySink` la police.

### <a name="remarks"></a>Notes

Vous devez appeler `InitializeFont` pour initialiser l’objet obtenu avant de l’utiliser.

##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString

Récupère une chaîne qui peut être affichée dans l’Explorateur de propriétés d’un conteneur.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Paramètres

*strValue*<br/>
Référence à la [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui doit contenir la chaîne d’affichage.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la chaîne est récupérée avec succès; Sinon, 0.

##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch

Appelez cette fonction pour récupérer un pointeur vers l’interface de dispatch de la police.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface `CFontHolder` de `IFontDisp` l’objet. Notez que la fonction qui appelle `GetFontDispatch` doit appeler `IUnknown::Release` sur ce pointeur d’interface lorsqu’elle est terminée.

### <a name="remarks"></a>Notes

Appelez `InitializeFont` avant d' `GetFontDispatch`appeler.

##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle

Appelez cette fonction pour obtenir un handle vers une police Windows.

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

Handle de l’objet font; Sinon, NULL.

### <a name="remarks"></a>Notes

Le ratio *cyLogical* et *cyHimetric* est utilisé pour calculer la taille d’affichage appropriée, en unités logiques, pour la taille de point de la police exprimée en unités MM_HIMETRIC:

Taille d’affichage = ( *cyLogical* / *cyHimetric*) X taille de police

La version sans paramètres retourne un handle à une police correctement dimensionnée pour l’écran.

##  <a name="initializefont"></a>  CFontHolder::InitializeFont

Initialise un `CFontHolder` objet.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Paramètres

*pFontDesc*<br/>
Pointeur vers une structure de description de police ( [fontdesc](/windows/win32/api/olectl/ns-olectl-fontdesc)) qui spécifie les caractéristiques de la police.

*pFontDispAmbient*<br/>
Pointeur vers la propriété de police ambiante du conteneur.

### <a name="remarks"></a>Notes

Si *pFontDispAmbient* n’a pas la valeur `CFontHolder` null, l’objet est connecté à un `IFont` clone de l’interface utilisée par la propriété de police ambiante du conteneur.

Si *pFontDispAmbient* a la valeur null, un nouvel objet font est créé à partir de la description de la police désignée par *pFontDesc* ou, si *pFontDesc* est null, à partir d’une description par défaut.

Appelez cette fonction après avoir construit un `CFontHolder` objet.

##  <a name="m_pfont"></a>  CFontHolder::m_pFont

Pointeur vers l’interface `CFontHolder` de `IFont` l’objet.

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics

Récupère des informations sur la police physique représentée par l' `CFontHolder` objet.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Paramètres

*lptm*<br/>
Pointeur vers une structure [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) qui recevra les informations.

##  <a name="releasefont"></a>  CFontHolder::ReleaseFont

Cette fonction déconnecte l' `CFontHolder` objet de son `IFont` interface.

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

*pDC*<br/>
Contexte de périphérique dans lequel la police est sélectionnée.

*cyLogical*<br/>
Hauteur, en unités logiques, du rectangle dans lequel le contrôle est dessiné.

*cyHimetric*<br/>
Hauteur, en unités MM_HIMETRIC, du contrôle.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la police qui est remplacée.

### <a name="remarks"></a>Notes

Consultez [GetFontHandle](#getfonthandle) pour en savoir plus sur les paramètres *cyLogical* et *cyHimetric* .

##  <a name="setfont"></a>  CFontHolder::SetFont

Libère toutes les polices existantes et connecte l' `CFontHolder` objet à une `IFont` interface.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Paramètres

*pNewFont*<br/>
Pointeur vers la nouvelle `IFont` interface.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange, classe](../../mfc/reference/cpropexchange-class.md)
