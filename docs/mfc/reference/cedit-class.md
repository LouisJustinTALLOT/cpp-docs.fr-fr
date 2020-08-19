---
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 0e15472ddaad214d575a7479680454ae6b4d3178
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561620"
---
# <a name="cedit-class"></a>CEdit Class

Fournit les fonctionnalités d'un contrôle d'édition Windows.

## <a name="syntax"></a>Syntaxe

```
class CEdit : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CEdit :: CEdit](#cedit)|Construit un `CEdit` objet de contrôle.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CEdit :: CanUndo](#canundo)|Détermine si une opération de modification de contrôle peut être annulée.|
|[CEdit :: CharFromPos](#charfrompos)|Récupère les index de ligne et de caractère pour le caractère le plus proche d’une position spécifiée.|
|[CEdit :: Clear](#clear)|Supprime (efface) la sélection actuelle (le cas échéant) dans le contrôle d’édition.|
|[CEdit :: Copy](#copy)|Copie la sélection actuelle (le cas échéant) dans le contrôle d’édition dans le presse-papiers au format CF_TEXT.|
|[CEdit :: Create](#create)|Crée le contrôle d’édition Windows et l’attache à l' `CEdit` objet.|
|[CEdit :: Cut](#cut)|Supprime (coupe) la sélection actuelle (le cas échéant) dans le contrôle d’édition et copie le texte supprimé dans le presse-papiers au format CF_TEXT.|
|[CEdit :: EmptyUndoBuffer](#emptyundobuffer)|Réinitialise (efface) l’indicateur d’annulation d’un contrôle d’édition.|
|[CEdit :: FmtLines](#fmtlines)|Définit l’inclusion de caractères de saut de ligne conditionnels dans un contrôle d’édition sur plusieurs lignes.|
|[CEdit :: GetCueBanner](#getcuebanner)|Récupère le texte affiché en tant que texte de la file d’attente, ou Conseil, dans un contrôle d’édition lorsque le contrôle est vide et n’a pas le focus.|
|[CEdit :: GetFirstVisibleLine](#getfirstvisibleline)|Détermine la ligne la plus visible dans un contrôle d’édition.|
|[CEdit :: GetHandle](#gethandle)|Récupère un handle vers la mémoire actuellement allouée pour un contrôle d’édition sur plusieurs lignes.|
|[CEdit :: GetHighlight](#gethighlight)|Obtient les index des caractères de début et de fin d’une plage de texte mise en surbrillance dans le contrôle d’édition actuel.|
|[CEdit :: GetLimitText](#getlimittext)|Obtient la quantité maximale de texte qu’il `CEdit` peut contenir.|
|[CEdit :: GetLine](#getline)|Récupère une ligne de texte à partir d’un contrôle d’édition.|
|[CEdit :: GetLineCount](#getlinecount)|Récupère le nombre de lignes dans un contrôle d’édition sur plusieurs lignes.|
|[CEdit :: GetMargins](#getmargins)|Obtient les marges gauche et droite de ce `CEdit` .|
|[CEdit :: GetModify](#getmodify)|Détermine si le contenu d’un contrôle d’édition a été modifié.|
|[CEdit :: GetPasswordChar](#getpasswordchar)|Récupère le caractère de mot de passe affiché dans un contrôle d’édition lorsque l’utilisateur entre du texte.|
|[CEdit :: GetRect](#getrect)|Obtient le rectangle de mise en forme d’un contrôle d’édition.|
|[CEdit :: GetSel](#getsel)|Obtient la position du premier et du dernier caractère de la sélection actuelle dans un contrôle d’édition.|
|[CEdit :: HideBalloonTip](#hideballoontip)|Masque les info-bulles associées au contrôle d’édition actuel.|
|[CEdit :: LimitText](#limittext)|Limite la longueur du texte que l’utilisateur peut entrer dans un contrôle d’édition.|
|[CEdit :: LineFromChar](#linefromchar)|Récupère le numéro de ligne de la ligne qui contient l’index de caractère spécifié.|
|[CEdit :: LineIndex](#lineindex)|Récupère l’index de caractère d’une ligne dans un contrôle d’édition à plusieurs lignes.|
|[CEdit :: LineLength](#linelength)|Récupère la longueur d’une ligne dans un contrôle d’édition.|
|[CEdit :: LineScroll](#linescroll)|Fait défiler le texte d’un contrôle d’édition sur plusieurs lignes.|
|[CEdit ::P Oller](#paste)|Insère les données du presse-papiers dans le contrôle d’édition à la position actuelle du curseur. Les données sont insérées uniquement si le presse-papiers contient des données au format CF_TEXT.|
|[CEdit ::P osFromChar](#posfromchar)|Récupère les coordonnées de l’angle supérieur gauche d’un index de caractère spécifié.|
|[CEdit :: ReplaceSel](#replacesel)|Remplace la sélection actuelle dans un contrôle d’édition par le texte spécifié.|
|[CEdit :: SetCueBanner](#setcuebanner)|Définit le texte affiché en tant que texte de la file d’attente, ou Conseil, dans un contrôle d’édition lorsque le contrôle est vide et n’a pas le focus.|
|[CEdit :: SetHandle](#sethandle)|Définit le handle sur la mémoire locale qui sera utilisée par un contrôle d’édition sur plusieurs lignes.|
|[CEdit :: SetHighlight](#sethighlight)|Met en surbrillance une plage de texte qui est affichée dans le contrôle d’édition actuel.|
|[CEdit :: SetLimitText](#setlimittext)|Définit la quantité maximale de texte qu’il `CEdit` peut contenir.|
|[CEdit :: SetMargins](#setmargins)|Définit les marges gauche et droite de ce `CEdit` .|
|[CEdit :: SetModify](#setmodify)|Définit ou efface l’indicateur de modification d’un contrôle d’édition.|
|[CEdit :: SetPasswordChar](#setpasswordchar)|Définit ou supprime un caractère de mot de passe affiché dans un contrôle d’édition lorsque l’utilisateur entre du texte.|
|[CEdit :: SetReadOnly](#setreadonly)|Définit l’État en lecture seule d’un contrôle d’édition.|
|[CEdit :: SetRect](#setrect)|Définit le rectangle de mise en forme d’un contrôle d’édition sur plusieurs lignes et met à jour le contrôle.|
|[CEdit :: SetRectNP](#setrectnp)|Définit le rectangle de mise en forme d’un contrôle d’édition sur plusieurs lignes sans redessiner la fenêtre du contrôle.|
|[CEdit :: SetSel](#setsel)|Sélectionne une plage de caractères dans un contrôle d’édition.|
|[CEdit :: SetTabStops](#settabstops)|Définit les taquets de tabulation dans un contrôle d’édition sur plusieurs lignes.|
|[CEdit :: ShowBalloonTip](#showballoontip)|Affiche une info-bulle associée au contrôle d’édition actuel.|
|[CEdit :: Undo](#undo)|Inverse la dernière opération de contrôle de modification.|

## <a name="remarks"></a>Notes

Un contrôle d’édition est une fenêtre enfant rectangulaire dans laquelle l’utilisateur peut entrer du texte.

Vous pouvez créer un contrôle d’édition à partir d’un modèle de boîte de dialogue ou directement dans votre code. Dans les deux cas, appelez d’abord le constructeur `CEdit` pour construire l' `CEdit` objet, puis appelez la fonction membre [Create](#create) pour créer le contrôle d’édition Windows et l’attacher à l' `CEdit` objet.

La construction peut être un processus en une étape dans une classe dérivée de `CEdit` . Écrivez un constructeur pour la classe dérivée et appelez `Create` à partir du constructeur.

`CEdit` hérite des fonctionnalités importantes de `CWnd` . Pour définir et récupérer du texte à partir d’un `CEdit` objet, utilisez les `CWnd` fonctions membres [SetWindowText](cwnd-class.md#setwindowtext) et [GetWindowText](cwnd-class.md#getwindowtext), qui définissent ou obtiennent la totalité du contenu d’un contrôle d’édition, même s’il s’agit d’un contrôle multiligne. Les lignes de texte dans un contrôle multiligne sont séparées par des séquences de caractères' \r\n'. En outre, si un contrôle d’édition est multiligne, récupérez et définissez une partie du texte du contrôle en appelant les `CEdit` fonctions membres [getline](#getline), [SetSel](#setsel), [GetSel](#getsel)et [ReplaceSel](#replacesel).

Si vous voulez gérer les messages de notification Windows envoyés par un contrôle d’édition à son parent (généralement une classe dérivée de `CDialog` ), ajoutez une entrée de la table des messages et une fonction membre du gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de la table des messages prend la forme suivante :

  **ON_**_Notification_**de on_ (** _ID_**,** _memberFxn_ **)**

où `id` spécifie l’ID de fenêtre enfant du contrôle d’édition qui envoie la notification, et `memberFxn` est le nom de la fonction membre parente que vous avez écrite pour gérer la notification.

Le prototype de fonction du parent est le suivant :

**afx_msg** void memberFxn **();**

Voici une liste d’entrées de table des messages potentielle et une description des cas dans lesquels ils sont envoyés au parent :

- ON_EN_CHANGE l’utilisateur a pris une action qui peut avoir modifié du texte dans un contrôle d’édition. Contrairement au message de notification EN_UPDATE, ce message de notification est envoyé une fois que Windows a mis à jour l’affichage.

- ON_EN_ERRSPACE le contrôle d’édition ne peut pas allouer suffisamment de mémoire pour répondre à une demande spécifique.

- ON_EN_HSCROLL l’utilisateur clique sur la barre de défilement horizontale d’un contrôle d’édition. La fenêtre parente est avertie avant la mise à jour de l’écran.

- ON_EN_KILLFOCUS le contrôle d’édition perd le focus d’entrée.

- ON_EN_MAXTEXT l’insertion actuelle a dépassé le nombre spécifié de caractères pour le contrôle d’édition et a été tronquée. Également envoyé lorsqu’un contrôle d’édition n’a pas le style ES_AUTOHSCROLL et que le nombre de caractères à insérer dépasse la largeur du contrôle d’édition. Également envoyé lorsqu’un contrôle d’édition n’a pas le style ES_AUTOVSCROLL et que le nombre total de lignes résultant d’une insertion de texte dépasse la hauteur du contrôle d’édition.

- ON_EN_SETFOCUS envoyé lorsqu’un contrôle d’édition reçoit le focus d’entrée.

- ON_EN_UPDATE le contrôle d’édition va afficher le texte modifié. Envoyé une fois que le contrôle a mis en forme le texte, mais avant de l’utiliser pour le texte afin que la taille de la fenêtre puisse être modifiée, si nécessaire.

- ON_EN_VSCROLL l’utilisateur clique sur la barre de défilement verticale d’un contrôle d’édition. La fenêtre parente est avertie avant la mise à jour de l’écran.

Si vous créez un `CEdit` objet dans une boîte de dialogue, l' `CEdit` objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CEdit` objet à partir d’une ressource de boîte de dialogue à l’aide de l’éditeur de boîtes de dialogue, l' `CEdit` objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CEdit` objet dans une fenêtre, vous devrez peut-être également le détruire. Si vous créez l' `CEdit` objet sur la pile, il est détruit automatiquement. Si vous créez l' `CEdit` objet sur le tas à l’aide de la **`new`** fonction, vous devez appeler **`delete`** sur l’objet pour le détruire lorsque l’utilisateur termine le contrôle d’édition Windows. Si vous allouez de la mémoire dans l' `CEdit` objet, substituez le `CEdit` destructeur pour supprimer les allocations.

Pour modifier certains styles dans un contrôle d’édition (par exemple, ES_READONLY), vous devez envoyer des messages spécifiques au contrôle au lieu d’utiliser [ModifyStyle](cwnd-class.md#modifystyle). Consultez [modifier les styles de contrôle](/windows/win32/Controls/edit-control-styles) dans le SDK Windows.

Pour plus d’informations sur `CEdit` , consultez [contrôles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a> CEdit :: CanUndo

Appelez cette fonction pour déterminer si la dernière opération de modification peut être annulée.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la dernière opération de modification peut être annulée par un appel à la `Undo` fonction membre ; 0 si elle ne peut pas être annulée.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [EM_CANUNDO](/windows/win32/Controls/em-canundo) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: Undo](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a> CEdit :: CEdit

Construit un objet `CEdit`.

```
CEdit();
```

### <a name="remarks"></a>Notes

Utilisez [créer](#create) pour construire le contrôle d’édition Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a> CEdit :: CharFromPos

Appelez cette fonction pour récupérer les index de ligne et de caractère de base zéro du caractère le plus proche du point spécifié dans ce `CEdit` contrôle

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Coordonnées d’un point dans la zone cliente de cet `CEdit` objet.

### <a name="return-value"></a>Valeur de retour

L’index de caractère dans le mot de poids faible, et l’index de ligne dans le mot de poids fort.

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette fonction membre est disponible à partir de Windows 95 et Windows NT 4,0.

Pour plus d’informations, consultez [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a> CEdit :: Clear

Appelez cette fonction pour supprimer (effacer) la sélection actuelle (le cas échéant) dans le contrôle d’édition.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

La suppression effectuée par `Clear` peut être annulée en appelant la fonction membre [Undo](#undo) .

Pour supprimer la sélection actuelle et placer le contenu supprimé dans le presse-papiers, appelez la fonction membre [Cut](#cut) .

Pour plus d’informations, consultez [WM_CLEAR](/windows/win32/dataxchg/wm-clear) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a> CEdit :: Copy

Appelez cette fonction pour copier des la sélection actuelle (le cas échéant) dans le contrôle d’édition dans le presse-papiers au format CF_TEXT.

```cpp
void Copy();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [WM_COPY](/windows/win32/dataxchg/wm-copy) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a> CEdit :: Create

Crée le contrôle d’édition Windows et l’attache à l' `CEdit` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle d’édition. Applique une combinaison de [styles de modification](styles-used-by-mfc.md#edit-styles) au contrôle.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle d’édition. Il peut s’agir d’un `CRect` objet ou d’une `RECT` structure.

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle d’édition (généralement `CDialog` ). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle d’édition.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’initialisation réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CEdit` objet en deux étapes. Tout d’abord, appelez le `CEdit` constructeur, puis appelez `Create` , qui crée le contrôle d’édition Windows et l’attache à l' `CEdit` objet.

Lorsque `Create` exécute, Windows envoie les messages [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)et [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) au contrôle d’édition.

Ces messages sont gérés par défaut par les fonctions membres [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate)et [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) dans la `CWnd` classe de base. Pour étendre la gestion des messages par défaut, dérivez une classe de `CEdit` , ajoutez une table des messages à la nouvelle classe et substituez les fonctions membres du gestionnaire de messages ci-dessus. Substituez `OnCreate` , par exemple, pour effectuer l’initialisation nécessaire pour la nouvelle classe.

Appliquez les [styles de fenêtre](styles-used-by-mfc.md#window-styles) suivants à un contrôle d’édition.

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_GROUP des contrôles de groupe

- WS_TABSTOP pour inclure le contrôle d’édition dans l’ordre de tabulation

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a> CEdit :: Cut

Appelez cette fonction pour supprimer (couper) la sélection actuelle (le cas échéant) dans le contrôle d’édition et copier le texte supprimé dans le presse-papiers au format CF_TEXT.

```cpp
void Cut();
```

### <a name="remarks"></a>Notes

La suppression effectuée par `Cut` peut être annulée en appelant la fonction membre [Undo](#undo) .

Pour supprimer la sélection actuelle sans placer le texte supprimé dans le presse-papiers, appelez la fonction membre [Clear](#clear) .

Pour plus d’informations, consultez [WM_CUT](/windows/win32/dataxchg/wm-cut) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a> CEdit :: EmptyUndoBuffer

Appelez cette fonction pour réinitialiser (effacer) l’indicateur d’annulation d’un contrôle d’édition.

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Notes

Le contrôle d’édition ne peut pas annuler la dernière opération. L’indicateur Undo est défini chaque fois qu’une opération dans le contrôle d’édition peut être annulée.

L’indicateur Undo est automatiquement effacé chaque fois que les fonctions membres [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) ou [SetHandle](#sethandle) `CWnd` sont appelées.

Pour plus d’informations, consultez [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a> CEdit :: FmtLines

Appelez cette fonction pour définir l’inclusion de caractères de saut de ligne conditionnels dans un contrôle d’édition à plusieurs lignes.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Paramètres

*bAddEOL*<br/>
Spécifie si les caractères de saut de ligne conditionnel doivent être insérés. La valeur TRUE insère les caractères ; la valeur FALSe les supprime.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si une mise en forme se produit ; Sinon, 0.

### <a name="remarks"></a>Notes

Un saut de ligne conditionnel se compose de deux retours chariot et d’un saut de ligne inséré à la fin d’une ligne qui est cassée en raison du retour automatique à la ligne. Un saut de ligne matériel consiste en un retour chariot et un saut de ligne. Les lignes qui se terminent par un saut de ligne fixe ne sont pas affectées par `FmtLines` .

Windows répondra uniquement si l' `CEdit` objet est un contrôle d’édition sur plusieurs lignes.

`FmtLines` affecte uniquement la mémoire tampon retournée par [GetHandle](#gethandle) et le texte retourné par [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). Elle n’a aucun impact sur l’affichage du texte dans le contrôle d’édition.

Pour plus d’informations, consultez [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a> CEdit :: GetCueBanner

Récupère le texte affiché en tant que texte de la file d’attente, ou Conseil, dans un contrôle d’édition lorsque le contrôle est vide.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
à Pointeur vers une chaîne qui contient le texte de la file d’attente.

*cchText*<br/>
dans Nombre de caractères qui peuvent être reçus. Ce nombre comprend le caractère NULL de fin.

### <a name="return-value"></a>Valeur de retour

Pour la première surcharge, TRUE si la méthode réussit ; Sinon, FALSe.

Pour la deuxième surcharge, un [CString](../../atl-mfc-shared/using-cstring.md) qui contient le texte de la file d’attente si la méthode réussit ; Sinon, la chaîne vide ("").

### <a name="remarks"></a>Notes

Cette méthode envoie le message [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) , qui est décrit dans le SDK Windows. Pour plus d’informations, consultez la macro [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) .

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a> CEdit :: GetFirstVisibleLine

Appelez cette fonction pour déterminer la ligne la plus visible dans un contrôle d’édition.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la ligne la plus visible au premier plan. Pour les contrôles d’édition sur une seule ligne, la valeur de retour est 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a> CEdit :: GetHandle

Appelez cette fonction pour récupérer un handle de la mémoire actuellement allouée pour un contrôle d’édition sur plusieurs lignes.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Handle de mémoire local qui identifie la mémoire tampon contenant le contenu du contrôle d’édition. Si une erreur se produit, telle que l’envoi du message à un contrôle d’édition sur une seule ligne, la valeur de retour est 0.

### <a name="remarks"></a>Notes

Le handle est un handle de mémoire local qui peut être utilisé par n’importe quelle fonction de mémoire Windows **locale** qui prend un handle de mémoire local comme paramètre.

`GetHandle` est traité uniquement par les contrôles d’édition sur plusieurs lignes.

Appelez `GetHandle` pour un contrôle d’édition sur plusieurs lignes dans une boîte de dialogue uniquement si la boîte de dialogue a été créée avec l’indicateur de style DS_LOCALEDIT défini. Si le style de DS_LOCALEDIT n’est pas défini, vous obtiendrez toujours une valeur de retour différente de zéro, mais vous ne pourrez pas utiliser la valeur retournée.

> [!NOTE]
> `GetHandle` ne fonctionne pas avec Windows 95/98. Si vous appelez `GetHandle` dans Windows 95/98, la valeur null est retournée. `GetHandle` fonctionnera comme indiqué sous Windows NT, versions 3,51 et ultérieures.

Pour plus d’informations, consultez [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a> CEdit :: GetHighlight

Obtient les index du premier et du dernier caractère d’une plage de texte mise en surbrillance dans le contrôle d’édition actuel.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Paramètres

*pichStart*\
à Index de base zéro du premier caractère de la plage de texte mise en surbrillance.

*pichEnd*\
à Index de base zéro du dernier caractère de la plage de texte mise en surbrillance.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [EM_GETHILITE](/windows/win32/Controls/em-gethilite) , qui est décrit dans le SDK Windows. `SetHighlight`Et `GetHighlight` sont actuellement activés pour les générations Unicode uniquement.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a> CEdit :: GetLimitText

Appelez cette fonction membre pour obtenir la limite de texte pour cet `CEdit` objet.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Valeur de retour

Limite de texte actuelle, en TCHARs, pour cet `CEdit` objet.

### <a name="remarks"></a>Notes

La limite de texte correspond à la quantité maximale de texte, en TCHARs, que le contrôle d’édition peut accepter.

> [!NOTE]
> Cette fonction membre est disponible à partir de Windows 95 et Windows NT 4,0.

Pour plus d’informations, consultez [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a> CEdit :: GetLine

Appelez cette fonction pour récupérer une ligne de texte à partir d’un contrôle d’édition et la placer dans *lpszbuffer a été*.

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie le numéro de ligne à récupérer à partir d’un contrôle d’édition sur plusieurs lignes. Les numéros de ligne sont de base zéro ; la valeur 0 spécifie la première ligne. Ce paramètre est ignoré par un contrôle d’édition sur une seule ligne.

*Lpszbuffer a été*<br/>
Pointe vers la mémoire tampon qui reçoit une copie de la ligne. Le premier mot de la mémoire tampon doit spécifier le nombre maximal de TCHARs qui peuvent être copiés dans la mémoire tampon.

*nMaxLength*<br/>
Spécifie le nombre maximal de caractères TCHAR qui peuvent être copiés dans la mémoire tampon. `GetLine` place cette valeur dans le premier mot de *lpszbuffer a été* avant d’effectuer l’appel à Windows.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés. La valeur de retour est 0 si le numéro de ligne spécifié par *nIndex* est supérieur au nombre de lignes dans le contrôle d’édition.

### <a name="remarks"></a>Notes

La ligne copiée ne contient pas de caractère de fin null.

Pour plus d’informations, consultez [EM_GETLINE](/windows/win32/Controls/em-getline) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: GetLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a> CEdit :: GetLineCount

Appelez cette fonction pour récupérer le nombre de lignes dans un contrôle d’édition sur plusieurs lignes.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Valeur de retour

Entier contenant le nombre de lignes dans le contrôle d’édition sur plusieurs lignes. Si aucun texte n’a été entré dans le contrôle d’édition, la valeur de retour est 1.

### <a name="remarks"></a>Notes

`GetLineCount` est traité uniquement par des contrôles d’édition à plusieurs lignes.

Pour plus d’informations, consultez [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a> CEdit :: GetMargins

Appelez cette fonction membre pour récupérer les marges gauche et droite de ce contrôle d’édition.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de la marge de gauche dans le mot de poids faible et largeur de la marge de droite dans le mot de poids fort.

### <a name="remarks"></a>Notes

Les marges sont mesurées en pixels.

> [!NOTE]
> Cette fonction membre est disponible à partir de Windows 95 et Windows NT 4,0.

Pour plus d’informations, consultez [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CEditView :: GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a> CEdit :: GetModify

Appelez cette fonction pour déterminer si le contenu d’un contrôle d’édition a été modifié.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le contenu du contrôle de modification a été modifié ; 0 si elles sont restées inchangées.

### <a name="remarks"></a>Notes

Windows maintient un indicateur interne indiquant si le contenu du contrôle d’édition a été modifié. Cet indicateur est effacé lorsque le contrôle d’édition est créé pour la première fois et peut également être effacé en appelant la fonction membre [SetModify](#setmodify) .

Pour plus d’informations, consultez [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a> CEdit :: GetPasswordChar

Appelez cette fonction pour récupérer le caractère de mot de passe affiché dans un contrôle d’édition lorsque l’utilisateur entre du texte.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Valeur de retour

Spécifie le caractère à afficher à la place du caractère tapé par l’utilisateur. La valeur de retour est NULL si aucun caractère de mot de passe n’existe.

### <a name="remarks"></a>Notes

Si vous créez le contrôle d’édition avec le style ES_PASSWORD, la DLL qui prend en charge le contrôle détermine le caractère de mot de passe par défaut. Le manifeste ou la méthode [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) détermine quelle dll prend en charge le contrôle d’édition. Si user32.dll prend en charge le contrôle d’édition, le caractère de mot de passe par défaut est l’astérisque (« * », U + 002A). Si comctl32.dll version 6 prend en charge le contrôle d’édition, le caractère par défaut est cercle noir (« ● », U + 25CF). Pour plus d’informations sur la DLL et la version prises en charge par les contrôles communs, consultez [versions de Shell et de contrôles communs](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Cette méthode envoie le message [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a> CEdit :: GetRect

Appelez cette fonction pour récupérer le rectangle de mise en forme d’un contrôle d’édition.

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers la `RECT` structure qui reçoit le rectangle de mise en forme.

### <a name="remarks"></a>Notes

Le rectangle de mise en forme est le rectangle de limitation du texte, qui est indépendant de la taille de la fenêtre Modifier le contrôle.

Le rectangle de mise en forme d’un contrôle d’édition sur plusieurs lignes peut être modifié par les fonctions membres [SetRect](#setrect) et [SetRectNP](#setrectnp) .

Pour plus d’informations, consultez [EM_GETRECT](/windows/win32/Controls/em-getrect) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: LimitText](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a> CEdit :: GetSel

Appelez cette fonction pour obtenir les positions des caractères de début et de fin de la sélection actuelle (le cas échéant) dans un contrôle d’édition, à l’aide de la valeur de retour ou des paramètres.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Paramètres

*nStartChar*<br/>
Référence à un entier qui recevra la position du premier caractère dans la sélection actuelle.

*nEndChar*<br/>
Référence à un entier qui recevra la position du premier caractère non sélectionné au-delà de la fin de la sélection actuelle.

### <a name="return-value"></a>Valeur de retour

La version qui retourne une valeur DWORD retourne une valeur qui contient la position de départ dans le mot de poids faible et la position du premier caractère non sélectionné après la fin de la sélection dans le mot de poids fort.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [EM_GETSEL](/windows/win32/Controls/em-getsel) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a> CEdit :: HideBalloonTip

Masque les info-bulles associées au contrôle d’édition actuel.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette fonction envoie le message [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) , qui est décrit dans le SDK Windows.

## <a name="ceditlimittext"></a><a name="limittext"></a> CEdit :: LimitText

Appelez cette fonction pour limiter la longueur du texte que l’utilisateur peut entrer dans un contrôle d’édition.

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Paramètres

*nChars*<br/>
Spécifie la longueur (en TCHARs) du texte que l’utilisateur peut entrer. Si ce paramètre a la valeur 0, la longueur du texte est définie sur UINT_MAX octets. Il s'agit du comportement par défaut.

### <a name="remarks"></a>Notes

La modification de la limite de texte restreint uniquement le texte que l’utilisateur peut entrer. Elle n’a aucun effet sur le texte déjà présent dans le contrôle d’édition, ni sur la longueur du texte copié dans le contrôle d’édition par la fonction membre [SetWindowText](cwnd-class.md#setwindowtext) dans `CWnd` . Si une application utilise la `SetWindowText` fonction pour placer plus de texte dans un contrôle d’édition que celui spécifié dans l’appel à `LimitText` , l’utilisateur peut supprimer n’importe quel texte dans le contrôle d’édition. Toutefois, la limite de texte empêche l’utilisateur de remplacer le texte existant par un nouveau texte, sauf si la suppression de la sélection actuelle provoque la chute du texte en dessous de la limite du texte.

> [!NOTE]
> Dans Win32 (Windows NT et Windows 95/98), [SetLimitText](#setlimittext) remplace cette fonction.

Pour plus d’informations, consultez [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a> CEdit :: LineFromChar

Appelez cette fonction pour récupérer le numéro de ligne de la ligne qui contient l’index de caractère spécifié.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient la valeur d’index de base zéro du caractère souhaité dans le texte du contrôle d’édition, ou contient-1. Si *nIndex* est-1, il spécifie la ligne active, autrement dit, la ligne qui contient le signe insertion.

### <a name="return-value"></a>Valeur de retour

Numéro de ligne de base zéro de la ligne contenant l’index de caractère spécifié par *nIndex*. Si *nIndex* a la valeur-1, le numéro de la ligne qui contient le premier caractère de la sélection est retourné. Si aucune sélection n’est effectuée, le numéro de la ligne active est retourné.

### <a name="remarks"></a>Notes

Un index de caractère est le nombre de caractères à partir du début du contrôle d’édition.

Cette fonction membre est utilisée uniquement par les contrôles d’édition sur plusieurs lignes.

Pour plus d’informations, consultez [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a> CEdit :: LineIndex

Appelez cette fonction pour récupérer l’index de caractère d’une ligne dans un contrôle d’édition sur plusieurs lignes.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Paramètres

*nLigne*<br/>
Contient la valeur d’index de la ligne souhaitée dans le texte du contrôle d’édition, ou contient-1. Si *nLigne* est-1, il spécifie la ligne active, autrement dit, la ligne qui contient le signe insertion.

### <a name="return-value"></a>Valeur de retour

Index de caractère de la ligne spécifiée dans *nLigne* ou-1 si le numéro de ligne spécifié est supérieur au nombre de lignes dans le contrôle d’édition.

### <a name="remarks"></a>Notes

L’index de caractère est le nombre de caractères à partir du début du contrôle d’édition jusqu’à la ligne spécifiée.

Cette fonction membre est traitée uniquement par des contrôles d’édition à plusieurs lignes.

Pour plus d’informations, consultez [EM_LINEINDEX](/windows/win32/controls/em-lineindex) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a> CEdit :: LineLength

Récupère la longueur d’une ligne dans un contrôle d’édition.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Paramètres

*nLigne*<br/>
Index de base zéro d’un caractère de la ligne dont la longueur doit être récupérée. La valeur par défaut est -1.

### <a name="return-value"></a>Valeur de retour

Pour les contrôles d’édition sur une seule ligne, la valeur de retour est la longueur, en TCHARs, du texte dans le contrôle d’édition.

Pour les contrôles d’édition multiligne, la valeur de retour est la longueur, en TCHARs, de la ligne spécifiée par le paramètre *nLigne* . Pour du texte ANSI, la longueur est le nombre d’octets dans la ligne ; pour le texte Unicode, la longueur est le nombre de caractères de la ligne. La longueur n’inclut pas le caractère de retour chariot à la fin de la ligne.

Si le paramètre *nLigne* est supérieur au nombre de caractères dans le contrôle, la valeur de retour est zéro.

Si le paramètre *nLigne* est-1, la valeur de retour est le nombre de caractères non sélectionnés dans les lignes qui contiennent des caractères sélectionnés. Par exemple, si la sélection s’étend du quatrième caractère d’une ligne jusqu’au huitième caractère à partir de la fin de la ligne suivante, la valeur de retour est 10. Autrement dit, trois caractères sur la première ligne et sept sur la suivante.

Pour plus d’informations sur le type TCHAR, consultez la ligne TCHAR dans le tableau des [types de données Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Notes

Cette méthode est prise en charge par le message [EM_LINELENGTH](/windows/win32/Controls/em-linelength) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: LineIndex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a> CEdit :: LineScroll

Appelez cette fonction pour faire défiler le texte d’un contrôle d’édition sur plusieurs lignes.

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Paramètres

*nLines*<br/>
Spécifie le nombre de lignes à faire défiler verticalement.

*nChars*<br/>
Spécifie le nombre de positions de caractère à faire défiler horizontalement. Cette valeur est ignorée si le contrôle d’édition a le style ES_RIGHT ou ES_CENTER.

### <a name="remarks"></a>Notes

Cette fonction membre est traitée uniquement par des contrôles d’édition à plusieurs lignes.

Le contrôle d’édition ne fait pas défiler verticalement la dernière ligne de texte dans le contrôle d’édition. Si la ligne actuelle plus le nombre de lignes spécifié par *nLines* dépasse le nombre total de lignes dans le contrôle d’édition, la valeur est ajustée de sorte que la dernière ligne du contrôle d’édition soit défilant en haut de la fenêtre de contrôle de modification.

`LineScroll` peut être utilisé pour faire défiler horizontalement le dernier caractère d’une ligne.

Pour plus d’informations, consultez [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: GetFirstVisibleLine](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a> CEdit ::P Oller

Appelez cette fonction pour insérer les données du presse-papiers dans le `CEdit` au niveau du point d’insertion.

```cpp
void Paste();
```

### <a name="remarks"></a>Notes

Les données sont insérées uniquement si le presse-papiers contient des données au format CF_TEXT.

Pour plus d’informations, consultez [WM_PASTE](/windows/win32/dataxchg/wm-paste) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a> CEdit ::P osFromChar

Appelez cette fonction pour obtenir la position (angle supérieur gauche) d’un caractère donné dans cet `CEdit` objet.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Paramètres

*nChar*<br/>
Index de base zéro du caractère spécifié.

### <a name="return-value"></a>Valeur de retour

Coordonnées du coin supérieur gauche du caractère spécifié par *nchar*.

### <a name="remarks"></a>Notes

Le caractère est spécifié en donnant sa valeur d’index de base zéro. Si *nchar* est supérieur à l’index du dernier caractère de cet `CEdit` objet, la valeur de retour spécifie les coordonnées de la position de caractère juste après le dernier caractère de cet `CEdit` objet.

> [!NOTE]
> Cette fonction membre est disponible à partir de Windows 95 et Windows NT 4,0.

Pour plus d’informations, consultez [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: LineFromChar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a> CEdit :: ReplaceSel

Appelez cette fonction pour remplacer la sélection actuelle dans un contrôle d’édition par le texte spécifié par *lpszNewText*.

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszNewText*<br/>
Pointe vers une chaîne se terminant par un caractère null qui contient le texte de remplacement.

*bCanUndo*<br/>
Pour spécifier que cette fonction peut être annulée, affectez la valeur TRUE à ce paramètre. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

Remplace uniquement une partie du texte dans un contrôle d’édition. Si vous souhaitez remplacer tout le texte, utilisez la fonction membre [CWnd :: SetWindowText](cwnd-class.md#setwindowtext) .

S’il n’y a aucune sélection actuelle, le texte de remplacement est inséré à l’emplacement actuel du curseur.

Pour plus d’informations, consultez [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: LineIndex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a> CEdit :: SetCueBanner

Définit le texte affiché en tant que texte de la file d’attente, ou Conseil, dans un contrôle d’édition lorsque le contrôle est vide.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
dans Pointeur vers une chaîne qui contient la pile à afficher dans le contrôle d’édition.

*fDrawWhenFocused*<br/>
dans Si la valeur est FALSe, la bannière de la pile n’est pas dessinée lorsque l’utilisateur clique dans le contrôle d’édition et donne le focus au contrôle.

Si la valeur est TRUE, la bannière de signal est dessinée même lorsque le contrôle a le focus. La bannière de signal disparaît lorsque l’utilisateur commence à taper dans le contrôle.

La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) , qui est décrit dans le SDK Windows. Pour plus d’informations, consultez la macro [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) .

### <a name="example"></a>Exemple

L’exemple suivant illustre la méthode [CEdit :: SetCueBanner](#setcuebanner) .

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a> CEdit :: SetHandle

Appelez cette fonction pour définir le handle sur la mémoire locale qui sera utilisée par un contrôle d’édition sur plusieurs lignes.

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Paramètres

*hBuffer*<br/>
Contient un handle vers la mémoire locale. Ce descripteur doit avoir été créé par un appel précédent à la fonction Windows [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) à l’aide de l’indicateur LMEM_MOVEABLE. La mémoire est supposée contenir une chaîne terminée par le caractère null. Si ce n’est pas le cas, le premier octet de la mémoire allouée doit être défini sur 0.

### <a name="remarks"></a>Notes

Le contrôle d’édition utilise ensuite cette mémoire tampon pour stocker le texte actuellement affiché au lieu d’allouer sa propre mémoire tampon.

Cette fonction membre est traitée uniquement par des contrôles d’édition à plusieurs lignes.

Avant qu’une application ne définisse un nouveau descripteur de mémoire, elle doit utiliser la fonction membre [GetHandle](#gethandle) pour obtenir le handle vers la mémoire tampon actuelle et libérer cette mémoire à l’aide de la `LocalFree` fonction Windows.

`SetHandle` efface la mémoire tampon d’annulation (la fonction membre [CanUndo](#canundo) retourne 0) et l’indicateur de modification interne (la fonction membre [GetModify](#getmodify) retourne alors 0). La fenêtre Modifier-contrôle est redessinée.

Vous pouvez utiliser cette fonction membre dans un contrôle d’édition sur plusieurs lignes dans une boîte de dialogue uniquement si vous avez créé la boîte de dialogue avec l’indicateur de style DS_LOCALEDIT défini.

> [!NOTE]
> `GetHandle` ne fonctionne pas avec Windows 95/98. Si vous appelez `GetHandle` dans Windows 95/98, la valeur null est retournée. `GetHandle` fonctionnera comme indiqué sous Windows NT, versions 3,51 et ultérieures.

Pour plus d’informations, consultez [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)et [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a> CEdit :: SetHighlight

Met en surbrillance une plage de texte qui est affichée dans le contrôle d’édition actuel.

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Paramètres

*ichStart*\
dans Index de base zéro du premier caractère de la plage de texte à mettre en surbrillance.

*ichEnd*\
dans Index de base zéro du dernier caractère de la plage de texte à mettre en surbrillance.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , qui est décrit dans le SDK Windows.  Cette méthode envoie le message [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , qui est décrit dans le SDK Windows. `SetHighlight`Et `GetHighlight` sont activés uniquement pour les générations Unicode.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a> CEdit :: SetLimitText

Appelez cette fonction membre pour définir la limite de texte pour cet `CEdit` objet.

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Paramètres

*nMax*<br/>
Nouvelle limite de texte, en caractères.

### <a name="remarks"></a>Notes

La limite de texte correspond à la quantité maximale de texte, en caractères, que le contrôle d’édition peut accepter.

La modification de la limite de texte restreint uniquement le texte que l’utilisateur peut entrer. Elle n’a aucun effet sur le texte déjà présent dans le contrôle d’édition, ni sur la longueur du texte copié dans le contrôle d’édition par la fonction membre [SetWindowText](cwnd-class.md#setwindowtext) dans `CWnd` . Si une application utilise la `SetWindowText` fonction pour placer plus de texte dans un contrôle d’édition que celui spécifié dans l’appel à `LimitText` , l’utilisateur peut supprimer n’importe quel texte dans le contrôle d’édition. Toutefois, la limite de texte empêche l’utilisateur de remplacer le texte existant par un nouveau texte, sauf si la suppression de la sélection actuelle provoque la chute du texte en dessous de la limite du texte.

Cette fonction remplace [LimitText](#limittext) dans Win32.

Pour plus d’informations, consultez [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CEditView :: GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a> CEdit :: SetMargins

Appelez cette méthode pour définir les marges gauche et droite de ce contrôle d’édition.

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Paramètres

*nLeft*<br/>
Largeur de la nouvelle marge de gauche, en pixels.

*nRight*<br/>
Largeur de la nouvelle marge de droite, en pixels.

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette fonction membre est disponible à partir de Windows 95 et Windows NT 4,0.

Pour plus d’informations, consultez [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CEditView :: GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a> CEdit :: SetModify

Appelez cette fonction pour définir ou désélectionner l’indicateur modifié d’un contrôle d’édition.

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Paramètres

*bModified*<br/>
La valeur TRUE indique que le texte a été modifié et la valeur FALSe indique qu’il n’est pas modifié. Par défaut, l’indicateur modifié est défini.

### <a name="remarks"></a>Notes

L’indicateur modifié indique si le texte du contrôle d’édition a été modifié ou non. Elle est définie automatiquement chaque fois que l’utilisateur modifie le texte. Sa valeur peut être récupérée à l’aide de la fonction membre [GetModify](#getmodify) .

Pour plus d’informations, consultez [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: GetModify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a> CEdit :: SetPasswordChar

Appelez cette fonction pour définir ou supprimer un caractère de mot de passe affiché dans un contrôle d’édition lorsque l’utilisateur tape du texte.

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Paramètres

*cascade*<br/>
Spécifie le caractère à afficher à la place du caractère tapé par l’utilisateur. Si *ch* est égal à 0, les caractères réels tapés par l’utilisateur sont affichés.

### <a name="remarks"></a>Notes

Lorsqu’un caractère de mot de passe est défini, ce caractère est affiché pour chaque caractère que l’utilisateur tape.

Cette fonction membre n’a aucun effet sur un contrôle d’édition sur plusieurs lignes.

Lorsque la `SetPasswordChar` fonction membre est appelée, `CEdit` redessine tous les caractères visibles à l’aide du caractère spécifié par *ch*.

Si le contrôle d’édition est créé avec le style [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) , le caractère de mot de passe par défaut est défini sur un astérisque ( <strong>\*</strong> ). Ce style est supprimé si `SetPasswordChar` est appelé avec *ch* défini sur 0.

Pour plus d’informations, consultez [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a> CEdit :: SetReadOnly

Appelle cette fonction pour définir l’État en lecture seule d’un contrôle d’édition.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bReadOnly*<br/>
Spécifie s’il faut définir ou supprimer l’État en lecture seule du contrôle d’édition. La valeur TRUE définit l’État en lecture seule ; la valeur FALSe définit l’État sur lecture/écriture.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération réussit, ou 0 si une erreur se produit.

### <a name="remarks"></a>Notes

Le paramètre actuel peut être trouvé en testant l’indicateur [ES_READONLY](styles-used-by-mfc.md#edit-styles) dans la valeur de retour de [CWnd :: getStyle](cwnd-class.md#getstyle).

Pour plus d’informations, consultez [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a> CEdit :: SetRect

Appelez cette fonction pour définir les dimensions d’un rectangle à l’aide des coordonnées spécifiées.

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers la `RECT` structure ou l' `CRect` objet qui spécifie les nouvelles dimensions du rectangle de mise en forme.

### <a name="remarks"></a>Notes

Ce membre est traité uniquement par les contrôles d’édition sur plusieurs lignes.

Utilisez `SetRect` pour définir le rectangle de mise en forme d’un contrôle d’édition sur plusieurs lignes. Le rectangle de mise en forme est le rectangle de limitation du texte, qui est indépendant de la taille de la fenêtre Modifier le contrôle. Lorsque le contrôle d’édition est créé pour la première fois, le rectangle de mise en forme est le même que la zone cliente de la fenêtre Modifier-contrôle. À l’aide de la `SetRect` fonction membre, une application peut rendre le rectangle de mise en forme plus grand ou plus petit que la fenêtre Modifier-contrôle.

Si le contrôle d’édition n’a pas de barre de défilement, le texte est coupé, pas encapsulé, si le rectangle de mise en forme est plus grand que la fenêtre. Si le contrôle d’édition contient une bordure, le rectangle de mise en forme est réduit de la taille de la bordure. Si vous ajustez le rectangle retourné par la `GetRect` fonction membre, vous devez supprimer la taille de la bordure avant de passer le rectangle à `SetRect` .

Lorsque `SetRect` est appelé, le texte du contrôle d’édition est également reformaté et réaffiché.

Pour plus d’informations, consultez [EM_SETRECT](/windows/win32/Controls/em-setrect) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a> CEdit :: SetRectNP

Appelez cette fonction pour définir le rectangle de mise en forme d’un contrôle d’édition sur plusieurs lignes.

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une `RECT` structure ou un `CRect` objet qui spécifie les nouvelles dimensions du rectangle.

### <a name="remarks"></a>Notes

Le rectangle de mise en forme est le rectangle de limitation du texte, qui est indépendant de la taille de la fenêtre Modifier le contrôle.

`SetRectNP` est identique à la `SetRect` fonction membre, sauf que la fenêtre Modifier-contrôle n’est pas redessinée.

Lorsque le contrôle d’édition est créé pour la première fois, le rectangle de mise en forme est le même que la zone cliente de la fenêtre Modifier-contrôle. En appelant la `SetRectNP` fonction membre, une application peut rendre le rectangle de mise en forme plus grand ou plus petit que la fenêtre Modifier-contrôle.

Si le contrôle d’édition n’a pas de barre de défilement, le texte est coupé, pas encapsulé, si le rectangle de mise en forme est plus grand que la fenêtre.

Ce membre est traité uniquement par les contrôles d’édition sur plusieurs lignes.

Pour plus d’informations, consultez [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a> CEdit :: SetSel

Appelez cette fonction pour sélectionner une plage de caractères dans un contrôle d’édition.

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Paramètres

*dwSelection*<br/>
Spécifie la position de départ dans le mot de poids faible et la position de fin dans le mot de poids fort. Si le mot de poids faible est 0 et que le mot de poids fort est-1, tout le texte du contrôle d’édition est sélectionné. Si le mot de poids faible est-1, toute sélection en cours est supprimée.

*bNoScroll*<br/>
Indique si le signe insertion doit être défilant dans la vue. Si la valeur est FALSe, le signe insertion est défilant dans la vue. Si la valeur est TRUE, le signe insertion n’est pas défilé dans la vue.

*nStartChar*<br/>
Spécifie la position de départ. Si *nStartChar* a la valeur 0 et que *nEndChar* est égal à-1, tout le texte du contrôle d’édition est sélectionné. Si *nStartChar* est-1, toute sélection en cours est supprimée.

*nEndChar*<br/>
Spécifie la position de fin.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [EM_SETSEL](/windows/win32/Controls/em-setsel) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à [CEdit :: GetSel](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a> CEdit :: SetTabStops

Appelez cette fonction pour définir les taquets de tabulation dans un contrôle d’édition à plusieurs lignes.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Paramètres

*cxEachStop*<br/>
Spécifie que les taquets de tabulation doivent être définis à chaque unité de boîte de dialogue *cxEachStop* .

*nTabStops*<br/>
Spécifie le nombre de taquets de tabulation contenus dans *rgTabStops*. Ce nombre doit être supérieur à 1.

*rgTabStops*<br/>
Pointe vers un tableau d’entiers non signés spécifiant les taquets de tabulation dans les unités du dialogue. Une unité de boîte de dialogue est une distance horizontale ou verticale. Une unité de boîte de dialogue horizontale est égale à un quart de l’unité de largeur de base de la boîte de dialogue actuelle, et 1 unité de boîte de dialogue verticale est égale à un huitième de l’unité de hauteur de base de la boîte de dialogue actuelle. Les unités de dialogue sont calculées en fonction de la hauteur et de la largeur de la police système actuelle. La `GetDialogBaseUnits` fonction Windows retourne les unités de base de la boîte de dialogue en pixels.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les onglets ont été définis ; Sinon, 0.

### <a name="remarks"></a>Notes

Lorsque le texte est copié dans un contrôle d’édition sur plusieurs lignes, tout caractère de tabulation dans le texte entraîne la génération de l’espace jusqu’au taquet de tabulation suivant.

Pour définir des taquets de tabulation sur la taille par défaut de 32 unités de boîte de dialogue, appelez la version sans paramètre de cette fonction membre. Pour définir des taquets de tabulation d’une taille autre que 32, appelez la version avec le paramètre *cxEachStop* . Pour définir des taquets de tabulation sur un tableau de tailles, utilisez la version avec deux paramètres.

Cette fonction membre est traitée uniquement par des contrôles d’édition à plusieurs lignes.

`SetTabStops` ne redessine pas automatiquement la fenêtre d’édition. Si vous modifiez les taquets de tabulation du texte déjà présent dans le contrôle d’édition, appelez [CWnd :: InvalidateRect](cwnd-class.md#invalidaterect) pour redessiner la fenêtre d’édition.

Pour plus d’informations, consultez [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) et [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CEditView :: SetTabStops](ceditview-class.md#settabstops).

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a> CEdit :: ShowBalloonTip

Affiche une info-bulle associée au contrôle d’édition actuel.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>Paramètres

*pEditBalloonTip*\
dans Pointeur vers une structure [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) qui décrit l’info-bulle.

*lpszTitle*\
dans Pointeur vers une chaîne Unicode qui contient le titre de l’info-bulle.

*lpszText*\
dans Pointeur vers une chaîne Unicode qui contient le texte d’info-bulle.

*ttiIcon*\
dans **Entier** qui spécifie le type d’icône à associer à l’info-bulle. La valeur par défaut est TTI_NONE. Pour plus d’informations, consultez le `ttiIcon` membre de la structure [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) .

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette fonction envoie le message [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) , qui est décrit dans le SDK Windows. Pour plus d’informations, consultez la macro [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) .

### <a name="example"></a>Exemple

L’exemple de code suivant définit une variable, `m_cedit` , qui est utilisée pour accéder au contrôle d’édition actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant affiche une info-bulle pour un contrôle d’édition. La méthode [CEdit :: ShowBalloonTip](#showballoontip) spécifie un titre et un texte d’info-bulle.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a> CEdit :: Undo

Appelez cette fonction pour annuler la dernière opération de contrôle de modification.

```
BOOL Undo();
```

### <a name="return-value"></a>Valeur de retour

Pour un contrôle d’édition sur une seule ligne, la valeur de retour est toujours différente de zéro. Pour un contrôle d’édition sur plusieurs lignes, la valeur de retour est différente de zéro si l’opération d’annulation réussit, ou 0 si l’opération d’annulation échoue.

### <a name="remarks"></a>Notes

Une opération d’annulation peut également être annulée. Par exemple, vous pouvez restaurer le texte supprimé avec le premier appel à `Undo` . Tant qu’il n’y a pas d’opération de modification intermédiaire, vous pouvez supprimer le texte avec un deuxième appel à `Undo` .

Pour plus d’informations, consultez [EM_UNDO](/windows/win32/Controls/em-undo) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](cwnd-class.md)<br/>
[CButton, classe](cbutton-class.md)<br/>
[CComboBox (classe)](ccombobox-class.md)<br/>
[CListBox, classe](clistbox-class.md)<br/>
[CScrollBar, classe](cscrollbar-class.md)<br/>
[CStatic, classe](cstatic-class.md)<br/>
[CDialog (classe)](cdialog-class.md)
