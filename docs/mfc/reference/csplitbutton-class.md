---
title: Classe de CSplitButton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
dev_langs:
- C++
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac4241bb19c6abc0fbbf489bf4efb43f56ede72e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374222"
---
# <a name="csplitbutton-class"></a>Classe de CSplitButton
La `CSplitButton` classe représente un contrôle bouton partagé. Le contrôle bouton partagé exécute un comportement par défaut lorsqu’un utilisateur clique sur la partie principale du bouton et affiche un menu déroulant lorsqu’un utilisateur clique sur la flèche déroulante du bouton.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSplitButton : public CButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSplitButton::CSplitButton](#csplitbutton)|Construit un objet `CSplitButton`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSplitButton::Create](#create)|Crée un contrôle bouton partagé avec des styles spécifiés et l’attache à actuel `CSplitButton` objet.|  
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Définit le menu déroulant qui s’affiche quand un utilisateur clique sur la flèche déroulante du contrôle de bouton Fractionner en cours.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](#ondropdown)|Gère la `BCN_DROPDOWN` notification envoyé par le système lorsqu’un utilisateur clique sur la flèche déroulante du contrôle de bouton Fractionner en cours.|  
  
## <a name="remarks"></a>Notes  
 Le `CSplitButton` classe est dérivée de la [CButton](../../mfc/reference/cbutton-class.md) classe. Le contrôle bouton partagé est un contrôle bouton dont le style est `BS_SPLITBUTTON`. Il affiche un menu personnalisé lorsqu’un utilisateur clique sur la flèche déroulante. Pour plus d’informations, consultez la `BS_SPLITBUTTON` et `BS_DEFSPLITBUTTON` styles dans [les Styles de bouton](http://msdn.microsoft.com/library/windows/desktop/bb775951).  
  
 La figure suivante représente une boîte de dialogue qui contient un contrôle pager et un contrôle bouton partagé (1). La flèche déroulante (2) a déjà été cliqué et le sous-menu (3) s’affiche.  
  
 ![Boîte de dialogue avec un bouton partagé et un contrôle pager. ] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxcmn.h  
  
 Cette classe est pris en charge dans [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] et versions ultérieures.  
  
 Exigences supplémentaires pour cette classe sont décrites dans [Build Configuration requise pour les contrôles communs Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="create"></a>  CSplitButton::Create  
 Crée un contrôle bouton partagé avec des styles spécifiés et l’attache à actuel `CSplitButton` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `dwStyle`|Combinaison de bits (OR) des styles à appliquer au contrôle. Pour plus d’informations, consultez [les Styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
|[in] `rect`|Une référence à un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui contient la position et la taille du contrôle.|  
|[in] `pParentWnd`|Un pointeur non null pour un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parente du contrôle.|  
|[in] `nID`|L’ID du contrôle.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton  
 Construit un objet `CSplitButton`. Les paramètres du constructeur spécifient un sous-menu qui s’affiche quand un utilisateur clique sur la flèche déroulante du contrôle bouton partagé.  
  
```  
CSplitButton();

 
CSplitButton(
    UINT nMenuId,   
    UINT nSubMenuId)  
CSplitButton(CMenu* pMenu)  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `nMenuId`|L’ID de ressource de la barre de menus.|  
|[in] `nSubMenuId`|L’ID de ressource d’un sous-menu.|  
|[in] `pMenu`|Un pointeur vers un [CMenu](../../mfc/reference/cmenu-class.md) objet qui spécifie un sous-menu. Le `CSplitButton` supprime l’objet le `CMenu` objet et qui lui est associée `HMENU` lorsque le `CSplitButton` objet devient hors de portée.|  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CSplitButton::Create](#create) méthode pour créer un contrôle bouton partagé et l’attacher à la `CSplitButton` objet.  
  
##  <a name="ondropdown"></a>  CSplitButton::OnDropDown  
 Gère la `BCN_DROPDOWN` notification envoyé par le système lorsqu’un utilisateur clique sur la flèche déroulante du contrôle de bouton Fractionner en cours.  
  
```  
afx_msg void OnDropDown(
    NMHDR* pNMHDR,   
    LRESULT* pResult);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `pNMHDR`|Pointeur vers un [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) structure qui contient des informations sur la [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) notification.|  
|[out] `pResult`|(Pas utilisé ; aucune valeur n’est retournée.) Valeur de retour de la [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) notification.|  
  
### <a name="remarks"></a>Notes  
 Lorsque l’utilisateur clique sur la flèche de déroulement sur un contrôle bouton partagé, le système envoie un `BCN_DROPDOWN` notification d’un message, ce qui le `OnDropDown` descripteurs de méthode. Toutefois, le `CSplitButton` objet ne transfère pas le `BCN_DROPDOWN` notification pour le contrôle qui contient le contrôle bouton partagé. Par conséquent, le contrôle conteneur ne peut pas prendre en charge une action personnalisée en réponse à la notification.  
  
 Pour implémenter une action personnalisée qui prend en charge le contrôle conteneur, utilisez un [CButton](../../mfc/reference/cbutton-class.md) objet avec un style de `BS_SPLITBUTTON` au lieu d’un `CSplitButton` objet. Ensuite implémenter un gestionnaire pour le `BCN_DROPDOWN` notification dans le `CButton` objet. Pour plus d’informations, consultez [les Styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 Pour implémenter une action personnalisée que le bouton partagé contrôle lui-même prend en charge, utilisez [réflexion de message](../../mfc/tn062-message-reflection-for-windows-controls.md). Dérivez votre propre classe de la `CSplitButton` classe et nommez-le, par exemple, CMySplitButton. Puis ajoutez la table des messages suivants à votre application pour gérer les `BCN_DROPDOWN` notification :  
  
```  
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)  
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)  
END_MESSAGE_MAP()  
```  
  
##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu  
 Définit le menu déroulant qui s’affiche quand un utilisateur clique sur la flèche déroulante du contrôle de bouton Fractionner en cours.  
  
```  
void SetDropDownMenu(
    UINT nMenuId,   
    UINT nSubMenuId);  
  
void SetDropDownMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `nMenuId`|L’ID de ressource de la barre de menus.|  
|[in] `nSubMenuId`|L’ID de ressource d’un sous-menu.|  
|[in] `pMenu`|Pointeur vers un [CMenu](../../mfc/reference/cmenu-class.md) objet qui spécifie un sous-menu. Le `CSplitButton` supprime l’objet le `CMenu` objet et qui lui est associée `HMENU` lorsque le `CSplitButton` objet devient hors de portée.|  
  
### <a name="remarks"></a>Notes  
 Le `nMenuId` paramètre identifie une barre de menus, qui est une liste horizontale d’éléments de barre de menus. Le `nSubMenuId` paramètre est un nombre index de base zéro qui identifie un sous-menu qui correspond à la liste déroulante d’éléments de menu associé à chaque élément de barre de menus. Par exemple, une application de type a un menu qui contient les éléments de barre de menu « Fichier », « Modifier » et « Help ». L’élément de barre de menu « Fichier » a un sous-menu qui contient les éléments de menu « Ouvrir », « Fermer » et « Exit ». Lorsque vous cliquez sur la flèche déroulante du contrôle bouton partagé, le contrôle affiche le sous-menu spécifié, pas la barre de menus.  
  
 La figure suivante représente une boîte de dialogue qui contient un contrôle pager et un contrôle bouton partagé (1). La flèche déroulante (2) a déjà été cliqué et le sous-menu (3) s’affiche.  
  
 ![Boîte de dialogue avec un bouton partagé et un contrôle pager. ] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
### <a name="example"></a>Exemple  
 La première instruction dans l’exemple de code suivant illustre la [CSplitButton::SetDropDownMenu](#setdropdownmenu) (méthode). Nous avons créé le menu avec Visual Studio éditeur de ressources, ce qui l’a nommé automatiquement l’ID de barre de menus, `IDR_MENU1`. Le `nSubMenuId` paramètre, qui est égale à zéro, fait référence au sous-menu uniquement de la barre de menus.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CSplitButton](../../mfc/reference/csplitbutton-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CButton, classe](../../mfc/reference/cbutton-class.md)
