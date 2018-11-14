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
ms.openlocfilehash: b3bf93a876f9092d5615b75ca45fea71341d3557
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327341"
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
|[CCheckListBox::Create](#create)|Crée la zone de liste de vérification de Windows et l’attache à la `CCheckListBox` objet.|
|[CCheckListBox::DrawItem](#drawitem)|Appelé par l’infrastructure lorsqu’un aspect visuel d’une change de zone de liste en mode owner-draw.|
|[CCheckListBox::Enable](#enable)|Active ou désactive un élément de zone de liste de vérification.|
|[CCheckListBox::GetCheck](#getcheck)|Obtient l’état de case à cocher d’un élément.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtient le style de cases à cocher du contrôle.|
|[CCheckListBox::IsEnabled](#isenabled)|Détermine si un élément est activé.|
|[CCheckListBox::MeasureItem](#measureitem)|Appelé par l’infrastructure lors de la création d’une zone de liste avec un style de dessin owner-drawn.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Appelé par le framework pour obtenir la position de la case à cocher d’un élément.|
|[CCheckListBox::SetCheck](#setcheck)|Définit l’état de case à cocher d’un élément.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Définit le style de cases à cocher du contrôle.|

## <a name="remarks"></a>Notes

Un « liste de vérification » affiche une liste d’éléments, tels que des noms de fichiers. Chaque élément dans la liste a une case à cocher en regard de celui-ci que l’utilisateur peut vérifier ou effacer.

`CCheckListBox` concerne uniquement les contrôles owner-drawn, car la liste contient plus de chaînes de texte. La plus simple, une zone de liste de contrôle contient des chaînes de texte et cases à cocher, mais vous n’avez pas besoin pour que tout le texte. Par exemple, vous pourriez avoir une liste de bitmaps de petite taille avec une case à cocher en regard de chaque élément.

Pour créer votre propre zone de liste de vérification, vous devez dériver votre propre classe de `CCheckListBox`. Pour dériver votre propre classe, écrire un constructeur pour la classe dérivée, puis appelez `Create`.

Si vous souhaitez gérer les messages de notification Windows envoyés par une zone de liste à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajouter une fonction de membre entrée et le Gestionnaire de messages-table des messages à la classe parente pour chaque message.

Chaque entrée de table des messages prend la forme suivante :

**ON\_**_Notification_ **(** _id_, _memberFxn_ **)**

où `id` Spécifie l’ID de fenêtre enfant du contrôle qui envoie la notification et `memberFxn` est le nom de la fonction de membre parent que vous avez écrit pour gérer les notifications.

Prototype de fonction du parent est la suivante :

`afx_msg void memberFxn();`

Il n'existe qu’une seule entrée de table des messages qui se rapporte spécifiquement à `CCheckListBox` (mais consultez également les entrées de table des messages pour [CListBox](../../mfc/reference/clistbox-class.md)) :

- ON_CLBN_CHKCHANGE l’utilisateur a modifié l’état de case à cocher d’un élément.

Si votre zone de liste de vérification est une zone de liste de vérification par défaut (il s’agit d’une liste de chaînes avec les cases à cocher à gauche de chaque taille par défaut), vous pouvez utiliser la valeur par défaut [CCheckListBox::DrawItem](#drawitem) pour dessiner la zone de liste de vérification. Sinon, vous devez substituer la [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) (fonction) et le [CCheckListBox::DrawItem](#drawitem) et [CCheckListBox::MeasureItem](#measureitem) fonctions.

Vous pouvez créer une zone de liste de vérification à partir d’un modèle de boîte de dialogue ou directement dans votre code.

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

Vous construisez un `CCheckListBox` objet en deux étapes. Tout d’abord définir une classe dérivée de `CCheckListBox`, puis appelez `Create`, qui initialise la zone de liste de vérification de Windows et l’attache à la `CCheckListBox` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>  CCheckListBox::Create

Crée la zone de liste de vérification de Windows et l’attache à la `CCheckListBox` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style de la zone de liste de vérification. Le style doit être LBS_HASSTRINGS et LBS_OWNERDRAWFIXED (tous les éléments dans la liste ont la même hauteur) ou LBS_OWNERDRAWVARIABLE (éléments de la liste sont de différentes hauteurs). Ce style peut être combiné avec d’autres [styles de zone de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) sauf LBS_USETABSTOPS.

*Rect*<br/>
Spécifie la taille de la zone de liste de vérification et la position. Peut être un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](../../mfc/reference/rect-structure1.md) structure.

*pParentWnd*<br/>
Spécifie la fenêtre parente de la zone de liste de vérification (généralement un `CDialog` objet). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle. de la zone de liste de vérification

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CCheckListBox` objet en deux étapes. Tout d’abord, définissez une classe dérivée de `CcheckListBox` , puis appelez `Create`, qui initialise la zone de liste de vérification de Windows et l’attache à la `CCheckListBox`. Consultez [CCheckListBox::CCheckListBox](#cchecklistbox) pour obtenir un exemple.

Lorsque `Create` s’exécute, les envois de Windows le [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) messages sur le contrôle de zone de liste de vérification.

Ces messages sont gérées par défaut par le [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), et [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) fonctions membres dans la `CWnd` classe de base. Pour étendre la gestion de message par défaut, ajouter une table des messages à la votre classe dérivée et les fonctions de membre de substitution le Gestionnaire de messages précédent. Substituer `OnCreate`, par exemple, pour effectuer une initialisation nécessaire pour une nouvelle classe.

Appliquer les éléments suivants [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle de zone de liste de vérification :

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_VSCROLL pour ajouter une barre de défilement verticale

- WS_HSCROLL pour ajouter une barre de défilement horizontale

- WS_GROUP aux contrôles de groupe

- WS_TABSTOP pour permettre la tabulation à ce contrôle

##  <a name="drawitem"></a>  CCheckListBox::DrawItem

Appelé par l’infrastructure lorsqu’un aspect visuel d’une zone change de liste de contrôle owner-drawn.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur long désignant un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` et `itemState` membres de la `DRAWITEMSTRUCT` structure définir l’action de dessin qui doit être effectuée.

Par défaut, cette fonction Dessine une liste de case à cocher par défaut, consistant en une liste de chaînes avec une case à cocher dimensionné par défaut à gauche. La taille de la liste de case à cocher est celui spécifié dans [créer](#create).

Remplacez cette fonction membre pour implémenter le dessin de zones de liste de contrôle en mode owner-draw qui ne sont pas la valeur par défaut, tels que les zones de liste de contrôle avec des listes qui ne sont pas des chaînes, des éléments de hauteur variable ou avec cases à cocher qui ne sont pas sur la gauche. L’application doit restaurer tous les objets interface (GDI) périphérique graphique sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant l’arrêt de cette fonction membre.

Si les éléments de zone de liste de vérification ne sont pas tous la même hauteur, la liste de contrôle de zone de style (spécifié dans `Create`) doit être ** LBS_OWNERVARIABLE et vous devez substituer la [MeasureItem](#measureitem) (fonction).

##  <a name="enable"></a>  CCheckListBox::Enable

Appelez cette fonction pour activer ou désactiver un élément de zone de liste de vérification.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément de zone de liste de contrôle doit être activé.

*case d’option bActivé*<br/>
Spécifie si l’élément est activé ou désactivé.

##  <a name="getcheck"></a>  CCheckListBox::GetCheck

Récupère l’état de la case à cocher spécifié.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro d’une case à cocher qui est contenue dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

L’état de la case à cocher spécifié. Le tableau suivant répertorie les valeurs possibles.

|Value|Description|
|-----------|-----------------|
|BST_CHECKED|La case à cocher est activée.|
|BST_UNCHECKED|La case à cocher n’est pas activée.|
|BST_INDETERMINATE|L’état de la case à cocher est indéterminé.|

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

*nIndex*<br/>
Index de l’élément.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément est activé ; sinon 0.

##  <a name="measureitem"></a>  CCheckListBox::MeasureItem

Appelé par l’infrastructure lors de la création d’une zone de liste de contrôle avec un style non défini par défaut.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Un pointeur long désignant un [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) structure.

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre et renseignez la `MEASUREITEMSTRUCT` structure afin d’informer Windows des dimensions d’éléments de la zone de liste de vérification. Si la zone de liste de vérification est créée avec le [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, l’infrastructure appelle cette fonction membre pour chaque élément dans la zone de liste. Sinon, ce membre est appelé une seule fois.

##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition

L’infrastructure appelle cette fonction pour obtenir la position et la taille de la case à cocher dans un élément.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Paramètres

*rectItem*<br/>
La position et la taille de l’élément de liste.

*rectCheckBox*<br/>
La position par défaut et la taille de la case à cocher d’un élément.

### <a name="return-value"></a>Valeur de retour

La position et la taille de la case à cocher d’un élément.

### <a name="remarks"></a>Notes

L’implémentation par défaut retourne uniquement la position par défaut et la taille de la case à cocher (`rectCheckBox`). Par défaut, une case à cocher est aligné dans le coin supérieur gauche d’un élément et la taille de la case à cocher standard. Il peut arriver dans lequel vous souhaitez les cases à cocher sur la droite, ou une case à cocher supérieure ou inférieure. Dans ces cas, remplacer `OnGetCheckPosition` pour modifier la position de la case à cocher et leur taille dans l’élément.

##  <a name="setcheck"></a>  CCheckListBox::SetCheck

Définit l’état de la case à cocher spécifié.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro d’une case à cocher qui est contenue dans la zone de liste.

*nVérifiez*<br/>
L’état du bouton de la case à cocher spécifié. Consultez la section Notes pour les valeurs possibles.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs possibles pour le *nVérifiez* paramètre.

|Value|Description|
|-----------|-----------------|
|BST_CHECKED|Sélectionnez la case à cocher spécifié.|
|BST_UNCHECKED|Désactivez la case à cocher spécifié.|
|BST_INDETERMINATE|Définir l’état de la case à cocher spécifiée à une valeur indéterminée.<br /><br /> Cet état est disponible uniquement si le style de case à cocher est BS_AUTO3STATE ou BS_3STATE. Pour plus d’informations, consultez [Styles de boutons](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle

Appelez cette fonction pour définir le style des cases à cocher dans la zone de liste de vérification.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Détermine le style de cases à cocher dans la zone de liste de vérification.

### <a name="remarks"></a>Notes

Les styles valides sont :

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Pour plus d’informations sur ces styles, consultez [Styles de boutons](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Voir aussi

[Exemple MFC TSTCON](../../visual-cpp-samples.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)
