---
title: CCheckListBox, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: f8c725ea30754a42ce3045f1160b7a09c4481e39
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507350"
---
# <a name="cchecklistbox-class"></a>CCheckListBox, classe

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
|[CCheckListBox::Create](#create)|Crée la zone de liste de contrôle Windows et l’attache `CCheckListBox` à l’objet.|
|[CCheckListBox::DrawItem](#drawitem)|Appelée par l’infrastructure quand un aspect visuel d’une zone de liste owner-draw change.|
|[CCheckListBox::Enable](#enable)|Active ou désactive un élément de zone de liste de contrôle.|
|[CCheckListBox::GetCheck](#getcheck)|Obtient l’état de la case à cocher d’un élément.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtient le style des cases à cocher du contrôle.|
|[CCheckListBox::IsEnabled](#isenabled)|Détermine si un élément est activé.|
|[CCheckListBox::MeasureItem](#measureitem)|Appelé par le Framework lorsqu’une zone de liste avec un style owner-draw est créée.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Appelé par le Framework pour afficher la position de la case à cocher d’un élément.|
|[CCheckListBox::SetCheck](#setcheck)|Définit l’état de la case à cocher d’un élément.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Définit le style des cases à cocher du contrôle.|

## <a name="remarks"></a>Notes

Une «zone de liste de vérification» affiche une liste d’éléments, tels que des noms de fichiers. Chaque élément de la liste comporte une case à cocher en regard de celui-ci que l’utilisateur peut activer ou désactiver.

`CCheckListBox`est uniquement destiné aux contrôles owner-drawn, car la liste contient plus de chaînes de texte. Au plus simple, une zone de liste de contrôle contient des chaînes de texte et des cases à cocher, mais vous n’avez pas besoin de disposer de texte. Par exemple, vous pouvez avoir une liste de petites bitmaps avec une case à cocher en regard de chaque élément.

Pour créer votre propre zone de liste de contrôle, vous devez dériver `CCheckListBox`votre propre classe de. Pour dériver votre propre classe, écrivez un constructeur pour la classe dérivée, `Create`puis appelez.

Si vous voulez gérer les messages de notification Windows envoyés par une zone de liste à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajoutez une entrée de table des messages et une fonction membre de gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de la table des messages prend la forme suivante:

**En\_cas de**_notification_ **(** _ID_, _memberFxn_ **)**

où `id` spécifie l’ID de fenêtre enfant du contrôle qui envoie la `memberFxn` notification et est le nom de la fonction membre parente que vous avez écrite pour gérer la notification.

Le prototype de fonction du parent est le suivant:

`afx_msg void memberFxn();`

Il n’existe qu’une seule entrée de table des messages qui concerne `CCheckListBox` spécifiquement (mais consultez également les entrées de la table des messages pour [CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE l’utilisateur a modifié l’état de la case à cocher d’un élément.

Si votre zone de liste de contrôle est une zone de liste de contrôle par défaut (une liste de chaînes avec les cases à cocher dimensionnées par défaut à gauche de chacune), vous pouvez utiliser la valeur par défaut [CCheckListBox::D rawitem](#drawitem) pour dessiner la zone de liste de vérification. Dans le cas contraire, vous devez substituer la fonction [CListBox:: CompareItem](../../mfc/reference/clistbox-class.md#compareitem) et les fonctions [CCheckListBox::D rawitem](#drawitem) et [CCheckListBox:: MeasureItem](#measureitem) .

Vous pouvez créer une zone de liste de contrôle à partir d’un modèle de boîte de dialogue ou directement dans votre code.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox

Construit un objet `CCheckListBox`.

```
CCheckListBox();
```

### <a name="remarks"></a>Notes

Vous construisez `CCheckListBox` un objet en deux étapes. Tout d’abord, définissez une `CCheckListBox`classe dérivée `Create`de, puis appelez, qui initialise la zone de liste de contrôle Windows `CCheckListBox` et l’attache à l’objet.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>  CCheckListBox::Create

Crée la zone de liste de contrôle Windows et l’attache `CCheckListBox` à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style de la zone de liste de contrôle. Le style doit être LBS_HASSTRINGS et LBS_OWNERDRAWFIXED (tous les éléments de la liste ont la même hauteur) ou LBS_OWNERDRAWVARIABLE (les éléments de la liste sont de différentes hauteurs). Ce style peut être combiné avec d’autres [styles de zone de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , à l’exception de LBS_USETABSTOPS.

*rect*<br/>
Spécifie la taille et la position de la zone de liste de contrôle. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Spécifie la fenêtre parente de la zone de `CDialog` liste de contrôle (généralement un objet). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la zone de liste de contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez `CCheckListBox` un objet en deux étapes. Tout d’abord, définissez une classe `CcheckListBox` dérivée de `Create`, puis appelez, qui initialise la zone de liste de contrôle Windows et `CCheckListBox`l’attache à. Pour obtenir un exemple, consultez [CCheckListBox:: CCheckListBox](#cchecklistbox) .

Lorsque `Create` exécute, Windows envoie les messages [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) au contrôle de zone de liste de vérification.

Ces messages sont gérés par défaut par les fonctions membres [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)et [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) dans la `CWnd` classe de base. Pour étendre la gestion des messages par défaut, ajoutez une table des messages à votre classe dérivée et substituez les fonctions membres du gestionnaire de messages précédentes. Substituez `OnCreate`, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Appliquez les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle de zone de liste de contrôle:

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_VSCROLL pour ajouter une barre de défilement verticale

- WS_HSCROLL pour ajouter une barre de défilement horizontale

- WS_GROUP pour regrouper les contrôles

- WS_TABSTOP pour autoriser la tabulation sur ce contrôle

##  <a name="drawitem"></a>  CCheckListBox::DrawItem

Appelée par l’infrastructure quand un aspect visuel d’une zone de liste de contrôle owner-drawn change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur long vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Les `itemAction` membres `itemState` et de la `DRAWITEMSTRUCT` structure définissent l’action de dessin à effectuer.

Par défaut, cette fonction dessine une liste de cases à cocher par défaut, composée d’une liste de chaînes, chacune avec une case à cocher dimensionnée par défaut à gauche. La taille de la liste de cases à cocher est celle spécifiée dans [Create](#create).

Remplacez cette fonction membre pour implémenter le dessin des zones de liste de contrôle owner-draw qui ne sont pas par défaut, telles que les zones de liste de contrôle avec des listes qui ne sont pas des chaînes, avec des éléments de hauteur variable, ou avec des cases à cocher qui ne sont pas sur la gauche. L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant l’arrêt de cette fonction membre.

Si les éléments de liste de contrôle ne sont pas tous de la même hauteur, le style `Create`de zone de liste de contrôle (spécifié dans) doit être * * LBS_OWNERVARIABLE, et vous devez remplacer la fonction [MeasureItem](#measureitem) .

##  <a name="enable"></a>  CCheckListBox::Enable

Appelez cette fonction pour activer ou désactiver un élément de zone de liste de contrôle.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément de zone de liste de contrôle à activer.

*bEnabled*<br/>
Spécifie si l’élément est activé ou désactivé.

##  <a name="getcheck"></a>  CCheckListBox::GetCheck

Récupère l’état de la case à cocher spécifiée.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro d’une case à cocher qui est contenue dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

État de la case à cocher spécifiée. Le tableau suivant répertorie les valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|BST_CHECKED|La case à cocher est activée.|
|BST_UNCHECKED|La case à cocher n’est pas activée.|
|BST_INDETERMINATE|L’état de la case à cocher est indéterminé.|

##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle

Appelez cette fonction pour récupérer le style de la zone de liste de contrôle.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Valeur de retour

Style des cases à cocher du contrôle.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les styles possibles, consultez [SetCheckStyle](#setcheckstyle).

##  <a name="isenabled"></a>  CCheckListBox::IsEnabled

Appelez cette fonction pour déterminer si un élément est activé.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément est activé; Sinon, 0.

##  <a name="measureitem"></a>  CCheckListBox::MeasureItem

Appelé par le Framework lorsqu’une zone de liste de contrôle avec un style non défini par défaut est créée.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Pointeur long vers une structure [measureitemstruct,](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre et remplissez la `MEASUREITEMSTRUCT` structure pour informer les fenêtres des dimensions des éléments de zone de liste de vérification. Si la zone de liste de contrôle est créée avec le style [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , l’infrastructure appelle cette fonction membre pour chaque élément de la zone de liste. Dans le cas contraire, ce membre n’est appelé qu’une seule fois.

##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition

L’infrastructure appelle cette fonction pour atteindre la position et la taille de la case à cocher dans un élément.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Paramètres

*rectItem*<br/>
Position et taille de l’élément de liste.

*rectCheckBox*<br/>
Position et taille par défaut de la case à cocher d’un élément.

### <a name="return-value"></a>Valeur de retour

La position et la taille de la case à cocher d’un élément.

### <a name="remarks"></a>Notes

L’implémentation par défaut retourne uniquement la position et la taille par défaut de la`rectCheckBox`case à cocher (). Par défaut, une case à cocher est alignée dans l’angle supérieur gauche d’un élément et correspond à la taille de case à cocher standard. Il peut arriver que vous souhaitiez les cases à cocher à droite, ou que vous souhaitiez une case à cocher plus grande ou plus petite. Dans ce cas, substituez `OnGetCheckPosition` pour modifier la position et la taille de la case à cocher dans l’élément.

##  <a name="setcheck"></a>  CCheckListBox::SetCheck

Définit l’état de la case à cocher spécifiée.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro d’une case à cocher qui est contenue dans la zone de liste.

*nCheck*<br/>
État du bouton pour la case à cocher spécifiée. Consultez la section Notes pour connaître les valeurs possibles.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs possibles pour le paramètre *nConsultez* .

|Valeur|Description|
|-----------|-----------------|
|BST_CHECKED|Activez la case à cocher spécifiée.|
|BST_UNCHECKED|Désactivez la case à cocher spécifiée.|
|BST_INDETERMINATE|Affectez à l’état de la case à cocher spécifié la valeur Indeterminate.<br /><br /> Cet État est disponible uniquement si le style de case à cocher est BS_AUTO3STATE ou BS_3STATE. Pour plus d’informations, consultez [styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle

Appelez cette fonction pour définir le style des cases à cocher dans la zone liste de vérification.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Détermine le style des cases à cocher de la zone de liste de vérification.

### <a name="remarks"></a>Notes

Les styles valides sont les suivants:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Pour plus d’informations sur ces styles, consultez [styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Voir aussi

[Exemple MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)
