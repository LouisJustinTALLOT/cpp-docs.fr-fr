---
title: CMFCToolBarInfo, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: 593d1665751f7322fc2a9cee307620df88d46876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376194"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo, classe

Contient les ID de ressources des images de barre d'outils dans différents états. `CMFCToolBarInfo`est une classe d’aide qui est utilisée comme paramètre de la méthode [CMFCToolBar:LoadToolBarEx.](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarInfo
```

## <a name="members"></a>Membres

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarInfo:m_uiColdResID](#m_uicoldresid)|Id de ressources de la bitmap de barre d’outils qui contient des images régulières (froides) de barre d’outils.|
|[CMFCToolBarInfo:m_uiDisabledResID](#m_uidisabledresid)|Id de ressources de la bitmap de barre d’outils qui contient des images désactivées de barre d’outils.|
|[CMFCToolBarInfo:m_uiHotResID](#m_uihotresid)|Id de ressources de la bitmap de barre d’outils qui contient des images sélectionnées (chaudes) de barre d’outils.|
|[CMFCToolBarInfo:m_uiLargeColdResID](#m_uilargecoldresid)|Id de ressource de la bitmap de barre d’outils qui contient de grandes images régulières de barre d’outils.|
|[CMFCToolBarInfo:m_uiLargeDisabledResID](#m_uilargedisabledresid)|Id de ressources de la bitmap de barre d’outils qui contient de grandes images de barre d’outils désactivées.|
|[CMFCToolBarInfo:m_uiLargeHotResID](#m_uilargehotresid)|Id de ressources de la bitmap de barre d’outils qui contient de grandes images sélectionnées de barre d’outils.|
|[CMFCToolBarInfo:m_uiMenuDisabledResID](#m_uimenudisabledresid)|Id de ressources de la bitmap barre d’outils qui contient des images de menu désactivées.|
|[CMFCToolBarInfo:m_uiMenuResID](#m_uimenuresid)|Id de ressources de la bitmap barre d’outils qui contient des images de menu.|

## <a name="remarks"></a>Notes

Un bitmap de barre d’outils complet se compose de petites images de barre d’outils (boutons) d’une taille fixe. Chaque pièce d’identité `CMFCToolBarInfo` de ressource stockée dans un objet est un bitmap qui contient un ensemble complet d’images de barres d’outils dans un seul état (par exemple, sélectionnés, désactivés, grands ou images de menu).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbar.h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarInfo:m_uiColdResID

Spécifie un identifiant de ressource pour toutes les images bouton régulières d’une barre d’outils.

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarInfo:m_uiDisabledResID

Spécifie un identifiant de ressource pour les images bouton-indisponibles d’une barre d’outils.

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarInfo:m_uiHotResID

Spécifie un identifiant de ressource pour toutes les images bouton surlignées d’une barre d’outils.

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo:m_uiLargeColdResID

Spécifie un identifiant de ressource pour toutes les grandes images régulières de bouton d’une barre d’outils.

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo:m_uiLargeDisabledResID

Spécifie une pièce d’identité de ressource pour toutes les grandes images de boutons désactivées d’une barre d’outils.

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo:m_uiLargeHotResID

Spécifie une pièce d’identité de ressource pour toutes les grandes images en surbrillance d’une barre d’outils.

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarInfo:m_uiMenuDisabledResID

Précise une pièce d’identité de ressource pour les images de commande indisponibles d’une barre d’outils.

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarInfo:m_uiMenuResID

Spécifie une pièce d’identité de ressource pour toutes les images régulières d’élément de menu d’une barre d’outils.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
