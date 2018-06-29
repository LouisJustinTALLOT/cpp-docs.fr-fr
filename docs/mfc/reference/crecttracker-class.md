---
title: CRectTracker (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
dev_langs:
- C++
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4ce3c4dbfbf49791673392a1e1234728a680611
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079666"
---
# <a name="crecttracker-class"></a>CRectTracker (classe)
Permet à un élément à afficher, déplacer et redimensionner de différentes manières.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRectTracker  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CRectTracker::CRectTracker](#crecttracker)|Construit un objet `CRectTracker`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CRectTracker::AdjustRect](#adjustrect)|Appelée lorsque le rectangle est redimensionné.|  
|[CRectTracker::Draw](#draw)|Restitue le rectangle.|  
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Appelé lors du dessin de la bordure d’un `CRectTracker` objet.|  
|[CRectTracker::GetHandleMask](#gethandlemask)|Appelé pour obtenir le masque d’un `CRectTracker` poignées de redimensionnement de l’élément.|  
|[CRectTracker::GetTrueRect](#gettruerect)|Retourne la largeur et la hauteur du rectangle, y compris les poignées de redimensionnement.|  
|[CRectTracker::HitTest](#hittest)|Retourne la position actuelle du curseur liée à la `CRectTracker` objet.|  
|[CRectTracker::NormalizeHit](#normalizehit)|Normalise un code de test de positionnement.|  
|[CRectTracker::OnChangedRect](#onchangedrect)|Appelé lorsque le rectangle a été redimensionné ou déplacé.|  
|[CRectTracker::SetCursor](#setcursor)|Définit le curseur, en fonction de sa position sur le rectangle.|  
|[CRectTracker::Track](#track)|Permet à l’utilisateur de manipuler le rectangle.|  
|[CRectTracker::TrackRubberBand](#trackrubberband)|Permet à l’utilisateur à « élastique » la sélection.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Détermine la taille de poignées de redimensionnement.|  
|[CRectTracker::m_nStyle](#m_nstyle)|Style(s) actuel du dispositif de suivi.|  
|[CRectTracker::m_rect](#m_rect)|Position actuelle (en pixels) du rectangle.|  
|[CRectTracker::m_sizeMin](#m_sizemin)|Détermine la hauteur et la largeur du rectangle minimum.|  
  
## <a name="remarks"></a>Notes  
 `CRectTracker` ne dispose pas d’une classe de base.  
  
 Bien que la `CRectTracker` classe est conçu pour permettre à l’utilisateur d’interagir avec les éléments OLE à l’aide d’une interface graphique, son utilisation n’est pas limitée aux applications compatibles OLE. Il peut être utilisé partout où une interface utilisateur est requise.  
  
 `CRectTracker` les bordures peuvent être pleins ou traits en pointillés. L’élément peut être donné d’une bordure hachurée ou à superposer un motif hachuré pour indiquer différents États de l’élément. Vous pouvez placer des huit poignées de redimensionnement sur l’extérieur ou à l’intérieur bordure de l’élément. (Pour une explication des poignées de redimensionnement, consultez [GetHandleMask](#gethandlemask).) Enfin, un `CRectTracker` vous permet de modifier l’orientation d’un élément lors du redimensionnement.  
  
 Pour utiliser `CRectTracker`, construisez un `CRectTracker` de l’objet et de spécifier les États d’affichage sont initialisés. Vous pouvez ensuite utiliser cette interface pour permettre à la rétroaction visuelle de l’état actuel de l’élément OLE associé à la `CRectTracker` objet.  
  
 Pour plus d’informations sur l’utilisation de `CRectTracker`, consultez l’article [dispositifs de suivi](../../mfc/trackers.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CRectTracker`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxext.h  
  
##  <a name="adjustrect"></a>  CRectTracker::AdjustRect  
 Appelé par le framework lorsque le rectangle de suivi est redimensionné à l’aide d’une poignée de redimensionnement.  
  
```  
virtual void AdjustRect(
    int nHandle,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *nHandle*  
 Index de handle utilisé.  
  
 *lpRect*  
 Pointeur vers la taille actuelle du rectangle. (La taille d’un rectangle est donnée par sa hauteur et sa largeur.)  
  
### <a name="remarks"></a>Notes  
 Le comportement par défaut de cette fonction permet l’orientation du rectangle à modifier uniquement lorsque `Track` et `TrackRubberBand` sont appelées avec inversion des autorisé.  
  
 Remplacez cette fonction pour contrôler l’ajustement du rectangle de suivi pendant une opération de glisser-déplacer. Une méthode consiste à ajuster les coordonnées spécifiées par *lpRect* avant de retourner.  
  
 Les fonctionnalités spéciales qui ne sont pas directement pris en charge par `CRectTracker`, tel que le composant logiciel enfichable à la grille ou conserver en proportions, peut être implémentée en substituant cette fonction.  
  
##  <a name="crecttracker"></a>  CRectTracker::CRectTracker  
 Crée et initialise un `CRectTracker` objet.  
  
```  
CRectTracker();

 
CRectTracker(
    LPCRECT lpSrcRect,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpSrcRect*  
 Les coordonnées de l’objet rectangle.  
  
 *nStyle*  
 Spécifie le style de la `CRectTracker` objet. Les styles suivants sont pris en charge :  
  
- **CRectTracker::solidLine** utiliser un trait de la bordure du rectangle.  
  
- **CRectTracker::dottedLine** utiliser une ligne en pointillés pour la bordure du rectangle.  
  
- **CRectTracker::hatchedBorder** utiliser un modèle hachuré pour la bordure du rectangle.  
  
- **CRectTracker::resizeInside** situées à l’intérieur du rectangle de poignées de redimensionnement.  
  
- **CRectTracker::resizeOutside** situées en dehors du rectangle de poignées de redimensionnement.  
  
- **CRectTracker::hatchInside** Hatched modèle couvre l’ensemble du rectangle.  
  
### <a name="remarks"></a>Notes  
 Le constructeur par défaut initialise le `CRectTracker` objet avec les valeurs de *lpSrcRect* et initialise les autres tailles pour les valeurs système par défaut. Si l’objet est créé sans paramètres, le `m_rect` et `m_nStyle` les membres de données ne sont pas initialisées.  
  
##  <a name="draw"></a>  CRectTracker::Draw  
 Appelez cette fonction pour dessiner du rectangle lignes externes et une région interne.  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *contrôleur de domaine principal*  
 Pointeur vers le contexte de périphérique sur lequel dessiner.  
  
### <a name="remarks"></a>Notes  
 Le style du dispositif de suivi détermine la façon dont le dessin est effectué. Consultez le constructeur pour `CRectTracker` pour plus d’informations sur les styles disponibles.  
  
##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect  
 Appelé par le framework chaque fois que la position du dispositif de suivi a changé alors que dans le `Track` ou `TrackRubberBand` fonction membre.  
  
```  
virtual void DrawTrackerRect(
    LPCRECT lpRect,  
    CWnd* pWndClipTo,  
    CDC* pDC,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpRect*  
 Pointeur vers le `RECT` qui contient le rectangle à dessiner.  
  
 *pWndClipTo*  
 Pointeur vers la fenêtre à utiliser dans le rectangle de détourage.  
  
 *contrôleur de domaine principal*  
 Pointeur vers le contexte de périphérique sur lequel dessiner.  
  
 *pWnd*  
 Pointeur vers la fenêtre sur laquelle le dessin se produit.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut effectue un appel à `CDC::DrawFocusRect`, qui dessine un rectangle en pointillé.  
  
 Remplacez cette fonction pour fournir des commentaires différents lors de l’opération de suivi.  
  
##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask  
 L’infrastructure appelle cette fonction membre pour récupérer le masque de poignées de redimensionnement d’un rectangle.  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le masque d’un `CRectTracker` poignées de redimensionnement de l’élément.  
  
### <a name="remarks"></a>Notes  
 Les poignées de redimensionnement apparaissent sur les côtés et les angles du rectangle et autoriser l’utilisateur de contrôler la forme et la taille du rectangle.  
  
 Un rectangle a 8 poignées de redimensionnement numérotées de 0 à 7. Chaque poignée de redimensionnement est représentée par un bit dans le masque ; la valeur de ce bit est 2 ^ *n*, où *n* est le nombre de poignée de redimensionnement. Bits 0-3 correspondent aux poignées de redimensionnement, en commençant à l’angle supérieur gauche de déplacement vers la droite. En commençant par le haut aiguilles de poignées de redimensionnement de bits correspondent à la partie 4-7. L’illustration suivante montre les poignées de redimensionnement d’un rectangle et leurs correspondantes redimensionner les nombres de handle et les valeurs :  
  
 ![Redimensionner les valeurs de la poignée](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 L’implémentation par défaut de **GetHandleMask** retourne le masque de bits de sorte que les poignées de redimensionnement apparaissent. Si le bit unique est activé, la poignée de redimensionnement correspondant sera dessinée.  
  
 Remplacez cette fonction membre pour masquer ou afficher les que poignées de redimensionnement indiqué.  
  
##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect  
 Appelez cette fonction pour récupérer les coordonnées du rectangle.  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpTrueRect*  
 Pointeur vers le `RECT` coordonnées de structure qui contiendra l’appareil de le `CRectTracker` objet.  
  
### <a name="remarks"></a>Notes  
 Les dimensions du rectangle incluent la hauteur et la largeur de toutes les poignées de redimensionnement situées sur la bordure externe. Lors du retour, *lpTrueRect* est toujours un rectangle normalisé en coordonnées de périphérique.  
  
##  <a name="hittest"></a>  CRectTracker::HitTest  
 Appelez cette fonction pour déterminer si l’utilisateur a saisi une poignée de redimensionnement.  
  
```  
int HitTest(CPoint point) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *Point*  
 Le point, en coordonnées de l’appareil, à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur retournée est basée sur le type énuméré **CRectTracker::TrackerHit** et peut avoir l’une des valeurs suivantes :  
  
- **CRectTracker::hitNothing** -1  
  
- **CRectTracker::hitTopLeft** 0  
  
- **CRectTracker::hitTopRight** 1  
  
- **CRectTracker::hitBottomRight** 2  
  
- **CRectTracker::hitBottomLeft** 3  
  
- **CRectTracker::hitTop** 4  
  
- **CRectTracker::hitRight** 5  
  
- **CRectTracker::hitBottom** 6  
  
- **CRectTracker::hitLeft** 7  
  
- **CRectTracker::hitMiddle** 8  
  
##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize  
 La taille, en pixels, de la `CRectTracker` des poignées de redimensionnement.  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>Notes  
 Initialisé avec la valeur par défaut du système.  
  
##  <a name="m_rect"></a>  CRectTracker::m_rect  
 La position actuelle du rectangle dans les coordonnées clientes (pixels).  
  
```  
CRect m_rect;  
```  
  
##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin  
 La taille minimale du rectangle.  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>Notes  
 Les deux valeurs par défaut, **cx** et **cy**, sont calculées à partir de la valeur système par défaut pour la largeur de bordure. Ce membre de données est utilisé uniquement par le `AdjustRect` fonction membre.  
  
##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle  
 Style actuel du rectangle.  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [CRectTracker::CRectTracker](#crecttracker) pour obtenir la liste des styles possibles.  
  
##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit  
 Appelez cette fonction pour convertir un handle potentiellement inversé.  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nHandle*  
 Handle sélectionnée par l’utilisateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de la poignée normalisée.  
  
### <a name="remarks"></a>Notes  
 Lorsque `CRectTracker::Track` ou `CRectTracker::TrackRubberBand` est appelée avec inversion des autorisé, il est possible pour le rectangle à inverser l’axe des abscisses, l’axe des ordonnées ou les deux. Dans ce cas, `HitTest` retournera les descripteurs sont également inversés en ce qui concerne le rectangle. Il s’agit inappropriée pour dessiner le curseur car les commentaires dépend de la position de l’écran du rectangle, pas la partie de la structure de données du rectangle qui est modifiée.  
  
##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect  
 Appelé par le framework chaque fois que le rectangle de suivi a changé pendant un appel à `Track`.  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>Paramètres  
 *rectOld*  
 Contient les coordonnées de périphérique ancien de la `CRectTracker` objet.  
  
### <a name="remarks"></a>Notes  
 Au moment où cette fonction est appelée, tous les commentaires sont dessinées à l’aide `DrawTrackerRect` a été supprimé. L’implémentation par défaut de cette fonction est sans effet.  
  
 Remplacez cette fonction lorsque vous souhaitez effectuer des actions après que le rectangle a été redimensionné.  
  
##  <a name="setcursor"></a>  CRectTracker::SetCursor  
 Appelez cette fonction pour modifier la forme de curseur au-dessus de la `CRectTracker` région de l’objet.  
  
```  
BOOL SetCursor(
    CWnd* pWnd,  
    UINT nHitTest) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre qui contient actuellement le curseur.  
  
 *nHitTest*  
 Résultats du test d’atteinte précédent, à partir du message WM_SETCURSOR.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le positionnement précédent était sur le rectangle de mise hors tension ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction à partir de la fonction de la fenêtre qui gère le message WM_SETCURSOR (généralement `OnSetCursor`).  
  
##  <a name="track"></a>  CRectTracker::Track  
 Appelez cette fonction pour afficher l’interface utilisateur pour redimensionner le rectangle.  
  
```  
BOOL Track(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = FALSE,  
    CWnd* pWndClipTo = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 L’objet de fenêtre qui contient le rectangle.  
  
 *Point*  
 Coordonnées de périphérique de la position actuelle de la souris par rapport à la zone cliente.  
  
 *bAllowInvert*  
 Si **TRUE**, le rectangle peut être inversé le long de l’axe x ou l’axe des ordonnées ; sinon **FALSE**.  
  
 *pWndClipTo*  
 La fenêtre opérations de dessin coïncident avec. Si **NULL**, *pWnd* est utilisé en tant que le rectangle de découpage.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la touche ÉCHAP est enfoncée, le processus de suivi est interrompu, le rectangle stocké dans le dispositif de suivi n’est pas modifié et 0 est retourné. Si la modification est validée, en déplacement de la souris et en relâchant le bouton gauche de la souris, la nouvelle position et/ou la taille est enregistrée dans le rectangle du dispositif de suivi et différente de zéro est retournée.  
  
### <a name="remarks"></a>Notes  
 Cela est généralement appelée à partir d’à l’intérieur de la fonction de votre application qui gère la `WM_LBUTTONDOWN` message (généralement `OnLButtonDown`).  
  
 Cette fonction capture la souris jusqu'à ce que l’utilisateur relâche le bouton gauche de la souris, appuie sur la touche ÉCHAP ou sur le bouton droit de la souris. Lorsque l’utilisateur déplace le curseur de souris, les commentaires sont mis à jour en appelant `DrawTrackerRect` et `OnChangedRect`.  
  
 Si *bAllowInvert* est **TRUE**, le rectangle de suivi peut être inversé sur l’axe des abscisses ou axe des ordonnées.  
  
##  <a name="trackrubberband"></a>  CRectTracker::TrackRubberBand  
 Appelez cette fonction pour faire la sélection élastique.  
  
```  
BOOL TrackRubberBand(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 L’objet de fenêtre qui contient le rectangle.  
  
 *Point*  
 Coordonnées de périphérique de la position actuelle de la souris par rapport à la zone cliente.  
  
 *bAllowInvert*  
 Si **valeur est TRUE,** le rectangle peut être inversé le long de l’axe x ou l’axe des ordonnées ; sinon **FALSE**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la souris a été déplacé et le rectangle n’est pas vide. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Il est généralement appelée à partir de la fonction de votre application qui gère le message WM_LBUTTONDOWN (généralement `OnLButtonDown`).  
  
 Cette fonction capture la souris jusqu'à ce que l’utilisateur relâche le bouton gauche de la souris, appuie sur la touche ÉCHAP ou sur le bouton droit de la souris. Lorsque l’utilisateur déplace le curseur de souris, les commentaires sont mis à jour en appelant `DrawTrackerRect` et `OnChangedRect`.  
  
 Le suivi est effectué avec une sélection de type de bande de caoutchouc à partir du handle à droite. Si l’inversion est autorisée, le rectangle peut être dimensionné en faisant glisser soit haut et vers la gauche ou vers le bas et de vers la droite.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC de mise hors tension](../../visual-cpp-samples.md)   
 [Exemple MFC DRAWCLI](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de COleResizeBar](../../mfc/reference/coleresizebar-class.md)   
 [CRect, classe](../../atl-mfc-shared/reference/crect-class.md)
