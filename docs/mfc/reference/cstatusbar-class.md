---
title: CStatusBar (classe) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c373f21762c1bf7f21d2a775453bab74c735891d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cstatusbar-class"></a>CStatusBar (classe)
Barre de contrôles avec une ligne de volets de sortie de texte ou « indicateurs ».  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStatusBar : public CControlBar  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](#cstatusbar)|Construit un objet `CStatusBar`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](#commandtoindex)|Obtient l’index pour un ID d’indicateur donné.|  
|[CStatusBar::Create](#create)|Crée la barre d’état, l’attache à le `CStatusBar` de l’objet et définit la hauteur de police et barre initiale.|  
|[CStatusBar::CreateEx](#createex)|Crée un `CStatusBar` objet avec les autres styles pour le texte incorporé `CStatusBarCtrl` objet.|  
|[CStatusBar::DrawItem](#drawitem)|Appelé lorsqu’un aspect visuel d’un mode owner-draw barre d’état contrôle change.|  
|[CStatusBar::GetItemID](#getitemid)|Obtient l’ID de l’indicateur d’un index donné.|  
|[CStatusBar::GetItemRect](#getitemrect)|Obtient affiche le rectangle d’un index donné.|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Obtient l’ID d’indicateur de style et la largeur d’un index donné.|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|Obtient le style d’indicateur d’un index donné.|  
|[CStatusBar::GetPaneText](#getpanetext)|Obtient le texte de l’indicateur d’un index donné.|  
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Permet un accès direct au contrôle commun sous-jacent.|  
|[CStatusBar::SetIndicators](#setindicators)|Définit l’ID de l’indicateur.|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Définit l’ID d’indicateur, le style et la largeur d’un index donné.|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|Définit le style d’indicateur d’un index donné.|  
|[CStatusBar::SetPaneText](#setpanetext)|Définit le texte de l’indicateur d’un index donné.|  
  
## <a name="remarks"></a>Notes  
 Les volets de sortie sont fréquemment utilisés en tant que lignes de message et comme indicateurs d’état. Exemples : les lignes de message à l’aide de menu qui expliquent brièvement la commande de menu sélectionné et les indicateurs qui indiquent l’état de l’arrêt défil, VERR. NUM et défil.  
  
 [CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), une fonction membre new 4.0 de MFC, vous permet de tirer parti de la prise en charge du contrôle commun Windows pour des fonctionnalités supplémentaires et de personnalisation de la barre d’état. `CStatusBar`fonctions membres vous donnent la plupart des fonctionnalités des contrôles communs Windows ; Toutefois, lorsque vous appelez `GetStatusBarCtrl`, vous pouvez donner à vos barres d’état davantage les caractéristiques d’une barre d’état Windows 95/98. Lorsque vous appelez `GetStatusBarCtrl`, il retourne une référence à un `CStatusBarCtrl` objet. Consultez [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) pour plus d’informations sur la conception des barres d’outils à l’aide de contrôles communs Windows. Pour plus d’informations sur les contrôles communs, consultez [contrôles communs](http://msdn.microsoft.com/library/windows/desktop/bb775493) dans le Kit de développement logiciel Windows.  
  
 Le framework stocke les informations de l’indicateur dans un tableau avec l’indicateur à l’extrême gauche à la position 0. Lorsque vous créez une barre d’état, vous utilisez un tableau de chaînes d’ID de l’infrastructure associe les indicateurs correspondants. Vous pouvez ensuite utiliser un ID de chaîne ou un index pour accéder à un indicateur.  
  
 Par défaut, le premier indicateur est « élastique » : il occupe la longueur de la barre d’état non utilisée par les autres volets de l’indicateur, afin que les autres volets sont alignés à droite.  
  
 Pour créer une barre d’état, procédez comme suit :  
  
1.  Construire la `CStatusBar` objet.  
  
2.  Appelez le [créer](#create) (ou [CreateEx](#createex)) afin de créer la fenêtre de la barre d’état et l’attacher à la `CStatusBar` objet.  
  
3.  Appelez [SetIndicators](#setindicators) à associer un ID de chaîne de chaque indicateur.  
  
 Il existe trois façons de mettre à jour le texte dans un volet de barre d’état :  
  
1.  Appelez [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) pour mettre à jour le texte dans le volet 0.  
  
2.  Appelez [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) dans la barre d’état `ON_UPDATE_COMMAND_UI` gestionnaire.  
  
3.  Appelez [SetPaneText](#setpanetext) pour mettre à jour le texte d’un volet.  
  
 Appelez [SetPaneStyle](#setpanestyle) pour mettre à jour le style d’un volet de barre d’état.  
  
 Pour plus d’informations sur l’utilisation de `CStatusBar`, consultez l’article [implémentation de barre d’état dans MFC](../../mfc/status-bar-implementation-in-mfc.md) et [Technical Note 31 : barres de contrôles](../../mfc/tn031-control-bars.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxext.h  
  
##  <a name="commandtoindex"></a>CStatusBar::CommandToIndex  
 Obtient l’index de l’indicateur pour un ID donné.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDFind`  
 ID de chaîne de l’indicateur dont l’index doit être récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’indicateur en cas de réussite ; -1 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 L’index du premier indicateur est 0.  
  
##  <a name="create"></a>CStatusBar::Create  
 Crée un état de la barre (une fenêtre enfant) et l’associe le `CStatusBar` objet.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentWnd`  
 Pointeur vers le [CWnd](../../mfc/reference/cwnd-class.md) objet dont la fenêtre Windows est le parent de la barre d’état.  
  
 `dwStyle`  
 Le style de la barre d’état. Outre les fenêtres standards [styles](../../mfc/reference/styles-used-by-mfc.md#window-styles), ces styles sont pris en charge.  
  
- `CBRS_TOP`Barre de contrôle est en haut de la fenêtre frame.  
  
- `CBRS_BOTTOM`Barre de contrôle est en bas de la fenêtre frame.  
  
- `CBRS_NOALIGN`Barre de contrôle n’est pas repositionné lorsque le parent est redimensionné.  
  
 `nID`  
 ID de fenêtre enfant. de la barre d’outils  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Également définit la police initiale et définit l’état de la hauteur de la barre à la valeur par défaut.  
  
##  <a name="createex"></a>CStatusBar::CreateEx  
 Appelez cette fonction pour créer un état de la barre (une fenêtre enfant) et l’associer avec le `CStatusBar` objet.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentWnd`  
 Pointeur vers le [CWnd](../../mfc/reference/cwnd-class.md) objet dont la fenêtre Windows est le parent de la barre d’état.  
  
 `dwCtrlStyle`  
 Styles supplémentaires pour la création de l’élément incorporé [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objet. La valeur par défaut spécifie une barre d’état sans une poignée de dimensionnement ou l’info-bulle prend en charge. Styles de barre d’état pris en charge sont :  
  
- **SBARS_SIZEGRIP** le contrôle de barre d’état inclut une poignée de dimensionnement à l’extrémité droite de la barre d’état. Une poignée de dimensionnement est similaire à une bordure de redimensionnement ; Il s’agit d’une zone rectangulaire que l’utilisateur peut cliquer et faites glisser pour redimensionner la fenêtre parente.  
  
- **SBT_TOOLTIPS** la barre d’état prend en charge les info-bulles.  
  
 Pour plus d’informations sur ces styles, consultez [paramètres de l’objet CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).  
  
 `dwStyle`  
 Le style de barre d’état. La valeur par défaut Spécifie qu’une barre d’état visible être créé en bas de la fenêtre frame. Appliquer n’importe quelle combinaison de styles de contrôle répertoriés dans la barre d’état [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Toutefois, ce paramètre doit toujours inclure les styles WS_CHILD et WS_VISIBLE.  
  
 `nID`  
 ID de la fenêtre la barre d’état enfant.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction définit la police initiale également et définit l’état de la hauteur de la barre à la valeur par défaut.  
  
 Utilisez `CreateEx`, au lieu de [créer](#create), lorsque certains styles doivent être présentes au cours de la création du contrôle de barre d’état incorporée. Par exemple, définissez `dwCtrlStyle` à **SBT_TOOLTIPS** pour afficher des info-bulles dans un objet de barre d’état.  
  
##  <a name="cstatusbar"></a>CStatusBar::CStatusBar  
 Construit un `CStatusBar` objet, crée une police de barre d’état par défaut, si nécessaire et définit les caractéristiques de la police pour les valeurs par défaut.  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>CStatusBar::DrawItem  
 Cette fonction membre est appelée par le framework lorsqu’un aspect visuel d’une modification de barre d’état owner-drawn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpDrawItemStruct`  
 Un pointeur vers un [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) structure qui contient des informations sur le type de dessin nécessaire.  
  
### <a name="remarks"></a>Notes  
 Le **itemAction** membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin qui doit être effectuée. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CStatusBar` objet. L’application doit restaurer tous les objets interface GDI périphérique graphique sélectionnés pour le contexte d’affichage fournie dans `lpDrawItemStruct` avant l’arrêt de cette fonction membre.  
  
##  <a name="getitemid"></a>CStatusBar::GetItemID  
 Retourne l’ID de l’indicateur spécifié par `nIndex`.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de l’indicateur dont l’ID doit être récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de l’indicateur spécifié par `nIndex`.  
  
##  <a name="getitemrect"></a>CStatusBar::GetItemRect  
 Copie les coordonnées de l’indicateur spécifié par `nIndex` dans la structure vers laquelle pointée `lpRect`.  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de l’indicateur dont coordonnées du rectangle doivent être récupérés.  
  
 `lpRect`  
 Pointe vers un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure ou un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui reçoit les coordonnées de l’indicateur spécifié par `nIndex`.  
  
### <a name="remarks"></a>Notes  
 Coordonnées sont exprimées en pixels par rapport au coin supérieur gauche de la barre d’état.  
  
##  <a name="getpaneinfo"></a>CStatusBar::GetPaneInfo  
 Jeux de `nID`, `nStyle`, et `cxWidth` à l’ID, le style et la largeur du volet d’indicateur à l’emplacement spécifié par `nIndex`.  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index du volet dont les informations sont à récupérer.  
  
 `nID`  
 Référence à un **UINT** qui est définie sur l’ID du volet.  
  
 `nStyle`  
 Référence à un **UINT** qui est défini sur le style du volet.  
  
 `cxWidth`  
 Référence à un entier qui est défini sur la largeur du volet.  
  
##  <a name="getpanestyle"></a>CStatusBar::GetPaneStyle  
 Appelez cette fonction membre pour récupérer le style du volet d’une barre état.  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index du volet dont le style doit être récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 Le style du volet de barre d’état spécifié par `nIndex`.  
  
### <a name="remarks"></a>Notes  
 Les style d’un volet détermine comment le volet s’affiche.  
  
 Pour obtenir la liste des styles disponibles pour les barres d’état, consultez [créer](#create).  
  
##  <a name="getpanetext"></a>CStatusBar::GetPaneText  
 Appelez cette fonction membre pour récupérer le texte qui apparaît dans un volet de barre d’état.  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index du volet dont le texte doit être récupéré.  
  
 `rString`  
 Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet qui contient le texte doit être récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 A `CString` objet contenant du texte du volet.  
  
### <a name="remarks"></a>Notes  
 La deuxième forme de ce membre fonction remplit un `CString` objet avec le texte de la chaîne.  
  
##  <a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl  
 Cette fonction membre permet un accès direct au contrôle commun sous-jacent.  
  
```  
CStatusBarCtrl& GetStatusBarCtrl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Contient une référence à un [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 Utilisez `GetStatusBarCtrl` pour tirer parti des fonctionnalités du contrôle commun de barre d’état Windows et pour tirer parti de la prise en charge [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) fournit pour la personnalisation de la barre d’état. Par exemple, à l’aide du contrôle commun, vous pouvez spécifier un style qui inclut une poignée de dimensionnement dans la barre d’état, ou vous pouvez spécifier un style pour que la barre d’état s’affichent en haut de la zone cliente de la fenêtre parente.  
  
 Pour plus d’informations sur les contrôles communs, consultez [contrôles communs](http://msdn.microsoft.com/library/windows/desktop/bb775493) dans le Kit de développement logiciel Windows.  
  
##  <a name="setindicators"></a>CStatusBar::SetIndicators  
 Définit les ID de chaque indicateur à la valeur spécifiée par l’élément correspondant du tableau `lpIDArray`, charge la ressource de chaîne spécifiée par chaque ID et définit le texte de l’indicateur sur la chaîne.  
  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpIDArray`  
 Pointeur vers un tableau d’ID.  
  
 `nIDCount`  
 Nombre d’éléments dans le tableau vers lequel pointe `lpIDArray`.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
##  <a name="setpaneinfo"></a>CStatusBar::SetPaneInfo  
 Définit le volet de l’indicateur spécifié à un nouvel ID, style et de largeur.  
  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index du volet indicateur dont le style doit être défini.  
  
 `nID`  
 Nouvel ID pour le volet de l’indicateur.  
  
 `nStyle`  
 Nouveau style pour le volet de l’indicateur.  
  
 `cxWidth`  
 Nouvelle largeur du volet de l’indicateur.  
  
### <a name="remarks"></a>Notes  
 Les styles d’indicateur suivants sont pris en charge :  
  
- **SBPS_NOBORDERS** aucune bordure 3D autour du volet.  
  
- **SBPS_POPOUT** inverse de la bordure afin que le texte « dépile. »  
  
- **SBPS_DISABLED** pas dessiner du texte.  
  
- **SBPS_STRETCH** volet Stretch pour remplir l’espace inutilisé. Un seul volet par la barre d’état peut avoir ce style.  
  
- **SBPS_NORMAL** aucun stretch, les bordures ou contextuelle.  
  
##  <a name="setpanestyle"></a>CStatusBar::SetPaneStyle  
 Appelez cette fonction membre pour définir le style du volet d’une barre état.  
  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index du volet dont le style doit être défini.  
  
 `nStyle`  
 Style du volet dont le style doit être défini.  
  
### <a name="remarks"></a>Notes  
 Les style d’un volet détermine comment le volet s’affiche.  
  
 Pour obtenir la liste des styles disponibles pour les barres d’état, consultez [SetPaneInfo](#setpaneinfo).  
  
##  <a name="setpanetext"></a>CStatusBar::SetPaneText  
 Appelez cette fonction membre pour définir le texte du volet de la chaîne pointée par `lpszNewText`.  
  
```  
BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index du volet dont le texte doit être défini.  
  
 `lpszNewText`  
 Pointeur vers le nouveau texte du volet.  
  
 *bUpdate*  
 Si **TRUE**, le volet est invalidé après le texte est défini.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé `SetPaneText`, vous devez ajouter un gestionnaire de mise à jour de l’interface utilisateur pour afficher le nouveau texte dans la barre d’état.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CTRLBARS](../../visual-cpp-samples.md)   
 [MFC exemple DLGCBR32](../../visual-cpp-samples.md)   
 [CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl (classe)](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)
