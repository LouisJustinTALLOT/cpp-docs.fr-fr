---
title: CMFCTasksPaneTask, classe
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
ms.openlocfilehash: 49fccdf161da7deb1fd88a12a107df40bafdae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375864"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask, classe

La `CMFCTasksPaneTask` classe est une classe d’aide qui représente les tâches pour le contrôle de la fonction panoramique ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). L’objet de tâche représente un élément du groupe de travail ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Chaque tâche peut avoir une commande exécutée par l’infrastructure lorsqu’un utilisateur clique sur la tâche et une icône qui apparaît à gauche du nom de la tâche.

## <a name="syntax"></a>Syntaxe

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Crée et initialise un objet `CMFCTasksPaneTask`.|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Détermine les données d’accessibilité pour la tâche actuelle.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTask:m_bAutoDestroyWindow](#m_bautodestroywindow)|Détermine si la fenêtre de tâche est automatiquement détruite.|
|[CMFCTasksPaneTask:m_bIsBold](#m_bisbold)|Détermine si le cadre dessine une étiquette de tâche en texte gras.|
|[CMFCTasksPaneTask:m_dwUserData](#m_dwuserdata)|Contient des données définies par l’utilisateur que le cadre associe à la tâche. Définissez à zéro si la tâche n’a pas de données associées.|
|[CMFCTasksPaneTask:m_hwndTask](#m_hwndtask)|Une poignée à la fenêtre de tâche.|
|[CMFCTasksPaneTask:m_nIcon](#m_nicon)|L’index dans la liste d’images de l’image que le cadre affiche à côté de la tâche.|
|[CMFCTasksPaneTask:m_nWindowHeight](#m_nwindowheight)|La hauteur de la fenêtre de tâche. Si la tâche n’a pas de fenêtre de tâche, cette valeur est nulle.|
|[CMFCTasksPaneTask:m_pGroup](#m_pgroup)|Un pointeur `CMFCTasksPaneTaskGroup` à la que cette tâche appartient à.|
|[CMFCTasksPaneTask:m_rect](#m_rect)|Spécifie le rectangle de délimitation de la tâche.|
|[CMFCTasksPaneTask:m_strName](#m_strname)|Nom de la tâche.|
|[CMFCTasksPaneTask:m_uiCommandID](#m_uicommandid)|Spécifie l’ID de commande de la commande que le cadre exécute lorsque l’utilisateur clique sur la tâche. Si cette valeur n’est pas une pièce d’identité de commande valide, la tâche est traitée comme une simple étiquette.|

## <a name="remarks"></a>Notes

L’illustration suivante montre un groupe de travail qui contient trois tâches :

![Groupe de travail, élargi](../../mfc/reference/media/nexttaskgrpexpand.png "Groupe de tâches, développé")

> [!NOTE]
> Si une tâche n’a pas d’id de commande valide, elle est traitée comme une simple étiquette.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxTasksPane.h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a>CMFCTasksPaneTask::CMFCTasksPaneTask

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

*pGroup (en anglais)*<br/>
Précise le [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) auquel appartient la tâche.

*lpszName (en)*<br/>
Spécifie le nom de la tâche.

*nIcon (en)*<br/>
Spécifie l’index de l’image de la tâche dans la liste d’images.

*uiCommandID*<br/>
Spécifie l’ID de commande de la commande qui est exécuté lorsque la tâche est cliqué.

*dwUserData*<br/>
Données définies par l’utilisateur.

*hwndTask hwndTask*<br/>
Spécifie la poignée à la fenêtre de tâche.

*bAutoDestroyWindow*<br/>
Si VRAI, la fenêtre de tâche sera détruite automatiquement.

*nWindowHeight*<br/>
Spécifie la hauteur de la fenêtre de tâche.

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCTasksPaneTask:m_bAutoDestroyWindow

Détermine si la fenêtre de tâche est automatiquement détruite.

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Notes

Définissez à TRUE pour spécifier que la fenêtre de tâche ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) doit être détruite automatiquement; autrement, FALSE.

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a>CMFCTasksPaneTask:m_bIsBold

Détermine si une étiquette de tâche est dessinée en texte gras.

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Notes

Définissez ce membre à TRUE pour afficher du texte gras pour l’étiquette de tâche.

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a>CMFCTasksPaneTask:m_dwUserData

Contient des données définies par l’utilisateur qui sont associées à la tâche. Définissez à zéro si aucune donnée n’est associée à la tâche.

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a>CMFCTasksPaneTask:m_hwndTask

Une poignée à la fenêtre de tâche.

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Notes

Pour ajouter une fenêtre de tâche, appelez [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a>CMFCTasksPaneTask:m_nIcon

La position de l’index dans une liste d’images qui identifie une image qui s’affiche à côté de la tâche spécifiée.

```
int m_nIcon;
```

### <a name="remarks"></a>Notes

La liste d’images est définie par [CMFCTasksPane:SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).

Définissez `m_nIcon` -1 si vous souhaitez afficher la tâche sans image.

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a>CMFCTasksPaneTask:m_nWindowHeight

La hauteur de la fenêtre de tâche. Si la tâche n’a pas de fenêtre de tâche, cette valeur est nulle.

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a>CMFCTasksPaneTask:m_pGroup

Pointeur vers le [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) auquel cette tâche appartient.

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Notes

Chaque tâche doit avoir un groupe de parents. Vous ajoutez des groupes à un volet de tâche en appelant [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTask:m_rect

Spécifie le rectangle de délimitation de la tâche.

```
CRect m_rect;
```

### <a name="remarks"></a>Notes

Cette valeur est calculée par le cadre lorsque la tâche est tirée.

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTask:m_strName

Nom de la tâche.

```
CString m_strName;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a>CMFCTasksPaneTask:m_uiCommandID

Spécifie l’ID de commande de la commande qui est exécuté lorsque l’utilisateur clique sur la tâche. Si cette valeur n’est pas une pièce d’identité de commande valide, la tâche est traitée comme une simple étiquette.

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTask::SetACCData

Détermine les données d’accessibilité pour la tâche actuelle.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
[dans] Représente la fenêtre parente de la tâche actuelle.

*data*<br/>
[out] Un objet `CAccessibilityData` de type qui est peuplé avec les données d’accessibilité de la tâche actuelle.

### <a name="return-value"></a>Valeur de retour

VRAI si le paramètre *de données* a été peuplé avec succès avec les données d’accessibilité de la tâche actuelle; autrement, FALSE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)
