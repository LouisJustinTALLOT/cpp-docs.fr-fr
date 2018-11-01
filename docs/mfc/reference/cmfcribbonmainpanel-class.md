---
title: Cmfcribbonmainpanel, classe
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
ms.openlocfilehash: 101c718d25a2e06461156045deea5f42d85e2f4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638215"
---
# <a name="cmfcribbonmainpanel-class"></a>Cmfcribbonmainpanel, classe

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
|[CMFCRibbonMainPanel::Add](#add)|Ajoute un élément de ruban vers le volet gauche du panneau bouton application. (Substitue [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Ajoute une chaîne de texte dans le menu de liste de fichiers récents.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Ajoute un élément de ruban vers le volet en bas du panneau d’application de ruban.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Ajoute un élément de ruban vers le volet droit du panneau bouton application.|
|`CMFCRibbonMainPanel::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Retourne un rectangle qui représente la zone du panneau principal du ruban.|
|`CMFCRibbonMainPanel::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|

## <a name="remarks"></a>Notes

L’infrastructure affiche le `CMFCRibbonMainPanel` lorsque vous ouvrez le panneau de l’application. Il contient trois volets :

- Le volet gauche contient les commandes associées à des fichiers, tel que **Open**, **enregistrer**, **impression**, et **fermer**. Pour ajouter une commande à ce volet, appelez [CMFCRibbonMainPanel::Add](#add).

- Le volet droit contient les options qui modifient la commande que vous cliquez sur dans le volet gauche. Par exemple, si vous cliquez sur **Enregistrer sous** dans le volet gauche, le volet droit pour afficher les types de fichiers disponibles. Pour ajouter un élément à ce volet, appelez [CMFCRibbonMainPanel::AddToRight](#addtoright).

- Le volet inférieur contient les boutons qui vous permettent de modifier les paramètres de l’application et pour quitter le programme. Pour ajouter un élément à ce volet, appelez [CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxRibbonMainPanel.h

##  <a name="add"></a>  CMFCRibbonMainPanel::Add

Ajoute un élément de ruban vers le volet gauche du panneau bouton application.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Paramètres

*pElem*<br/>
[in, out] Un pointeur vers l’élément de ruban à ajouter au panneau principal.

### <a name="remarks"></a>Notes

Ajoute un élément de ruban dans le panneau. Éléments ajoutés à l’aide de cette méthode seront situées dans la colonne gauche du panneau principal.

##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList

Ajoute une chaîne de texte dans le menu de liste de fichiers récents.

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
Spécifie la chaîne à ajouter à la liste des fichiers récents.

*nWidth*<br/>
Spécifie la largeur, en pixels, du Panneau de liste de fichiers récents.

### <a name="remarks"></a>Notes

##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom

Ajoute un élément de ruban vers le volet en bas du panneau d’application de ruban.

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Paramètres

*pElem*<br/>
[in, out] Pointeur vers l’élément de ruban pour ajouter vers le bas du panneau principal.

### <a name="remarks"></a>Notes

##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight

Ajoute un élément de ruban vers le volet droit du panneau bouton application.

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Paramètres

*pElem*<br/>
Pointeur vers un élément de ruban à ajouter à droite du panneau principal.

*nWidth*<br/>
Spécifie la largeur, en pixels, du panneau droit.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour ajouter un élément de ruban vers le panneau droit. Le volet droit affiche généralement la liste des fichiers récents, mais vous pouvez ajouter n’importe quel autre élément de ruban ici.

##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame

Retourne un rectangle qui représente la zone du panneau principal du ruban.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Valeur de retour

Un rectangle qui représente la zone du panneau principal du ruban.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel, classe](../../mfc/reference/cmfcribbonpanel-class.md)
