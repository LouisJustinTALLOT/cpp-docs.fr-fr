---
title: Classe de CMFCRibbonComboBox | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ebe013e8ce674efb0782112cc8cbc8b1462ef24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371512"
---
# <a name="cmfcribboncombobox-class"></a>Classe de CMFCRibbonComboBox
La `CMFCRibbonComboBox` classe implémente un contrôle de zone de liste déroulante que vous pouvez ajouter à une barre de ruban, un panneau de ruban ou un menu contextuel de ruban.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>Membres  
  
### <a name="constructors"></a>Constructeurs  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Construit un objet CMFCRibbonComboBox.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|Ajoute un élément unique à la zone de liste.|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Supprime un élément spécifié à partir de la zone de liste.|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Indique si la zone de liste peut changer de taille lorsqu’il se déroule.|  
|[CMFCRibbonComboBox::FindItem](#finditem)|Retourne l’index du premier élément dans la zone de liste qui correspond à une chaîne spécifiée.|  
|[CMFCRibbonComboBox::GetCount](#getcount)|Retourne le nombre d’éléments dans la zone de liste.|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Obtient l’index de l’élément actuellement sélectionné dans la zone de liste.|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Obtient la hauteur de la zone de liste lors de la zone de liste est déroulée.|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Retourne la taille de la zone de liste déroulante affichées en mode intermédiaire.|  
|[CMFCRibbonComboBox::GetItem](#getitem)|Retourne la chaîne associée à un élément à l’index spécifié dans la zone de liste.|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Retourne les données associées à un élément à l’index spécifié dans la zone de liste.|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Indique si le contrôle contient une zone d’édition.|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Indique si la zone de liste peut être redimensionnée.|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Appelé par le framework lorsque l’utilisateur sélectionne un élément dans la zone de liste.|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Supprime tous les éléments à partir de la zone de liste et la zone d’édition.|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Sélectionne un élément dans la zone de liste.|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Définit la hauteur de la zone de liste lorsqu’il est déplacé vers le bas.|  
  
## <a name="remarks"></a>Notes  
 La zone de liste déroulante du ruban se compose d’une zone de liste associée à une étiquette statique ou une étiquette qui peut être modifié par l’utilisateur. Vous devez spécifier le type souhaité lorsque vous créez votre zone de liste déroulante du ruban.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCRibbonComboBox` classe, ajoutez un élément à la zone de liste déroulante, sélectionnez un élément dans la zone de liste déroulante et ajouter une zone de liste déroulante à un panneau.  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxribboncombobox.h  
  
##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem  
 Ajoute un élément unique à la zone de liste.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszItem`  
 La chaîne de l’élément à ajouter.  
  
 [in] `dwData`  
 Les données associées à l’élément à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de l’élément ajouté.  
  
##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox  
 Construit un objet `CMFCRibbonComboBox`.  
  
```  
public:  
CMFCRibbonComboBox(
    UINT nID,  
    BOOL bHasEditBox=TRUE,  
    Int nWidth=-1,  
    LPCTSTR lpszLabel=NULL,  
    Int nImage=-1);

protected:  
CMFCRibbonComboBox();
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nID`  
 ID de la zone de liste déroulante.  
  
 [in] `bHasEditBox`  
 `TRUE` Si vous souhaitez une zone d’édition dans le contrôle ; `FALSE` dans le cas contraire.  
  
 [in] `nWidth`  
 Largeur de la zone de liste déroulante en pixels. ou -1 pour la largeur par défaut.  
  
 [in] `lpszLabel`  
 L’étiquette de l’affichage de la zone de liste déroulante.  
  
 [in] `nImage`  
 L’index de la petite image de la zone de liste déroulante.  
  
### <a name="remarks"></a>Notes  
 La largeur par défaut est 108 pixels.  
  
##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem  
 Supprime un élément spécifié à partir de la zone de liste.  
  
```  
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro de l’élément à supprimer.  
  
 [in] `dwData`  
 Les données associées à l’élément à supprimer.  
  
 [in] `lpszText`  
 La chaîne de l’élément à supprimer. S’il existe plusieurs éléments avec la même chaîne, le premier élément est supprimé.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si l’élément spécifié a été supprimé ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize  
 Indique si la zone de liste peut changer de taille lorsqu’il se déroule.  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE` Pour activer le redimensionnement ; `FALSE` pour désactiver le redimensionnement.  
  
### <a name="remarks"></a>Notes  
 Lorsque le redimensionnement est activée, la zone de liste change taille pour ajuster les éléments qu’il affiche.  
  
##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem  
 Retourne l’index du premier élément dans la zone de liste qui correspond à une chaîne spécifiée.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszText`  
 La chaîne d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de l’élément ; ou -1 si l’élément est introuvable.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount  
 Retourne le nombre d’éléments dans la zone de liste.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans la zone de liste, ou 0 si la zone de liste ne contient aucun élément.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel  
 Obtient l’index de l’élément actuellement sélectionné dans la zone de liste.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de l’élément actuellement sélectionné dans la zone de liste ; ou -1 si aucun élément n’est sélectionné.  
  
##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight  
 Obtient la hauteur de la zone de liste lors de la zone de liste est déroulée.  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur, en pixels, de la zone de liste.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize  
 Retourne la taille de la zone de liste déroulante affichées en mode intermédiaire.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour la zone de liste déroulante.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille de la zone de liste déroulante.  
  
### <a name="remarks"></a>Notes  
 La taille retournée est basée sur la taille de la zone de liste déroulante lors de l’affichage de petites images.  
  
##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem  
 Retourne la chaîne associée à un élément à l’index spécifié dans la zone de liste.  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la chaîne qui est associé à l’élément ; dans le cas contraire, `NULL` si le paramètre d’index n’est pas valide, ou si le paramètre d’index est -1 et il n’existe aucun élément sélectionné dans la zone de liste déroulante.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData  
 Retourne les données associées à un élément à l’index spécifié dans la zone de liste.  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Les données associées à l’élément ; ou 0 si l’élément n’existe pas, ou si le paramètre d’index est -1 et aucun élément n’est sélectionné dans la zone de liste.  
  
##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox  
 Indique si le contrôle contient une zone d’édition.  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le contrôle contient une zone d’édition ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList  
 Indique si la zone de liste peut être redimensionnée.  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la zone de liste peut être redimensionnée ; dans le cas contraire `FALSE`. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>Notes  
 Vous pouvez activer le redimensionnement de zone de liste à l’aide de la [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) (méthode).  
  
##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem  
 Appelé par l’infrastructure lorsqu’un utilisateur sélectionne un élément dans la zone de liste.  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nItem`  
 L’index de l’élément sélectionné.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode si vous souhaitez traiter une sélection d’entrée utilisateur.  
  
##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems  
 Supprime tous les éléments à partir de la zone de liste et la zone d’édition.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem  
 Sélectionne un élément dans la zone de liste.  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
 [in] `dwData`  
 Les données associées à un élément dans la zone de liste.  
  
 [in] `lpszText`  
 La chaîne d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight  
 Définit la hauteur de la zone de liste lorsqu’il est déplacé vers le bas.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nHeight`  
 La hauteur, en pixels, de la zone de liste.  
  
### <a name="remarks"></a>Notes  
 La hauteur par défaut est 150 pixels.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit, classe](../../mfc/reference/cmfcribbonedit-class.md)
