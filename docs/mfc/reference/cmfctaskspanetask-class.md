---
title: Cmfctaskspanetask, classe
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
ms.openlocfilehash: 7d7f5a87dc005ee67f9ce65f4ad686cb27d007c2
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176547"
---
# <a name="cmfctaskspanetask-class"></a>Cmfctaskspanetask, classe

Le `CMFCTasksPaneTask` est une classe d’assistance qui représente des tâches pour le contrôle de volet de tâches ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). L’objet tâche représente un élément dans le groupe de tâches ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Chaque tâche peut avoir une commande exécutée par l’infrastructure lorsqu’un utilisateur clique sur la tâche et une icône qui apparaît à gauche du nom de la tâche.

## <a name="syntax"></a>Syntaxe

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Crée et initialise un `CMFCTasksPaneTask` objet.|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Détermine les données d’accessibilité pour la tâche actuelle.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Détermine si la fenêtre de la tâche est automatiquement détruite.|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Détermine si le framework Dessine une étiquette de la tâche en gras.|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Contient des données définies par l’utilisateur, le framework associe à la tâche. La valeur zéro si la tâche ne comporte aucune donnée associée.|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Handle vers la fenêtre des tâches.|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|L’index dans la liste d’images de l’image affichée par l’infrastructure en regard de la tâche.|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|La hauteur de la fenêtre des tâches. Si la tâche a aucune fenêtre de tâche, cette valeur est zéro.|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Un pointeur vers le `CMFCTasksPaneTaskGroup` appartenant à cette tâche.|
|[CMFCTasksPaneTask::m_rect](#m_rect)|Spécifie le rectangle englobant de la tâche.|
|[CMFCTasksPaneTask::m_strName](#m_strname)|Le nom de la tâche.|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Spécifie l’ID de commande de la commande exécutée par l’infrastructure lorsque l’utilisateur clique sur la tâche. Si cette valeur n’est pas un ID de commande valide, la tâche est traitée comme une simple étiquette.|

## <a name="remarks"></a>Notes

L’illustration suivante montre un groupe de tâches contenant trois tâches :

![Groupe de tâches, développé](../../mfc/reference/media/nexttaskgrpexpand.png "groupe de tâches, développé")

> [!NOTE]
> Si une tâche n’a pas un ID de commande valide, il est traité comme une simple étiquette.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxTasksPane.h

##  <a name="cmfctaskspanetask"></a>  CMFCTasksPaneTask::CMFCTasksPaneTask

Crée et initialise un `CMFCTasksPaneTask` objet.

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
Spécifie le [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) auquel appartient la tâche.

*Caractère*<br/>
Spécifie le nom de la tâche.

*nIcon*<br/>
Spécifie l’index d’image de la tâche dans la liste d’images.

*uiCommandID*<br/>
Spécifie l’ID de commande de la commande est exécutée lorsque l’utilisateur clique sur la tâche.

*dwUserData*<br/>
Données définies par l’utilisateur.

*hwndTask*<br/>
Spécifie le handle vers la fenêtre des tâches.

*bAutoDestroyWindow*<br/>
Si la valeur est TRUE, la fenêtre des tâches est détruite automatiquement.

*nWindowHeight*<br/>
Spécifie la hauteur de la fenêtre de la tâche.

### <a name="remarks"></a>Notes

##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow

Détermine si la fenêtre de la tâche est automatiquement détruite.

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Notes

Défini sur TRUE pour spécifier que la fenêtre des tâches ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) doit être détruit automatiquement ; sinon, FALSE.

##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold

Détermine si une étiquette de la tâche est dessinée dans le texte en gras.

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Notes

Définissez ce membre sur True pour afficher gras au texte de l’étiquette de la tâche.

##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData

Contient des données définies par l’utilisateur qui sont associées à la tâche. La valeur zéro si aucune donnée n’est associée à la tâche.

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Notes

##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask

Handle vers la fenêtre des tâches.

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Notes

Pour ajouter une fenêtre de tâche, appelez [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).

##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon

Position d’index dans une liste d’images qui identifie une image qui est affichée en regard de la tâche spécifiée.

```
int m_nIcon;
```

### <a name="remarks"></a>Notes

La liste d’images est définie par [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).

Définissez `m_nIcon` sur -1 si vous souhaitez afficher la tâche sans une image.

##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight

La hauteur de la fenêtre des tâches. Si la tâche a aucune fenêtre de tâche, cette valeur est zéro.

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Notes

##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup

Pointeur vers le [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) auquel appartient cette tâche.

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Notes

Chaque tâche doit avoir un groupe parent. Ajouter des groupes à un volet de tâches en appelant [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect

Spécifie le rectangle englobant de la tâche.

```
CRect m_rect;
```

### <a name="remarks"></a>Notes

Cette valeur est calculée par le framework lorsque la tâche est dessinée.

##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName

Le nom de la tâche.

```
CString m_strName;
```

### <a name="remarks"></a>Notes

##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID

Spécifie l’ID de commande de la commande est exécutée lorsque l’utilisateur clique sur la tâche. Si cette valeur n’est pas un ID de commande valide, la tâche est traitée comme une simple étiquette.

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Notes

##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData

Détermine les données d’accessibilité pour la tâche actuelle.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
[in] Représente la fenêtre parente de la tâche en cours.

*data*<br/>
[out] Un objet de type `CAccessibilityData` qui est rempli avec les données d’accessibilité de la tâche en cours.

### <a name="return-value"></a>Valeur de retour

TRUE si le *données* paramètre a été correctement remplis avec les données d’accessibilité de la tâche en cours ; sinon, FALSE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)
