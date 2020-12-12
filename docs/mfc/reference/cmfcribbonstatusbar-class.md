---
description: 'En savoir plus sur : classe CMFCRibbonStatusBar'
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
ms.openlocfilehash: 01436d535b410fd4a6c70f52760908e3547b7af8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264997"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar, classe

La `CMFCRibbonStatusBar` classe implémente un contrôle de barre d’État qui peut afficher des éléments de ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Ajoute un élément dynamique à la barre d’État du ruban.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Ajoute un nouvel élément de ruban à la barre d’État du ruban.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Ajoute un élément de ruban à la zone étendue de la barre d’État du ruban.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Ajoute un séparateur à la barre d’État du ruban.|
|[CMFCRibbonStatusBar :: Create](#create)|Crée une barre d’état de ruban.|
|[CMFCRibbonStatusBar :: CreateEx](#createex)|Crée une barre d’état de ruban avec un style étendu.|
|[CMFCRibbonStatusBar :: FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Retourne un pointeur vers l’élément qui a l’ID de commande spécifié.|
|[CMFCRibbonStatusBar :: GetCount](#getcount)|Retourne le nombre d’éléments qui se trouvent dans la zone principale de la barre d’État du ruban.|
|[CMFCRibbonStatusBar :: GetElement](#getelement)|Retourne un pointeur vers l’élément situé à un index spécifié.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Retourne le nombre d’éléments situés dans la zone étendue de la barre d’État du ruban.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Retourne un pointeur vers l'élément situé à l'index spécifié dans la zone étendue de la barre d'état du ruban.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Détermine si le mode d’informations est activé pour la barre d’État du ruban.|
|[CMFCRibbonStatusBar :: RecalcLayout](#recalclayout)|(Substitue [CMFCRibbonBar :: RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar :: RemoveAll](#removeall)|Supprime tous les éléments de la barre d’État du ruban.|
|[CMFCRibbonStatusBar :: RemoveElement](#removeelement)|Supprime l’élément qui a un ID de commande spécifié de la barre d’État du ruban.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Active ou désactive le mode informations pour la barre d’État du ruban.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Affiche la chaîne d’informations qui s’affiche dans la barre d’État du ruban lorsque le mode d’informations est activé.|

## <a name="remarks"></a>Notes

Les utilisateurs peuvent modifier la visibilité des éléments du ruban sur une barre d’État du ruban en utilisant le menu contextuel intégré pour la barre d’État du ruban. Vous pouvez ajouter ou supprimer des éléments de manière dynamique.

Une barre d’état de ruban comporte deux zones : une zone principale et une zone étendue. La zone étendue s’affiche sur le côté droit de la barre d’État du ruban et s’affiche dans une couleur différente de celle de la zone principale.

En règle générale, la zone principale de la barre d’état affiche les notifications d’État et la zone étendue affiche les contrôles d’affichage. La zone étendue reste visible aussi longtemps que possible lorsque l’utilisateur redimensionne la barre d’État du ruban.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonStatusBar` . L’exemple montre comment ajouter un nouvel élément de ruban à la barre d’État du ruban, ajouter un élément de ruban à la zone étendue de la barre d’État du ruban, ajouter un séparateur et activer le mode normal pour la barre d’État du ruban.

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

**En-tête :** afxribbonstatusbar. h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a> CMFCRibbonStatusBar::AddDynamicElement

Ajoute un élément dynamique à la barre d’État du ruban.

```cpp
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Paramètres

*empelement*<br/>
dans Pointeur vers un élément dynamique.

### <a name="remarks"></a>Notes

Contrairement aux éléments ordinaires, les éléments dynamiques ne sont pas personnalisables et le menu personnaliser de la barre d’État ne les affiche pas.

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a> CMFCRibbonStatusBar::AddElement

Ajoute un nouvel élément de ruban à la barre d’État du ruban.

```cpp
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Paramètres

*empelement*<br/>
dans Pointeur vers l’élément ajouté.

*lpszLabel*<br/>
dans Étiquette de texte de l’élément.

*bIsVisible*<br/>
dans TRUE si vous souhaitez ajouter l’élément comme étant visible, FALSe si vous souhaitez ajouter l’élément comme masqué.

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a> CMFCRibbonStatusBar::AddExtendedElement

Ajoute un élément de ruban à la zone étendue de la barre d’État du ruban.

```cpp
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Paramètres

*empelement*<br/>
dans Pointeur vers l’élément ajouté.

*lpszLabel*<br/>
dans Étiquette de texte de l’élément.

*bIsVisible*<br/>
dans TRUE si vous souhaitez ajouter l’élément comme étant visible, FALSe si vous souhaitez ajouter l’élément comme masqué.

### <a name="remarks"></a>Notes

La zone étendue se trouve sur le côté droit du contrôle de barre d'état.

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a> CMFCRibbonStatusBar::AddSeparator

Ajoute un séparateur à la barre d’État du ruban.

```cpp
void AddSeparator();
```

### <a name="remarks"></a>Notes

Le Framework ajoute un séparateur après la méthode [CMFCRibbonStatusBar :: AddElement](#addelement). insère le dernier élément.

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a> CMFCRibbonStatusBar :: Create

Crée une barre d’état de ruban.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
dans Pointeur vers la fenêtre parente.

*dwStyle*<br/>
dans Combinaison logique ou de styles de contrôle.

*nID*<br/>
dans ID de contrôle de la barre d’État.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la barre d’État est créée avec succès ; sinon, FALSe.

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a> CMFCRibbonStatusBar :: CreateEx

Crée une barre d’état de ruban avec un style étendu.

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

*dwCtrlStyle*<br/>
Combinaison logique ou de styles supplémentaires pour la création de l’objet de barre d’État.

*dwStyle*<br/>
Style de contrôle de la barre d’État.

*nID*<br/>
ID de contrôle de la barre d’État.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la barre d’État est créée avec succès ; sinon, FALSe.

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a> CMFCRibbonStatusBar :: FindByID

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *uiCmdID*<br/>
dans Valeur *booléenne*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a> CMFCRibbonStatusBar::FindElement

Retourne un pointeur vers l’élément qui a l’ID de commande spécifié.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans ID de l’élément.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément qui a l’ID de commande spécifié. NULL s’il n’existe aucun élément de ce type.

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a> CMFCRibbonStatusBar :: GetCount

Retourne le nombre d’éléments qui se trouvent dans la zone principale de la barre d’État du ruban.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments situés dans la zone principale de la barre d’État du ruban.

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a> CMFCRibbonStatusBar :: GetElement

Retourne un pointeur vers l’élément situé à un index spécifié.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie un index de base zéro d’un élément situé dans la zone principale du contrôle de barre d’État.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément situé à l’index spécifié. NULL si l’index est négatif ou dépasse le nombre d’éléments dans la barre d’État.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a> CMFCRibbonStatusBar::GetExCount

Retourne le nombre d’éléments situés dans la zone étendue de la barre d’État du ruban.

```
int GetExCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments situés dans la zone étendue de la barre d’État du ruban.

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a> CMFCRibbonStatusBar::GetExElement

Retourne un pointeur vers l'élément situé à l'index spécifié dans la zone étendue de la barre d'état du ruban. La zone étendue se trouve sur le côté droit du contrôle de barre d'état.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index de base zéro d’un élément situé dans la zone étendue du contrôle de barre d’État.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l'élément situé à l'index spécifié dans la zone étendue de la barre d'état du ruban. NULL si *nIndex* est négatif ou dépasse le nombre d’éléments dans la zone étendue de la barre d’État du ruban.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a> CMFCRibbonStatusBar::GetExtendedArea

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a> CMFCRibbonStatusBar::GetSpace

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a> CMFCRibbonStatusBar::IsBottomFrame

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a> CMFCRibbonStatusBar::IsExtendedElement

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Paramètres

dans *Empelement*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a> CMFCRibbonStatusBar::IsInformationMode

Détermine si le mode d’informations est activé pour la barre d’État du ruban.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la barre d’État peut fonctionner en mode informations ; Sinon, FALSe.

### <a name="remarks"></a>Notes

En mode informations, la barre d’État masque tous les volets normaux et affiche une chaîne de message.

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a> CMFCRibbonStatusBar::OnDrawInformation

Affiche la chaîne qui apparaît dans la barre d’État du ruban lorsque le mode d’informations est activé.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*strInfo*<br/>
dans Chaîne d’informations.

*rectInfo*<br/>
dans Rectangle englobant.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée si vous souhaitez personnaliser l’apparence de la chaîne d’informations dans la barre d’État. Utilisez la méthode [CMFCRibbonStatusBar :: SetInformation](#setinformation) pour placer la barre d’État en mode informations. Dans ce mode, la barre d’État masque tous les volets et affiche la chaîne d’informations spécifiée par *strInfo*.

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a> CMFCRibbonStatusBar :: RecalcLayout

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a> CMFCRibbonStatusBar :: RemoveAll

Supprime tous les éléments de la barre d’État du ruban.

```cpp
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a> CMFCRibbonStatusBar :: RemoveElement

Supprime l’élément qui a un ID de commande spécifié de la barre d’État du ruban.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans ID de l’élément à supprimer de la barre d’État.

### <a name="return-value"></a>Valeur renvoyée

TRUE si un élément avec le *uiID* spécifié est supprimé. Sinon, la valeur est FALSE.

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a> CMFCRibbonStatusBar::SetInformation

Active ou désactive le mode informations pour la barre d’État du ruban.

```cpp
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Paramètres

*lpszInfo*<br/>
dans Chaîne d’informations.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour placer la barre d’État dans le mode d’informations. Dans ce mode, la barre d’État masque tous les volets et affiche la chaîne d’informations spécifiée par *lpszInfo*.

Quand lpszInfo a la valeur NULL, la barre d’État revient en mode normal.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement, classe](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
