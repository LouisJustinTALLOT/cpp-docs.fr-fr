---
title: Cmfctoolbarinfo, classe
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
ms.openlocfilehash: e1e460fe3efb5401227e91f49d8f7c4f6689fa27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651163"
---
# <a name="cmfctoolbarinfo-class"></a>Cmfctoolbarinfo, classe

Contient les ID de ressources des images de barre d'outils dans différents états. `CMFCToolBarInfo` est une classe d’assistance qui est utilisée en tant que paramètre de la [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) (méthode).

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarInfo
```

## <a name="members"></a>Membres

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|ID de ressource de la bitmap de barre d’outils qui contient des images de barre d’outils (à froid) régulière.|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|ID de ressource de la bitmap de barre d’outils qui contient des images de barre d’outils désactivées.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|ID de ressource de la bitmap de barre d’outils qui contient des images de barre d’outils (chaud) sélectionné.|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|ID de ressource de la bitmap de barre d’outils qui contient des images de barre d’outils régulières et volumineux.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|ID de ressource de la bitmap de barre d’outils qui contient un grand, désactivé les images de barre d’outils.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|ID de ressource de la bitmap de barre d’outils qui contient des images de barre d’outils de grande taille, sélectionné.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|ID de ressource de la bitmap de barre d’outils qui contient les images de menu désactivé.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|ID de ressource de la bitmap de barre d’outils qui contient les images de menu.|

## <a name="remarks"></a>Notes

Une image bitmap de barre d’outils complète se compose d’images de petite barre d’outils (boutons) d’une taille fixe. Chaque ID de ressource qui est stocké dans un `CMFCToolBarInfo` objet est une image bitmap qui contient un ensemble complet d’images de barre d’outils dans un état unique (par exemple, sélectionné, les désactivé, grande ou les images de menu).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtoolbar.h

##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID

Spécifie un ID de ressource pour toutes les images de bouton standard d’une barre d’outils.

```
UINT m_uiColdResID;
```

##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID

Spécifie un ID de ressource pour les images non disponible de bouton de barre d’outils.

```
UINT m_uiDisabledResID;
```

##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID

Spécifie un ID de ressource pour toutes les images de bouton mis en surbrillance d’une barre d’outils.

```
UINT m_uiHotResID
```

##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID

Spécifie un ID de ressource pour toutes les images de grand bouton régulière d’une barre d’outils.

```
UINT m_uiLargeColdResID
```

##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID

Spécifie un ID de ressource pour toutes les images de grand bouton désactivé d’une barre d’outils.

```
UINT m_uiLargeDisabledResID;
```

##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID

Spécifie un ID de ressource pour toutes les images volumineux en surbrillance d’une barre d’outils.

```
UINT m_uiLargeHotResID;
```

##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID

Spécifie un ID de ressource pour les images non disponible de commande d’une barre d’outils.

```
UINT m_uiMenuDisabledResID;
```

##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID

Spécifie un ID de ressource pour toutes les images d’élément de menu standard d’une barre d’outils.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)
