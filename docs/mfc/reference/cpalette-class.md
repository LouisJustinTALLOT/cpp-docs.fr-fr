---
title: CPalette, classe
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
ms.openlocfilehash: 27f4f14c9e93091728e256c890dcffee26a43de4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502999"
---
# <a name="cpalette-class"></a>CPalette, classe

Encapsule une palette de couleurs Windows.

## <a name="syntax"></a>Syntaxe

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|Construit un `CPalette` objet sans palette Windows attachée. Vous devez initialiser l' `CPalette` objet avec l’une des fonctions membres d’initialisation avant de pouvoir l’utiliser.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Remplace les entrées de la palette logique identifiée `CPalette` par l’objet. L’application n’a pas besoin de mettre à jour sa zone client, car Windows mappe immédiatement les nouvelles entrées dans la palette système.|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Crée une palette de demi-teintes pour le contexte de périphérique et `CPalette` l’attache à l’objet.|
|[CPalette::CreatePalette](#createpalette)|Crée une palette de couleurs Windows et l’attache à l' `CPalette` objet.|
|[CPalette::FromHandle](#fromhandle)|Retourne un pointeur vers un `CPalette` objet lorsqu’un handle est fourni à un objet palette Windows.|
|[CPalette::GetEntryCount](#getentrycount)|Récupère le nombre d’entrées de palette dans une palette logique.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Retourne l’index de l’entrée dans la palette logique qui correspond le mieux à une valeur de couleur.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Récupère une plage d’entrées de palette dans une palette logique.|
|[CPalette::ResizePalette](#resizepalette)|Modifie la taille de la palette logique spécifiée par l' `CPalette` objet en spécifiant le nombre d’entrées spécifié.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Définit les valeurs de couleur RVB et les indicateurs d’une plage d’entrées dans une palette logique.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPalette:: Operator HPALETTE](#operator_hpalette)|Retourne le HPALETTE attaché à `CPalette`.|

## <a name="remarks"></a>Notes

Une palette fournit une interface entre une application et un périphérique de sortie couleur (tel qu’un périphérique d’affichage). L’interface permet à l’application de tirer pleinement parti des fonctionnalités de couleur du périphérique de sortie sans interférer gravement avec les couleurs affichées par d’autres applications. Windows utilise la palette logique de l’application (une liste des couleurs nécessaires) et la palette système (qui définit les couleurs disponibles) pour déterminer les couleurs utilisées.

Un `CPalette` objet fournit des fonctions membres pour manipuler la palette référencée par l’objet. Construisez `CPalette` un objet et utilisez ses fonctions membres pour créer la palette réelle, un objet GDI (Graphics Device Interface) et pour manipuler ses entrées et d’autres propriétés.

Pour plus d’informations sur `CPalette`l’utilisation de, consultez [objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="animatepalette"></a>  CPalette::AnimatePalette

Remplace les entrées de la palette logique attachée `CPalette` à l’objet.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Paramètres

*nStartIndex*<br/>
Spécifie la première entrée de la palette à animer.

*nNumEntries*<br/>
Spécifie le nombre d’entrées dans la palette à animer.

*lpPaletteColors*<br/>
Pointe vers le premier membre d’un tableau de structures [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) pour remplacer les entrées de palette identifiées par *nStartIndex* et *nNumEntries*.

### <a name="remarks"></a>Notes

Quand une application appelle `AnimatePalette`, elle n’a pas besoin de mettre à jour sa zone cliente, car Windows mappe immédiatement les nouvelles entrées dans la palette système.

La `AnimatePalette` fonction modifie uniquement les entrées avec l’indicateur PC_RESERVED défini dans le membre `palPaletteEntry` correspondant de la structure [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) jointe à l' `CPalette` objet. Pour plus d’informations sur cette structure, consultez LOGPALETTE dans le SDK Windows.

##  <a name="cpalette"></a>  CPalette::CPalette

Construit un objet `CPalette`.

```
CPalette();
```

### <a name="remarks"></a>Notes

L’objet n’a pas de palette attachée `CreatePalette` tant que vous n’appelez pas pour en joindre un.

##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette

Crée une palette de demi-teintes pour le contexte de périphérique.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Identifie le contexte de périphérique.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Une application doit créer une palette de demi-teintes lorsque le mode d’étirement d’un contexte de périphérique est défini sur des demi-TEINTes. La palette de demi-teintes logique retournée par la fonction membre [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) doit ensuite être sélectionnée et réalisée dans le contexte de périphérique avant l’appel de la fonction [CDC:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) ou [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) .

Pour plus d’informations sur `CreateHalftonePalette` et, `StretchDIBits`consultez la SDK Windows.

##  <a name="createpalette"></a>  CPalette::CreatePalette

Initialise un `CPalette` objet en créant une palette de couleurs logiques Windows et en l’attachant à `CPalette` l’objet.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Paramètres

*lpLogPalette*<br/>
Pointe vers une structure [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) qui contient des informations sur les couleurs dans la palette logique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la `LOGPALETTE` structure, consultez le SDK Windows.

##  <a name="fromhandle"></a>  CPalette::FromHandle

Retourne un pointeur vers un `CPalette` objet lorsqu’un handle est fourni à un objet palette Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Paramètres

*hPalette*<br/>
Handle d’une palette de couleurs Windows GDI.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CPalette` objet en cas de réussite; sinon, null.

### <a name="remarks"></a>Notes

Si un `CPalette` objet n’est pas déjà attaché à la palette Windows, un `CPalette` objet temporaire est créé et attaché. Cet objet `CPalette` temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire est valide uniquement pendant le traitement d’un message de fenêtre.

##  <a name="getentrycount"></a>  CPalette::GetEntryCount

Appelez cette fonction membre pour récupérer le nombre d’entrées dans une palette logique donnée.

```
int GetEntryCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’entrées dans une palette logique.

##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex

Retourne l’index de l’entrée dans la palette logique qui correspond le mieux à la valeur de couleur spécifiée.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Paramètres

*crColor*<br/>
Spécifie la couleur à mettre en correspondance.

### <a name="return-value"></a>Valeur de retour

Index d’une entrée dans une palette logique. L’entrée contient la couleur qui correspond le plus à la couleur spécifiée.

##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries

Récupère une plage d’entrées de palette dans une palette logique.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Paramètres

*nStartIndex*<br/>
Spécifie la première entrée de la palette logique à récupérer.

*nNumEntries*<br/>
Spécifie le nombre d’entrées dans la palette logique à récupérer.

*lpPaletteColors*<br/>
Pointe vers un tableau de structures de données [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) pour recevoir les entrées de palette. Le tableau doit contenir au moins autant de structures de données que ce qui est spécifié par *nNumEntries*.

### <a name="return-value"></a>Valeur de retour

Nombre d’entrées récupérées à partir de la palette logique; 0 si la fonction a échoué.

##  <a name="operator_hpalette"></a>CPalette:: Operator HPALETTE

Utilisez cet opérateur pour récupérer le handle Windows GDI attaché de l' `CPalette` objet.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle vers l’objet Windows GDI représenté par `CPalette` l’objet; sinon, null.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast qui prend en charge l’utilisation directe d’un objet HPALETTE.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez l’article [objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

##  <a name="resizepalette"></a>  CPalette::ResizePalette

Remplace la taille de la palette logique attachée à `CPalette` l’objet par le nombre d’entrées spécifié par *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Paramètres

*nNumEntries*<br/>
Spécifie le nombre d’entrées dans la palette une fois qu’elle a été redimensionnée.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la palette a été redimensionnée avec succès; Sinon, 0.

### <a name="remarks"></a>Notes

Si une application appelle `ResizePalette` pour réduire la taille de la palette, les entrées restantes dans la palette redimensionnée sont inchangées. Si l’application appelle `ResizePalette` pour agrandir la palette, les entrées de palette supplémentaires sont définies sur noir (les valeurs rouge, vert et bleu sont toutes 0) et les indicateurs de toutes les entrées supplémentaires ont la valeur 0.

Pour plus d’informations sur l’API `ResizePalette`Windows, consultez [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) dans le SDK Windows.

##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries

Définit les valeurs de couleur RVB et les indicateurs d’une plage d’entrées dans une palette logique.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Paramètres

*nStartIndex*<br/>
Spécifie la première entrée de la palette logique à définir.

*nNumEntries*<br/>
Spécifie le nombre d’entrées dans la palette logique à définir.

*lpPaletteColors*<br/>
Pointe vers un tableau de structures de données [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) pour recevoir les entrées de palette. Le tableau doit contenir au moins autant de structures de données que ce qui est spécifié par *nNumEntries*.

### <a name="return-value"></a>Valeur de retour

Nombre d’entrées définies dans la palette logique; 0 si la fonction a échoué.

### <a name="remarks"></a>Notes

Si la palette logique est sélectionnée dans un contexte de périphérique lors de l' `SetPaletteEntries`appel de l’application, les modifications ne prendront effet qu’une fois que l’application a appelé [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Pour plus d’informations, consultez [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
