---
title: CMFCRibbonStatusBar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: 8d90e01db022c33edd654e83af05e9986799f2b9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754056"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar, classe

La `CMFCRibbonStatusBar` classe implémente un contrôle de barre d’état qui peut afficher des éléments de ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Ajoute un élément dynamique à la barre d’état du ruban.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Ajoute un nouvel élément ruban à la barre d’état du ruban.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Ajoute un élément ruban à la zone étendue de la barre d’état du ruban.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Ajoute un séparateur à la barre d’état du ruban.|
|[CMFCRibbonStatusBar::Créer](#create)|Crée une barre d’état de ruban.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Crée une barre de statut ruban avec un style étendu.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Renvoie un pointeur à l’élément qui a l’ID de commande spécifié.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Retourne le nombre d’éléments qui sont situés dans la zone principale de la barre d’état du ruban.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Renvoie un pointeur à l’élément qui se trouve à un index spécifié.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Retourne le nombre d’éléments qui sont situés dans la zone étendue de la barre d’état du ruban.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Retourne un pointeur vers l'élément situé à l'index spécifié dans la zone étendue de la barre d'état du ruban.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar:IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar:IsInformationMode](#isinformationmode)|Détermine si le mode d’information est activé pour la barre d’état du ruban.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Overrides [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Supprime tous les éléments de la barre d’état du ruban.|
|[CMFCRibbonStatusBar::EnlèvementElement](#removeelement)|Supprime l’élément qui a une pièce d’identité de commande spécifiée de la barre d’état du ruban.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Permet ou désactive le mode d’information pour la barre d’état du ruban.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Affiche la chaîne d’information qui apparaît sur la barre d’état du ruban lorsque le mode d’information est activé.|

## <a name="remarks"></a>Notes

Les utilisateurs peuvent modifier la visibilité des éléments ruban sur une barre d’état de ruban en utilisant le menu contexte intégré pour la barre d’état du ruban. Vous pouvez ajouter ou supprimer les éléments de façon dynamique.

Une barre d’état de ruban a deux secteurs : une zone principale et une zone étendue. La zone étendue est affichée sur le côté droit de la barre d’état du ruban et apparaît dans une couleur différente de la zone principale.

En règle générale, la zone principale de la barre d’état affiche les notifications d’état, et la zone étendue affiche les commandes de vue. La zone étendue reste visible aussi longtemps que possible lorsque l’utilisateur resize la barre d’état du ruban.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonStatusBar` . L’exemple montre comment ajouter un nouvel élément ruban à la barre d’état du ruban, ajouter un élément ruban à la zone étendue de la barre d’état du ruban, ajouter un séparateur et activer le mode régulier pour la barre d’état du ruban.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribbonstatusbar.h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFCRibbonStatusBar::AddDynamicElement

Ajoute un élément dynamique à la barre d’état du ruban.

```cpp
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Paramètres

*pElement*<br/>
[dans] Un pointeur vers un élément dynamique.

### <a name="remarks"></a>Notes

Contrairement aux éléments réguliers, les éléments dynamiques ne sont pas personnalisables et le menu personnalisé de la barre d’état ne les affiche pas.

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFCRibbonStatusBar::AddElement

Ajoute un nouvel élément ruban à la barre d’état du ruban.

```cpp
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Paramètres

*pElement*<br/>
[dans] Un pointeur à l’élément ajouté.

*lpszLabel*<br/>
[dans] Une étiquette de texte de l’élément.

*bIsVisible*<br/>
[dans] VRAI si vous voulez ajouter l’élément comme visible, FALSE si vous voulez ajouter l’élément comme caché.

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement

Ajoute un élément ruban à la zone étendue de la barre d’état du ruban.

```cpp
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Paramètres

*pElement*<br/>
[dans] Un pointeur à l’élément ajouté.

*lpszLabel*<br/>
[dans] L’étiquette de texte de l’élément.

*bIsVisible*<br/>
[dans] VRAI si vous voulez ajouter l’élément comme visible, FALSE si vous voulez ajouter l’élément comme caché.

### <a name="remarks"></a>Notes

La zone étendue se trouve sur le côté droit du contrôle de barre d'état.

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFCRibbonStatusBar::AddSeparator

Ajoute un séparateur à la barre d’état du ruban.

```cpp
void AddSeparator();
```

### <a name="remarks"></a>Notes

Le cadre ajoute un séparateur après la méthode [CMFCRibbonStatusBar::AddElement](#addelement). insère le dernier élément.

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFCRibbonStatusBar::Créer

Crée une barre d’état de ruban.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[dans] Un pointeur à la fenêtre parente.

*dwStyle (en)*<br/>
[dans] Une combinaison logique ou de styles de contrôle.

*nID*<br/>
[dans] L’ID de contrôle de la barre d’état.

### <a name="return-value"></a>Valeur de retour

VRAI si la barre d’état est créée avec succès, FALSE autrement.

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFCRibbonStatusBar::CreateEx

Crée une barre de statut de ruban qui a un style étendu.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre parente.

*dwCtrlStyle (en)*<br/>
Une combinaison de styles supplémentaires pour créer l’objet de barre d’état.

*dwStyle (en)*<br/>
Le style de contrôle de la barre d’état.

*nID*<br/>
L’ID de contrôle de la barre d’état.

### <a name="return-value"></a>Valeur de retour

VRAI si la barre d’état est créée avec succès, FALSE autrement.

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFCRibbonStatusBar::FindByID

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *uiCmdID*<br/>
[dans] *BOOL (en anglais)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFCRibbonStatusBar::FindElement

Renvoie un pointeur à l’élément qui a l’ID de commande spécifié.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] L’ID de l’élément.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément qui a l’ID de commande spécifié. NULL s’il n’y a pas un tel élément.

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFCRibbonStatusBar::GetCount

Retourne le nombre d’éléments qui sont situés dans la zone principale de la barre d’état du ruban.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments qui sont situés dans la zone principale de la barre d’état du ruban.

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFCRibbonStatusBar::GetElement

Renvoie un pointeur à l’élément qui se trouve à un index spécifié.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie un index zéro d’un élément qui se trouve dans la zone principale du contrôle de la barre d’état.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément qui se trouve à l’index spécifié. NULL si l’indice est négatif ou dépasse le nombre d’éléments de la barre d’état.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount

Retourne le nombre d’éléments qui sont situés dans la zone étendue de la barre d’état du ruban.

```
int GetExCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments qui se trouvent dans la zone étendue de la barre d’état du ruban.

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFCRibbonStatusBar::GetExElement

Retourne un pointeur vers l'élément situé à l'index spécifié dans la zone étendue de la barre d'état du ruban. La zone étendue se trouve sur le côté droit du contrôle de barre d'état.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’index zéro d’un élément qui se trouve dans la zone étendue du contrôle de la barre d’état.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l'élément situé à l'index spécifié dans la zone étendue de la barre d'état du ruban. NULL si *nIndex* est négatif ou dépasse le nombre d’éléments dans la zone étendue de la barre d’état du ruban.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

[dans] *rect*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFCRibbonStatusBar::GetSpace

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomFrame

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFCRibbonStatusBar:IsExtendedElement

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Paramètres

[dans] *pElement*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFCRibbonStatusBar:IsInformationMode

Détermine si le mode d’information est activé pour la barre d’état du ruban.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la barre d’état peut fonctionner en mode information; autrement FALSE.

### <a name="remarks"></a>Notes

En mode information, la barre d’état cache tous les volets réguliers et affiche une chaîne de message.

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFCRibbonStatusBar::OnDrawInformation

Affiche la chaîne qui apparaît sur la barre d’état du ruban lorsque le mode d’information est activé.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*strInfo (en anglais)*<br/>
[dans] La chaîne d’information.

*rectInfo (en anglais)*<br/>
[dans] Le rectangle de délimitation.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée si vous souhaitez personnaliser l’apparence de la chaîne d’informations sur la barre d’état. Utilisez la méthode [CMFCRibbonStatusBar::SetInformation](#setinformation) pour mettre la barre d’état en mode information. Dans ce mode, la barre d’état cache toutes les vitres et affiche la chaîne d’information spécifiée par *strInfo*.

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFCRibbonStatusBar::RecalcLayout

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFCRibbonStatusBar::RemoveAll

Supprime tous les éléments de la barre d’état du ruban.

```cpp
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFCRibbonStatusBar::EnlèvementElement

Supprime l’élément qui a une pièce d’identité de commande spécifiée de la barre d’état du ruban.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] L’ID de l’élément à supprimer de la barre d’état.

### <a name="return-value"></a>Valeur de retour

VRAI si un élément avec *l’uiID* spécifié est supprimé. Sinon, la valeur est FALSE.

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFCRibbonStatusBar::SetInformation

Permet ou désactive le mode d’information pour la barre d’état du ruban.

```cpp
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Paramètres

*lpszInfo (en anglais)*<br/>
[dans] La chaîne d’information.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour mettre la barre d’état dans le mode d’information. Dans ce mode, la barre d’état cache toutes les vitres et affiche la chaîne d’information spécifiée par *lpszInfo*.

Lorsque lpszInfo est NULL, la barre d’état revient en mode régulier.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[Classe CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
