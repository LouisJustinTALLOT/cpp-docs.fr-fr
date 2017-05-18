---
title: Classe de CMFCToolBarComboBoxButton | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxButton class
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: 30
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 43369e8869f9dd58543016bd74547b24fbe183a5
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton (classe)
Un bouton de barre d’outils qui contient un contrôle combo box ( [CComboBox (classe)](../../mfc/reference/ccombobox-class.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Construit un objet `CMFCToolBarComboBoxButton`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Ajoute un élément à la fin de la liste déroulante.|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Ajoute un élément à la liste déroulante. L’ordre des éléments dans la liste est spécifié par `Compare`.|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|Compare deux éléments. Appelé pour trier les éléments `AddSortedItems` ajoute à la liste déroulante.|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Crée un nouveau contrôle d’édition pour le bouton de la zone de liste déroulante.|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Supprime un élément de la liste déroulante.|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Retourne l’index de l’élément qui contient une chaîne spécifiée.|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Retourne un pointeur vers le bouton de la zone de liste déroulante avec un ID de commande spécifié.|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Retourne un pointeur vers le contrôle de zone de liste déroulante qui est incorporé dans le bouton de la zone de liste déroulante.|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Retourne le nombre d’éléments dans la liste déroulante de la zone de liste.|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Recherche la liste déroulante bouton de zone qui possède un ID de commande spécifié. Retourne le nombre d’éléments dans la liste déroulante zone de liste de ce bouton.|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Retourne l’index de l’élément sélectionné dans la liste déroulante de la zone de liste.|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Recherche la liste déroulante bouton de zone qui possède un ID de commande spécifié et retourne l’index de l’élément sélectionné dans la liste déroulante zone de liste de ce bouton.|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Retourne un pointeur vers le contrôle d’édition qui est incorporé dans le bouton de la zone de liste déroulante.|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Retourne la chaîne associée à un index spécifié dans la liste déroulante de la zone de liste.|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Recherche la liste déroulante bouton de zone qui possède un ID de commande spécifié et retourne la chaîne qui est associée à un index dans la liste déroulante de ce bouton.|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Retourne la valeur de 32 bits qui est associée à un index spécifié dans la liste déroulante de la zone de liste.|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Recherche la liste déroulante bouton de zone qui possède un ID de commande spécifié et retourne la valeur de 32 bits qui est associée à un index dans la liste déroulante de ce bouton.|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Recherche la liste déroulante bouton de zone qui possède un ID de commande spécifié. Récupère la valeur de 32 bits qui est associé à un index dans la liste déroulante de ce bouton et retourne la valeur comme un pointeur 32 bits.|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Renvoie le texte du contrôle d’édition de la zone de liste déroulante.|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Recherche la liste déroulante bouton de zone qui possède un ID de commande spécifié et retourne le texte de contrôle d’édition de ce bouton.|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Détermine si les boutons de zone de liste modifiable dans l’application sont centrés ou alignés avec le haut de la barre d’outils.|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Détermine si les boutons de zone de liste modifiable dans l’application ont un aspect plat.|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Supprime tous les éléments de la liste de zone et de modifier le contrôle de zone de liste déroulante.|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Sélectionne un élément dans la zone de liste déroulante en fonction de son index, la valeur 32 bits ou la chaîne et informe le contrôle de zone de liste déroulante sur la sélection.|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Recherche la liste déroulante bouton de zone qui possède un ID de commande spécifié. Appels `SelectItem` pour sélectionner un élément dans la zone de liste déroulante de ce bouton en fonction de sa chaîne, l’index ou valeur 32 bits.|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Indique si les boutons de zone de liste modifiable dans l’application sont centrés verticalement ou alignés en haut de la barre d’outils.|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Définit la hauteur de la zone de liste déroulante.|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Spécifie si les boutons de zone de liste modifiable dans l’application ont un aspect plat.|  
  
## <a name="remarks"></a>Notes  
 Pour ajouter un bouton de zone de liste modifiable à une barre d’outils, procédez comme suit :  
  
 1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.  
  
 2. Construire un `CMFCToolBarComboBoxButton` objet.  
  
 3. Dans le Gestionnaire de messages qui traite le `AFX_WM_RESETTOOLBAR` du message, remplacez le bouton fictif avec le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Pour plus d’informations, consultez [procédure pas à pas : placer le contrôle sur la barre de d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour obtenir un exemple d’un bouton de barre d’outils de zone de liste déroulante, consultez l’exemple de projet VisualStudioDemo.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes dans la `CMFCToolBarComboBoxButton` classe. L’exemple montre comment activer les zones d’édition et de liste déroulante, définir la position verticale de la zone de liste déroulante à boutons de zone dans l’application, définissez la hauteur de la zone de liste lorsqu’il est supprimé, définir l’apparence de style à deux dimensions de boutons de zone de liste modifiable dans l’application et définir le texte dans la zone d’édition du bouton de zone de liste déroulante. Cet extrait de code fait partie de la [exemple de Visual Studio démonstration](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo n °&36;](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo&#37;](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>CMFCToolBarComboBoxButton::AddItem  
 Ajoute un élément unique à la zone de liste.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszItem`  
 Le texte de l’élément à ajouter à la zone de liste.  
  
 [in] `dwData`  
 Les données associées à l’élément à ajouter à la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index du dernier élément dans la zone de liste.  
  
### <a name="remarks"></a>Remarques  
 N’utilisez pas cette méthode lorsque le style de zone de liste est trié.  
  
 Si le texte de l’élément est déjà dans la zone de liste, les nouvelles données sont stockées avec l’élément existant. La recherche respecte la casse.  
  
##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem  
 Ajoute un élément à la zone de liste dans l’ordre défini par le [comparer](#compare) méthode.  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszItem`  
 Le texte de l’élément à ajouter à la zone de liste.  
  
 [in] `dwData`  
 Les données associées à l’élément à ajouter à la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de l’élément qui a été ajouté à la zone de liste.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet d’ajouter des éléments à la zone de liste dans un ordre spécifique.  
  
##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched  
 Indique si la taille de bouton de la zone de liste déroulante peut changer.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE`.  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 Construit un [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objet.  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiID`  
 L’ID de commande du bouton Nouveau.  
  
 [in] `iImage`  
 L’index d’image de l’image associée au bouton Nouveau.  
  
 [in] `dwStyle`  
 Le style du nouveau bouton.  
  
 [in] `iWidth`  
 La largeur, en pixels, du nouveau bouton.  
  
### <a name="remarks"></a>Remarques  
 La largeur par défaut est 150 pixels.  
  
 Pour obtenir la liste des styles de bouton de barre d’outils, consultez [Styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData  
 Supprime des données définies par l’utilisateur.  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>Remarques  
 Par défaut, cette méthode ne fait rien. Substituez cette méthode dans une classe dérivée si vous souhaitez supprimer toutes les données définies par l’utilisateur.  
  
##  <a name="compare"></a>CMFCToolBarComboBoxButton::Compare  
 Compare deux chaînes.  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszItem1`  
 Première chaîne à comparer.  
  
 [in] `lpszItem2`  
 Deuxième chaîne à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui indique la relation lexicographique respectant la casse entre les chaînes. Le tableau suivant répertorie les valeurs possibles :  
  
|Valeur|Description|  
|-----------|-----------------|  
|\<0|La première chaîne est inférieure à la seconde.|  
|0|La première chaîne est égale à la seconde.|  
|>0|La première chaîne est supérieure à la seconde.|  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour modifier la façon dont les éléments sont triés dans la zone de liste.  
  
 La comparaison respecte la casse.  
  
 Cette méthode est appelée uniquement à partir de la [AddSortedItem](#addsorteditem) (méthode).  
  
##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom  
 Copie de l’état de l’objet `CMFCToolBarComboBoxButton` à l’objet actuel.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `src`  
 Objet `CMFCToolBarComboBoxButton` source.  
  
##  <a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo  
 Crée une nouvelle zone de liste déroulante pour le bouton de la zone de liste déroulante.  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParent`  
 Pointeur vers la fenêtre parent du bouton.  
  
 [in] `rect`  
 Rectangle englobant de la zone de liste déroulante.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la nouvelle zone de liste déroulante si la méthode a réussi ; dans le cas contraire, `NULL`.  
  
##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit  
 Crée une nouvelle zone d’édition pour le bouton de la zone de liste déroulante.  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParent`  
 Pointeur vers la fenêtre parent du bouton.  
  
 [in] `rect`  
 Rectangle englobant de la zone d’édition.  
  
 [in] `dwEditStyle`  
 Style de contrôle de la zone d’édition.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la nouvelle zone d’édition si la méthode a réussi ; dans le cas contraire, `NULL`.  
  
### <a name="remarks"></a>Remarques  
 L’infrastructure appelle cette méthode lorsqu’il crée une nouvelle zone d’édition pour un bouton de zone de liste déroulante. Substituez cette méthode pour modifier la [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) est créé.  
  
##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem  
 Supprime un élément spécifié dans la zone de liste.  
  
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
 Le texte de l’élément à supprimer. S’il existe plusieurs éléments avec le même texte, le premier élément est supprimé.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’élément a été situé et supprimé avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData  
 Données définies par l’utilisateur de doublons.  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>Remarques  
 Par défaut, cette méthode ne fait rien. Substituez cette méthode dans une classe dérivée si vous souhaitez copier toutes les données définies par l’utilisateur.  
  
##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow  
 Active ou désactive les zones d’édition et de liste déroulante.  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer les zones d’édition et de liste déroulante ; `FALSE` pour désactiver les zones d’édition et de liste déroulante.  
  
### <a name="remarks"></a>Remarques  
 Lorsque désactivé, les contrôles ne devient actifs et ne peut pas accepter une entrée utilisateur.  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton  
 Copie une chaîne à partir de la table de chaînes d’application au menu spécifié à l’aide de la commande de bouton de la zone de liste déroulante ID.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `menuButton`  
 Référence à un bouton de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours `TRUE`.  
  
##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem  
 Retourne l’index du premier élément dans la zone de liste qui contient une chaîne spécifiée.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszText`  
 Le texte à rechercher dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément ; ou `CB_ERR` si l’élément est introuvable.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd  
 Obtient un pointeur vers le bouton de zone de liste déroulante qui possède un ID de commande spécifié.  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 L’ID de commande d’un bouton de zone de liste déroulante.  
  
 [in] `bIsFocus`  
 `TRUE`Pour rechercher uniquement axées boutons ; `FALSE` pour rechercher tous les boutons.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un bouton de zone de liste modifiable ; ou `NULL` si le bouton n’est pas trouvé.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox  
 Retourne un pointeur vers la zone de liste déroulante dans la liste déroulante bouton de zone.  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le [CComboBox (classe)](../../mfc/reference/ccombobox-class.md) de l’objet si la méthode a réussi ; sinon `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID  
 Obtient l’ID de ressource de menu contextuel pour le bouton de la zone de liste déroulante.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de ressource raccourci menu.  
  
##  <a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount  
 Retourne le nombre d’éléments dans la zone de liste.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans la zone de liste.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll  
 Obtient le nombre d’éléments dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifié.  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 L’ID de commande d’un bouton de zone de liste déroulante.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans la zone de liste ; dans le cas contraire, `CB_ERR` si le bouton de la zone de liste déroulante est introuvable.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel  
 Obtient l’index de l’élément actuellement sélectionné dans la zone de liste.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément actuellement sélectionné dans la zone de liste ; ou `CB_ERR` si aucun élément n’est sélectionné.  
  
### <a name="remarks"></a>Remarques  
 L’index de zone de liste est de base zéro.  
  
##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll  
 Retourne l’index de l’élément actuellement sélectionné dans la zone de liste déroulante bouton de zone qui possède un ID de commande spécifié.  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 L’ID de commande d’un bouton de zone de liste déroulante.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément actuellement sélectionné dans la zone de liste ; dans le cas contraire, `CB_ERR` si aucun élément n’est sélectionné ou un bouton de zone de liste déroulante est introuvable.  
  
### <a name="remarks"></a>Notes  
 L’index de zone de liste est de base zéro.  
  
##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl  
 Retourne un pointeur vers la zone d’édition dans la liste déroulante bouton de zone.  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la zone d’édition si la méthode a réussi ; dans le cas contraire, `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd  
 Retourne le handle de fenêtre pour la zone de liste déroulante.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de fenêtre, ou `NULL` si la zone de liste déroulante n’est pas associée à un objet window.  
  
##  <a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem  
 Retourne la chaîne associée à un élément à l’index spécifié dans la zone de liste.  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la chaîne associée à l’élément ; dans le cas contraire, `NULL` si le paramètre d’index n’est pas valide ou si le paramètre d’index est -1 et il n’existe aucun élément sélectionné dans la zone de liste déroulante.  
  
### <a name="remarks"></a>Notes  
 Un paramètre d’index de -1 retourne la chaîne de l’élément actuellement sélectionné.  
  
##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll  
 Retourne la chaîne associée à un élément à l’index spécifié dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifié.  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 L’ID de commande d’un bouton de zone de liste déroulante.  
  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la chaîne de l’élément si la méthode a réussi ; dans le cas contraire, `NULL` si l’index n’est pas valide, un bouton de zone de liste déroulante n’est pas trouvée, ou si l’index est -1 et il n’existe aucun élément sélectionné dans la zone de liste déroulante.  
  
### <a name="remarks"></a>Remarques  
 Une valeur d’index de -1 retourne la chaîne de l’élément actuellement sélectionné.  
  
##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData  
 Retourne les données associées à un élément à un index spécifique dans la zone de liste.  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Les données associées à l’élément ; ou 0 si l’élément n’existe pas.  
  
### <a name="remarks"></a>Remarques  
 Un paramètre d’index de -1 retourne les données associées à l’élément actuellement sélectionné.  
  
##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll  
 Retourne les données associées à un élément à un index spécifique dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifique.  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 L’ID de commande d’un bouton de zone de liste déroulante.  
  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Les données associées à l’élément si la méthode a réussi ; Sinon, 0 si l’index spécifié n’est pas valide, ou CB_ERR si la liste déroulante zone de bouton est introuvable.  
  
### <a name="remarks"></a>Remarques  
 Un paramètre d’index de -1 retourne les données associées à l’élément actuellement sélectionné.  
  
##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 Retourne les données associées à un élément à un index spécifique dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifique. Ces données sont retournées en tant que pointeur.  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 ID de commande du bouton de zone de liste déroulante.  
  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur associé à l’élément si la méthode a réussi ; Sinon, -1 si une erreur se produit, ou `NULL` si le bouton de la zone de liste déroulante est introuvable.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt  
 Retourne la chaîne d’invite pour la liste déroulante bouton de zone.  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La chaîne d’invite.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode n’est actuellement pas implémentée.  
  
##  <a name="gettext"></a>CMFCToolBarComboBoxButton::GetText  
 Obtient le texte dans la zone d’édition.  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le texte dans la zone d’édition.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll  
 Obtient le texte dans la zone d’édition d’un bouton de zone de liste déroulante qui possède un ID de commande spécifié.  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 L’ID de commande d’un bouton de zone de liste déroulante spécifique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le texte dans la zone d’édition si la méthode a réussi ; dans le cas contraire, `NULL`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus  
 Indique si la zone de liste déroulante possède actuellement le focus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la zone de liste déroulante a actuellement le focus ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode retourne également `TRUE` si n’importe quelle fenêtre enfant de la zone de liste déroulante a actuellement le focus.  
  
##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert  
 Renvoie la position verticale de boutons de zone de liste modifiable dans l’application.  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si les boutons sont centrées ; `FALSE` si les boutons sont alignés en haut.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode  
 Retourne l’apparence du style à deux dimensions de boutons de zone de liste modifiable dans l’application.  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si les boutons ont un style à deux dimensions ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Le style à deux dimensions par défaut pour les boutons de zone de liste déroulante est`FALSE.`  
  
##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf  
 Indique si le handle spécifié est associé avec le bouton de la zone de liste déroulante, ou l’un de ses enfants.  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hwnd`  
 Un handle de fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le handle est associé le bouton de la zone de liste déroulante, ou l’un de ses enfants ; dans le cas contraire, `FALSE`.  
  
##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton  
 Indique si le bouton de la zone de liste déroulante réside sur un panneau de ruban.  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette méthode retourne toujours `FALSE`, ce qui signifie que la liste déroulante bouton de zone n’est jamais affiché dans un panneau de ruban.  
  
##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible  
 Retourne l’état de visibilité de la liste déroulante bouton de zone.  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’état de visibilité du bouton de zone de liste déroulante.  
  
##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand  
 Indique si le bouton de la zone de liste déroulante traite le message.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iNotifyCode`  
 Le message de notification qui est associé à la commande.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le bouton de la zone de liste déroulante traite le message.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 Appelé par l’infrastructure lorsque le bouton est ajouté à la **personnaliser** boîte de dialogue.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize  
 Appelé par l’infrastructure pour calculer la taille du bouton.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Le contexte de périphérique qui affiche le bouton de la zone de liste déroulante.  
  
 [in] `sizeDefault`  
 La taille par défaut du bouton de zone de liste déroulante.  
  
 [in] `bHorz`  
 L’état d’ancrage de la barre d’outils parent. `TRUE`Lorsque la barre d’outils est ancrée horizontalement et `FALSE` lorsque la barre d’outils est ancrée verticalement.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `SIZE` structure qui contient les dimensions de la zone de liste déroulante du bouton de zone, en pixels.  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd  
 Appelé par l’infrastructure lorsque le bouton de la zone de liste déroulante est inséré dans une barre d’outils.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParent`  
 Pointeur vers la nouvelle barre d’outils parent.  
  
##  <a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick  
 Appelé par l’infrastructure lorsque l’utilisateur clique sur le bouton de la zone de liste déroulante.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWnd`  
 Pointeur vers la fenêtre parente de la liste déroulante du bouton de zone.  
  
 [in] `bDelay`  
 Réservé pour une utilisation dans une classe dérivée.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode gère l’événement. dans le cas contraire, `FALSE`.  
  
##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor  
 Appelé par l’infrastructure lorsque l’utilisateur modifie la couleur de la barre d’outils parent pour définir la liste déroulante couleur de la zone.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Le contexte de périphérique qui affiche le bouton de la zone de liste déroulante.  
  
 [in] `nCtlColor`  
 Non utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers le pinceau de l’infrastructure utilise pour peindre l’arrière-plan du bouton de zone de liste déroulante.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode définit également la couleur de texte de bouton zone modifiable.  
  
##  <a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw  
 Appelé par l’infrastructure pour dessiner le bouton de la zone de liste déroulante en utilisant les options et les styles spécifiés.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `Pdc`  
 Le contexte de périphérique qui affiche le bouton.  
  
 [in] `rect`  
 Le rectangle englobant du bouton.  
  
 [in] `pImages`  
 La collection d’images qui est associée au bouton.  
  
 [in] `bHorz`  
 L’état d’ancrage de la barre d’outils parent. `TRUE`Lorsque la barre d’outils est ancrée horizontalement et `FALSE` lorsque la barre d’outils est ancrée verticalement.  
  
 [in] `bCustomizeMode`  
 Si l’application est en mode de personnalisation.  
  
 [in] `bHighlight`  
 Si vous souhaitez dessiner le bouton de zone de liste déroulante mis en surbrillance.  
  
 [in] `bDrawBorder`  
 Si vous souhaitez dessiner le bouton de la zone de liste déroulante avec une bordure.  
  
 [in] `bGrayDisabledButtons`  
 `TRUE`Pour dessiner des boutons désactivés grisés ; `FALSE` à utiliser le désactivé de l’image de collection.  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 Appelé par l’infrastructure pour dessiner le bouton de la zone de liste déroulante dans le **commandes** volet de la **personnaliser** boîte de dialogue.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Le contexte de périphérique qui affiche le bouton de la zone de liste déroulante.  
  
 [in] `rect`  
 Le rectangle englobant d’un bouton de zone de liste déroulante.  
  
 [in] `bSelected`  
 `TRUE`Si le bouton de zone de liste déroulante est sélectionné ; dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur, en pixels, du bouton de zone de liste déroulante.  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 Appelé par l’infrastructure pour affecter à la liste déroulante zone bouton police lors de la modification de la police de l’application.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove  
 Appelée par l’infrastructure pour modifier l’emplacement du bouton de zone de liste déroulante lorsque la barre d’outils parent se déplace.  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow  
 Appelé par l’infrastructure lorsque le bouton de la zone de liste déroulante est masqué ou affiché.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bShow`  
 Si vous souhaitez masquer ou afficher le bouton de la zone de liste déroulante.  
  
##  <a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize  
 Appelée par l’infrastructure pour modifier la taille du bouton de zone de liste déroulante lors de la barre d’outils parent change de taille.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iSize`  
 La nouvelle largeur du bouton de zone de liste déroulante.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip  
 Appelé par l’infrastructure lorsque l’utilisateur modifie l’info-bulle pour le bouton de la zone de liste déroulante.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParent`  
 Pointeur vers la fenêtre parente pour le bouton de la zone de liste déroulante.  
  
 [in] `iButtonIndex`  
 ID de la liste déroulante du bouton de zone.  
  
 [in] `wndToolTip`  
 L’info-bulle à associer avec le bouton de la zone de liste déroulante.  
  
 [in] `str`  
 Le texte info-bulle.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode gère l’événement. dans le cas contraire, `FALSE`.  
  
##  <a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems  
 Supprime tous les éléments dans les zones de liste et les modifier.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Notes  
 Supprime tous les éléments de la liste de zone et de modifier le contrôle de zone de liste déroulante.  
  
##  <a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem  
 Sélectionne un élément dans la zone de liste.  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro d’un élément dans la zone de liste.  
  
 [in] `bNotify`  
 `TRUE`pour notifier le bouton de la zone de liste déroulante de la sélection ; dans le cas contraire `FALSE`.  
  
 [in] `dwData`  
 Les données associées à un élément dans la zone de liste.  
  
 [in] `lpszText`  
 Le texte d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll  
 Sélectionne un élément dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifié.  
  
```  
static BOOL SelectItemAll(
    UINT uiCmd,  
    int iIndex);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    DWORD_PTR dwData);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 ID de commande du bouton de zone de liste déroulante qui contient la zone de liste.  
  
 [in] `iIndex`  
 Index de base zéro de l’élément dans la zone de liste. La valeur -1 supprime la sélection actuelle dans la zone de liste et efface la zone d’édition.  
  
 [in] `dwData`  
 Les données d’un élément dans la zone de liste.  
  
 [in] `lpszText`  
 Le texte d’un élément dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize  
 Lit de cet objet dans une archive ou écrit dans une archive.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in, out] `ar`  
 Le `CArchive` objet à sérialiser.  
  
### <a name="remarks"></a>Remarques  
 Les paramètres dans les `CArchive` déterminer si cette méthode lit ou écrit dans l’archive.  
  
##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData  
 Remplit spécifié `CAccessibilityData` à l’aide de données d’accessibilité à partir du bouton de zone de liste déroulante.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pParent`  
 La fenêtre parent du bouton de zone de liste déroulante.  
  
 [out] `data`  
 Un `CAccessibilityData` objet qui reçoit l’accessibilité des données à partir du bouton de zone de liste déroulante.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert  
 Définit la position verticale de boutons de zone de liste déroulante de l’application.  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bCenterVert`  
 `TRUE`au centre du bouton de zone de liste déroulante dans la barre d’outils ; `FALSE` pour aligner le bouton de la zone de liste déroulante en haut de la barre d’outils.  
  
### <a name="remarks"></a>Remarques  
 Par défaut, les boutons de zone de liste déroulante sont alignés en haut.  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID  
 Définit l’ID de ressource de menu contextuel de la liste déroulante bouton de zone.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiResID`  
 L’ID de ressource raccourci menu.  
  
##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight  
 Définit la hauteur de la zone de liste lorsqu’il est déplacé vers le bas.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nHeight`  
 La hauteur, en pixels, de la zone de liste.  
  
### <a name="remarks"></a>Notes  
 La hauteur par défaut est 150 pixels.  
  
##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode  
 Définit l’apparence du style à deux dimensions de boutons de zone de liste déroulante de l’application.  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bFlat`  
 `TRUE`Pour obtenir une apparence de style à deux dimensions ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Le style à deux dimensions par défaut pour les boutons de zone de liste déroulante est `FALSE`.  
  
##  <a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle  
 Définit le style spécifié pour la liste déroulante bouton de zone et redessine le contrôle s’il n’est pas désactivé.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nStyle`  
 Combinaison de bits (OR) des styles de barre d’outils.  
  
### <a name="remarks"></a>Remarques  
 Pour obtenir la liste des styles de bouton de barre d’outils, consultez [Styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>CMFCToolBarComboBoxButton::SetText  
 Définit le texte dans la zone de liste déroulante bouton de zone.  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszText`  
 Pointeur vers une chaîne contenant le texte de la zone d’édition.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton (classe)](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox (classe)](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)




