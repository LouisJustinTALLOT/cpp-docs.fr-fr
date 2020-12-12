---
description: 'En savoir plus sur : classe Cmfctaskspanetask,'
title: Cmfctaskspanetask,, classe
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
ms.openlocfilehash: 8dad8520c938cae655143464189897d216a5f3ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306766"
---
# <a name="cmfctaskspanetask-class"></a>Cmfctaskspanetask,, classe

La `CMFCTasksPaneTask` classe est une classe d’assistance qui représente des tâches pour le contrôle de volet de tâches ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). L’objet de tâche représente un élément du groupe de tâches ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Chaque tâche peut avoir une commande exécutée par l’infrastructure lorsqu’un utilisateur clique sur la tâche et une icône qui apparaît à gauche du nom de la tâche.

## <a name="syntax"></a>Syntaxe

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cmfctaskspanetask, :: Cmfctaskspanetask,](#cmfctaskspanetask)|Crée et initialise un objet `CMFCTasksPaneTask`.|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cmfctaskspanetask, :: SetACCData](#setaccdata)|Détermine les données d’accessibilité pour la tâche actuelle.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[Cmfctaskspanetask, :: m_bAutoDestroyWindow](#m_bautodestroywindow)|Détermine si la fenêtre de tâche est automatiquement détruite.|
|[Cmfctaskspanetask, :: m_bIsBold](#m_bisbold)|Détermine si l’infrastructure dessine une étiquette de tâche en texte gras.|
|[Cmfctaskspanetask, :: m_dwUserData](#m_dwuserdata)|Contient les données définies par l’utilisateur que l’infrastructure associe à la tâche. Défini à zéro si la tâche n’a pas de données associées.|
|[Cmfctaskspanetask, :: m_hwndTask](#m_hwndtask)|Handle de la fenêtre de tâche.|
|[Cmfctaskspanetask, :: m_nIcon](#m_nicon)|Index dans la liste d’images de l’image que l’infrastructure affiche en regard de la tâche.|
|[Cmfctaskspanetask, :: m_nWindowHeight](#m_nwindowheight)|Hauteur de la fenêtre de tâche. Si la tâche n’a pas de fenêtre de tâche, cette valeur est égale à zéro.|
|[Cmfctaskspanetask, :: m_pGroup](#m_pgroup)|Pointeur vers le auquel `CMFCTasksPaneTaskGroup` cette tâche appartient.|
|[Cmfctaskspanetask, :: m_rect](#m_rect)|Spécifie le rectangle englobant de la tâche.|
|[Cmfctaskspanetask, :: m_strName](#m_strname)|Nom de la tâche.|
|[Cmfctaskspanetask, :: m_uiCommandID](#m_uicommandid)|Spécifie l’ID de commande de la commande que l’infrastructure exécute lorsque l’utilisateur clique sur la tâche. Si cette valeur n’est pas un ID de commande valide, la tâche est traitée comme une étiquette simple.|

## <a name="remarks"></a>Notes

L’illustration suivante montre un groupe de tâches qui contient trois tâches :

![Groupe de tâches développé](../../mfc/reference/media/nexttaskgrpexpand.png "Groupe de tâches, développé")

> [!NOTE]
> Si une tâche n’a pas d’ID de commande valide, elle est traitée comme une étiquette simple.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxTasksPane. h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a> Cmfctaskspanetask, :: Cmfctaskspanetask,

Crée et initialise un objet `CMFCTasksPaneTask`.

```
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,
    LPCTSTR lpszName,
    int nIcon,
    UINT uiCommandID,
    DWORD dwUserData = 0,
    HWND hwndTask = NULL,
    BOOL bAutoDestroyWindow = FALSE,
    int nWindowHeight = 0);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Spécifie le [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) auquel la tâche appartient.

*lpszName*<br/>
Spécifie le nom de la tâche.

*nIcon*<br/>
Spécifie l’index de l’image de la tâche dans la liste d’images.

*uiCommandID*<br/>
Spécifie l’ID de commande de la commande qui est exécutée lorsque l’utilisateur clique sur la tâche.

*dwUserData*<br/>
Données définies par l’utilisateur.

*hwndTask*<br/>
Spécifie le handle vers la fenêtre de tâche.

*bAutoDestroyWindow*<br/>
Si la valeur est TRUE, la fenêtre de tâche est détruite automatiquement.

*nWindowHeight*<br/>
Spécifie la hauteur de la fenêtre de tâche.

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a> Cmfctaskspanetask, :: m_bAutoDestroyWindow

Détermine si la fenêtre de tâche est automatiquement détruite.

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE pour spécifier que la fenêtre de tâche ( [cmfctaskspanetask, :: m_hwndTask](#m_hwndtask)) doit être détruite automatiquement ; Sinon, FALSe.

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a> Cmfctaskspanetask, :: m_bIsBold

Détermine si une étiquette de tâche est dessinée en texte gras.

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre pour afficher le texte en gras pour l’étiquette de tâche.

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a> Cmfctaskspanetask, :: m_dwUserData

Contient les données définies par l’utilisateur qui sont associées à la tâche. Défini à zéro si aucune donnée n’est associée à la tâche.

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a> Cmfctaskspanetask, :: m_hwndTask

Handle de la fenêtre de tâche.

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Notes

Pour ajouter une fenêtre de tâche, appelez [CMFCTasksPane :: AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a> Cmfctaskspanetask, :: m_nIcon

Position d’index dans une liste d’images qui identifie une image qui est affichée en regard de la tâche spécifiée.

```
int m_nIcon;
```

### <a name="remarks"></a>Notes

La liste d’images est définie par [CMFCTasksPane :: SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).

Affectez `m_nIcon` la valeur-1 si vous souhaitez afficher la tâche sans image.

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a> Cmfctaskspanetask, :: m_nWindowHeight

Hauteur de la fenêtre de tâche. Si la tâche n’a pas de fenêtre de tâche, cette valeur est égale à zéro.

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a> Cmfctaskspanetask, :: m_pGroup

Pointeur vers le [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) auquel cette tâche appartient.

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Notes

Chaque tâche doit avoir un groupe parent. Vous ajoutez des groupes à un volet de tâches en appelant [CMFCTasksPane :: addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a> Cmfctaskspanetask, :: m_rect

Spécifie le rectangle englobant de la tâche.

```
CRect m_rect;
```

### <a name="remarks"></a>Notes

Cette valeur est calculée par le Framework lorsque la tâche est dessinée.

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a> Cmfctaskspanetask, :: m_strName

Nom de la tâche.

```
CString m_strName;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a> Cmfctaskspanetask, :: m_uiCommandID

Spécifie l’ID de commande de la commande qui est exécutée lorsque l’utilisateur clique sur la tâche. Si cette valeur n’est pas un ID de commande valide, la tâche est traitée comme une étiquette simple.

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a> Cmfctaskspanetask, :: SetACCData

Détermine les données d’accessibilité pour la tâche actuelle.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
dans Représente la fenêtre parente de la tâche actuelle.

*data*<br/>
à Objet de type `CAccessibilityData` qui est rempli avec les données d’accessibilité de la tâche actuelle.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le paramètre de *données* a été correctement rempli avec les données d’accessibilité de la tâche actuelle ; Sinon, FALSe.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)
