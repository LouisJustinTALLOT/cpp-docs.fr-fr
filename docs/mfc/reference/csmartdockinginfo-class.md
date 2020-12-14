---
description: 'En savoir plus sur : classe CSmartDockingInfo'
title: CSmartDockingInfo, classe
ms.date: 11/19/2018
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
ms.openlocfilehash: 290f9eef208ceed425739ab26e7811c04309e057
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345132"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo, classe

Définit l'apparence des marqueurs d'ancrage intelligents.

## <a name="syntax"></a>Syntaxe

```
class CSmartDockingInfo : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CSmartDockingInfo::CSmartDockingInfo`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSmartDockingInfo :: CopyTo](#copyto)|Copie les paramètres d’informations d’ancrage actifs actuels dans l’objet [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) fourni.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CSmartDockingInfo :: m_bUseThemeColorInShading](#m_busethemecolorinshading)|Spécifie s’il faut utiliser la couleur de thème actuelle lorsque l’infrastructure affiche des marqueurs d’ancrage intelligents.|
|[CSmartDockingInfo :: m_clrBaseBackground](#m_clrbasebackground)|Spécifie la couleur d’arrière-plan de base des marqueurs d’ancrage intelligents.|
|[CSmartDockingInfo :: m_clrToneDest](#m_clrtonedest)|Spécifie la couleur qui remplace `m_clrToneSrc` dans les bitmaps de marqueurs d’ancrage intelligent.|
|[CSmartDockingInfo :: m_clrToneSrc](#m_clrtonesrc)|Spécifie la couleur des bitmaps du marqueur d’ancrage intelligent.|
|[CSmartDockingInfo :: m_clrTransparent](#m_clrtransparent)|Spécifie la couleur des bitmaps de marqueurs d’ancrage intelligent lorsqu’ils sont transparents.|
|[CSmartDockingInfo :: m_nCentralGroupOffset](#m_ncentralgroupoffset)|Spécifie le décalage du groupe central de marqueurs d’ancrage intelligents à partir des limites du rectangle du groupe central.|
|[CSmartDockingInfo :: m_sizeTotal](#m_sizetotal)|Spécifie la taille totale de tous les marqueurs d’ancrage intelligents dans un groupe.|
|[CSmartDockingInfo :: m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Définit les ID de ressource des bitmaps que le Framework utilise pour les marqueurs d’ancrage intelligent qui ne sont pas mis en surbrillance.|
|[CSmartDockingInfo :: m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Définit les ID de ressource des bitmaps que le Framework utilise pour les marqueurs d’ancrage intelligents qui sont mis en surbrillance.|

## <a name="remarks"></a>Notes

Le Framework gère les marqueurs d’ancrage actifs en interne. L’illustration suivante montre les marqueurs d’ancrage intelligents standard :

![Marqueurs d'ancrage actifs standard](../../mfc/reference/media/nextsdmarkers.png "Marqueurs d'ancrage actifs standard")

Dans cette illustration, l’image sur la gauche affiche un marqueur d’ancrage intelligent de groupe central qui n’a pas d’ancrage sur un onglet activé. L’image du milieu affiche un marqueur d’ancrage intelligent de droite. L’image à droite affiche un marqueur d’ancrage intelligent de groupe central qui est activé pour l’ancrage sur un onglet. Le marqueur d’ancrage intelligent du groupe central a une bitmap principale et cinq bitmaps de marqueurs d’ancrage intelligents.

Vous pouvez personnaliser les paramètres suivants des marqueurs d’ancrage intelligents :

- Couleur. Par exemple, vous pouvez remplacer la couleur bleue des marqueurs dans la figure par toute couleur définie par l’utilisateur.

- Couleur de transparence.

- Décalage d’un marqueur d’ancrage intelligent dans le groupe central à partir de la bordure du rectangle englobant.

- Bitmap principale qui représente le groupe central.

- Bitmaps qui représentent les marqueurs d’ancrage actifs standard et mis en surbrillance.

L’illustration suivante montre un exemple de marqueurs d’ancrage intelligents qui ont été personnalisés :

![Marqueurs d'ancrage actif personnalisés](../../mfc/reference/media/nextsdmarkerscustom.png "Marqueurs d'ancrage actif personnalisés")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxDockingManager. h

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a> CSmartDockingInfo :: CopyTo

Copie les paramètres d’ancrage actifs actuels dans l’objet [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) fourni.

```cpp
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Paramètres

*params*<br/>
à Objet de type `CSmartDockingInfo` qui est rempli avec les paramètres d’ancrage actifs actuels.

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a> CSmartDockingInfo :: m_bUseThemeColorInShading

Spécifie s’il faut utiliser la couleur de thème actuelle lorsque l’infrastructure affiche des marqueurs d’ancrage intelligents.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, les marqueurs sont dessinés à l’aide de la couleur de thème actuelle ; Sinon, les marqueurs sont dessinés avec une couleur bleu clair.

La valeur par défaut est FALSE.

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a> CSmartDockingInfo :: m_clrBaseBackground

Spécifie la couleur d’arrière-plan de base des marqueurs d’ancrage intelligents.

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a> CSmartDockingInfo :: m_clrToneDest

Spécifie la couleur qui sera remplacée `m_clrToneSrc` dans les bitmaps de marqueurs d’ancrage intelligent.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Notes

Définissez cette valeur pour modifier la couleur des bitmaps de marqueur par programmation. Par exemple, si vous souhaitez modifier la couleur des marqueurs standard fournis avec l’infrastructure, définissez cette valeur sur la couleur souhaitée. Par défaut, [CSmartDockingInfo :: m_clrToneSrc](#m_clrtonesrc) a la valeur RGB (61, 123, 241) (couleur bleutée).

Pour modifier la couleur des marqueurs personnalisés, vous devez spécifier à la fois `m_clrToneDest` et `m_clrToneSrc` .

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a> CSmartDockingInfo :: m_clrToneSrc

Spécifie la couleur des bitmaps du marqueur d’ancrage intelligent.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Notes

Définissez cette valeur uniquement lorsque vous souhaitez remplacer la couleur d’un bitmap personnalisé par une autre couleur. Vous n’avez pas besoin de définir cette valeur si vous modifiez la couleur d’un marqueur standard (fourni par l’infrastructure).

Utilisez `(COLORREF)-1` pour conserver un membre du groupe d’ancrage intelligent vide.

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a> CSmartDockingInfo :: m_clrTransparent

Spécifie la couleur des bitmaps de marqueurs d’ancrage intelligent lorsqu’ils sont transparents.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Notes

Vous devez définir cette valeur lorsque vous affichez des marqueurs personnalisés et des bitmaps personnalisées dans le groupe d’ancrage.

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a> CSmartDockingInfo :: m_nCentralGroupOffset

Spécifie l’offset entre le groupe central de marqueurs d’ancrage intelligents et les limites du rectangle du groupe central.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Notes

Spécifiez cette valeur si vous souhaitez modifier le décalage par défaut entre les marqueurs personnalisés et les limites du groupe central des marqueurs d’ancrage intelligents. Le décalage par défaut est de 5 pixels.

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a> CSmartDockingInfo :: m_sizeTotal

Spécifie la taille totale d’un rectangle englobant qui englobe tous les marqueurs d’ancrage intelligents dans le groupe central.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Notes

Défini `m_sizeTotal` sur la taille du rectangle englobant du marqueur de groupe central. Vous devez spécifier cette valeur si vous utilisez des bitmaps personnalisées pour les marqueurs.

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a> CSmartDockingInfo :: m_uiMarkerBmpResID

Définit les ID de ressource des bitmaps utilisés pour les marqueurs d’ancrage intelligents personnalisés non mis en surbrillance.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Notes

Remplissez ce tableau avec les ID de ressource des bitmaps représentant les marqueurs d’ancrage intelligents. AFX_SD_MARKERS_NUM est actuellement défini comme 5. Pour remplir le tableau, procédez comme suit :

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a> CSmartDockingInfo :: m_uiMarkerLightBmpResID

Définit les ID de ressource des bitmaps utilisés pour la mise en surbrillance des marqueurs d’ancrage intelligents personnalisés.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Notes

Remplissez ce tableau avec les ID de ressource des bitmaps représentant les marqueurs d’ancrage actifs mis en surbrillance. AFX_SD_MARKERS_NUM est actuellement défini comme 5. Pour remplir le tableau, procédez comme suit :

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)
