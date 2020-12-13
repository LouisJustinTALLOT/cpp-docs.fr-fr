---
description: 'En savoir plus sur : classe CMFCToolBarInfo'
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
ms.openlocfilehash: 9b85ef4f39c8b42c35975a15836a21e7cc6dd6b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331704"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo, classe

Contient les ID de ressources des images de barre d'outils dans différents états. `CMFCToolBarInfo` est une classe d’assistance utilisée comme paramètre de la méthode [CMFCToolBar :: LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) .

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarInfo
```

## <a name="members"></a>Membres

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarInfo :: m_uiColdResID](#m_uicoldresid)|ID de ressource de la bitmap de la barre d’outils qui contient les images de barre d’outils normales (froides).|
|[CMFCToolBarInfo :: m_uiDisabledResID](#m_uidisabledresid)|ID de ressource de la bitmap de la barre d’outils qui contient les images de barre d’outils désactivées.|
|[CMFCToolBarInfo :: m_uiHotResID](#m_uihotresid)|ID de ressource de la bitmap de la barre d’outils qui contient les images de barre d’outils (à chaud) sélectionnées.|
|[CMFCToolBarInfo :: m_uiLargeColdResID](#m_uilargecoldresid)|ID de ressource de la bitmap de la barre d’outils qui contient des images de barre d’outils volumineuses et normales.|
|[CMFCToolBarInfo :: m_uiLargeDisabledResID](#m_uilargedisabledresid)|ID de ressource de la bitmap de barre d’outils qui contient des images de barre d’outils volumineuses et désactivées.|
|[CMFCToolBarInfo :: m_uiLargeHotResID](#m_uilargehotresid)|ID de ressource de la bitmap de barre d’outils qui contient les images de barre d’outils volumineuses sélectionnées.|
|[CMFCToolBarInfo :: m_uiMenuDisabledResID](#m_uimenudisabledresid)|ID de ressource de la bitmap de la barre d’outils qui contient les images de menu désactivées.|
|[CMFCToolBarInfo :: m_uiMenuResID](#m_uimenuresid)|ID de ressource de la bitmap de la barre d’outils qui contient des images de menu.|

## <a name="remarks"></a>Notes

Une image bitmap de barre d’outils complète se compose de petites images de barre d’outils (boutons) d’une taille fixe. Chaque ID de ressource stocké dans un `CMFCToolBarInfo` objet est une image bitmap qui contient un ensemble complet d’images de barre d’outils dans un seul État (par exemple, les images sélectionnées, désactivées, volumineuses ou de menus).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbar. h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a> CMFCToolBarInfo :: m_uiColdResID

Spécifie un ID de ressource pour toutes les images de bouton normales d’une barre d’outils.

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a> CMFCToolBarInfo :: m_uiDisabledResID

Spécifie un ID de ressource pour les images de bouton non disponibles d’une barre d’outils.

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a> CMFCToolBarInfo :: m_uiHotResID

Spécifie un ID de ressource pour toutes les images de bouton mises en surbrillance d’une barre d’outils.

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a> CMFCToolBarInfo :: m_uiLargeColdResID

Spécifie un ID de ressource pour toutes les grandes images de bouton normales d’une barre d’outils.

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a> CMFCToolBarInfo :: m_uiLargeDisabledResID

Spécifie un ID de ressource pour toutes les grandes images de bouton désactivées d’une barre d’outils.

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a> CMFCToolBarInfo :: m_uiLargeHotResID

Spécifie un ID de ressource pour toutes les grandes images en surbrillance d’une barre d’outils.

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a> CMFCToolBarInfo :: m_uiMenuDisabledResID

Spécifie un ID de ressource pour les images de commande non disponibles d’une barre d’outils.

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a> CMFCToolBarInfo :: m_uiMenuResID

Spécifie un ID de ressource pour toutes les images d’élément de menu normales d’une barre d’outils.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)
