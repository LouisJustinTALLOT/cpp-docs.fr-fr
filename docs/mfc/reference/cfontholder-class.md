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
ms.openlocfilehash: 36fbebc39101c5534bd52d4f79fee5286487a6e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754984"
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
|[CFontHolder::GetDisplayString](#getdisplaystring)|Récupère la chaîne affichée dans le navigateur de propriété d’un conteneur.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Retourne l’interface `IDispatch` de la police.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Retourne une poignée à une police Windows.|
|[CFontHolder::InitializeFont](#initializefont)|Initialise un objet `CFontHolder`.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Récupère des informations pour la police connexe.|
|[CFontHolder::ReleaseFont](#releasefont)|Déconnecte `CFontHolder` l’objet `IFontNotification` de la et des `IFont` interfaces.|
|[CFontHolder::Sélectionner](#select)|Sélectionne une ressource de police dans un contexte d’appareil.|
|[CFontHolder::SetFont](#setfont)|Connecte `CFontHolder` l’objet `IFont` à une interface.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Un pointeur `CFontHolder` sur `IFont` l’interface de l’objet.|

## <a name="remarks"></a>Notes

`CFontHolder`n’a pas de classe de base.

Utilisez cette classe pour implémenter des propriétés de police personnalisées pour votre contrôle. Pour plus d’informations sur la création de telles propriétés, consultez l’article [ActiveX Controls: Using Fonts](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CFontHolder`

## <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder::CFontHolder

Construit un objet `CFontHolder`.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Paramètres

*pNotifier*<br/>
Pointeur sur l’interface de `IPropertyNotifySink` la police.

### <a name="remarks"></a>Notes

Vous devez `InitializeFont` appeler pour initialiser l’objet résultant avant de l’utiliser.

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder::GetDisplayString

Récupère une chaîne qui peut être affichée dans le navigateur de propriété d’un conteneur.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Paramètres

*strValue*<br/>
Référence au [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est de tenir la chaîne d’affichage.

### <a name="return-value"></a>Valeur de retour

Nonzero si la chaîne est récupérée avec succès; sinon 0.

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

Appelez cette fonction pour récupérer un pointeur sur l’interface de répartition de la police.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CFontHolder` sur `IFontDisp` l’interface de l’objet. Notez que la `GetFontDispatch` fonction `IUnknown::Release` que les appels doivent faire appel à ce pointeur d’interface lorsqu’il est fait avec elle.

### <a name="remarks"></a>Notes

Appelez `InitializeFont` avant `GetFontDispatch`d’appeler .

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder::GetFontHandle

Appelez cette fonction pour obtenir une poignée à une police Windows.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Paramètres

*cyLogisme*<br/>
Hauteur, dans les unités logiques, du rectangle dans lequel le contrôle est dessiné.

*cyHimétrique*<br/>
Hauteur, dans MM_HIMETRIC unités, du contrôle.

### <a name="return-value"></a>Valeur de retour

Une poignée à l’objet Font; autrement NULL.

### <a name="remarks"></a>Notes

Le rapport de *cyLogical* et *cyHimetric* est utilisé pour calculer la taille d’affichage appropriée, dans les unités logiques, pour la taille du point de la police exprimée dans MM_HIMETRIC unités:

Taille de l’écran ( *cyLogical* / *cyHimetric*) X taille de police

La version sans paramètres renvoie une poignée à une police de taille correcte pour l’écran.

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder::InitializeFont

Initialise un objet `CFontHolder`.

```cpp
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Paramètres

*pFontDesc (en)*<br/>
Pointeur vers une structure de description de police ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)) qui spécifie les caractéristiques de la police.

*pFontDispAmbient*<br/>
Pointeur vers la propriété Font ambiante du conteneur.

### <a name="remarks"></a>Notes

Si *pFontDispAmbient* n’est `CFontHolder` pas NULL, l’objet est connecté à un clone de l’interface `IFont` utilisée par la propriété Font ambiante du conteneur.

Si *pFontDispAmbient* est NULL, un nouvel objet Font est créé soit à partir de la description de police indiquée par *pFontDesc* ou, si *pFontDesc* est NULL, à partir d’une description par défaut.

Appelez cette fonction après `CFontHolder` la construction d’un objet.

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a>CFontHolder::m_pFont

Un pointeur `CFontHolder` sur `IFont` l’interface de l’objet.

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

Récupère des informations sur la police `CFontHolder` physique représentée par l’objet.

```cpp
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Paramètres

*lptm lptm*<br/>
Un pointeur vers une structure [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) qui recevra l’information.

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a>CFontHolder::ReleaseFont

Cette fonction déconnecte `CFontHolder` `IFont` l’objet de son interface.

```cpp
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a>CFontHolder::Sélectionner

Appelez cette fonction pour sélectionner la police de votre contrôle dans le contexte de l’appareil spécifié.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Contexte de l’appareil dans lequel la police est sélectionnée.

*cyLogisme*<br/>
Hauteur, dans les unités logiques, du rectangle dans lequel le contrôle est dessiné.

*cyHimétrique*<br/>
Hauteur, dans MM_HIMETRIC unités, du contrôle.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la police qui est remplacé.

### <a name="remarks"></a>Notes

Voir [GetFontHandle](#getfonthandle) pour une discussion sur les paramètres *cyLogical* et *cyHimetric.*

## <a name="cfontholdersetfont"></a><a name="setfont"></a>CFontHolder::SetFont

Communiqués toute police existante `CFontHolder` et `IFont` connecte l’objet à une interface.

```cpp
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Paramètres

*pNewFont*<br/>
Pointeur vers `IFont` la nouvelle interface.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CPropExchange](../../mfc/reference/cpropexchange-class.md)
