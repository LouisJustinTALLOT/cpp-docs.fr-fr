---
title: Classe de CMDITabInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
dev_langs:
- C++
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b3676db7cedbca1fe831e44c9ff7cf018360adc
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040051"
---
# <a name="cmditabinfo-class"></a>Classe de CMDITabInfo
Le `CMDITabInfo` classe est utilisée pour passer des paramètres à [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) (méthode). Définissez les membres de cette classe de manière à contrôler le comportement des groupes avec onglet MDI.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMDITabInfo   
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CMDITabInfo::CMDITabInfo`|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMDITabInfo::Serialize](#serialize)|Lit ou écrit cet objet dans une archive.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CMDITabInfo::m_bActiveTabCloseButton ;](#m_bactivetabclosebutton_)|Spécifie si un **fermer** bouton est affiché sur l’étiquette de l’onglet actif.|  
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Spécifie si les onglets MDI de couleur.|  
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Spécifie si le groupe d’onglets affiche un menu contextuel qui affiche une liste des documents ouverts ou affiche des boutons de défilement.|  
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Spécifie si l’utilisateur peut échanger les positions des onglets en faisant glisser.|  
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Spécifie si les onglets ont un frame plat.|  
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Spécifie si chaque étiquette de l’onglet affiche une **fermer** bouton.|  
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Spécifie si les info-bulles personnalisées sont activées.|  
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Spécifie s’il faut afficher les icônes sous les onglets MDI.|  
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Spécifie la taille de la bordure de chaque fenêtre de l’onglet.|  
|[CMDITabInfo::m_style](#m_style)|Spécifie le style des étiquettes d’onglet.|  
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Spécifie si les étiquettes d’onglets sont situés en haut ou bas de la page.|  
  
## <a name="remarks"></a>Notes  
 Cette classe spécifie les paramètres des groupes d’onglet MDI qui crée de l’infrastructure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir les valeurs des variables membres différents dans `CMDITabInfo` classe.  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxmdiclientareawnd.h  
  
##  <a name="m_bactivetabclosebutton_"></a>  CMDITabInfo::m_bActiveTabCloseButton ;  
 Spécifie si un **fermer** bouton est affiché sur l’étiquette de l’onglet actif.  
  
```  
BOOL m_bActiveTabCloseButton;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, l’étiquette de l’onglet actif affichera un **fermer** bouton. Le **fermer** bouton sera supprimé de l’angle supérieur droit de la zone d’onglet. Dans le cas contraire, l’étiquette de l’onglet actif n’affichera pas un **fermer** bouton. Le **fermer** bouton s’affiche dans le coin supérieur droit de la zone d’onglet.  
  
##  <a name="m_bautocolor"></a>  CMDITabInfo::m_bAutoColor  
 Spécifie si chaque onglet MDI possède sa propre couleur.  
  
```  
BOOL m_bAutoColor;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, chaque onglet aura sa propre couleur. Le jeu de couleurs est géré par la bibliothèque MFC. Dans le cas contraire, les onglets sont affichés en blanc. La valeur par défaut est `FALSE`.  
  
##  <a name="m_bdocumentmenu"></a>  CMDITabInfo::m_bDocumentMenu  
 Spécifie si chaque onglet affiche un menu contextuel qui affiche une liste des documents ouverts sur le bord droit de la zone d’onglet.  
  
```  
BOOL m_bDocumentMenu;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, windows de chaque onglet affiche un menu contextuel qui affiche une liste des documents ouverts sur le bord droit de la zone d’onglet ; Dans le cas contraire, la fenêtre de l’onglet affiche les boutons de défilement sur le bord droit de la zone d’onglet. La valeur par défaut est `FALSE`.  
  
##  <a name="m_benabletabswap"></a>  CMDITabInfo::m_bEnableTabSwap  
 Spécifie si l’utilisateur peut échanger les positions des onglets en faisant glisser.  
  
```  
BOOL m_bEnableTabSwap;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, l’utilisateur peut modifier les positions des onglets en faisant glisser les onglets. Dans le cas contraire, l’utilisateur ne peut pas modifier les positions des onglets. La valeur par défaut est `TRUE`.  
  
##  <a name="m_bflatframe"></a>  CMDITabInfo::m_bFlatFrame  
 Spécifie si chaque fenêtre de l’onglet possède un cadre plat.  
  
```  
BOOL m_bFlatFrame;  
```  
  
##  <a name="m_btabclosebutton"></a>  CMDITabInfo::m_bTabCloseButton  
 Spécifie si chaque fenêtre de l’onglet affiche une **fermer** bouton.  
  
```  
BOOL m_bTabCloseButton;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, chaque fenêtre de l’onglet affiche les **fermer** bouton sur le bord droit de l’onglet. Dans le cas contraire, le **fermer** bouton n’est pas affiché. La valeur par défaut est `TRUE`.  
  
##  <a name="m_btabcustomtooltips"></a>  CMDITabInfo::m_bTabCustomTooltips  
 Spécifie si les onglets affichent des info-bulles.  
  
```  
BOOL m_bTabCustomTooltips;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, l’application envoie une `AFX_WM_ON_GET_TAB_TOOLTIP` message au frame principal. Vous pouvez gérer ce message à l’aide de la `ON_REGISTERED_MESSAGE` (macro).  
  
##  <a name="m_btabicons"></a>  CMDITabInfo::m_bTabIcons  
 Spécifie s’il faut afficher les icônes sous les onglets MDI.  
  
```  
BOOL m_bTabIcons;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, icônes sont affichées sous chaque onglet MDI. Dans le cas contraire, les icônes ne sont pas affichés sur les onglets. La valeur par défaut est `FALSE`.  
  
##  <a name="m_ntabbordersize"></a>  CMDITabInfo::m_nTabBorderSize  
 Spécifie la taille de la bordure, en pixels, de chaque fenêtre de l’onglet.  
  
```  
int m_nTabBorderSize;  
```  
  
### <a name="remarks"></a>Notes  
 [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) renvoie la valeur par défaut.  
  
##  <a name="m_style"></a>  CMDITabInfo::m_style  
 Spécifie le style des étiquettes d’onglet.  
  
```  
CMFCTabCtrl::Style m_style  
```  
  
### <a name="remarks"></a>Notes  
 Spécifiez un des styles pour les étiquettes d’onglets suivants :  
  
 `STYLE_3D`  
 Style 3D.  
  
 `STYLE_3D_ONENOTE`  
 Style Microsoft OneNote.  
  
 `STYLE_3D_VS2005`  
 Style de Microsoft Visual Studio 2005.  
  
 `STYLE_3D_SCROLLED`  
 Style 3D avec des étiquettes d’onglets rectangle.  
  
 `STYLE_FLAT_SHARED_HORZ_SCROLL`  
 Style à deux dimensions avec barre de défilement horizontale partagé.  
  
 `STYLE_3D_ROUNDED_SCROLL`  
 Style 3D avec des étiquettes d’onglets round.  
  
##  <a name="m_tablocation"></a>  CMDITabInfo::m_tabLocation  
 Spécifie si les étiquettes d’onglets sont situés en haut ou bas de la page.  
  
```  
CMFCTabCtrl::Location m_tabLocation;  
```  
  
### <a name="remarks"></a>Notes  
 S’appliquent aux onglets un des indicateurs d’emplacement suivants :  
  
-   LOCATION_BOTTOM : les étiquettes d’onglets figurent au bas de la page.  
  
-   LOCATION_TOP : les étiquettes d’onglets figurent en haut de la page  
  
##  <a name="serialize"></a>  CMDITabInfo::Serialize  
 Lit ou écrit cet objet à partir d’une archive dans une archive.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *ar*  
 A [CArchive (classe)](../../mfc/reference/carchive-class.md) objet à sérialiser.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)   
 [Groupes avec onglet MDI](../../mfc/mdi-tabbed-groups.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
