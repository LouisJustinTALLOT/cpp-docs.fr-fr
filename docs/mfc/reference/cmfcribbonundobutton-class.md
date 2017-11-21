---
title: Classe de CMFCRibbonUndoButton | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f7d59d91f82a0fa86efcae7214874e0b2ca16a12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcribbonundobutton-class"></a>Classe de CMFCRibbonUndoButton
La `CMFCRibbonUndoButton` classe implémente un bouton de liste déroulante qui contient les commandes d’utilisateur les plus récentes. Les utilisateurs peuvent sélectionner un ou plusieurs des commandes les plus récentes à partir de la liste déroulante pour les annuler ou rétablir.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Construit un nouveau `CMFCRibbonUndoButton` objet à l’aide de l’ID de commande que vous spécifiez, étiquette de texte et des images à partir de la liste d’images de l’objet parent.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Ajoute une nouvelle action à la liste d’actions.|  
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Efface la liste des actions, qui est la liste déroulante.|  
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Détermine le nombre d’éléments dont un utilisateur a sélectionné dans la liste déroulante.|  
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Indique si l’objet contienne un menu.|  
  
## <a name="remarks"></a>Remarques  
 La `CMFCRibbonUndoButton` classe utilise une pile pour représenter la liste déroulante.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCRibbonUndoButton` classe et ajoutez une nouvelle action à la liste des actions. Cet extrait de code fait partie de la [exemple de Gadgets de ruban](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxribbonundobutton.h  
  
##  <a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction  
 Ajoute une nouvelle action à la liste d’actions.  
  
```  
void AddUndoAction(LPCTSTR lpszLabel);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszLabel`  
 L’étiquette d’action qui s’affichera dans la liste déroulante.  
  
##  <a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList  
 Efface la liste des actions, qui est la liste déroulante.  
  
```  
void CleanUpUndoList();
```  
  
##  <a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton  
 Construit un nouveau `CMFCRibbonUndoButton` objet à l’aide de l’ID de commande que vous spécifiez, étiquette de texte et des images à partir de la liste d’images de l’objet parent.  
  
```  
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1);

 
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nID`  
 Spécifie l’identificateur de commande.  
  
 [in] `lpszText`  
 Spécifie l’étiquette de texte du bouton.  
  
 [in] `nSmallImageIndex`  
 Index de base zéro dans la liste d’images de l’objet parent de l’image du bouton petit.  
  
 [in] `nLargeImageIndex`  
 Index de base zéro dans la liste d’images de l’objet parent pour le d’image de grande taille du bouton.  
  
 [in] `hIcon`  
 Un handle d’une icône que vous pouvez utiliser en tant qu’image d’un bouton.  
  
##  <a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber  
 Détermine le nombre d’éléments dont un utilisateur a sélectionné dans la liste déroulante.  
  
```  
int GetActionNumber() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments qu’un utilisateur sélectionnés.  
  
##  <a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu  
 Indique si l’objet contienne un menu.  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours `TRUE`.  
  
### <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Cmfcribbongallery, classe](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
