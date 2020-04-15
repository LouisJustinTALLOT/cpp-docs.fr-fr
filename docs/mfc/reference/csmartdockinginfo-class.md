---
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
ms.openlocfilehash: c0ccb9f728add37230cbfd88cc8f6c9b1696fa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318226"
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
|[CSmartDockingInfo::CopyTo](#copyto)|Copie les paramètres d’information d’amarrage intelligents actuels dans l’objet [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) fourni.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CSmartDockingInfo:m_bUseThemeColorInShading](#m_busethemecolorinshading)|Précise s’il faut utiliser la couleur de thème actuelle lorsque le cadre affiche des marqueurs d’amarrage intelligents.|
|[CSmartDockingInfo:m_clrBaseBackground](#m_clrbasebackground)|Spécifie la couleur de fond de base des marqueurs d’amarrage intelligents.|
|[CSmartDockingInfo:m_clrToneDest](#m_clrtonedest)|Specifie la couleur `m_clrToneSrc` qui remplace dans les bitmaps marqueur d’amarrage intelligent.|
|[CSmartDockingInfo:m_clrToneSrc](#m_clrtonesrc)|Specifie la couleur des bitmaps de marqueur d’amarrage intelligents.|
|[CSmartDockingInfo:m_clrTransparent](#m_clrtransparent)|Spécifie la couleur des bitmaps de marqueur d’amarrage intelligents lorsqu’ils sont transparents.|
|[CSmartDockingInfo:m_nCentralGroupOffset](#m_ncentralgroupoffset)|Spécifie le décalage du groupe central de marqueurs d’amarrage intelligents des limites du rectangle du groupe central.|
|[CSmartDockingInfo:m_sizeTotal](#m_sizetotal)|Spécifie la taille totale de tous les marqueurs d’amarrage intelligents dans un groupe.|
|[CSmartDockingInfo:m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Définit les cartes d’ID de ressource des bitmaps que le cadre utilise pour les marqueurs d’amarrage intelligents qui ne sont pas mis en évidence.|
|[CSmartDockingInfo:m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Définit les cartes d’ID de ressource des bitmaps que le cadre utilise pour les marqueurs d’amarrage intelligents qui sont mis en évidence.|

## <a name="remarks"></a>Notes

Le cadre gère les marqueurs d’amarrage intelligents à l’interne. L’illustration suivante montre les marqueurs d’amarrage intelligents standard :

![Marqueurs d'ancrage actifs standard](../../mfc/reference/media/nextsdmarkers.png "Marqueurs d'ancrage actifs standard")

Dans ce chiffre, l’image de gauche montre un marqueur d’amarrage intelligent du groupe central qui n’a pas d’amarrage à un onglet activé. L’image au milieu montre un marqueur d’amarrage intelligent de bord droit. L’image de droite montre un marqueur d’amarrage intelligent du groupe central qui accoste à un onglet activé. Le marqueur d’amarrage intelligent du groupe central a une bitmap principale et cinq bitmaps marqueur d’amarrage intelligent.

Vous pouvez personnaliser les paramètres suivants des marqueurs d’amarrage intelligents :

- Couleur. Par exemple, vous pouvez remplacer la couleur bleue des marqueurs de la figure par n’importe quelle couleur définie par l’utilisateur.

- Couleur de transparence.

- Décalage d’un marqueur d’amarrage intelligent dans le groupe central de la bordure du rectangle de délimitation.

- La bitmap principale qui représente le groupe central.

- Les bitmaps qui représentent les marqueurs d’amarrage intelligents réguliers et mis en évidence.

L’illustration suivante montre un exemple de marqueurs d’amarrage intelligents qui ont été personnalisés :

![Marqueurs d'ancrage actif personnalisés](../../mfc/reference/media/nextsdmarkerscustom.png "Marqueurs d'ancrage actif personnalisés")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxDockingManager.h

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a>CSmartDockingInfo::CopyTo

Copie les paramètres d’amarrage intelligents actuels dans l’objet [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) fourni.

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Paramètres

*params*<br/>
[out] Un objet `CSmartDockingInfo` de type qui est peuplé des paramètres d’amarrage intelligents actuels.

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a>CSmartDockingInfo:m_bUseThemeColorInShading

Précise s’il faut utiliser la couleur de thème actuelle lorsque le cadre affiche des marqueurs d’amarrage intelligents.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Notes

Si VRAI, les marqueurs sont dessinés en utilisant la couleur de thème actuelle; sinon les marqueurs sont dessinés avec une couleur bleu clair.

La valeur par défaut est FALSE.

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a>CSmartDockingInfo:m_clrBaseBackground

Spécifie la couleur de fond de base des marqueurs d’amarrage intelligents.

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a>CSmartDockingInfo:m_clrToneDest

Specifie la couleur `m_clrToneSrc` qui remplacera dans les bitmaps marqueur d’amarrage intelligent.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Notes

Définissez cette valeur pour changer la couleur des bitmaps marqueurs programmatiquement. Par exemple, si vous voulez changer la couleur des marqueurs standard fournis avec le cadre, définissez cette valeur à la couleur désirée. Par défaut, [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) est réglé sur RGB (61, 123, 241) (une couleur bleutée).

Pour changer la couleur des marqueurs `m_clrToneDest` personnalisés, vous devez spécifier à la fois et `m_clrToneSrc`.

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a>CSmartDockingInfo:m_clrToneSrc

Specifie la couleur des bitmaps de marqueur d’amarrage intelligents.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Notes

Définissez cette valeur seulement lorsque vous voulez remplacer la couleur d’une bitmap personnalisée par une autre couleur. Vous n’avez pas à définir cette valeur si vous modifiez la couleur d’un marqueur standard (cadre fourni).

Utilisez `(COLORREF)-1` pour laisser un membre du groupe d’amarrage intelligent vide.

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a>CSmartDockingInfo:m_clrTransparent

Spécifie la couleur des bitmaps de marqueur d’amarrage intelligents lorsqu’ils sont transparents.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Notes

Vous devez définir cette valeur lorsque vous affichez des marqueurs personnalisés et des bitmaps personnalisés dans le groupe d’amarrage.

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a>CSmartDockingInfo:m_nCentralGroupOffset

Spécifie le décalage entre le groupe central de marqueurs d’amarrage intelligents et les limites du rectangle du groupe central.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Notes

Spécifiez cette valeur si vous souhaitez modifier le décalage par défaut entre les marqueurs personnalisés et les limites du groupe central de marqueurs d’amarrage intelligents. Le décalage par défaut est de 5 pixels.

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a>CSmartDockingInfo:m_sizeTotal

Spécifie la taille totale d’un rectangle de délimitation qui enferme tous les marqueurs d’amarrage intelligents dans le groupe central.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Notes

Réglé `m_sizeTotal` à la taille du rectangle de délimitation du marqueur central du groupe. Vous devez spécifier cette valeur si vous utilisez des bitmaps personnalisés pour les marqueurs.

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a>CSmartDockingInfo:m_uiMarkerBmpResID

Définit les cartes d’ID de ressource des bitmaps qui sont utilisées pour les marqueurs d’amarrage intelligents personnalisés non mis en évidence.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Notes

Remplissez ce tableau avec les cartes d’Œuvre de ressources des bitmaps représentant les marqueurs d’amarrage intelligents. AFX_SD_MARKERS_NUM est actuellement défini comme 5. Vous remplissez le tableau comme suit :

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a>CSmartDockingInfo:m_uiMarkerLightBmpResID

Définit les cartes d’ID de ressource des bitmaps qui sont utilisées pour les marqueurs d’amarrage intelligents personnalisés mis en évidence.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Notes

Remplissez ce tableau avec les cartes d’Œuvre de ressources des bitmaps représentant les marqueurs d’amarrage intelligents mis en évidence. AFX_SD_MARKERS_NUM est actuellement défini comme 5. Vous remplissez le tableau comme suit :

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
[Classe CObject](../../mfc/reference/cobject-class.md)
