---
title: CStatusBarCtrl (classe) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CStatusBarCtrl
- CStatusBarCtrl class
- status bar controls
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: d9fc341963572e343123994577a1bec735775386
ms.lasthandoff: 04/01/2017

---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl (classe)
Fournit les fonctionnalités du contrôle commun de barre d'état Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Construit un objet `CStatusBarCtrl`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|Crée un contrôle de barre d’état et l’attache à un `CStatusBarCtrl` objet.|  
|[CStatusBarCtrl::CreateEx](#createex)|Crée un contrôle de barre d’état avec les styles étendus Windows spécifiés et l’attache à un `CStatusBarCtrl` objet.|  
|[CStatusBarCtrl::DrawItem](#drawitem)|Appelé lorsqu’un aspect visuel d’un mode owner-draw barre d’état contrôle change.|  
|[CStatusBarCtrl::GetBorders](#getborders)|Récupère la largeur actuelle des bordures horizontales et verticales d’un contrôle de barre d’état.|  
|[CStatusBarCtrl::GetIcon](#geticon)|Récupère l’icône d’un composant (également appelé un volet) dans le contrôle de barre d’état en cours.|  
|[CStatusBarCtrl::GetParts](#getparts)|Récupère un nombre de parties dans un contrôle de barre d’état.|  
|[CStatusBarCtrl::GetRect](#getrect)|Récupère le rectangle englobant d’une partie dans un contrôle de barre d’état.|  
|[CStatusBarCtrl::GetText](#gettext)|Récupère le texte de la partie spécifiée d’un contrôle de barre d’état.|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Récupérer la longueur, en caractères, du texte à partir de la partie spécifiée d’un contrôle de barre d’état.|  
|[CStatusBarCtrl::GetTipText](#gettiptext)|Récupère le texte d’info-bulle pour un volet dans une barre d’état.|  
|[CStatusBarCtrl::IsSimple](#issimple)|Vérifie un contrôle de fenêtre d’état pour déterminer si elle est en mode simple.|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan dans une barre d’état.|  
|[CStatusBarCtrl::SetIcon](#seticon)|Définit l’icône pour un volet dans une barre d’état.|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Définit la hauteur minimale d’un état de la zone de dessin du contrôle de la barre.|  
|[CStatusBarCtrl::SetParts](#setparts)|Définit le nombre de parties dans un contrôle et les coordonnées du bord droit de chaque partie de la barre d’état.|  
|[CStatusBarCtrl::SetSimple](#setsimple)|Spécifie si un contrôle de barre d’état affiche le texte simple ou tous les composants de contrôle définis par un appel précédent à `SetParts`.|  
|[CStatusBarCtrl::SetText](#settext)|Définit le texte dans la partie spécifiée d'un contrôle de barre d'état.|  
|[CStatusBarCtrl::SetTipText](#settiptext)|Définit le texte info-bulle pour un volet dans une barre d’état.|  
  
## <a name="remarks"></a>Remarques  
 Un « contrôle barre d’état » est une fenêtre horizontale, qui s’affichée habituellement au bas d’une fenêtre parent, dans laquelle une application peut afficher différents types d’informations d’état. Le contrôle de barre d’état peut être divisé en parties pour afficher plusieurs types d’informations.  
  
 Ce contrôle (et par conséquent la `CStatusBarCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT version 3.51 et ultérieures.  
  
 Pour plus d’informations sur l’utilisation de `CStatusBarCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxcmn.h  
  
##  <a name="create"></a>CStatusBarCtrl::Create  
 Crée un contrôle de barre d’état et l’attache à un `CStatusBarCtrl` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwStyle`  
 Spécifie le style du contrôle de barre de statut. Appliquer n’importe quelle combinaison de styles de contrôle répertoriés dans la barre d’état [des Styles de contrôle courants](http://msdn.microsoft.com/library/windows/desktop/bb775498) dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Ce paramètre doit inclure le **WS_CHILD** style. Il doit également inclure le **WS_VISIBLE** style.  
  
 `rect`  
 Spécifie la taille et la position du contrôle barre d’état. Il peut être soit un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure.  
  
 `pParentWnd`  
 Spécifie l’état de la fenêtre parente du contrôle barre généralement un `CDialog`. Il ne doit pas être **NULL.**  
  
 `nID`  
 Spécifie l’ID. du contrôle de barre de statut  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CStatusBarCtrl` en deux étapes. Tout d’abord, appelez le constructeur, puis **créer**, ce qui crée le contrôle de barre d’état et l’attache à le `CStatusBarCtrl` objet.  
  
 La position par défaut d’une fenêtre d’état est au bas de la fenêtre parente, mais vous pouvez spécifier le `CCS_TOP` style pour qu’elle s’affiche en haut de la zone cliente de la fenêtre parente. Vous pouvez spécifier le **SBARS_SIZEGRIP** style à inclure une poignée de dimensionnement à l’extrémité droite de la fenêtre d’état. Combinaison de la `CCS_TOP` et **SBARS_SIZEGRIP** styles n’est pas recommandée, car la poignée de dimensionnement résultant ne fonctionne pas même si le système dessine dans la fenêtre d’état.  
  
 Pour créer une barre d’état avec les styles de fenêtre étendus, appelez [CStatusBarCtrl::CreateEx](#createex) au lieu de **créer**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl n° 1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CStatusBarCtrl::CreateEx  
 Crée un contrôle (une fenêtre enfant) et l’associe le `CStatusBarCtrl` objet.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwExStyle`  
 Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le `dwExStyle` paramètre [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Spécifie le style du contrôle de barre de statut. Appliquer n’importe quelle combinaison de styles de contrôle répertoriés dans la barre d’état [des Styles de contrôle courants](http://msdn.microsoft.com/library/windows/desktop/bb775498) dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Ce paramètre doit inclure le **WS_CHILD** style. Il doit également inclure le **WS_VISIBLE** style.  
  
 `rect`  
 Une référence à un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure décrivant la taille et la position de la fenêtre doit être créée, en coordonnées clientes de `pParentWnd`.  
  
 `pParentWnd`  
 Pointeur vers la fenêtre qui est le parent du contrôle.  
  
 `nID`  
 ID de fenêtre enfant. du contrôle  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus Windows spécifiés par la préface style étendu de Windows **WS_EX_**.  
  
##  <a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl  
 Construit un objet `CStatusBarCtrl`.  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>CStatusBarCtrl::DrawItem  
 Appelé par le framework lorsqu’un aspect visuel d’un mode owner-draw barre d’état contrôle change.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpDrawItemStruct`  
 Un pointeur long désignant un [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) structure qui contient des informations sur le type de dessin nécessaire.  
  
### <a name="remarks"></a>Remarques  
 Le **itemAction** membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin qui doit être effectuée.  
  
 Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CStatusBarCtrl` objet.  
  
 L’application doit restaurer tous les objets interface GDI périphérique graphique sélectionnés pour le contexte d’affichage fournie dans `lpDrawItemStruct` avant ce membre de la fonction s’arrête.  
  
##  <a name="getborders"></a>CStatusBarCtrl::GetBorders  
 Récupère actuel des largeurs du contrôle barre d’état des bordures horizontales et verticales et de l’espace entre les rectangles.  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pBorders*  
 Adresse d’un tableau d’entiers comportant trois éléments. Le premier élément reçoit la largeur de la bordure horizontale, le deuxième reçoit la largeur de la bordure verticale et la troisième reçoit la largeur de la bordure entre rectangles.  
  
 *nHorz*  
 Référence à un entier qui reçoit la largeur de la bordure horizontale.  
  
 *convertir en*  
 Référence à un entier qui reçoit la largeur de la bordure verticale.  
  
 *nSpacing*  
 Référence à un entier qui reçoit la largeur de la bordure entre les rectangles.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Remarques  
 Ces bordures déterminent l’espacement entre le bord extérieur du contrôle et les rectangles qui contiennent du texte dans le contrôle.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>CStatusBarCtrl::GetIcon  
 Récupère l’icône d’un composant (également appelé un volet) dans le contrôle de barre d’état en cours.  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `iPart`|Index de base zéro de la partie qui contient l’icône doit être récupéré. Si ce paramètre est -1, la barre d’état est censée pour être une barre d’état en mode simple.|  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de l’icône si la méthode réussite ; dans le cas contraire, `NULL`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744) message, ce qui est décrit dans la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Un contrôle de barre d’état se compose d’une ligne de volets de sortie de texte, qui sont également appelés parties. Pour plus d’informations sur la barre d’état, consultez [implémentation de barre d’état dans MFC](../../mfc/status-bar-implementation-in-mfc.md) et [définition du Mode d’un objet CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit une variable, `m_statusBar`, qui est utilisé pour accéder au contrôle de barre d’état en cours. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1 n° 1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant copie une icône à deux volets de contrôle de barre d’état en cours. Dans une section précédente de l’exemple de code nous avons créé un contrôle de barre d’état avec trois volets et ajouté une icône au premier volet. Cet exemple récupère l’icône du premier volet et puis l’ajoute au volet des deuxième et troisième.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s&#1;2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>CStatusBarCtrl::GetParts  
 Récupère un nombre de parties dans un contrôle de barre d’état.  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nParts`  
 Nombre de parties pour lequel récupérer les coordonnées. Si ce paramètre est supérieur au nombre de parties dans le contrôle, le message récupère les coordonnées des articles existants uniquement.  
  
 *pParts*  
 Adresse d’un tableau d’entiers ayant le même nombre d’éléments en tant que le nombre de parties spécifié par `nParts`. Chaque élément du tableau reçoit les coordonnées clientes du bord droit de la partie correspondante. Si un élément est défini sur - 1, la position du bord droit de cette partie s’étend vers le bord droit de la barre d’état.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de parties dans le contrôle en cas de réussite, ou 0 dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction membre récupère également les coordonnées du bord droit du nombre donné de parties.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl n° 3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>CStatusBarCtrl::GetRect  
 Récupère le rectangle englobant d’une partie dans un contrôle de barre d’état.  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nPane`  
 Index de base zéro de la partie dont le rectangle englobant doit être récupéré.  
  
 `lpRect`  
 Adresse d’un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui reçoit le rectangle englobant.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>CStatusBarCtrl::GetText  
 Récupère le texte de la partie spécifiée d’un contrôle de barre d’état.  
  
```  
CString GetText(
    int nPane,  
    int* pType = NULL) const;  
  
int GetText(
    LPCTSTR lpszText,  
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszText`  
 Adresse de la mémoire tampon qui reçoit le texte. Ce paramètre est une chaîne se terminant par null.  
  
 `nPane`  
 Index de base zéro de la partie à partir duquel récupérer le texte.  
  
 `pType`  
 Pointeur vers un entier qui reçoit les informations de type. Le type peut être une des valeurs suivantes :  
  
- **0** le texte est dessiné avec une bordure s’affichent plus bas que le plan de la barre d’état.  
  
- `SBT_NOBORDERS`Le texte est dessiné sans bordures.  
  
- `SBT_POPOUT`Le texte est dessiné avec une bordure à apparaître plus haut que le plan de la barre d’état.  
  
- `SBT_OWNERDRAW`Si le texte a la `SBT_OWNERDRAW` type, de dessin `pType` reçoit ce message et retourne la valeur de 32 bits associée au texte au lieu du type de longueur et l’opération.  
  
### <a name="return-value"></a>Valeur de retour  
 La longueur, en caractères, du texte ou un [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le texte en cours.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl n ° 5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>CStatusBarCtrl::GetTextLength  
 Récupère la longueur, en caractères, du texte à partir de la partie spécifiée d’un contrôle de barre d’état.  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nPane`  
 Index de base zéro de la partie à partir duquel récupérer le texte.  
  
 `pType`  
 Pointeur vers un entier qui reçoit les informations de type. Le type peut être une des valeurs suivantes :  
  
- **0** le texte est dessiné avec une bordure s’affichent plus bas que le plan de la barre d’état.  
  
- `SBT_NOBORDERS`Le texte est dessiné sans bordures.  
  
- `SBT_OWNERDRAW`Le texte est dessiné par la fenêtre parente.  
  
- `SBT_POPOUT`Le texte est dessiné avec une bordure à apparaître plus haut que le plan de la barre d’état.  
  
### <a name="return-value"></a>Valeur de retour  
 La longueur, en caractères, du texte.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl n° 6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>CStatusBarCtrl::GetTipText  
 Récupère le texte d’info-bulle pour un volet dans une barre d’état.  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nPane`  
 Index de base zéro du volet de barre d’état pour le texte d’info-bulle s’affiche.  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet contenant le texte à utiliser dans l’info-bulle.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction membre implémente le comportement du message Win32 [SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751), comme décrit dans la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>CStatusBarCtrl::IsSimple  
 Vérifie un contrôle de fenêtre d’état pour déterminer si elle est en mode simple.  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contrôle de fenêtre d’état est en mode simple ; Sinon, zéro.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction membre implémente le comportement du message Win32 [SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753), comme décrit dans la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor  
 Définit la couleur d’arrière-plan dans une barre d’état.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Paramètres  
 `cr`  
 **COLORREF** valeur qui spécifie la couleur d’arrière-plan. Spécifiez le `CLR_DEFAULT` valeur entraîne la barre d’état à utiliser sa couleur d’arrière-plan par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui représente la couleur d’arrière-plan par défaut précédent.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction membre implémente le comportement du message Win32 [SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754), comme décrit dans la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>CStatusBarCtrl::SetIcon  
 Définit l’icône pour un volet dans une barre d’état.  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPane`  
 Index de base zéro du volet qui recevra l’icône. Si ce paramètre est -1, la barre d’état est censée pour être une barre d’état simple.  
  
 `hIcon`  
 Handle vers l’icône à définir. Si cette valeur est **NULL**, l’icône est supprimée de la partie.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction membre implémente le comportement du message Win32 [SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755), comme décrit dans la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CStatusBarCtrl::SetBkColor](#setbkcolor).  
  
##  <a name="setminheight"></a>CStatusBarCtrl::SetMinHeight  
 Définit la hauteur minimale d’un état de la zone de dessin du contrôle de la barre.  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMin`  
 Hauteur minimale, en pixels, du contrôle.  
  
### <a name="remarks"></a>Notes  
 La hauteur minimale est la somme des `nMin` et deux fois la largeur, en pixels, de la bordure verticale du contrôle de barre d’état.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>CStatusBarCtrl::SetParts  
 Définit le nombre de parties dans un contrôle et les coordonnées du bord droit de chaque partie de la barre d’état.  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>Paramètres  
 `nParts`  
 Nombre de parties à définir. Le nombre de parties ne peut pas être supérieur à 255.  
  
 *pWidths*  
 Adresse d’un tableau d’entiers ayant le même nombre d’éléments en tant que parties spécifiés par `nParts`. Chaque élément du tableau spécifie, en coordonnées clientes, la position du bord droit de la partie correspondante. Si un élément est - 1, la position du bord droit de cette partie s’étend vers le bord droit du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>CStatusBarCtrl::SetSimple  
 Spécifie si un contrôle de barre d’état affiche le texte simple ou tous les composants de contrôle définis par un appel précédent à [SetParts](#setparts).  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bSimple`  
 Indicateur de type d’affichage. Si ce paramètre est `TRUE`, le contrôle affiche le texte simple ; s’il est `FALSE`, il affiche plusieurs parties.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours 0.  
  
### <a name="remarks"></a>Notes  
 Si votre application passe le contrôle de barre d’état de non simple simple, ou vice versa, le système redessine immédiatement le contrôle.  
  
##  <a name="settext"></a>CStatusBarCtrl::SetText  
 Définit le texte dans la partie spécifiée d'un contrôle de barre d'état.  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszText`  
 Adresse d'une chaîne se terminant par null spécifiant le texte à définir. Si `nType` a la valeur `SBT_OWNERDRAW`, `lpszText` représente 32 bits de données.  
  
 `nPane`  
 Index de base zéro de la partie à définir. Si cette valeur est égale à 255, le contrôle de barre d'état est considéré comme un simple contrôle constitué d'une seule partie.  
  
 `nType`  
 Type d'opération de dessin. Consultez [message SB_SETTEXT](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx) pour obtenir la liste des valeurs possibles.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Remarques  
 Le message invalide la partie du contrôle qui a changé, provoquant l'affichage du nouveau texte quand le contrôle reçoit le message `WM_PAINT`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>CStatusBarCtrl::SetTipText  
 Définit le texte info-bulle pour un volet dans une barre d’état.  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPane`  
 Index de base zéro du volet de barre d’état pour le texte d’info-bulle s’affiche.  
  
 *pszTipText*  
 Un pointeur vers une chaîne contenant le texte info-bulle.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction membre implémente le comportement du message Win32 [SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759), comme décrit dans la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl, classe](../../mfc/reference/ctoolbarctrl-class.md)

