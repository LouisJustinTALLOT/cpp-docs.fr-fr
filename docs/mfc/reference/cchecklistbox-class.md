---
title: Classe de CCheckListBox | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
dev_langs:
- C++
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4129da35eca5aecfb1e976361d1716d1cd78e906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="cchecklistbox-class"></a>Classe de CCheckListBox
Fournit les fonctionnalités d'une zone de liste de contrôle Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCheckListBox : public CListBox  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Construit un objet `CCheckListBox`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CCheckListBox::Create](#create)|Crée la zone de liste de vérification de Windows et l’attache à le `CCheckListBox` objet.|  
|[CCheckListBox::DrawItem](#drawitem)|Appelé par le framework lorsqu’un aspect visuel d’une modification de zone de liste owner-draw.|  
|[CCheckListBox::Enable](#enable)|Active ou désactive un élément de zone de liste de vérification.|  
|[CCheckListBox::GetCheck](#getcheck)|Obtient l’état de la case à cocher d’un élément.|  
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtient le style de cases à cocher du contrôle.|  
|[CCheckListBox::IsEnabled](#isenabled)|Détermine si un élément est activé.|  
|[CCheckListBox::MeasureItem](#measureitem)|Appelé par l’infrastructure lors de la création d’une zone de liste avec un style de mode owner-draw.|  
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Appelé par l’infrastructure pour obtenir la position de la case à cocher d’un élément.|  
|[CCheckListBox::SetCheck](#setcheck)|Définit l’état de la case à cocher d’un élément.|  
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Définit le style de cases à cocher du contrôle.|  
  
## <a name="remarks"></a>Notes  
 Une « zone de liste de vérification » affiche une liste d’éléments, tels que des noms de fichiers. Chaque élément dans la liste a une case à cocher en regard de celui-ci pour que l’utilisateur peut vérifier ou effacer.  
  
 `CCheckListBox` est uniquement pour les contrôles owner-drawn, car la liste contient plus de chaînes de texte. Dans sa plus simple expression, une zone de liste de vérification contient des chaînes de texte et cases à cocher, mais vous n’avez pas besoin pour que tout le texte. Par exemple, vous pourriez avoir une liste de petites images bitmap avec une case à cocher en regard de chaque élément.  
  
 Pour créer votre propre boîte de dialogue liste de vérification, vous devez dériver votre propre classe de `CCheckListBox`. Dérivez votre propre classe, d’écrire un constructeur de la classe dérivée, puis appelez **créer**.  
  
 Si vous souhaitez traiter les messages de notification Windows envoyés par une zone de liste à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajouter une fonction table des messages de membre des entrée et le Gestionnaire de messages à la classe parente pour chaque message.  
  
 Chaque entrée de table des messages prend la forme suivante :  
  
 **ON_** Notification **(**`id`, `memberFxn` **)**  
  
 où `id` Spécifie l’ID de fenêtre enfant du contrôle qui envoie la notification et `memberFxn` est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.  
  
 Prototype de fonction du parent est la suivante :  
  
 **afx_msg** `void` `memberFxn` **() ;**  
  
 Il existe une seule entrée de table des messages qui se rapporte spécifiquement à **CCheckListBox** (mais consultez également les entrées de table des messages pour [CListBox](../../mfc/reference/clistbox-class.md)) :  
  
- **ON_CLBN_CHKCHANGE** l’utilisateur a modifié l’état de la case à cocher d’un élément.  
  
 Si votre zone de liste de vérification est une zone de liste de vérification par défaut (il s’agit d’une liste de chaînes avec les cases à cocher à gauche de chaque taille par défaut), vous pouvez utiliser la valeur par défaut [CCheckListBox::DrawItem](#drawitem) pour dessiner la zone de liste de vérification. Dans le cas contraire, vous devez substituer la [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) (fonction) et le [CCheckListBox::DrawItem](#drawitem) et [CCheckListBox::MeasureItem](#measureitem) fonctions.  
  
 Vous pouvez créer une zone de liste de vérification à partir d’un modèle de boîte de dialogue ou directement dans votre code.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox  
 Construit un objet `CCheckListBox`.  
  
```  
CCheckListBox();
```  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CCheckListBox` objet en deux étapes. Tout d’abord définir une classe dérivée de `CCheckListBox`, puis appelez **créer**, qui initialise la zone de liste de vérification de Windows et l’attache à le `CCheckListBox` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]  
  
##  <a name="create"></a>  CCheckListBox::Create  
 Crée la zone de liste de vérification de Windows et l’attache à le `CCheckListBox` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwStyle`  
 Spécifie le style de la zone de liste de vérification. Le style doit être **LBS_HASSTRINGS** et **LBS_OWNERDRAWFIXED** (tous les éléments dans la liste ont la même hauteur) ou **LBS_OWNERDRAWVARIABLE** (éléments de la liste sont de différentes hauteurs). Ce style peut être combiné avec d’autres [styles de zone de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) sauf **LBS_USETABSTOPS**.  
  
 `rect`  
 Spécifie la taille de la zone de liste de vérification et la position. Peut être un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](../../mfc/reference/rect-structure1.md) structure.  
  
 `pParentWnd`  
 Spécifie la fenêtre parente de la zone de liste de vérification (généralement un `CDialog` objet). Il ne doit pas être **NULL**.  
  
 `nID`  
 Spécifie l’ID du contrôle. de la zone de liste de vérification  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CCheckListBox` objet en deux étapes. Tout d’abord définir une classe dérivée de **CcheckListBox** , puis appelez **créer**, qui initialise la zone de liste de vérification de Windows et l’attache à le `CCheckListBox`. Consultez [CCheckListBox::CCheckListBox](#cchecklistbox) pour obtenir un exemple.  
  
 Lorsque **créer** s’exécute, Windows envoie les [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) messages pour le contrôle de zone de liste de vérification.  
  
 Ces messages sont gérées par défaut par le [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), et [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) fonctions membres dans la `CWnd` classe de base. Pour étendre le traitement du message par défaut, ajoutez une table des messages pour le votre classe dérivée et les fonctions membres de remplacement, le Gestionnaire de message précédent. Substituer `OnCreate`, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.  
  
 Appliquez ce qui suit [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle de zone de liste de vérification :  
  
- **WS_CHILD** toujours  
  
- **WS_VISIBLE** généralement  
  
- **WS_DISABLED** rarement  
  
- **WS_VSCROLL** pour ajouter une barre de défilement verticale  
  
- **WS_HSCROLL** pour ajouter une barre de défilement horizontale  
  
- **WS_GROUP** aux contrôles de groupe  
  
- **WS_TABSTOP** pour permettre à ce contrôle de tabulation  
  
##  <a name="drawitem"></a>  CCheckListBox::DrawItem  
 Appelé par le framework lorsqu’un aspect visuel d’une modification de zone de liste de contrôle owner-drawn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpDrawItemStruct`  
 Un pointeur long désignant un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure qui contient des informations sur le type de dessin nécessaire.  
  
### <a name="remarks"></a>Notes  
 Le **itemAction** et **itemState** membres de le `DRAWITEMSTRUCT` structure définir l’action de dessin qui doit être effectuée.  
  
 Par défaut, cette fonction Dessine une liste de case à cocher par défaut, consistant en une liste de chaînes avec une case à cocher taille par défaut à gauche. La taille de la liste case à cocher est celui spécifié dans [créer](#create).  
  
 Remplacez cette fonction membre pour implémenter le dessin des zones de liste de contrôle en mode owner-draw qui ne sont pas la valeur par défaut, tels que des zones de liste de vérification avec des listes qui ne sont pas des chaînes, avec les éléments de hauteur variable ou avec des cases à cocher qui ne sont pas sur la gauche. L’application doit restaurer tous les objets interface GDI périphérique graphique sélectionnés pour le contexte d’affichage fournie dans `lpDrawItemStruct` avant l’arrêt de cette fonction membre.  
  
 Si les éléments de zone de liste de vérification ne sont pas toutes la même hauteur, la liste de contrôle de zone de style (spécifié dans **créer**) doit être **LBS_OWNERVARIABLE**, et vous devez substituer la [MeasureItem](#measureitem) fonction.  
  
##  <a name="enable"></a>  CCheckListBox::Enable  
 Appelez cette fonction pour activer ou désactiver un élément de zone de liste de vérification.  
  
```  
void Enable(
    int nIndex,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de l’élément de zone de liste de contrôle doit être activée.  
  
 `bEnabled`  
 Spécifie si l’élément est activé ou désactivé.  
  
##  <a name="getcheck"></a>  CCheckListBox::GetCheck  
 Récupère l’état de la case à cocher spécifiée.  
  
```  
int GetCheck(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de base zéro de la case à cocher qui est contenue dans la zone de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 L’état de la case à cocher spécifiée. Le tableau suivant répertorie les valeurs possibles.  
  
|Value|Description|  
|-----------|-----------------|  
|`BST_CHECKED`|La case à cocher est activée.|  
|`BST_UNCHECKED`|La case à cocher n’est pas activée.|  
|`BST_INDETERMINATE`|L’état de la case à cocher est indéterminé.|  
  
##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle  
 Appelez cette fonction pour obtenir le style de la zone de liste de vérification.  
  
```  
UINT GetCheckStyle();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le style de cases à cocher du contrôle.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les styles possibles, consultez [SetCheckStyle](#setcheckstyle).  
  
##  <a name="isenabled"></a>  CCheckListBox::IsEnabled  
 Appelez cette fonction pour déterminer si un élément est activé.  
  
```  
BOOL IsEnabled(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément est activé ; Sinon, 0.  
  
##  <a name="measureitem"></a>  CCheckListBox::MeasureItem  
 Appelé par l’infrastructure lors de la création d’une zone de liste de vérification avec un style par défaut.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpMeasureItemStruct`  
 Un pointeur long désignant un [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) structure.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre et renseignez la `MEASUREITEMSTRUCT` structure pour informer Windows les dimensions des éléments de zone de liste de vérification. Si la zone de liste de vérification est créée avec le [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, l’infrastructure appelle cette fonction membre pour chaque élément dans la zone de liste. Sinon, ce membre est appelé une seule fois.  
  
##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition  
 L’infrastructure appelle cette fonction pour obtenir la position et la taille de la case à cocher dans un élément.  
  
```  
virtual CRect OnGetCheckPosition(
    CRect rectItem,  
    CRect rectCheckBox);
```  
  
### <a name="parameters"></a>Paramètres  
 *rectItem*  
 La position et la taille de l’élément de liste.  
  
 `rectCheckBox`  
 La position par défaut et la taille de la case à cocher d’un élément.  
  
### <a name="return-value"></a>Valeur de retour  
 La position et la taille de la case à cocher d’un élément.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut retourne uniquement la position par défaut et la taille de la case à cocher ( `rectCheckBox`). Par défaut, une case à cocher est aligné dans le coin supérieur gauche d’un élément et la taille de la case à cocher standard. Il peut arriver dans lequel vous souhaitez les cases à cocher sur la droite, ou une case à cocher supérieure ou inférieure. Dans ces cas, remplacer `OnGetCheckPosition` pour modifier la position de la case à cocher et la taille de l’élément.  
  
##  <a name="setcheck"></a>  CCheckListBox::SetCheck  
 Définit l’état de la case à cocher spécifiée.  
  
```  
void SetCheck(
    int nIndex,  
    int nCheck);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de base zéro de la case à cocher qui est contenue dans la zone de liste.  
  
 `nCheck`  
 L’état du bouton de la case à cocher spécifiée. Consultez la section Notes pour les valeurs possibles.  
  
### <a name="remarks"></a>Notes  
 Le tableau suivant répertorie les valeurs possibles pour le `nCheck` paramètre.  
  
|Value|Description|  
|-----------|-----------------|  
|**BST_CHECKED**|Activez la case à cocher spécifiée.|  
|**BST_UNCHECKED**|Désactivez la case à cocher spécifiée.|  
|**BST_INDETERMINATE**|Définir l’état de la case à cocher spécifiée est indéterminé.<br /><br /> Cet état est disponible uniquement si le style de la case à cocher est `BS_AUTO3STATE` ou `BS_3STATE`. Pour plus d’informations, consultez [les Styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
  
##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle  
 Appelez cette fonction pour définir le style des cases à cocher dans la zone de liste de vérification.  
  
```  
void SetCheckStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 `nStyle`  
 Détermine le style de cases à cocher dans la zone de liste de vérification.  
  
### <a name="remarks"></a>Notes  
 Les styles valides sont :  
  
- **BS_CHECKBOX**  
  
- **BS_AUTOCHECKBOX**  
  
- **BS_AUTO3STATE**  
  
- **BS_3STATE**  
  
 Pour plus d’informations sur ces styles, consultez [les Styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC TSTCON](../../visual-cpp-samples.md)   
 [CListBox (classe)](../../mfc/reference/clistbox-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CListBox, classe](../../mfc/reference/clistbox-class.md)
