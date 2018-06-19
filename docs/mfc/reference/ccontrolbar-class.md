---
title: CControlBar (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
dev_langs:
- C++
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 443e55ab69bc9585a780374a82d5d99b0fd9eef9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356030"
---
# <a name="ccontrolbar-class"></a>CControlBar Class
La classe de base pour les classes de barre de contrôle [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md), et [ COleResizeBar](../../mfc/reference/coleresizebar-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CControlBar : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CControlBar::CControlBar](#ccontrolbar)|Construit un objet `CControlBar`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Retourne la taille d’une barre de contrôle dynamique comme une [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.|  
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Retourne la taille de la barre de contrôle comme un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.|  
|[CControlBar::CalcInsideRect](#calcinsiderect)|Retourne les dimensions actuelles de la zone de barre de contrôle ; y compris les bordures.|  
|[CControlBar::DoPaint](#dopaint)|Restitue les bordures et la barre de redimensionnement de la barre de contrôle.|  
|[CControlBar::DrawBorders](#drawborders)|Affiche les bordures de la barre de contrôle.|  
|[CControlBar::DrawGripper](#drawgripper)|Affiche la barre de redimensionnement de la barre de contrôle.|  
|[CControlBar::EnableDocking](#enabledocking)|Permet à une barre de contrôle doit être ancré ou flottant.|  
|[CControlBar::GetBarStyle](#getbarstyle)|Récupère les paramètres de style de barre de contrôle.|  
|[CControlBar::GetBorders](#getborders)|Récupère les valeurs de la bordure de la barre de contrôle.|  
|[CControlBar::GetCount](#getcount)|Retourne le nombre de non - `HWND` éléments dans la barre de contrôle.|  
|[CControlBar::GetDockingFrame](#getdockingframe)|Retourne un pointeur vers le frame auquel une barre de contrôle est ancrée.|  
|[CControlBar::IsFloating](#isfloating)|Retourne une valeur différente de zéro si la barre de contrôle en question est une barre de contrôle flottante.|  
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Appelle les gestionnaires de l’interface utilisateur de la commande.|  
|[Fonctions CControlBar::SetBarStyle](#setbarstyle)|Modifie les paramètres de style de barre de contrôle.|  
|[CControlBar::SetBorders](#setborders)|Définit les valeurs de la bordure de la barre de contrôle.|  
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Modifie le propriétaire de la place d’une barre de contrôle.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Si elle est différente de zéro, le `CControlBar` objet est supprimé lorsque la barre de contrôle de Windows est détruite.|  
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Le propriétaire de la place de la barre de contrôle.|  
  
## <a name="remarks"></a>Notes  
 Une barre de contrôle est une fenêtre qui est généralement alignée à gauche ou à droite d’une fenêtre frame. Il peut contenir des éléments enfants qui sont soit `HWND`- en fonction des contrôles, qui sont des fenêtres qui génèrent et répondent aux messages de Windows, ou non - `HWND`-en fonction des éléments qui ne sont pas des fenêtres et sont gérés par le code d’application ou le code d’infrastructure. Zones de liste et les contrôles d’édition sont des exemples de `HWND`- en fonction des contrôles ; les volets de barre d’état et des boutons de bitmap sont des exemples de non - `HWND`-en fonction des contrôles.  
  
 Windows de la barre de contrôle sont généralement les fenêtres enfants d’une fenêtre frame parente et sont généralement frères de la vue du client ou du client MDI de la fenêtre frame. A `CControlBar` objet utilise plus d’informations sur le rectangle client de la fenêtre parente pour se positionner. Il informe ensuite la fenêtre parente à la quantité d’espace reste non alloué dans la zone cliente de la fenêtre parente.  
  
 Pour plus d’informations sur `CControlBar`, consultez :  
  
- [Barres de contrôles](../../mfc/control-bars.md)  
  
- [Note technique 31 : Barres de contrôles](../../mfc/tn031-control-bars.md).  
  
-   L’article de la Base de connaissances Q242577 : PRB : mise à jour de commande UI gestionnaires ne fonctionnent pas de Menu attaché à une boîte de dialogue  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxext.h  
  
##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout  
 L’infrastructure appelle cette fonction membre pour calculer les dimensions d’une barre d’outils dynamique.  
  
```  
virtual CSize CalcDynamicLayout(
    int nLength,  
    DWORD nMode);
```  
  
### <a name="parameters"></a>Paramètres  
 `nLength`  
 La dimension demandée de la barre de contrôle horizontale ou verticale, en fonction de `dwMode`.  
  
 `nMode`  
 Les indicateurs prédéfinis suivants sont utilisés pour déterminer la hauteur et la largeur de la barre de contrôle dynamique. Utilisez l’opérateur de bits OR (&#124;) (opérateur) pour combiner les indicateurs.  
  
|Indicateurs de mode de disposition|Cela signifie que|  
|-----------------------|-------------------|  
|`LM_STRETCH`|Indique si la barre de contrôle doit être étirée pour la taille de l’image. Définir si la barre n’est pas une barre d’ancrage (non disponible pour la station d’accueil). Non défini lors de la barre est ancrée ou flottant (disponible pour la station d’accueil). Si la valeur, `LM_STRETCH` ignore `nLength` et retourne les dimensions basées sur les `LM_HORZ` état. `LM_STRETCH` fonctionne de façon similaire à la `bStretch` paramètre utilisé dans [CalcFixedLayout](#calcfixedlayout); consultez cette fonction membre pour plus d’informations sur la relation entre l’étirement et l’orientation.|  
|`LM_HORZ`|Indique que la barre est orientée horizontalement ou verticalement. Définit si la barre est orientée horizontalement, et si elle est orienté verticalement, il n’est pas définie. `LM_HORZ` fonctionne de façon similaire à la `bHorz` paramètre utilisé dans [CalcFixedLayout](#calcfixedlayout); consultez cette fonction membre pour plus d’informations sur la relation entre l’étirement et l’orientation.|  
|**LM_MRUWIDTH**|Utilisés récemment largeur dynamique. Ignore `nLength` paramètre et utilise le mémorisés utilisés le plus récemment largeur.|  
|`LM_HORZDOCK`|Horizontal ancré Dimensions. Ignore `nLength` paramètre et retourne la taille dynamique avec la plus grande largeur.|  
|`LM_VERTDOCK`|Vertical ancré Dimensions. Ignore `nLength` paramètre et retourne la taille dynamique avec la plus grande hauteur.|  
|`LM_LENGTHY`|Définir si `nLength` indique la hauteur (axe Y) au lieu de la largeur.|  
|`LM_COMMIT`|Réinitialise **LM_MRUWIDTH** à la largeur actuelle de la barre de contrôle flottante.|  
  
### <a name="return-value"></a>Valeur de retour  
 La barre de contrôle de taille, en pixels, d’un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction membre pour fournir votre propre disposition dynamique dans les classes dérivées de `CControlBar`. Les classes MFC dérivées de `CControlBar`, tel que [CToolbar](../../mfc/reference/ctoolbar-class.md), remplacez cette fonction membre et de fournir leur propre implémentation.  
  
##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout  
 Appelez cette fonction membre pour calculer la taille horizontale de la barre de contrôle.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 `bStretch`  
 Indique si la barre doit être étirée pour la taille de l’image. Le `bStretch` paramètre est différente de zéro lorsque la barre n’est pas une barre d’ancrage (non disponible pour la station d’accueil) et 0 lorsqu’il est ancré ou flottant (disponible pour la station d’accueil).  
  
 `bHorz`  
 Indique que la barre est orientée horizontalement ou verticalement. Le `bHorz` paramètre est différente de zéro si la barre est orientée horizontalement et 0 s’il est orienté verticalement.  
  
### <a name="return-value"></a>Valeur de retour  
 La barre de contrôle de taille, en pixels, d’un `CSize` objet.  
  
### <a name="remarks"></a>Notes  
 Barres de contrôle tels que les barres d’outils peuvent d’étendre horizontalement ou verticalement pour accueillir les boutons contenus dans la barre de contrôle.  
  
 Si `bStretch` est **TRUE**, étendre la dimension de l’orientation, fournie par `bHorz`. En d’autres termes, si `bHorz` est **FALSE**, la barre de contrôle est étirée verticalement. Si `bStretch` est **FALSE**, aucune extension se produit. Le tableau suivant montre les permutations possibles et les styles de barre de contrôle résultante, de `bStretch` et `bHorz`.  
  
|bStretch|bHorz|Étirement|Orientation|Ne pas d’ancrage d’ancrage|  
|--------------|-----------|----------------|-----------------|--------------------------|  
|**TRUE**|**TRUE**|Étirement horizontal|Orientation horizontale|Pas d’ancrage|  
|**TRUE**|**FALSE**|Étirement vertical|Orientation verticale|Pas d’ancrage|  
|**FALSE**|**TRUE**|Aucune extension disponible|Orientation horizontale|Ancrage|  
|**FALSE**|**FALSE**|Aucune extension disponible|Orientation verticale|Ancrage|  
  
##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect  
 L’infrastructure appelle cette fonction pour calculer la zone cliente de la barre de contrôle.  
  
```  
virtual void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `rect`  
 Contient les dimensions actuelles de la barre de contrôle. y compris les bordures.  
  
 `bHorz`  
 Indique que la barre est orientée horizontalement ou verticalement. Le `bHorz` paramètre est différente de zéro si la barre est orientée horizontalement et 0 s’il est orienté verticalement.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée avant que la barre de contrôle est peint.  
  
 Remplacez cette fonction pour personnaliser le rendu de la bordure et la barre de redimensionnement de la barre de contrôle.  
  
##  <a name="ccontrolbar"></a>  CControlBar::CControlBar  
 Construit un objet `CControlBar`.  
  
```  
CControlBar();
```  
  
##  <a name="dopaint"></a>  CControlBar::DoPaint  
 Appelé par le framework pour rendre les bordures et la barre de redimensionnement de la barre de contrôle.  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Pointe vers le contexte de périphérique à utiliser pour le rendu de la bordure et la barre de redimensionnement de la barre de contrôle.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour personnaliser le comportement de dessin de la barre de contrôle.  
  
 Une autre méthode de personnalisation consiste à remplacer le `DrawBorders` et `DrawGripper` des fonctions et ajoutez le code de dessin personnalisé pour les bordures et la barre de redimensionnement. Étant donné que ces méthodes sont appelées par la valeur par défaut `DoPaint` d’une méthode, une substitution de `DoPaint` n’est pas nécessaire.  
  
##  <a name="drawborders"></a>  CControlBar::DrawBorders  
 Appelé par le framework pour rendre les bordures de la barre de contrôle.  
  
```  
virtual void DrawBorders(
    CDC* pDC,  
    CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Pointe vers le contexte de périphérique à utiliser pour restituer les bordures de la barre de contrôle.  
  
 `rect`  
 A `CRect` objet qui contient les dimensions de la barre de contrôle.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour personnaliser l’apparence des bordures de barre de contrôle.  
  
##  <a name="drawgripper"></a>  CControlBar::DrawGripper  
 Appelé par l’infrastructure pour afficher la barre de redimensionnement de la barre de contrôle.  
  
```  
virtual void DrawGripper(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Pointe vers le contexte de périphérique à utiliser pour le rendu de la barre de redimensionnement de barre de contrôle.  
  
 `rect`  
 A `CRect` objet qui contient les dimensions de la barre de redimensionnement de barre de contrôle.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour personnaliser l’apparence de la barre de redimensionnement de barre de contrôle.  
  
##  <a name="enabledocking"></a>  CControlBar::EnableDocking  
 Appelez cette fonction pour activer une barre de contrôle être ancrée.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwDockStyle`  
 Spécifie si la barre de contrôle prend en charge d’ancrage et les côtés de sa fenêtre parente à laquelle la barre de contrôle peut être ancrée, si pris en charge. Peut être une ou plusieurs des opérations suivantes :  
  
- `CBRS_ALIGN_TOP` Permet d’ancrage en haut de la zone cliente.  
  
- `CBRS_ALIGN_BOTTOM` Permet d’ancrage en bas de la zone cliente.  
  
- `CBRS_ALIGN_LEFT` Permet d’ancrage à gauche de la zone cliente.  
  
- `CBRS_ALIGN_RIGHT` Permet d’ancrage sur le côté droit de la zone cliente.  
  
- `CBRS_ALIGN_ANY` Permet d’ancrage sur n’importe quel côté de la zone cliente.  
  
- `CBRS_FLOAT_MULTI` Permet à plusieurs barres de contrôles à flotter dans une fenêtre unique mini-frame.  
  
 La valeur 0 (autrement dit, ce qui indique aucun indicateur), la barre de contrôle ne sera pas ancrer.  
  
### <a name="remarks"></a>Notes  
 Les côtés spécifiées doivent correspondre à un des côtés activées pour l’ancrage dans la fenêtre frame de destination, ou la barre de contrôle ne peut pas être ancrée à cette fenêtre frame.  
  
##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle  
 Appelez cette fonction pour déterminer quelle **CBRS_** (styles de barre de contrôle) paramètres sont actuellement définis pour la barre de contrôle.  
  
```  
DWORD GetBarStyle();
```  
  
### <a name="return-value"></a>Valeur de retour  
 En cours **CBRS_** (styles de barre de contrôle) des paramètres de la barre de contrôle. Consultez [fonctions CControlBar::SetBarStyle](#setbarstyle) pour la liste complète des styles disponibles.  
  
### <a name="remarks"></a>Notes  
 Ne gère pas **WS_** (fenêtre) de style.  
  
##  <a name="getborders"></a>  CControlBar::GetBorders  
 Retourne les valeurs actuelles de la bordure de la barre de contrôle.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A `CRect` objet qui contient la largeur actuelle (en pixels) de chaque côté de l’objet de barre de contrôle. Par exemple, la valeur de la `left` membre, de [CRect](../../atl-mfc-shared/reference/crect-class.md) d’objet, la largeur de la bordure gauche.  
  
##  <a name="getcount"></a>  CControlBar::GetCount  
 Retourne le nombre de non - `HWND` sur les éléments de la `CControlBar` objet.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de non - `HWND` sur les éléments de la `CControlBar` objet. Cette fonction retourne 0 pour un [CDialogBar](../../mfc/reference/cdialogbar-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 Le type de l’élément dépend de l’objet dérivé : volets pour [CStatusBar](../../mfc/reference/cstatusbar-class.md) objets et des boutons et des séparateurs pour [CToolBar](../../mfc/reference/ctoolbar-class.md) objets.  
  
##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame  
 Appelez cette fonction membre pour obtenir un pointeur vers la fenêtre frame actuelle à laquelle votre barre de contrôle est ancré.  
  
```  
CFrameWnd* GetDockingFrame() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers une fenêtre frame en cas de réussite ; dans le cas contraire **NULL**.  
  
 Si la barre de contrôle n’est pas ancrée à une fenêtre frame (autrement dit, si la barre de contrôle est flottant), cette fonction retourne un pointeur à son parent [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les barres de contrôle, consultez [CControlBar::EnableDocking](#enabledocking) et [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).  
  
##  <a name="isfloating"></a>  CControlBar::IsFloating  
 Appelez cette fonction membre pour déterminer si la barre de contrôle est ancrée ou flottante.  
  
```  
BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la barre de contrôle est flottante. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour modifier l’état d’une barre de contrôle à partir d’ancré en virgule flottante, appelez [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).  
  
##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete  
 Si elle est différente de zéro, le `CControlBar` objet est supprimé lorsque la barre de contrôle de Windows est détruite.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Notes  
 `m_bAutoDelete` est une variable publique de type **BOOL**.  
  
 Un objet de barre de contrôle est généralement incorporé dans un objet fenêtre frame. Dans ce cas, `m_bAutoDelete` est 0, car l’objet de barre de contrôle incorporé est détruite quand la fenêtre frame est détruite.  
  
 Définir cette variable une valeur différente de zéro si vous allouez un `CControlBar` objet sur le tas et que vous n’envisagez pas d’appeler **supprimer**.  
  
##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner  
 Le propriétaire de la place de la barre de contrôle.  
  
```  
CWnd* m_pInPlaceOwner;  
```  
  
##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI  
 Cette fonction membre est appelée par l’infrastructure pour mettre à jour l’état de la barre d’état ou de la barre d’outils.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler) = 0;  
```  
  
### <a name="parameters"></a>Paramètres  
 `pTarget`  
 Pointe vers la fenêtre frame principale de l’application. Ce pointeur est utilisé pour le routage des messages de mise à jour.  
  
 `bDisableIfNoHndler`  
 Indicateur qui indique si un contrôle qui ne possède aucun gestionnaire de mise à jour doit être affiché automatiquement comme étant désactivé.  
  
### <a name="remarks"></a>Notes  
 Pour mettre à jour d’un bouton ou un volet, utilisez le `ON_UPDATE_COMMAND_UI` macro dans votre table des messages pour définir un gestionnaire de mise à jour de manière appropriée. Consultez [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) pour plus d’informations sur l’utilisation de cette macro.  
  
 `OnUpdateCmdUI` est appelé par l’infrastructure lors de l’application est inactive. La fenêtre frame à mettre à jour doit être au moins indirectement, une fenêtre enfant, d’une fenêtre frame visible. `OnUpdateCmdUI` avancée substituable.  
  
##  <a name="setbarstyle"></a>  Fonctions CControlBar::SetBarStyle  
 Appelez cette fonction pour définir le texte souhaité **CBRS_** styles de la barre de contrôle.  
  
```  
void SetBarStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwStyle`  
 Les styles de votre choisis pour la barre de contrôle. Peut être une ou plusieurs des opérations suivantes :  
  
- `CBRS_ALIGN_TOP` Permet à la barre de contrôle pour être ancrée en haut de la zone cliente d’une fenêtre frame.  
  
- `CBRS_ALIGN_BOTTOM` Permet à la barre de contrôle pour être ancré en bas de la zone cliente d’une fenêtre frame.  
  
- `CBRS_ALIGN_LEFT` Permet d’être ancrés au côté gauche de la zone cliente d’une fenêtre frame, la barre de contrôle.  
  
- `CBRS_ALIGN_RIGHT` Permet d’être ancrés au côté droit de la zone cliente d’une fenêtre frame, la barre de contrôle.  
  
- `CBRS_ALIGN_ANY` Permet à la barre de contrôle pour être ancrés dans n’importe quel côté de la zone cliente d’une fenêtre frame.  
  
- `CBRS_BORDER_TOP` Provoque une bordure à dessiner sur le bord supérieur de la barre de contrôle quand il est visible.  
  
- `CBRS_BORDER_BOTTOM` Provoque une bordure à dessiner sur le bord inférieur de la barre de contrôle quand il est visible.  
  
- `CBRS_BORDER_LEFT` Provoque une bordure à dessiner sur le bord gauche de la barre de contrôle quand il est visible.  
  
- `CBRS_BORDER_RIGHT` Provoque une bordure à dessiner sur le bord droit de la barre de contrôle quand il est visible.  
  
- `CBRS_FLOAT_MULTI` Permet à plusieurs barres de contrôles à flotter dans une fenêtre unique mini-frame.  
  
- `CBRS_TOOLTIPS` Provoque l’info-bulles à afficher pour la barre de contrôle.  
  
- `CBRS_FLYBY` Provoque le texte du message à mettre à jour en même temps en tant qu’info-bulles.  
  
- **CBRS_GRIPPER** provoque une barre de redimensionnement, semblable à celle utilisée sur les bandes dans un **CReBar** à dessiner pour tout objet `CControlBar`-classe dérivée.  
  
### <a name="remarks"></a>Notes  
 N’affecte pas la **WS_** les paramètres (style de fenêtre).  
  
##  <a name="setborders"></a>  CControlBar::SetBorders  
 Appelez cette fonction pour définir la taille des bordures de la barre de contrôle.  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *cxLeft*  
 La largeur (en pixels) de la bordure gauche de la barre de contrôle.  
  
 *cyTop*  
 La hauteur (en pixels) de la bordure supérieure de la barre de contrôle.  
  
 *cxRight*  
 La largeur (en pixels) de la bordure droite de la barre de contrôle.  
  
 *cyBottom*  
 La hauteur (en pixels) de la bordure inférieure de la barre de contrôle.  
  
 `lpRect`  
 Un pointeur vers un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui contient la largeur actuelle (en pixels) de chaque bordure de l’objet de barre de contrôle.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit les bordures supérieure et inférieure de la barre de contrôle à 5 pixels et les bordures gauche et droite de 2 pixels :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]  
  
##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner  
 Modifie le propriétaire de la place d’une barre de contrôle.  
  
```  
void SetInPlaceOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWnd`  
 Un pointeur vers un `CWnd` objet.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CTRLBARS](../../visual-cpp-samples.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CToolBar (classe)](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar (classe)](../../mfc/reference/cdialogbar-class.md)   
 [CStatusBar (classe)](../../mfc/reference/cstatusbar-class.md)   
 [CReBar, classe](../../mfc/reference/crebar-class.md)
