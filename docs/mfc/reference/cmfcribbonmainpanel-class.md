---
description: 'En savoir plus sur : classe CMFCRibbonMainPanel'
title: CMFCRibbonMainPanel, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: 823a1ce8a8684ca791f838346a1fb50727096a62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321805"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel, classe

Implémente un panneau de ruban qui s’affiche lorsque vous cliquez sur le [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Constructeur par défaut.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonMainPanel :: Add](#add)|Ajoute un élément de ruban au volet gauche du panneau du bouton de l’application. (Substitue [CMFCRibbonPanel :: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Ajoute une chaîne de texte dans le menu de liste des fichiers récents.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Ajoute un élément de ruban au volet inférieur du panneau d’application du ruban.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Ajoute un élément de ruban au volet droit du panneau de bouton de l’application.|
|`CMFCRibbonMainPanel::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Retourne un rectangle qui représente la zone du panneau principal du ruban.|
|`CMFCRibbonMainPanel::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|

## <a name="remarks"></a>Notes

L’infrastructure affiche le `CMFCRibbonMainPanel` lorsque vous ouvrez le panneau de l’application. Il contient trois volets :

- Le volet gauche contient des commandes associées aux fichiers, telles que **ouvrir**, **Enregistrer**, **Imprimer** et **Fermer**. Pour ajouter une commande à ce volet, appelez [CMFCRibbonMainPanel :: Add](#add).

- Le volet droit contient des options qui modifient la commande sur laquelle vous cliquez dans le volet gauche. Par exemple, si vous cliquez sur **Enregistrer sous** dans le volet gauche, le volet droit peut afficher les types de fichiers disponibles. Pour ajouter un élément à ce volet, appelez [CMFCRibbonMainPanel :: AddToRight](#addtoright).

- Le volet inférieur contient des boutons qui vous permettent de modifier les paramètres de l’application et de quitter le programme. Pour ajouter un élément à ce volet, appelez [CMFCRibbonMainPanel :: AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxRibbonMainPanel. h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a> CMFCRibbonMainPanel :: Add

Ajoute un élément de ruban au volet gauche du panneau du bouton de l’application.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Paramètres

*pEler*<br/>
[in, out] Pointeur vers l’élément de ruban à ajouter au panneau principal.

### <a name="remarks"></a>Notes

Ajoute un élément de ruban au panneau. Les éléments ajoutés à l’aide de cette méthode se trouvent dans la colonne de gauche du panneau principal.

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a> CMFCRibbonMainPanel::AddRecentFilesList

Ajoute une chaîne de texte dans le menu de liste des fichiers récents.

```cpp
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
Spécifie la chaîne à ajouter à la liste des fichiers récents.

*nWidth*<br/>
Spécifie la largeur, en pixels, du panneau de liste des fichiers récents.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a> CMFCRibbonMainPanel::AddToBottom

Ajoute un élément de ruban au volet inférieur du panneau d’application du ruban.

```cpp
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Paramètres

*pEler*<br/>
[in, out] Pointeur vers l’élément de ruban à ajouter en bas du panneau principal.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a> CMFCRibbonMainPanel::AddToRight

Ajoute un élément de ruban au volet droit du panneau de bouton de l’application.

```cpp
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Paramètres

*pEler*<br/>
Pointeur vers un élément de ruban à ajouter à droite du panneau principal.

*nWidth*<br/>
Spécifie la largeur, en pixels, du panneau droit.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour ajouter un élément de ruban au volet droit. Le volet droit affiche généralement la liste fichiers récents, mais vous pouvez ajouter n’importe quel autre élément de ruban ici.

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a> CMFCRibbonMainPanel::GetCommandsFrame

Retourne un rectangle qui représente la zone du panneau principal du ruban.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Valeur renvoyée

Rectangle qui représente la zone du panneau principal du ruban.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel, classe](../../mfc/reference/cmfcribbonpanel-class.md)
