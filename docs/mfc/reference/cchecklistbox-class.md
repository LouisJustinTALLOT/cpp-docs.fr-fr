---
title: Classe CCheckListBox
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
ms.openlocfilehash: dc0e80e80d61104a4d8cb5f1cfd4e26a64c42249
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752743"
---
# <a name="cchecklistbox-class"></a>Classe CCheckListBox

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
|[CCheckListBox::Créer](#create)|Crée la case de liste de `CCheckListBox` contrôle Windows et la fixe à l’objet.|
|[CCheckListBox::DrawItem](#drawitem)|Appelé par le cadre quand un aspect visuel d’une boîte de liste propriétaire-tirage change.|
|[CCheckListBox::Active](#enable)|Permet ou désactive un élément de la case de contrôle.|
|[CCheckListBox::GetCheck](#getcheck)|Obtient l’état de la case à cocher d’un article.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtient le style des cases à cocher du contrôle.|
|[CCheckListBox::IsEnabled](#isenabled)|Détermine si un élément est activé.|
|[CCheckListBox::MeasureItem](#measureitem)|Appelé par le cadre quand une boîte de liste avec un style propriétaire-tirage est créé.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Appelé par le cadre pour obtenir la position de la case à cocher d’un article.|
|[CCheckListBox::SetCheck](#setcheck)|Définit l’état de la case à cocher d’un article.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Définit le style des cases à cocher du contrôle.|

## <a name="remarks"></a>Notes

Une « case de liste de contrôle » affiche une liste d’éléments, tels que les noms de fichiers. Chaque élément de la liste dispose d’une case à cocher à côté de celle-ci que l’utilisateur peut vérifier ou effacer.

`CCheckListBox`est uniquement pour les contrôles tirés par le propriétaire parce que la liste contient plus que des chaînes de texte. À son plus simple, une case de liste de contrôle contient des chaînes de texte et des cases à cocher, mais vous n’avez pas besoin d’avoir du texte du tout. Par exemple, vous pouvez avoir une liste de petits bitmaps avec une case à cocher à côté de chaque élément.

Pour créer votre propre case de liste de `CCheckListBox`contrôle, vous devez tirer votre propre classe de . Pour dériver votre propre classe, écrivez un `Create`constructeur pour la classe dérivée, puis appelez .

Si vous souhaitez traiter les messages de notification Windows envoyés par une case de liste à son parent (généralement une classe dérivée de [CDialog),](../../mfc/reference/cdialog-class.md)ajoutez une entrée de carte de message et une fonction de membre de gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de carte de message prend la forme suivante :

**ON\_**_Notification_ **(** _id_, _memberFxn_ **)**

lorsque `id` spécifie l’ID de fenêtre `memberFxn` de l’enfant du contrôle envoyant la notification et est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.

Le prototype de fonction du parent est le suivant :

`afx_msg void memberFxn();`

Il n’y a qu’une seule `CCheckListBox` entrée de carte de message qui se rapporte spécifiquement à (mais voir aussi les entrées de carte de message pour [CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE L’utilisateur a modifié l’état de la case à cocher d’un article.

Si votre case de liste de contrôle est une case de liste de contrôle par défaut (une liste de chaînes avec les cases à cocher de la taille d’un défaut à gauche de chacune), vous pouvez utiliser la [CCheckListBox::DrawItem](#drawitem) pour dessiner la case de liste de contrôle. Sinon, vous devez passer outre à la fonction [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) et à la fonction [CCheckListBox::DrawItem](#drawitem) et [CCheckListBox::MeasureItem](#measureitem) fonctions.

Vous pouvez créer une case de liste de contrôle à partir d’un modèle de dialogue ou directement dans votre code.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cchecklistboxcchecklistbox"></a><a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

Construit un objet `CCheckListBox`.

```
CCheckListBox();
```

### <a name="remarks"></a>Notes

Vous construisez un `CCheckListBox` objet en deux étapes. D’abord définir `CCheckListBox`une classe `Create`dérivée de , puis appeler , qui `CCheckListBox` initialise la case de liste de contrôle Windows et la fixe à l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

## <a name="cchecklistboxcreate"></a><a name="create"></a>CCheckListBox::Créer

Crée la case de liste de `CCheckListBox` contrôle Windows et la fixe à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style de la case de liste de contrôle. Le style doit être LBS_HASSTRINGS et soit LBS_OWNERDRAWFIXED (tous les éléments de la liste sont de la même hauteur) ou LBS_OWNERDRAWVARIABLE (les éléments de la liste sont de hauteurs variables). Ce style peut être combiné avec d’autres [styles de liste-boîte,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) sauf LBS_USETABSTOPS.

*Rect*<br/>
Spécifie la taille et la position de la liste de contrôle. Peut être soit un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente de `CDialog` la case à cocher (généralement un objet). Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la case de contrôle de la liste de contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CCheckListBox` objet en deux étapes. Tout d’abord, `CcheckListBox` définir une `Create`classe dérivée de puis appeler , qui `CCheckListBox`initialise la case liste de contrôle Windows et l’attache à la . Voir [CCheckListBox:CCheckListBox](#cchecklistbox) pour un échantillon.

Lors `Create` de l’exécution, Windows envoie le [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) messages au contrôle de la liste de contrôle.

Ces messages sont traités par défaut par le [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize) `CWnd` , et les fonctions des membres [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) dans la classe de base. Pour étendre la manipulation par défaut du message, ajoutez une carte de message à la classe dérivée et remplacez les fonctions de membre de message précédente. `OnCreate`Remplacer, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Appliquer les styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle de la case à cocher :

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

- WS_VSCROLL Pour ajouter une barre de défilement verticale

- WS_HSCROLL Pour ajouter une barre de défilement horizontal

- WS_GROUP Pour les contrôles de groupe

- WS_TABSTOP pour permettre le tabbing à ce contrôle

## <a name="cchecklistboxdrawitem"></a><a name="drawitem"></a>CCheckListBox::DrawItem

Appelé par le cadre lorsqu’un aspect visuel d’une case de contrôle tirée par le propriétaire change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un long pointeur vers une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` `itemState` et les `DRAWITEMSTRUCT` membres de la structure définissent l’action de dessin qui doit être effectuée.

Par défaut, cette fonction tire une liste de case à cocher par défaut, composée d’une liste de chaînes chacune avec une case à cocher de taille par défaut à gauche. La taille de la liste de cocher est celle spécifiée dans [Create](#create).

Remplacer cette fonction de membre pour implémenter le dessin des cases de liste de contrôle propriétaire-tirage qui ne sont pas la valeur par défaut, telles que les cases de liste de contrôle avec des listes qui ne sont pas des chaînes, avec des éléments à hauteur variable, ou avec des cases à cocher qui ne sont pas sur la gauche. L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction de membre.

Si les articles de la case de liste de contrôle `Create`ne sont pas tous de la même hauteur, le style de la case de contrôle (spécifié dans ) doit être **LBS_OWNERVARIABLE,** et vous devez passer outre à la fonction [MeasureItem.](#measureitem)

## <a name="cchecklistboxenable"></a><a name="enable"></a>CCheckListBox::Active

Appelez cette fonction pour activer ou désactiver un élément de la case de liste de contrôle.

```cpp
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément de la case de liste de contrôle à activer.

*bEnabled*<br/>
Précise si l’élément est activé ou désactivé.

## <a name="cchecklistboxgetcheck"></a><a name="getcheck"></a>CCheckListBox::GetCheck

Récupère l’état de la case à cocher spécifiée.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index à base zéro d’une case à cocher qui est contenu dans la case de liste.

### <a name="return-value"></a>Valeur de retour

L’état de la case à cocher spécifiée. Le tableau suivant énumère les valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|BST_CHECKED|La case à cocher est cochée.|
|BST_UNCHECKED|La case à cocher n’est pas cochée.|
|BST_INDETERMINATE|L’état de la case à cocher est indéterminé.|

## <a name="cchecklistboxgetcheckstyle"></a><a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

Appelez cette fonction pour obtenir le style de la case de la liste de contrôle.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Valeur de retour

Le style des cases à cocher du contrôle.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les styles possibles, voir [SetCheckStyle](#setcheckstyle).

## <a name="cchecklistboxisenabled"></a><a name="isenabled"></a>CCheckListBox::IsEnabled

Appelez cette fonction pour déterminer si un élément est activé.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément est activé; sinon 0.

## <a name="cchecklistboxmeasureitem"></a><a name="measureitem"></a>CCheckListBox::MeasureItem

Appelé par le cadre quand une case de liste de contrôle avec un style non-default est créé.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Un long pointeur vers une structure [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Notes

Par défaut, cette fonction de membre ne fait rien. Remplacez cette fonction de `MEASUREITEMSTRUCT` membre et remplissez la structure pour informer Windows des dimensions des éléments de la liste de contrôle. Si la case de liste de contrôle est créée avec le style [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) le cadre appelle cette fonction de membre pour chaque élément de la boîte de liste. Sinon, ce membre n’est appelé qu’une seule fois.

## <a name="cchecklistboxongetcheckposition"></a><a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

Le cadre appelle cette fonction pour obtenir la position et la taille de la case à cocher dans un élément.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Paramètres

*rectItem (rectItem)*<br/>
La position et la taille de l’élément de liste.

*rectCheckBox (en)*<br/>
La position par défaut et la taille de la case à cocher d’un article.

### <a name="return-value"></a>Valeur de retour

La position et la taille de la case à cocher d’un article.

### <a name="remarks"></a>Notes

L’implémentation par défaut ne renvoie`rectCheckBox`que la position par défaut et la taille de la case à cocher ( ). Par défaut, une case à cocher est alignée dans le coin supérieur gauche d’un article et est la taille standard de la case à cocher. Il peut y avoir des cas où vous voulez les cases à cocher sur la droite, ou que vous voulez une case à cocher plus grande ou plus petite. Dans ces cas, `OnGetCheckPosition` remplacez-les pour modifier la position et la taille de la case à cocher à l’intérieur de l’article.

## <a name="cchecklistboxsetcheck"></a><a name="setcheck"></a>CCheckListBox::SetCheck

Définit l’état de la case à cocher spécifiée.

```cpp
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index à base zéro d’une case à cocher qui est contenu dans la case de liste.

*nCheck (en)*<br/>
L’état du bouton pour la case à cocher spécifiée. Consultez la section Remarques pour les valeurs possibles.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs possibles pour le *paramètre nCheck.*

|Valeur|Description|
|-----------|-----------------|
|BST_CHECKED|Sélectionnez la case à cocher spécifiée.|
|BST_UNCHECKED|Effacer la case à cocher spécifiée.|
|BST_INDETERMINATE|Réglez l’état de la case à cocher spécifié pour une durée indéterminée.<br /><br /> Cet état n’est disponible que si le style de la case à cocher est BS_AUTO3STATE ou BS_3STATE. Pour plus d’informations, voir [Button Styles](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

## <a name="cchecklistboxsetcheckstyle"></a><a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

Appelez cette fonction pour définir le style des cases à cocher dans la case de liste de contrôle.

```cpp
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Détermine le style des cases à cocher dans la case de liste de contrôle.

### <a name="remarks"></a>Notes

Les styles valides sont les :

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Pour plus d’informations sur ces styles, voir [Button Styles](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Voir aussi

[Échantillon MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)
