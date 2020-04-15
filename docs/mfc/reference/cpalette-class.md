---
title: Classe CPalette
ms.date: 11/04/2016
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
ms.openlocfilehash: 83cd125fa7ab64aa39c606bc048022400d158e72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374760"
---
# <a name="cpalette-class"></a>Classe CPalette

Encapsule une palette de couleurs Windows.

## <a name="syntax"></a>Syntaxe

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|Construit un `CPalette` objet sans palette Windows attachée. Vous devez initialiser l’objet `CPalette` avec l’une des fonctions de membre de initialisation avant qu’il puisse être utilisé.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Remplace les entrées dans la `CPalette` palette logique identifiée par l’objet. L’application n’a pas à mettre à jour sa zone client, parce que Windows cartographie les nouvelles entrées dans la palette du système immédiatement.|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Crée une palette de demi-teinte pour le `CPalette` contexte de l’appareil et l’attache à l’objet.|
|[CPalette::CreatePalette](#createpalette)|Crée une palette de couleurs Windows `CPalette` et la fixe à l’objet.|
|[CPalette::DeHandle](#fromhandle)|Retourne un pointeur à un `CPalette` objet lorsqu’on lui donne une poignée à un objet de palette Windows.|
|[CPalette::GetEntryCount](#getentrycount)|Récupère le nombre d’entrées de palette dans une palette logique.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Retourne l’index de l’entrée dans la palette logique qui correspond le plus étroitement à une valeur de couleur.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Récupère une gamme d’entrées de palette dans une palette logique.|
|[CPalette::ResizePalette](#resizepalette)|Modifie la taille de la `CPalette` palette logique spécifiée par l’objet sur le nombre spécifié d’entrées.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Définit les valeurs de couleur RGB et les drapeaux dans une gamme d’entrées dans une palette logique.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPalette::opérateur HPALETTE](#operator_hpalette)|Retourne le HPALETTE `CPalette`attaché à la .|

## <a name="remarks"></a>Notes

Une palette fournit une interface entre une application et un dispositif de sortie de couleur (comme un dispositif d’affichage). L’interface permet à l’application de profiter pleinement des capacités de couleur du périphérique de sortie sans interférer gravement avec les couleurs affichées par d’autres applications. Windows utilise la palette logique de l’application (une liste de couleurs nécessaires) et la palette du système (qui définit les couleurs disponibles) pour déterminer les couleurs utilisées.

Un `CPalette` objet fournit des fonctions de membre pour manipuler la palette mentionnée par l’objet. Construisez `CPalette` un objet et utilisez ses fonctions de membre pour créer la palette réelle, un objet d’interface graphique (GDI), et pour manipuler ses entrées et autres propriétés.

Pour plus d’informations sur l’utilisation `CPalette`, voir Objets [graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette::AnimatePalette

Remplace les entrées dans la `CPalette` palette logique attachée à l’objet.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Paramètres

*nStartIndex*<br/>
Spécifie la première entrée dans la palette à être animée.

*nNumEntries (en)*<br/>
Spécifie le nombre d’entrées dans la palette à animer.

*lpPaletteColors*<br/>
Points au premier membre d’un tableau de structures [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) pour remplacer les entrées de palette identifiées par *nStartIndex* et *nNumEntries*.

### <a name="remarks"></a>Notes

Lorsqu’une `AnimatePalette`application appelle, il n’a pas à mettre à jour sa zone client, parce que Windows cartographie les nouvelles entrées dans la palette du système immédiatement.

La `AnimatePalette` fonction ne modifiera les entrées qu’avec `palPaletteEntry` le drapeau PC_RESERVED fixé dans le `CPalette` membre correspondant de la structure [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) qui est attaché à l’objet. Voir LOGPALETTE dans le Windows SDK pour plus d’informations sur cette structure.

## <a name="cpalettecpalette"></a><a name="cpalette"></a>CPalette::CPalette

Construit un objet `CPalette`.

```
CPalette();
```

### <a name="remarks"></a>Notes

L’objet n’a pas `CreatePalette` de palette attachée jusqu’à ce que vous appeliez pour en attacher un.

## <a name="cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette::CreateHalftonePalette

Crée une palette de demi-teinte pour le contexte de l’appareil.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Identifie le contexte de l’appareil.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Une application doit créer une palette d’étirement lorsque le mode d’étirement d’un contexte d’appareil est réglé sur HALFTONE. La palette d’ampnalité logique retournée par la fonction membre [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) doit alors être sélectionnée et réalisée dans le contexte de l’appareil avant que la fonction [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) ou [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) fonction est appelé.

Voir le Windows SDK `CreateHalftonePalette` pour `StretchDIBits`plus d’informations sur et .

## <a name="cpalettecreatepalette"></a><a name="createpalette"></a>CPalette::CreatePalette

Initialise un `CPalette` objet en créant une palette de couleurs `CPalette` logiques Windows et en l’attachant à l’objet.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Paramètres

*lpLogPalette*<br/>
Points à une structure [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) qui contient des informations sur les couleurs dans la palette logique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Consultez le Windows SDK pour `LOGPALETTE` plus d’informations sur la structure.

## <a name="cpalettefromhandle"></a><a name="fromhandle"></a>CPalette::DeHandle

Retourne un pointeur à un `CPalette` objet lorsqu’on lui donne une poignée à un objet de palette Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Paramètres

*hPalette (en)*<br/>
Une poignée à une palette de couleurs Windows GDI.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CPalette` à un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si `CPalette` un objet n’est pas déjà `CPalette` attaché à la palette Windows, un objet temporaire est créé et joint. Cet `CPalette` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire n’est valable que pendant le traitement d’un message de fenêtre.

## <a name="cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette::GetEntryCount

Appelez cette fonction de membre pour récupérer le nombre d’entrées dans une palette logique donnée.

```
int GetEntryCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’entrées dans une palette logique.

## <a name="cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex

Retourne l’index de l’entrée dans la palette logique qui correspond le plus étroitement à la valeur de couleur spécifiée.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Paramètres

*crColor (en)*<br/>
Spécifie la couleur à apparier.

### <a name="return-value"></a>Valeur de retour

L’index d’une entrée dans une palette logique. L’entrée contient la couleur qui correspond presque à la couleur spécifiée.

## <a name="cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette::GetPaletteEntries

Récupère une gamme d’entrées de palette dans une palette logique.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Paramètres

*nStartIndex*<br/>
Spécifie la première entrée dans la palette logique à récupérer.

*nNumEntries (en)*<br/>
Spécifie le nombre d’entrées dans la palette logique à récupérer.

*lpPaletteColors*<br/>
Indique un éventail de structures de données [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) pour recevoir les entrées de palette. Le tableau doit contenir au moins autant de structures de données que spécifié par *nNumEntries*.

### <a name="return-value"></a>Valeur de retour

Le nombre d’entrées récupérées dans la palette logique; 0 si la fonction a échoué.

## <a name="cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette::opérateur HPALETTE

Utilisez cet opérateur pour obtenir la poignée `CPalette` Windows GDI attachée de l’objet.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, une poignée à `CPalette` l’objet GDI Windows représenté par l’objet; autrement NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de coulée, qui prend en charge l’utilisation directe d’un objet HPALETTE.

Pour plus d’informations sur l’utilisation d’objets graphiques, voir l’article [Objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

## <a name="cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette::ResizePalette

Modifie la taille de la `CPalette` palette logique attachée à l’objet au nombre d’entrées spécifiées par *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Paramètres

*nNumEntries (en)*<br/>
Spécifie le nombre d’entrées dans la palette après qu’elle a été resized.

### <a name="return-value"></a>Valeur de retour

Nonzero si la palette a été resized avec succès; sinon 0.

### <a name="remarks"></a>Notes

Si une `ResizePalette` application appelle pour réduire la taille de la palette, les entrées restantes dans la palette ressétisée sont inchangées. Si l’application appelle `ResizePalette` à agrandir la palette, les entrées de palette supplémentaires sont réglées en noir (les valeurs rouges, vertes et bleues sont toutes 0), et les drapeaux pour toutes les entrées supplémentaires sont réglés à 0.

Pour plus d’informations `ResizePalette`sur l’API Windows , voir [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) dans le SDK Windows.

## <a name="cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette::SetPaletteEntries

Définit les valeurs de couleur RGB et les drapeaux dans une gamme d’entrées dans une palette logique.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Paramètres

*nStartIndex*<br/>
Spécifie la première entrée dans la palette logique à définir.

*nNumEntries (en)*<br/>
Spécifie le nombre d’entrées dans la palette logique à définir.

*lpPaletteColors*<br/>
Indique un éventail de structures de données [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) pour recevoir les entrées de palette. Le tableau doit contenir au moins autant de structures de données que spécifié par *nNumEntries*.

### <a name="return-value"></a>Valeur de retour

Le nombre d’entrées placées dans la palette logique; 0 si la fonction a échoué.

### <a name="remarks"></a>Notes

Si la palette logique est sélectionnée dans `SetPaletteEntries`un contexte d’appareil lorsque l’application appelle, les modifications n’entreront pas en vigueur jusqu’à ce que l’application appelle [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Pour plus d’informations, voir [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) dans windows SDK.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
