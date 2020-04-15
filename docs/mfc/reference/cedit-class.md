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
ms.openlocfilehash: 3ca2fe4486ae0751f37d046ef28ed11e60e776ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373983"
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
|[CEdit::CEdit](#cedit)|Construit un `CEdit` objet de contrôle.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Détermine si une opération de modification-contrôle peut être annulée.|
|[CEdit::CharDepos](#charfrompos)|Récupère la ligne et les index de caractère pour le personnage le plus proche d’une position spécifiée.|
|[CEdit::Clair](#clear)|Supprime (efface) la sélection actuelle (le cas échéant) dans le contrôle de modification.|
|[CEdit::Copie](#copy)|Copie la sélection actuelle (le cas échéant) dans le contrôle de modification au Clipboard en format CF_TEXT.|
|[CEdit::Créer](#create)|Crée le contrôle de modification Windows `CEdit` et l’attache à l’objet.|
|[CEdit::Cut](#cut)|Supprime (coupes) la sélection actuelle (le cas échéant) dans le contrôle de modification et copie le texte supprimé au Clipboard dans CF_TEXT format.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Réinitialise (efface) le drapeau annuler d’un contrôle de modification.|
|[CEdit::FmtLines](#fmtlines)|Définit l’inclusion de caractères de rupture de ligne souples dans un contrôle de modification à plusieurs lignes.|
|[CEdit::GetCueBanner](#getcuebanner)|Récupère le texte qui s’affiche sous forme de signal texte, ou de pointe, dans un contrôle de modification lorsque le contrôle est vide et n’a pas de mise au point.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Détermine la ligne visible la plus haute dans un contrôle de modification.|
|[CEdit::GetHandle](#gethandle)|Récupère une poignée à la mémoire qui est actuellement allouée pour un contrôle de modification à plusieurs lignes.|
|[CEdit::GetHighlight](#gethighlight)|Obtient les index des caractères de départ et de fin dans une gamme de texte qui est mis en évidence dans le contrôle de modification actuel.|
|[CEdit::GetLimitText](#getlimittext)|Obtient la quantité maximale `CEdit` de texte que cela peut contenir.|
|[CEdit::GetLine](#getline)|Récupère une ligne de texte à partir d’un contrôle de modification.|
|[CEdit::GetLineCount](#getlinecount)|Récupère le nombre de lignes dans un contrôle de modification à plusieurs lignes.|
|[CEdit::GetMargins](#getmargins)|Obtient les marges gauche `CEdit`et droite pour cela .|
|[CEdit::GetModify](#getmodify)|Détermine si le contenu d’un contrôle de modification a été modifié.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Récupère le caractère de mot de passe affiché dans un contrôle de modification lorsque l’utilisateur entre le texte.|
|[CEdit::GetRect](#getrect)|Obtient le rectangle de formatage d’un contrôle de modification.|
|[CEdit::GetSel](#getsel)|Obtient les premières et dernières positions de caractère de la sélection actuelle dans un contrôle de modification.|
|[CEdit::HideBalloonTip](#hideballoontip)|Cache toute pointe de ballon associée au contrôle de modification en cours.|
|[CEdit::LimitText](#limittext)|Limite la longueur du texte que l’utilisateur peut entrer dans un contrôle de modification.|
|[CEdit::LineDeChar](#linefromchar)|Récupère le numéro de ligne de la ligne qui contient l’index de caractère spécifié.|
|[CEdit::LineIndex](#lineindex)|Récupère l’index de caractère d’une ligne dans un contrôle de modification à plusieurs lignes.|
|[CEdit::LineLength](#linelength)|Récupère la longueur d’une ligne dans un contrôle de modification.|
|[CEdit::LineScroll](#linescroll)|Faites défiler le texte d’un contrôle de modification à plusieurs lignes.|
|[CEdit::Paste](#paste)|Insère les données du Clipboard dans le contrôle de modification à la position de curseur actuel. Les données ne sont insérées que si le Clipboard contient des données en format CF_TEXT.|
|[CEdit::PFromChar](#posfromchar)|Récupère les coordonnées du coin supérieur gauche d’un index de caractère spécifié.|
|[CEdit::ReplaceSel](#replacesel)|Remplace la sélection actuelle dans un contrôle de modification par le texte spécifié.|
|[CEdit::SetCueBanner](#setcuebanner)|Définit le texte qui s’affiche sous forme de signal texte, ou de pointe, dans un contrôle de modification lorsque le contrôle est vide et n’a pas de mise au point.|
|[CEdit::SetHandle](#sethandle)|Définit la poignée à la mémoire locale qui sera utilisée par un contrôle de modification à plusieurs lignes.|
|[CEdit::SetHighlight](#sethighlight)|Met en évidence une gamme de texte qui est affichée dans le contrôle de modification en cours.|
|[CEdit::SetLimitText](#setlimittext)|Définit la quantité maximale `CEdit` de texte que cela peut contenir.|
|[CEdit::SetMargins](#setmargins)|Définit les marges gauche `CEdit`et droite pour cela .|
|[CEdit::SetModify](#setmodify)|Définit ou efface le drapeau de modification pour un contrôle de modification.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Définit ou supprime un personnage de mot de passe affiché dans un contrôle de modification lorsque l’utilisateur entre le texte.|
|[CEdit::SetReadOnly](#setreadonly)|Définit l’état de lecture seulement d’un contrôle de modification.|
|[CEdit::SetRect](#setrect)|Définit le rectangle de formatage d’un contrôle de modification à plusieurs lignes et met à jour le contrôle.|
|[CEdit::SetRectNP](#setrectnp)|Définit le rectangle de formatage d’un contrôle de modification à plusieurs lignes sans redessiner la fenêtre de contrôle.|
|[CEdit::SetSel](#setsel)|Sélectionne une gamme de caractères dans un contrôle de modification.|
|[CEdit::SetTabStops](#settabstops)|Définit l’onglet s’arrête dans un contrôle de modification à plusieurs lignes.|
|[CEdit::ShowBalloonTip](#showballoontip)|Affiche une pointe de ballon associée au contrôle de modification en cours.|
|[CEdit::Défaire](#undo)|Renverse la dernière opération de modification-contrôle.|

## <a name="remarks"></a>Notes

Un contrôle de modification est une fenêtre d’enfant rectangulaire dans laquelle l’utilisateur peut entrer du texte.

Vous pouvez créer un contrôle de modification à partir d’un modèle de dialogue ou directement dans votre code. Dans les deux cas, `CEdit` appelez d’abord le constructeur pour construire l’objet, `CEdit` puis appelez la fonction du membre [Create](#create) pour créer le contrôle de modification Windows et l’attacher à l’objet. `CEdit`

La construction peut être un processus en `CEdit`une seule étape dans une classe dérivée de . Écrivez un constructeur pour la `Create` classe dérivée et appelez à l’intérieur du constructeur.

`CEdit`hérite d’une `CWnd`fonctionnalité significative de . Pour définir et récupérer `CEdit` le texte `CWnd` d’un objet, utilisez les fonctions membres [SetWindowText](cwnd-class.md#setwindowtext) et [GetWindowText](cwnd-class.md#getwindowtext), qui configurent ou obtiennent l’intégralité du contenu d’un contrôle de modification, même s’il s’agit d’un contrôle multiligne. Les lignes de texte dans un contrôle multiligne sont séparées par des séquences de caractères ' 'r’n'. En outre, si un contrôle de modification est multilinré, obtenir `CEdit` et définir une partie du texte du contrôle en appelant les fonctions du membre [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel), et [ReplaceSel](#replacesel).

Si vous souhaitez traiter les messages de notification Windows envoyés par `CDialog`un contrôle de modification à son parent (généralement une classe dérivée), ajoutez une entrée de carte de message et une fonction de membre de gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de carte de message prend la forme suivante :

  **ON_**_NOTIFICATION_**(** _id_**,** _memberFxn_ **)**

lorsque `id` spécifie l’ID de fenêtre de `memberFxn` l’enfant du contrôle de modification envoyant la notification, et est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.

Le prototype de fonction du parent est le suivant :

**afx_msg** membre videFxn **( );**

Voici une liste d’entrées potentielles de carte de message et une description des cas dans lesquels elles seraient envoyées au parent :

- ON_EN_CHANGE L’utilisateur a pris une mesure qui peut avoir modifié le texte dans un contrôle de modification. Contrairement au message de notification EN_UPDATE, ce message de notification est envoyé après que Windows a mis à jour l’écran.

- ON_EN_ERRSPACE Le contrôle de modification ne peut pas allouer suffisamment de mémoire pour répondre à une demande spécifique.

- ON_EN_HSCROLL L’utilisateur clique sur la barre de défilement horizontal d’un contrôle d’édition. La fenêtre parente est notifiée avant que l’écran ne soit mis à jour.

- ON_EN_KILLFOCUS Le contrôle de modification perd la mise au point des entrées.

- ON_EN_MAXTEXT L’insertion actuelle a dépassé le nombre spécifié de caractères pour le contrôle de modification et a été tronquée. Également envoyé quand un contrôle de modification n’a pas le style ES_AUTOHSCROLL et le nombre de caractères à insérer dépasserait la largeur du contrôle de modification. Également envoyé quand un contrôle de modification n’a pas le style ES_AUTOVSCROLL et le nombre total de lignes résultant d’une insertion de texte dépasserait la hauteur du contrôle de modification.

- ON_EN_SETFOCUS Envoyé lorsqu’un contrôle de modification reçoit la mise au point des entrées.

- ON_EN_UPDATE Le contrôle de modification est sur le point d’afficher du texte modifié. Envoyé après le contrôle a formaté le texte, mais avant qu’il n’affiche le texte afin que la taille de la fenêtre peut être modifiée, si nécessaire.

- ON_EN_VSCROLL L’utilisateur clique sur la barre de défilement verticale d’un contrôle d’édition. La fenêtre parente est notifiée avant que l’écran ne soit mis à jour.

Si vous `CEdit` créez un objet dans `CEdit` une boîte de dialogue, l’objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous `CEdit` créez un objet à partir d’une `CEdit` ressource de dialogue à l’aide de l’éditeur de dialogue, l’objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous `CEdit` créez un objet à l’intérieur d’une fenêtre, vous devrez peut-être aussi le détruire. Si vous `CEdit` créez l’objet sur la pile, il est détruit automatiquement. Si vous `CEdit` créez l’objet sur le tas en utilisant la **nouvelle** fonction, vous devez appeler **supprimer** sur l’objet pour le détruire lorsque l’utilisateur met fin au contrôle de modification Windows. Si vous allouez `CEdit` de la mémoire `CEdit` dans l’objet, remplacez le destructeur pour disposer des allocations.

Pour modifier certains styles dans un contrôle de modification (comme ES_READONLY), vous devez envoyer des messages spécifiques au contrôle au lieu d’utiliser [ModifyStyle](cwnd-class.md#modifystyle). Voir [Edit Control Styles](/windows/win32/Controls/edit-control-styles) dans le SDK Windows.

Pour plus `CEdit`d’informations sur , voir [Contrôles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>CEdit::CanUndo

Appelez cette fonction pour déterminer si la dernière opération de modification peut être annulée.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la dernière opération de modification peut `Undo` être annulée par un appel à la fonction membre; 0 s’il ne peut pas être annulé.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [EM_CANUNDO](/windows/win32/Controls/em-canundo) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:Undo](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a>CEdit::CEdit

Construit un objet `CEdit`.

```
CEdit();
```

### <a name="remarks"></a>Notes

Utilisez [Create](#create) pour construire le contrôle de modification Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>CEdit::CharDepos

Appelez cette fonction pour récupérer la ligne zéro et les indices `CEdit` de caractère du personnage le plus proche du point spécifié dans ce contrôle

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Les coordonnées d’un point dans `CEdit` la zone client de cet objet.

### <a name="return-value"></a>Valeur de retour

L’indice de caractère dans le WORD à faible ordre, et l’indice de ligne dans le WORD de haut ordre.

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette fonction de membre est disponible en commençant par Windows 95 et Windows NT 4.0.

Pour plus d’informations, voir [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>CEdit::Clair

Appelez cette fonction pour supprimer (clairement) la sélection actuelle (le cas échéant) dans le contrôle de modification.

```
void Clear();
```

### <a name="remarks"></a>Notes

La suppression effectuée `Clear` par peut être annulée en appelant la fonction membre [Annuler.](#undo)

Pour supprimer la sélection actuelle et placer le contenu supprimé dans le Clipboard, appelez la fonction [membre Cut.](#cut)

Pour plus d’informations, voir [WM_CLEAR](/windows/win32/dataxchg/wm-clear) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>CEdit::Copie

Appelez cette fonction pour coy la sélection actuelle (le cas échéant) dans le contrôle de modification au Clipboard dans CF_TEXT format.

```
void Copy();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [WM_COPY](/windows/win32/dataxchg/wm-copy) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>CEdit::Créer

Crée le contrôle de modification Windows `CEdit` et l’attache à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle de modification. Appliquer toute combinaison de [styles d’édition](styles-used-by-mfc.md#edit-styles) au contrôle.

*Rect*<br/>
Spécifie la taille et la position du contrôle de modification. Peut être `CRect` un `RECT` objet ou une structure.

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog`du contrôle de modification (généralement un ). Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de modification.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation est réussie; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CEdit` objet en deux étapes. Tout d’abord, appelez `CEdit` `Create`le constructeur, puis appelez , ce `CEdit` qui crée le contrôle de modification Windows et le fixe à l’objet.

Lors `Create` de l’exécution, Windows envoie le [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create), et [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) messages au contrôle de modification.

Ces messages sont traités par défaut par le [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate) `CWnd` , et Les fonctions des membres [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) dans la classe de base. Pour étendre la manipulation par défaut `CEdit`du message, extraire une classe, ajouter une carte de message à la nouvelle classe et remplacer les fonctions de membre de message ci-dessus. `OnCreate`Remplacer, par exemple, pour effectuer l’initialisation nécessaire pour la nouvelle classe.

Appliquer les [styles de fenêtre](styles-used-by-mfc.md#window-styles) suivants à un contrôle de modification.

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

- WS_GROUP Pour les contrôles de groupe

- WS_TABSTOP Inclure le contrôle de modification dans l’ordre de tabbing

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>CEdit::Cut

Appelez cette fonction pour supprimer (couper) la sélection actuelle (le cas échéant) dans le contrôle de modification et copier le texte supprimé sur le Clipboard dans CF_TEXT format.

```
void Cut();
```

### <a name="remarks"></a>Notes

La suppression effectuée `Cut` par peut être annulée en appelant la fonction membre [Annuler.](#undo)

Pour supprimer la sélection actuelle sans placer le texte supprimé dans le Clipboard, appelez la fonction [membre Clear.](#clear)

Pour plus d’informations, voir [WM_CUT](/windows/win32/dataxchg/wm-cut) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer

Appelez cette fonction pour réinitialiser (clair) le drapeau annuler d’un contrôle de modification.

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Notes

Le contrôle de modification sera désormais incapable de défaire la dernière opération. Le drapeau annuler est réglé chaque fois qu’une opération dans le contrôle de modification peut être annulée.

Le drapeau de défaire est automatiquement effacé chaque fois que les fonctions des membres [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) ou [SetHandle](#sethandle) `CWnd` sont appelées.

Pour plus d’informations, voir [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>CEdit::FmtLines

Appelez cette fonction pour définir l’inclusion de caractères de rupture de ligne souples sur ou hors d’un contrôle de modification à plusieurs lignes.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Paramètres

*bAddEOL (en)*<br/>
Précise si des caractères de rupture de ligne souple doivent être insérés. Une valeur de TRUE insère les personnages; une valeur de FALSE les supprime.

### <a name="return-value"></a>Valeur de retour

Nonzero si un formatage se produit; sinon 0.

### <a name="remarks"></a>Notes

Un bris de ligne souple se compose de deux retours de chariot et d’un alimentation en ligne inséré à la fin d’une ligne qui est cassée à cause de l’emballage des mots. Un bris de ligne dure se compose d’un retour de voiture et d’un alimentation en ligne. Les lignes qui se terminent par `FmtLines`une rupture de ligne dure ne sont pas affectées par .

Windows ne répondra `CEdit` que si l’objet est un contrôle de modification à plusieurs lignes.

`FmtLines`affecte uniquement le tampon retourné par [GetHandle](#gethandle) et le texte retourné par [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). Il n’a aucun impact sur l’affichage du texte dans le contrôle de modification.

Pour plus d’informations, voir [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit::GetCueBanner

Récupère le texte qui s’affiche sous forme de signal texte, ou de pointe, dans un contrôle de modification lorsque le contrôle est vide.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[out] Un pointeur à une chaîne qui contient le texte de repère.

*cchText*<br/>
[dans] Le nombre de caractères qui peuvent être reçus. Ce nombre comprend le caractère NULL de fin.

### <a name="return-value"></a>Valeur de retour

Pour la première surcharge, TRUE si la méthode est réussie; autrement FALSE.

Pour la deuxième surcharge, un [CString](../../atl-mfc-shared/using-cstring.md) qui contient le texte de repère si la méthode est réussie; sinon, la ficelle vide ("").

### <a name="remarks"></a>Notes

Cette méthode envoie le [message EM_GETCUEBANNER,](/windows/win32/Controls/em-getcuebanner) qui est décrit dans le SDK Windows. Pour plus d’informations, voir le [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) macro.

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine

Appelez cette fonction pour déterminer la ligne visible la plus élevée dans un contrôle de modification.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Valeur de retour

L’indice zéro de la ligne visible la plus élevée. Pour les commandes de modification à une seule ligne, la valeur de retour est de 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>CEdit::GetHandle

Appelez cette fonction pour récupérer une poignée à la mémoire actuellement allouée pour un contrôle de modification à plusieurs lignes.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée de mémoire locale qui identifie le tampon contenant le contenu du contrôle de modification. Si une erreur se produit, comme l’envoi du message à un contrôle de modification à une seule ligne, la valeur de retour est de 0.

### <a name="remarks"></a>Notes

Le manche est une poignée de mémoire locale et peut être utilisé par l’une des fonctions de mémoire **Windows locale** qui prennent une poignée de mémoire locale comme un paramètre.

`GetHandle`n’est traitée que par des contrôles de modification à plusieurs lignes.

Appelez `GetHandle` pour un contrôle de modification à plusieurs lignes dans une boîte de dialogue seulement si la boîte de dialogue a été créée avec l’ensemble de drapeau de style DS_LOCALEDIT. Si le style DS_LOCALEDIT n’est pas défini, vous obtiendrez toujours une valeur de retour non zéro, mais vous ne serez pas en mesure d’utiliser la valeur retournée.

> [!NOTE]
> `GetHandle`ne fonctionnera pas avec Windows 95/98. Si vous `GetHandle` appelez Windows 95/98, il retournera NULL. `GetHandle`fonctionnera comme documenté sous Windows NT, versions 3.51 et plus tard.

Pour plus d’informations, voir [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>CEdit::GetHighlight

Obtient les index des premiers et derniers caractères dans une gamme de texte qui est mis en évidence dans le contrôle de modification actuel.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pichStart*|[out] Indice zéro du premier personnage de la gamme de texte qui est mis en évidence.|
|*pichEnd*|[out] Indice zéro du dernier personnage de la gamme de texte qui est mis en évidence.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message EM_GETHILITE,](/windows/win32/Controls/em-gethilite) qui est décrit dans le SDK Windows. Les `SetHighlight` `GetHighlight` deux et sont actuellement activés pour uniCODE construit uniquement.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>CEdit::GetLimitText

Appelez cette fonction de membre pour `CEdit` obtenir la limite de texte pour cet objet.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Valeur de retour

La limite de texte actuelle, dans `CEdit` les TCHAR, pour cet objet.

### <a name="remarks"></a>Notes

La limite de texte est la quantité maximale de texte, dans les TCHAR, que le contrôle de modification peut accepter.

> [!NOTE]
> Cette fonction de membre est disponible en commençant par Windows 95 et Windows NT 4.0.

Pour plus d’informations, voir [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>CEdit::GetLine

Appelez cette fonction pour récupérer une ligne de texte à partir d’un contrôle de modification et le place dans *lpszBuffer*.

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
Spécifie le numéro de ligne à récupérer à partir d’un contrôle de modification à plusieurs lignes. Les numéros de ligne sont basés à zéro; une valeur de 0 spécifie la première ligne. Ce paramètre est ignoré par un contrôle de modification à une seule ligne.

*lpszBuffer (en)*<br/>
Indique le tampon qui reçoit une copie de la ligne. Le premier mot du tampon doit spécifier le nombre maximum de TCHAR qui peuvent être copiés au tampon.

*nMaxLength (en)*<br/>
Spécifie le nombre maximum de caractères TCHAR qui peuvent être copiés sur le tampon. `GetLine`place cette valeur dans le premier mot de *lpszBuffer* avant de faire l’appel à Windows.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés. La valeur de retour est de 0 si le numéro de ligne spécifié par *nIndex* est supérieur au nombre de lignes dans le contrôle de modification.

### <a name="remarks"></a>Notes

La ligne copiée ne contient pas de caractère de résiliation nulle.

Pour plus d’informations, voir [EM_GETLINE](/windows/win32/Controls/em-getline) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:GetLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>CEdit::GetLineCount

Appelez cette fonction pour récupérer le nombre de lignes dans un contrôle de modification à plusieurs lignes.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Valeur de retour

Un intégrant contenant le nombre de lignes dans le contrôle de modification à plusieurs lignes. Si aucun texte n’a été entré dans le contrôle de modification, la valeur de retour est de 1.

### <a name="remarks"></a>Notes

`GetLineCount`n’est traité que par des contrôles de modification à plusieurs lignes.

Pour plus d’informations, voir [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>CEdit::GetMargins

Appelez cette fonction de membre pour récupérer les marges gauche et droite de ce contrôle de modification.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la marge gauche dans le WORD de faible ordre et la largeur de la marge droite dans le WORD de haut ordre.

### <a name="remarks"></a>Notes

Les marges sont mesurées en pixels.

> [!NOTE]
> Cette fonction de membre est disponible en commençant par Windows 95 et Windows NT 4.0.

Pour plus d’informations, voir [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a>CEdit::GetModify

Appelez cette fonction pour déterminer si le contenu d’un contrôle de modification a été modifié.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le contenu de modification-contrôle ont été modifiés; 0 s’ils sont restés inchangés.

### <a name="remarks"></a>Notes

Windows maintient un drapeau interne indiquant si le contenu du contrôle de modification a été modifié. Ce drapeau est effacé lorsque le contrôle de modification est créé et peut également être effacé en appelant la fonction [membre SetModify.](#setmodify)

Pour plus d’informations, voir [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit::GetPasswordChar

Appelez cette fonction pour récupérer le caractère de mot de passe qui s’affiche dans un contrôle de modification lorsque l’utilisateur entre le texte.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Valeur de retour

Spécifie le personnage à afficher au lieu du personnage que l’utilisateur a tapé. La valeur de retour est NULL si aucun caractère de mot de passe n’existe.

### <a name="remarks"></a>Notes

Si vous créez le contrôle de modification avec le style ES_PASSWORD, le DLL qui prend en charge le contrôle détermine le caractère de mot de passe par défaut. Le manifeste ou la méthode [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) détermine quel DLL prend en charge le contrôle de modification. Si user32.dll prend en charge le contrôle de modification, le caractère de mot de passe par défaut est ASTERISK ('' , U-002A). Si la version 6 comctl32.dll prend en charge le contrôle de modification, le caractère par défaut est BLACK CIRCLE ('' , U-25CF). Pour plus d’informations sur les DLL et la version qui prend en charge les contrôles communs, voir [Shell et Common Controls Versions](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Cette méthode envoie le [message EM_GETPASSWORDCHAR,](/windows/win32/Controls/em-getpasswordchar) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>CEdit::GetRect

Appelez cette fonction pour obtenir le rectangle de formatage d’un contrôle de modification.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Points à `RECT` la structure qui reçoit le rectangle de formatage.

### <a name="remarks"></a>Notes

Le rectangle de formatage est le rectangle limitatif du texte, qui est indépendant de la taille de la fenêtre de modification-contrôle.

Le rectangle de formatage d’un contrôle d’édition à plusieurs lignes peut être modifié par les fonctions des membres [SetRect](#setrect) et [SetRectNP.](#setrectnp)

Pour plus d’informations, voir [EM_GETRECT](/windows/win32/Controls/em-getrect) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:LimitText](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a>CEdit::GetSel

Appelez cette fonction pour obtenir les positions de caractère de départ et de fin de la sélection actuelle (le cas échéant) dans un contrôle de modification, en utilisant soit la valeur de retour ou les paramètres.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Paramètres

*nStartChar (en)*<br/>
Référence à un intégrant qui recevra la position du premier personnage dans la sélection actuelle.

*nEndChar (en)*<br/>
Référence à un intégrant qui recevra la position du premier personnage non sélectionné après la fin de la sélection actuelle.

### <a name="return-value"></a>Valeur de retour

La version qui renvoie un DWORD renvoie une valeur qui contient la position de départ dans le mot de faible ordre et la position du premier personnage non sélectionné après la fin de la sélection dans le mot de haute commande.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [EM_GETSEL](/windows/win32/Controls/em-getsel) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>CEdit::HideBalloonTip

Cache toute pointe de ballon associée au contrôle de modification en cours.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette fonction envoie le [message EM_HIDEBALLOONTIP,](/windows/win32/Controls/em-hideballoontip) qui est décrit dans le SDK Windows.

## <a name="ceditlimittext"></a><a name="limittext"></a>CEdit::LimitText

Appelez cette fonction pour limiter la durée du texte que l’utilisateur peut entrer dans un contrôle de modification.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Paramètres

*nChars (nChars)*<br/>
Spécifie la longueur (en TCHAR) du texte que l’utilisateur peut entrer. Si ce paramètre est de 0, la longueur du texte est réglée pour UINT_MAX octets. Il s'agit du comportement par défaut.

### <a name="remarks"></a>Notes

La modification de la limite de texte restreint uniquement le texte que l’utilisateur peut entrer. Il n’a aucun effet sur un texte déjà dans le contrôle de modification, ni n’affecte la `CWnd`longueur du texte copié au contrôle de modification par la fonction [membre SetWindowText](cwnd-class.md#setwindowtext) dans . Si une application `SetWindowText` utilise la fonction pour placer plus de texte `LimitText`dans un contrôle de modification que ce qui est spécifié dans l’appel, l’utilisateur peut supprimer n’importe quel texte dans le contrôle de modification. Toutefois, la limite de texte empêchera l’utilisateur de remplacer le texte existant par un nouveau texte, à moins que la suppression de la sélection actuelle ne fait tomber le texte en dessous de la limite de texte.

> [!NOTE]
> Dans Win32 (Windows NT et Windows 95/98), [SetLimitText](#setlimittext) remplace cette fonction.

Pour plus d’informations, voir [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>CEdit::LineDeChar

Appelez cette fonction pour récupérer le numéro de ligne de la ligne qui contient l’index de caractère spécifié.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient la valeur d’index zéro pour le caractère désiré dans le texte du contrôle de modification, ou contient -1. Si *nIndex* est -1, il spécifie la ligne actuelle, c’est-à-dire la ligne qui contient le caret.

### <a name="return-value"></a>Valeur de retour

Le numéro de ligne à base nulle de la ligne contenant l’indice de caractère spécifié par *nIndex*. Si *nIndex* est de -1, le nombre de la ligne qui contient le premier caractère de la sélection est retourné. S’il n’y a pas de sélection, le numéro de ligne actuel est retourné.

### <a name="remarks"></a>Notes

Un index de caractère est le nombre de caractères depuis le début du contrôle de modification.

Cette fonction de membre n’est utilisée que par les commandes de modification multi-lignes.

Pour plus d’informations, voir [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>CEdit::LineIndex

Appelez cette fonction pour récupérer l’index de caractère d’une ligne dans un contrôle de modification à plusieurs lignes.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Paramètres

*nLine (en)*<br/>
Contient la valeur indicative de la ligne souhaitée dans le texte du contrôle de modification, ou contient -1. Si *nLine* est de -1, il spécifie la ligne actuelle, c’est-à-dire la ligne qui contient le caret.

### <a name="return-value"></a>Valeur de retour

L’index de caractère de la ligne spécifié dans *nLine* ou -1 si le numéro de ligne spécifié est supérieur au nombre de lignes dans le contrôle de modification.

### <a name="remarks"></a>Notes

L’index de caractère est le nombre de caractères du début du contrôle de modification à la ligne spécifiée.

Cette fonction de membre n’est traitée que par des commandes de modification à plusieurs lignes.

Pour plus d’informations, voir [EM_LINEINDEX](/windows/win32/controls/em-lineindex) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>CEdit::LineLength

Récupère la longueur d’une ligne dans un contrôle de modification.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Paramètres

*nLine (en)*<br/>
L’index zéro d’un personnage de la ligne dont la longueur doit être récupérée. La valeur par défaut est -1.

### <a name="return-value"></a>Valeur de retour

Pour les commandes de modification à une seule ligne, la valeur de retour est la longueur, dans les TCHAR, du texte dans le contrôle de modification.

Pour les commandes d’édition multilignes, la valeur de retour est la longueur, dans les TCHAR, de la ligne spécifiée par le paramètre *nLine.* Pour le texte de l’ANSI, la longueur est le nombre d’octets dans la ligne; pour le texte Unicode, la longueur est le nombre de caractères dans la ligne. La longueur n’inclut pas le caractère de transport-retour à la fin de la ligne.

Si le *paramètre nLine* est supérieur au nombre de caractères dans le contrôle, la valeur de retour est nulle.

Si le *paramètre nLine* est de -1, la valeur de retour est le nombre de caractères non sélectionnés dans les lignes qui contiennent des caractères sélectionnés. Par exemple, si la sélection s’étend du quatrième caractère d’une ligne jusqu’à la huitième image de la fin de la ligne suivante, la valeur de retour est de 10. C’est-à-dire trois personnages sur la première ligne et sept sur la suivante.

Pour plus d’informations sur le type TCHAR, voir la ligne TCHAR dans le tableau dans [Windows Data Types](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Notes

Cette méthode est prise en charge par le [message EM_LINELENGTH,](/windows/win32/Controls/em-linelength) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:LineIndex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a>CEdit::LineScroll

Appelez cette fonction pour faire défiler le texte d’un contrôle de modification à plusieurs lignes.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Paramètres

*nLines*<br/>
Spécifie le nombre de lignes à défiler verticalement.

*nChars (nChars)*<br/>
Spécifie le nombre de positions de caractères à défiler horizontalement. Cette valeur est ignorée si le contrôle de modification a soit le ES_RIGHT ou ES_CENTER style.

### <a name="remarks"></a>Notes

Cette fonction de membre n’est traitée que par des commandes de modification à plusieurs lignes.

Le contrôle de modification ne défile pas verticalement au-delà de la dernière ligne de texte dans le contrôle de modification. Si la ligne actuelle plus le nombre de lignes spécifiées par *nLines* dépasse le nombre total de lignes dans le contrôle de modification, la valeur est ajustée de sorte que la dernière ligne du contrôle de modification est défichée en haut de la fenêtre de modification-contrôle.

`LineScroll`peut être utilisé pour faire défiler horizontalement le dernier caractère de n’importe quelle ligne.

Pour plus d’informations, voir [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:GetFirstVisibleLine](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a>CEdit::Paste

Appelez cette fonction pour insérer les `CEdit` données du Clipboard dans le point d’insertion.

```
void Paste();
```

### <a name="remarks"></a>Notes

Les données ne sont insérées que si le Clipboard contient des données en format CF_TEXT.

Pour plus d’informations, voir [WM_PASTE](/windows/win32/dataxchg/wm-paste) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>CEdit::PFromChar

Appelez cette fonction pour obtenir la position (coin supérieur `CEdit` gauche) d’un personnage donné dans cet objet.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Paramètres

*Nchar*<br/>
L’index zéro du caractère spécifié.

### <a name="return-value"></a>Valeur de retour

Les coordonnées du coin supérieur gauche du personnage spécifié par *nChar*.

### <a name="remarks"></a>Notes

Le caractère est spécifié en donnant sa valeur d’index à base de zéro. Si *nChar* est supérieur à l’index `CEdit` du dernier personnage de cet objet, la valeur de retour `CEdit` spécifie les coordonnées de la position du personnage juste après le dernier personnage de cet objet.

> [!NOTE]
> Cette fonction de membre est disponible en commençant par Windows 95 et Windows NT 4.0.

Pour plus d’informations, voir [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:LineFromChar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a>CEdit::ReplaceSel

Appelez cette fonction pour remplacer la sélection actuelle dans un contrôle de modification avec le texte spécifié par *lpszNewText*.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszNewText*<br/>
Indique une chaîne non terminée contenant le texte de remplacement.

*bCanUndo (en)*<br/>
Pour spécifier que cette fonction peut être annulée, définissez la valeur de ce paramètre à TRUE . La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

Remplace seulement une partie du texte dans un contrôle de modification. Si vous souhaitez remplacer l’ensemble du texte, utilisez la fonction de membre [CWnd::SetWindowText.](cwnd-class.md#setwindowtext)

S’il n’y a pas de sélection en cours, le texte de remplacement est inséré à l’emplacement actuel du curseur.

Pour plus d’informations, voir [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:LineIndex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit::SetCueBanner

Définit le texte qui s’affiche sous forme de signal texte, ou de pointe, dans un contrôle de modification lorsque le contrôle est vide.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[dans] Pointeur vers une chaîne qui contient la queue pour afficher dans le contrôle de modification.

*fDrawWhenFocused*<br/>
[dans] Si FALSE, la bannière de repère n’est pas dessinée lorsque l’utilisateur clique dans le contrôle de modification et donne au contrôle la mise au point.

Si VRAI, la bannière de repère est dessinée même lorsque le contrôle est focal. La bannière de repère disparaît lorsque l’utilisateur commence à taper dans le contrôle.

La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode est réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message EM_SETCUEBANNER,](/windows/win32/Controls/em-setcuebanner) qui est décrit dans le SDK Windows. Pour plus d’informations, voir le [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) macro.

### <a name="example"></a>Exemple

L’exemple suivant montre la méthode [CEdit:SetCueBanner.](#setcuebanner)

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>CEdit::SetHandle

Appelez cette fonction pour définir la poignée à la mémoire locale qui sera utilisée par un contrôle de modification à plusieurs lignes.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Paramètres

*hBuffer (en)*<br/>
Contient une poignée à la mémoire locale. Cette poignée doit avoir été créée par un appel précédent à la fonction [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows à l’aide du drapeau LMEM_MOVEABLE. La mémoire est supposée contenir une corde non terminée. Si ce n’est pas le cas, le premier byte de la mémoire allouée doit être réglé à 0.

### <a name="remarks"></a>Notes

Le contrôle de modification utilisera ensuite ce tampon pour stocker le texte actuellement affiché au lieu d’allouer son propre tampon.

Cette fonction de membre n’est traitée que par des commandes de modification à plusieurs lignes.

Avant qu’une application ne fixe une nouvelle poignée de mémoire, elle doit utiliser la fonction `LocalFree` membre [GetHandle](#gethandle) pour obtenir la poignée du tampon mémoire actuel et libérer cette mémoire à l’aide de la fonction Windows.

`SetHandle`efface le tampon annuler (la fonction membre [CanUndo](#canundo) retourne alors 0) et le drapeau de modification interne (la fonction [membre GetModify](#getmodify) retourne alors 0). La fenêtre de modification-contrôle est redessiné.

Vous pouvez utiliser cette fonction de membre dans un contrôle d’édition à plusieurs lignes dans une boîte de dialogue seulement si vous avez créé la boîte de dialogue avec l’ensemble de drapeau de style DS_LOCALEDIT.

> [!NOTE]
> `GetHandle`ne fonctionnera pas avec Windows 95/98. Si vous `GetHandle` appelez Windows 95/98, il retournera NULL. `GetHandle`fonctionnera comme documenté sous Windows NT, versions 3.51 et plus tard.

Pour plus d’informations, voir [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc), et [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>CEdit::SetHighlight

Met en évidence une gamme de texte qui est affichée dans le contrôle de modification en cours.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ichStart*|[dans] Indice zéro du premier personnage de la gamme de texte à mettre en évidence.|
|*ichEnd*|[dans] Indice zéro du dernier personnage de la gamme de texte à mettre en évidence.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [message EM_SETHILITE,](/windows/win32/Controls/em-sethilite) qui est décrit dans le SDK Windows.  Cette méthode envoie le [message EM_SETHILITE,](/windows/win32/Controls/em-sethilite) qui est décrit dans le SDK Windows. Les `SetHighlight` `GetHighlight` deux et sont activés pour UNICODE construit uniquement.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>CEdit::SetLimitText

Appelez cette fonction de membre pour `CEdit` définir la limite de texte pour cet objet.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Paramètres

*Nmax*<br/>
La nouvelle limite de texte, en caractères.

### <a name="remarks"></a>Notes

La limite de texte est la quantité maximale de texte, en caractères, que le contrôle de modification peut accepter.

La modification de la limite de texte restreint uniquement le texte que l’utilisateur peut entrer. Il n’a aucun effet sur un texte déjà dans le contrôle de modification, ni n’affecte la `CWnd`longueur du texte copié au contrôle de modification par la fonction [membre SetWindowText](cwnd-class.md#setwindowtext) dans . Si une application `SetWindowText` utilise la fonction pour placer plus de texte `LimitText`dans un contrôle de modification que ce qui est spécifié dans l’appel, l’utilisateur peut supprimer n’importe quel texte dans le contrôle de modification. Toutefois, la limite de texte empêchera l’utilisateur de remplacer le texte existant par un nouveau texte, à moins que la suppression de la sélection actuelle ne fait tomber le texte en dessous de la limite de texte.

Cette fonction remplace [LimitText](#limittext) dans Win32.

Pour plus d’informations, voir [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a>CEdit::SetMargins

Appelez cette méthode pour définir les marges gauche et droite de ce contrôle de modification.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Paramètres

*nLeft (en)*<br/>
La largeur de la nouvelle marge gauche, en pixels.

*nRight (en)*<br/>
La largeur de la nouvelle marge droite, en pixels.

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette fonction de membre est disponible en commençant par Windows 95 et Windows NT 4.0.

Pour plus d’informations, voir [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a>CEdit::SetModify

Appelez cette fonction pour définir ou effacer le drapeau modifié pour un contrôle de modification.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Paramètres

*bModifié*<br/>
Une valeur de TRUE indique que le texte a été modifié, et une valeur de FALSE indique qu’il n’est pas modifié. Par défaut, le drapeau modifié est défini.

### <a name="remarks"></a>Notes

Le drapeau modifié indique si le texte dans le contrôle de modification a été modifié. Il est automatiquement défini chaque fois que l’utilisateur modifie le texte. Sa valeur peut être récupérée avec la fonction membre [GetModify.](#getmodify)

Pour plus d’informations, voir [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:GetModify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit::SetPasswordChar

Appelez cette fonction pour définir ou supprimer un personnage de mot de passe affiché dans un contrôle de modification lorsque l’utilisateur tape du texte.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Paramètres

*Ch*<br/>
Spécifie le personnage à afficher à la place du personnage tapé par l’utilisateur. Si *ch* est 0, les caractères réels tapés par l’utilisateur sont affichés.

### <a name="remarks"></a>Notes

Lorsqu’un personnage de mot de passe est défini, ce personnage s’affiche pour chaque personnage que l’utilisateur tape.

Cette fonction de membre n’a aucun effet sur un contrôle de modification à plusieurs lignes.

Lorsque `SetPasswordChar` la fonction du `CEdit` membre est appelée, redessinera tous les caractères visibles à l’aide du personnage spécifié par *ch*.

Si le contrôle de modification est créé avec le style [ES_PASSWORD,](styles-used-by-mfc.md#edit-styles) le caractère <strong>\*</strong>de mot de passe par défaut est réglé sur un astérisque ( ). Ce style est `SetPasswordChar` supprimé si est appelé avec *ch* réglé à 0.

Pour plus d’informations, voir [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>CEdit::SetReadOnly

Appelle cette fonction pour définir l’état de lecture seulement d’un contrôle de modification.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bReadOnly*<br/>
Précise s’il faut définir ou supprimer l’état de lecture uniquement du contrôle de modification. Une valeur de TRUE définit l’État à la lecture seulement; une valeur de FALSE définit l’état à lire/écrire.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération est réussie, ou 0 si une erreur se produit.

### <a name="remarks"></a>Notes

Le réglage actuel peut être trouvé en testant le [drapeau ES_READONLY](styles-used-by-mfc.md#edit-styles) dans la valeur de retour de [CWnd::GetStyle](cwnd-class.md#getstyle).

Pour plus d’informations, voir [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>CEdit::SetRect

Appelez cette fonction pour définir les dimensions d’un rectangle à l’aide des coordonnées spécifiées.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Points à `RECT` la `CRect` structure ou à l’objet qui spécifie les nouvelles dimensions du rectangle de mise en forme.

### <a name="remarks"></a>Notes

Ce membre n’est traité que par des commandes de modification à plusieurs lignes.

Utilisez `SetRect` pour définir le rectangle de formatage d’un contrôle de modification à plusieurs lignes. Le rectangle de formatage est le rectangle limitatif du texte, qui est indépendant de la taille de la fenêtre de modification-contrôle. Lorsque le contrôle de modification est créé pour la première fois, le rectangle de formatage est le même que la zone client de la fenêtre de contrôle d’édition. En utilisant `SetRect` la fonction membre, une application peut rendre le rectangle de formatage plus grand ou plus petit que la fenêtre de contrôle de modification.

Si le contrôle de modification n’a pas de barre de défilement, le texte sera coupé, pas enveloppé, si le rectangle de formatage est rendu plus grand que la fenêtre. Si le contrôle de modification contient une bordure, le rectangle de formatage est réduit par la taille de la bordure. Si vous ajustez `GetRect` le rectangle retourné par la fonction membre, vous devez `SetRect`enlever la taille de la bordure avant de passer le rectangle à .

Lorsqu’il `SetRect` est appelé, le texte du contrôle de modification est également reformaté et redisjoué.

Pour plus d’informations, voir [EM_SETRECT](/windows/win32/Controls/em-setrect) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>CEdit::SetRectNP

Appelez cette fonction pour définir le rectangle de formatage d’un contrôle de modification à plusieurs lignes.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une `RECT` structure `CRect` ou un objet qui spécifie les nouvelles dimensions du rectangle.

### <a name="remarks"></a>Notes

Le rectangle de formatage est le rectangle limitatif du texte, qui est indépendant de la taille de la fenêtre de modification-contrôle.

`SetRectNP`est identique `SetRect` à la fonction membre, sauf que la fenêtre de contrôle de modification n’est pas redessiné.

Lorsque le contrôle de modification est créé pour la première fois, le rectangle de formatage est le même que la zone client de la fenêtre de contrôle d’édition. En appelant `SetRectNP` la fonction membre, une application peut rendre le rectangle de formatage plus grand ou plus petit que la fenêtre de contrôle de modification.

Si le contrôle de modification n’a pas de barre de défilement, le texte sera coupé, pas enveloppé, si le rectangle de formatage est rendu plus grand que la fenêtre.

Ce membre n’est traité que par des commandes de modification à plusieurs lignes.

Pour plus d’informations, voir [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a>CEdit::SetSel

Appelez cette fonction pour sélectionner une gamme de caractères dans un contrôle de modification.

```
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
Spécifie la position de départ dans le mot de bas ordre et la position de fin dans le mot de haut ordre. Si le mot de bas ordre est de 0 et que le mot de haute commande est de -1, tout le texte du contrôle de modification est sélectionné. Si le mot de faible ordre est de -1, toute sélection actuelle est supprimée.

*bNoScroll (en)*<br/>
Indique si le caret doit être défilé en vue. Si FALSE, le caret est défilé en vue. Si VRAI, le caret n’est pas défilé en vue.

*nStartChar (en)*<br/>
Spécifie la position de départ. Si *nStartChar* est 0 et *nEndChar* est -1, tout le texte dans le contrôle de modification est sélectionné. Si *nStartChar* est de -1, toute sélection en cours est supprimée.

*nEndChar (en)*<br/>
Spécifie la position de fin.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [EM_SETSEL](/windows/win32/Controls/em-setsel) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEdit:GetSel](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a>CEdit::SetTabStops

Appelez cette fonction pour définir les arrêts de l’onglet dans un contrôle de modification à plusieurs lignes.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Paramètres

*cxEachStop*<br/>
Précise que les arrêts d’onglet doivent être réglés à chaque unité de dialogue *cxEachStop.*

*nTabStops (en)*<br/>
Spécifie le nombre d’arrêts d’onglets contenus dans *rgTabStops*. Ce nombre doit être supérieur à 1.

*rgTabStops*<br/>
Indique un tableau d’intégreurs non signés spécifiant les arrêts de l’onglet dans les unités de dialogue. Une unité de dialogue est une distance horizontale ou verticale. Une unité de dialogue horizontale est égale à un quart de l’unité actuelle de largeur de base de dialogue, et 1 unité verticale de dialogue est égale à un huitième de l’unité actuelle de hauteur de base de dialogue. Les unités de dialogue sont calculées en fonction de la hauteur et de la largeur de la police système actuelle. La `GetDialogBaseUnits` fonction Windows renvoie les unités de base de dialogue actuelles en pixels.

### <a name="return-value"></a>Valeur de retour

Nonzero si les onglets ont été fixés; sinon 0.

### <a name="remarks"></a>Notes

Lorsque le texte est copié sur un contrôle de modification à plusieurs lignes, tout personnage d’onglet dans le texte entraînera la production d’espace jusqu’à l’arrêt d’onglet suivant.

Pour définir des arrêts d’onglet à la taille par défaut de 32 unités de dialogue, appelez la version sans paramètres de cette fonction de membre. Pour définir l’onglet s’arrête à une taille autre que 32, appelez la version avec le *paramètre cxEachStop.* Pour définir des arrêts d’onglet à un tableau de tailles, utilisez la version avec deux paramètres.

Cette fonction de membre n’est traitée que par des commandes de modification à plusieurs lignes.

`SetTabStops`ne redessinera pas automatiquement la fenêtre de modification. Si vous modifiez les arrêts d’onglet pour le texte déjà dans le contrôle de modification, appelez [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) pour redessiner la fenêtre de modification.

Pour plus d’informations, voir [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) et [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CEditView:SetTabStops](ceditview-class.md#settabstops).

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>CEdit::ShowBalloonTip

Affiche une pointe de ballon associée au contrôle de modification en cours.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pEditBalloonTip*|[dans] Pointeur vers une structure [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) qui décrit la pointe du ballon.|
|*lpszTitle (lpszTitle)*|[dans] Pointeur vers une chaîne Unicode qui contient le titre de la pointe du ballon.|
|*lpszText*|[dans] Pointeur vers une chaîne Unicode qui contient le texte de pointe de ballon.|
|*ttiIcon*|[dans] Un **INT** qui spécifie le type d’icône à associer à la pointe du ballon. La valeur par défaut est TTI_NONE. Pour plus d’informations, consultez le `ttiIcon` membre de la structure [EDITBALLOONTIP.](/windows/win32/api/commctrl/ns-commctrl-editballoontip)|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette fonction envoie le [message EM_SHOWBALLOONTIP,](/windows/win32/Controls/em-showballoontip) qui est décrit dans le SDK Windows. Pour plus d’informations, voir le [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) macro.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_cedit`définit une variable, qui est utilisée pour accéder au contrôle de modification actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant affiche une pointe de ballon pour un contrôle de modification. Le [CEdit::ShowBalloonTip](#showballoontip) méthode spécifie un titre et ballon texte pointe.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>CEdit::Défaire

Appelez cette fonction pour annuler la dernière opération de modification-contrôle.

```
BOOL Undo();
```

### <a name="return-value"></a>Valeur de retour

Pour un contrôle de modification à une seule ligne, la valeur de retour est toujours non zéro. Pour un contrôle de modification à plusieurs lignes, la valeur de retour n’est pas zéro si l’opération de défaire est réussie, ou 0 si l’opération annuler échoue.

### <a name="remarks"></a>Notes

Une opération annulée peut également être annulée. Par exemple, vous pouvez restaurer le texte `Undo`supprimé avec le premier appel à . Tant qu’il n’y a pas d’opération de modification `Undo`intermédiaire, vous pouvez supprimer le texte à nouveau avec un deuxième appel à .

Pour plus d’informations, voir [EM_UNDO](/windows/win32/Controls/em-undo) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](cwnd-class.md)<br/>
[Classe CButton](cbutton-class.md)<br/>
[Classe CComboBox](ccombobox-class.md)<br/>
[CListBox, classe](clistbox-class.md)<br/>
[CScrollBar, classe](cscrollbar-class.md)<br/>
[Classe CStatic](cstatic-class.md)<br/>
[Classe CDialog](cdialog-class.md)
