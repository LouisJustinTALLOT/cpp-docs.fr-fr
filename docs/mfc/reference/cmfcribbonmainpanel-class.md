---
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
ms.openlocfilehash: 0fd1cd2fec31f9da0c2bec36d08586780f4f95c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753571"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel, classe

Implémente un panneau ruban qui s’affiche lorsque vous cliquez sur le [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

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
|[CMFCRibbonMainPanel::Ajouter](#add)|Ajoute un élément ruban à la vitre gauche du panneau bouton d’application. (Overrides [CMFCRibbonPanel::Ajouter](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Ajoute une chaîne de texte au menu de liste de fichiers récents.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Ajoute un élément ruban à la vitre inférieure du panneau d’application de ruban.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Ajoute un élément ruban à la vitre droite du panneau bouton d’application.|
|`CMFCRibbonMainPanel::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Retourne un rectangle qui représente la zone du panneau principal du ruban.|
|`CMFCRibbonMainPanel::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|

## <a name="remarks"></a>Notes

Le cadre `CMFCRibbonMainPanel` affiche le moment où vous ouvrez le panneau d’application. Il contient trois volets :

- Le volet gauche contient des commandes associées à des fichiers, tels que **Open**, **Enregistrer**, **Imprimer**, et **Fermer**. Pour ajouter une commande à ce volet, appelez [CMFCRibbonMainPanel::Ajouter](#add).

- Le volet droit contient des options qui modifient la commande que vous cliquez dans la vitre gauche. Par exemple, si vous cliquez sur **Enregistrer comme** à partir de la vitre gauche, la vitre droite peut afficher les types de fichiers disponibles. Pour ajouter un élément à ce volet, appelez [CMFCRibbonMainPanel::AddToRight](#addtoright).

- Le volet inférieur contient des boutons qui vous permettent de modifier les paramètres de l’application et de quitter le programme. Pour ajouter un élément à ce volet, appelez [CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxRibbonMainPanel.h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a>CMFCRibbonMainPanel::Ajouter

Ajoute un élément ruban à la vitre gauche du panneau bouton d’application.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Paramètres

*pElem (en)*<br/>
[dans, dehors] Un pointeur à l’élément ruban à ajouter au panneau principal.

### <a name="remarks"></a>Notes

Ajoute un élément ruban au panneau. Les éléments ajoutés à l’aide de cette méthode seront situés dans la colonne gauche du panneau principal.

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList

Ajoute une chaîne de texte au menu de liste de fichiers récents.

```cpp
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
Spécifie la chaîne à ajouter à la liste de fichiers récents.

*nWidth (en)*<br/>
Spécifie la largeur, en pixels, du panneau de liste de fichiers récents.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom

Ajoute un élément ruban à la vitre inférieure du panneau d’application de ruban.

```cpp
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Paramètres

*pElem (en)*<br/>
[dans, dehors] Un pointeur à l’élément ruban à ajouter au bas du panneau principal.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight

Ajoute un élément ruban à la vitre droite du panneau bouton d’application.

```cpp
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Paramètres

*pElem (en)*<br/>
Un pointeur à un élément ruban à ajouter sur le côté droit du panneau principal.

*nWidth (en)*<br/>
Spécifie la largeur, en pixels, du panneau droit.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour ajouter un élément ruban au panneau droit. Le panneau droit affiche généralement la liste de fichiers récents, mais vous pouvez ajouter n’importe quel autre élément ruban ici.

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame

Retourne un rectangle qui représente la zone du panneau principal du ruban.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Valeur de retour

Un rectangle qui représente la zone du panneau principal du ruban.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
