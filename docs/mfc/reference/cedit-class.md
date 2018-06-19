---
title: Classe CEdit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fba91f4c16c5b356b1e7a11e35380a15eb98eb1
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463077"
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
|[CEdit::CEdit](#cedit)|Construit un `CEdit` objet contrôle.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CEdit::CanUndo](#canundo)|Détermine si une opération de contrôle d’édition peut être annulée.|  
|[CEdit::CharFromPos](#charfrompos)|Récupère les index de ligne et de caractère pour le caractère le plus proche à une position spécifiée.|  
|[CEdit::Clear](#clear)|Supprime (efface) contrôle de la sélection actuelle (le cas échéant) dans la modification.|  
|[CEdit::Copy](#copy)|Copie la sélection actuelle (le cas échéant) dans le contrôle d’édition dans le Presse-papiers dans **CF_TEXT** format.|  
|[CEdit::Create](#create)|Crée le contrôle d’édition Windows et l’attache à le `CEdit` objet.|  
|[CEdit::Cut](#cut)|Contrôle de la sélection actuelle (le cas échéant) dans la modification de suppressions (morceaux) et copie le texte supprimé dans le Presse-papiers dans **CF_TEXT** format.|  
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Réinitialise le contrôle de (efface), l’indicateur d’annulation d’une modification.|  
|[CEdit::FmtLines](#fmtlines)|Définit l’inclusion de caractères de saut de ligne conditionnel ou de désactiver au sein d’un contrôle d’édition de plusieurs lignes.|  
|[CEdit::GetCueBanner](#getcuebanner)|Récupère le texte qui s’affiche en tant que l’indice de texte, ou Conseil, dans un contrôle d’édition lorsque le contrôle est vide et n’a pas le focus.|  
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Détermine la ligne visible au premier plan dans un contrôle d’édition.|  
|[CEdit::GetHandle](#gethandle)|Récupère un handle vers la mémoire actuellement allouée pour un contrôle d’édition de plusieurs lignes.|  
|[CEdit::GetHighlight](#gethighlight)|Obtient l’index de début et de fin des caractères d’une plage de texte qui est mis en surbrillance dans le contrôle d’édition actuel.|  
|[CEdit::GetLimitText](#getlimittext)|Obtient la quantité maximale de texte ce `CEdit` peut contenir.|  
|[CEdit::GetLine](#getline)|Récupère une ligne de texte à partir d’un contrôle d’édition.|  
|[CEdit::GetLineCount](#getlinecount)|Récupère le nombre de lignes dans un contrôle d’édition de plusieurs lignes.|  
|[CEdit::GetMargins](#getmargins)|Obtient les marges gauche et droite pour ce `CEdit`.|  
|[CEdit::GetModify](#getmodify)|Détermine si le contenu d’un contrôle d’édition a été modifié.|  
|[CEdit::GetPasswordChar](#getpasswordchar)|Récupère le caractère de mot de passe affiché dans un contrôle d’édition lorsque l’utilisateur entre du texte.|  
|[CEdit::GetRect](#getrect)|Obtient le rectangle de mise en forme d’un contrôle d’édition.|  
|[CEdit::GetSel](#getsel)|Obtient les positions de premier et dernier caractères de la sélection actuelle dans un contrôle d’édition.|  
|[CEdit::HideBalloonTip](#hideballoontip)|Masque les info-bulle associé au contrôle d’édition actuel.|  
|[CEdit::LimitText](#limittext)|Limite la longueur du texte que l’utilisateur peut entrer dans un contrôle d’édition.|  
|[CEdit::LineFromChar](#linefromchar)|Récupère le numéro de ligne de la ligne qui contient l’index de caractère spécifié.|  
|[CEdit::LineIndex](#lineindex)|Récupère l’index de caractère d’une ligne dans un contrôle d’édition de plusieurs lignes.|  
|[CEdit::LineLength](#linelength)|Récupère la longueur d’une ligne dans un contrôle d’édition.|  
|[CEdit::LineScroll](#linescroll)|Fait défiler le texte d’un contrôle d’édition de plusieurs lignes.|  
|[CEdit::Paste](#paste)|Insère les données à partir du Presse-papiers dans le contrôle d’édition à la position actuelle du curseur. Les données sont insérées que si le Presse-papiers contient des données **CF_TEXT** format.|  
|[CEdit::PosFromChar](#posfromchar)|Récupère les coordonnées du coin supérieur gauche d’un index de caractère spécifié.|  
|[CEdit::ReplaceSel](#replacesel)|Remplace la sélection actuelle dans un contrôle d’édition avec le texte spécifié.|  
|[CEdit::SetCueBanner](#setcuebanner)|Définit le texte qui s’affiche en tant que l’indice de texte, ou Conseil, dans un contrôle d’édition lorsque le contrôle est vide et n’a pas le focus.|  
|[CEdit::SetHandle](#sethandle)|Définit le handle vers la mémoire locale qui sera utilisée par un contrôle d’édition de plusieurs lignes.|  
|[CEdit::SetHighlight](#sethighlight)|Contrôle d’édition met en évidence une plage de texte qui s’affiche en cours.|  
|[CEdit::SetLimitText](#setlimittext)|Définit la quantité maximale de texte ce `CEdit` peut contenir.|  
|[CEdit::SetMargins](#setmargins)|Définit les marges gauche et droite de ce `CEdit`.|  
|[CEdit::SetModify](#setmodify)|Active ou désactive l’indicateur de modification pour un contrôle d’édition.|  
|[CEdit::SetPasswordChar](#setpasswordchar)|Définit ou supprime un caractère de mot de passe affiché dans un contrôle d’édition lorsque l’utilisateur entre du texte.|  
|[CEdit::SetReadOnly](#setreadonly)|Définit l’état en lecture seule d’un contrôle d’édition.|  
|[CEdit::SetRect](#setrect)|Définit le rectangle de mise en forme d’un contrôle d’édition de plusieurs lignes et met à jour le contrôle.|  
|[CEdit::SetRectNP](#setrectnp)|Définit le rectangle de mise en forme d’un contrôle d’édition de plusieurs lignes sans redessiner la fenêtre de contrôle.|  
|[CEdit::SetSel](#setsel)|Sélectionne une plage de caractères dans un contrôle d’édition.|  
|[CEdit::SetTabStops](#settabstops)|Les taquets de tabulation dans une ligne de plusieurs jeux de contrôle d’édition.|  
|[CEdit::ShowBalloonTip](#showballoontip)|Affiche une info-bulle qui est associée avec le contrôle d’édition actuel.|  
|[CEdit::Undo](#undo)|Annule la dernière opération de contrôle d’édition.|  
  
## <a name="remarks"></a>Notes  
 Un contrôle d’édition est une fenêtre enfant rectangulaire dans laquelle l’utilisateur peut entrer du texte.  
  
 Vous pouvez créer un contrôle d’édition à partir d’un modèle de boîte de dialogue ou directement dans votre code. Dans les deux cas, tout d’abord appeler le constructeur `CEdit` pour construire le `CEdit` de l’objet, puis appelez le [créer](#create) fonction membre pour créer les fenêtres de contrôle d’édition et attacher le `CEdit` objet.  
  
 Construction peut être un processus en une étape dans une classe dérivée de `CEdit`. Écrire un constructeur pour la classe dérivée et appelez **créer** à partir de dans le constructeur.  
  
 `CEdit` hérite des fonctionnalités importantes de `CWnd`. Pour définir et récupérer le texte à partir d’un `CEdit` de l’objet, utilisez le `CWnd` fonctions membres [SetWindowText](cwnd-class.md#setwindowtext) et [GetWindowText](cwnd-class.md#getwindowtext), ou les obtenir tout le contenu d’une modification contrôle, même si elle est un contrôle multiligne. Les lignes de texte dans un contrôle multiligne sont séparés par des séquences de caractères '\r\n'. En outre, si un contrôle d’édition est multiligne, obtenir et définir une partie du texte du contrôle en appelant le `CEdit` fonctions membres [GetLine](#getline), [fonction membre SetSel](#setsel), [fonction membre GetSel](#getsel)et [ ReplaceSel](#replacesel).  
  
 Si vous souhaitez traiter les messages de notification Windows envoyés par un contrôle d’édition à son parent (généralement une classe dérivée de `CDialog`), ajouter une fonction table des messages de membre des entrée et le Gestionnaire de messages à la classe parente pour chaque message.  
  
 Chaque entrée de table des messages prend la forme suivante :  
  
  **ON_**_NOTIFICATION_**(** _id_**,** _memberFxn_ **)**
  
 où `id` Spécifie l’ID de fenêtre enfant du contrôle d’édition envoie la notification, et `memberFxn` est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.  
  
 Prototype de fonction du parent est la suivante :  
  
 **afx_msg** memberFxn void **() ;**  
  
 Voici une liste d’éventuelles entrées de table des messages et une description des cas dans lequel ils sont envoyés au parent :  
  
- **ON_EN_CHANGE** l’utilisateur a effectué une action qui peut avoir modifié le texte dans un contrôle d’édition. Contrairement à la **EN_UPDATE** message de notification, ce message de notification est envoyé une fois que l’affichage des mises à jour Windows.  
  
- **ON_EN_ERRSPACE** le contrôle d’édition ne peut pas allouer suffisamment de mémoire pour répondre à une demande spécifique.  
  
- **ON_EN_HSCROLL** l’utilisateur clique sur la barre de défilement horizontale du contrôle d’édition. La fenêtre parente est notifiée avant la mise à jour de l’écran.  
  
- **ON_EN_KILLFOCUS** le contrôle d’édition perd le focus d’entrée.  
  
- **ON_EN_MAXTEXT** l’insertion actuelle a dépassé le nombre spécifié de caractères pour le contrôle d’édition et a été tronquée. Également envoyé lorsqu’un contrôle d’édition n’a pas la **ES_AUTOHSCROLL** style et le nombre de caractères à insérer dépasse la largeur du contrôle d’édition. Également envoyé lorsqu’un contrôle d’édition n’a pas la **ES_AUTOVSCROLL** style et le nombre total de lignes résultant d’une insertion de texte dépasse la hauteur du contrôle d’édition.  
  
- **ON_EN_SETFOCUS** envoyé lorsqu’un contrôle d’édition reçoit le focus d’entrée.  
  
- **ON_EN_UPDATE** le contrôle d’édition est sur le point d’afficher le texte modifié. Envoyé une fois que le contrôle a mis en forme le texte, mais avant qu’il analyse le texte afin que la taille de fenêtre peut être modifiée, si nécessaire.  
  
- **ON_EN_VSCROLL** l’utilisateur clique sur la barre de défilement verticale du contrôle d’édition. La fenêtre parente est notifiée avant la mise à jour de l’écran.  
  
 Si vous créez un `CEdit` objet dans une boîte de dialogue, la `CEdit` objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.  
  
 Si vous créez un `CEdit` objet à partir d’une ressource de boîte de dialogue à l’aide de l’éditeur de boîte de dialogue, la `CEdit` objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.  
  
 Si vous créez un `CEdit` de l’objet dans une fenêtre, vous devrez peut-être également détruire. Si vous créez le `CEdit` de l’objet sur la pile, il est supprimé automatiquement. Si vous créez le `CEdit` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet pour détruire quand l’utilisateur ferme les fenêtres de contrôle d’édition. Si vous allouez davantage de mémoire dans le `CEdit` de l’objet, substituez le `CEdit` destructeur pour éliminer les allocations.  
  
 Pour modifier certains styles dans un contrôle d’édition (tels que **ES_READONLY**) vous devez envoyer des messages spécifiques au contrôle au lieu d’utiliser [ModifyStyle](cwnd-class.md#modifystyle). Consultez [modifier les Styles de contrôle](http://msdn.microsoft.com/library/windows/desktop/bb775464) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations sur `CEdit`, consultez :  
  
- [Contrôles](../../mfc/controls-mfc.md)  
  
-   L’article de la Base de connaissances Q259949 : informations : SetCaretPos() n’est pas approprié avec CEdit ou des contrôles de CRichEditCtrl  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CEdit`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="canundo"></a>  CEdit::CanUndo  
 Appelez cette fonction pour déterminer si la dernière opération de modification peut être annulée.  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la dernière opération de modification peut être annulée par un appel à la **Annuler** fonction membre ; 0 si elle ne peut pas être annulée.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::Undo](#undo).  
  
##  <a name="cedit"></a>  CEdit::CEdit  
 Construit un objet `CEdit`.  
  
```  
CEdit();
```  
  
### <a name="remarks"></a>Notes  
 Utilisez [créer](#create) pour construire les fenêtres de contrôle d’édition.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]  
  
##  <a name="charfrompos"></a>  CEdit::CharFromPos  
 Appelez cette fonction pour récupérer la ligne de base zéro et l’index de caractère du caractère le plus proche du point spécifié dans ce `CEdit` contrôle  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `pt`  
 Les coordonnées d’un point dans la zone cliente de cet `CEdit` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de caractère dans l’ordre de faible **WORD**et l’index de ligne dans l’ordre de haute **WORD**.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette fonction membre est disponible avec Windows 95 et Windows NT 4.0.  
  
 Pour plus d’informations, consultez [EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]  
  
##  <a name="clear"></a>  CEdit::Clear  
 Appelez cette fonction pour supprimer (clear) la sélection actuelle (le cas échéant) dans le contrôle d’édition.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Notes  
 La suppression effectuée par **clair** puissent être annulées en appelant le [Annuler](#undo) fonction membre.  
  
 Pour supprimer la sélection actuelle et placer le contenu supprimé dans le Presse-papiers, appelez le [couper](#cut) fonction membre.  
  
 Pour plus d’informations, consultez [WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]  
  
##  <a name="copy"></a>  CEdit::Copy  
 Appelez cette fonction pour copier de la sélection actuelle (le cas échéant) dans le contrôle d’édition dans le Presse-papiers dans **CF_TEXT** format.  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]  
  
##  <a name="create"></a>  CEdit::Create  
 Crée le contrôle d’édition Windows et l’attache à le `CEdit` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwStyle`  
 Spécifie le style du contrôle d’édition. Appliquer n’importe quelle combinaison de [modifier les styles](styles-used-by-mfc.md#edit-styles) au contrôle.  
  
 `rect`  
 Spécifie la taille et la position du contrôle d’édition. Peut être un `CRect` objet ou `RECT` structure.  
  
 `pParentWnd`  
 Spécifie la fenêtre du parent du contrôle d’édition (généralement un `CDialog`). Il ne doit pas être **NULL**.  
  
 `nID`  
 Spécifie l’ID. du contrôle de la modifier  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’initialisation a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CEdit` objet en deux étapes. Tout d’abord, appelez le `CEdit` constructeur, puis appelez **créer**, ce qui crée le contrôle d’édition Windows et l’attache à le `CEdit` objet.  
  
 Lorsque **créer** s’exécute, Windows envoie les [WM_NCCREATE](http://msdn.microsoft.com/library/windows/desktop/ms632635), [WM_NCCALCSIZE](http://msdn.microsoft.com/library/windows/desktop/ms632634), [WM_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619), et [WM_ GETMINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632626) messages pour le contrôle d’édition.  
  
 Ces messages sont gérées par défaut par le [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate), et [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) fonctions membres dans la `CWnd` classe de base. Pour étendre le traitement du message par défaut, dérivez une classe de `CEdit`, ajouter une table des messages à la nouvelle classe et substituer les fonctions membres de gestionnaire de messages ci-dessus. Substituer `OnCreate`, par exemple, pour effectuer l’initialisation nécessaire pour la nouvelle classe.  
  
 Appliquez ce qui suit [styles de fenêtre](styles-used-by-mfc.md#window-styles) à un contrôle d’édition.  
  
- **WS_CHILD** toujours  
  
- **WS_VISIBLE** généralement  
  
- **WS_DISABLED** rarement  
  
- **WS_GROUP** aux contrôles de groupe  
  
- **WS_TABSTOP** pour inclure le contrôle d’édition dans l’ordre de tabulation  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]  
  
##  <a name="cut"></a>  CEdit::Cut  
 Appelez cette fonction pour supprimer (Couper) à la sélection actuelle (le cas échéant) dans le contrôle d’édition et de copier le texte supprimé dans le Presse-papiers dans **CF_TEXT** format.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Notes  
 La suppression effectuée par **couper** puissent être annulées en appelant le [Annuler](#undo) fonction membre.  
  
 Pour supprimer la sélection actuelle sans la placer le texte supprimé dans le Presse-papiers, appelez le [clair](#clear) fonction membre.  
  
 Pour plus d’informations, consultez [WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]  
  
##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer  
 Appelez cette fonction pour réinitialiser (Effacer) de l’indicateur d’annulation d’un contrôle d’édition.  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>Notes  
 Le contrôle d’édition sera désormais impossible d’annuler la dernière opération. L’indicateur d’annulation est défini chaque fois qu’une opération dans le contrôle d’édition peut être annulée.  
  
 L’indicateur d’annulation est automatiquement effacé chaque fois que le [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) ou [SetHandle](#sethandle) `CWnd` des fonctions de membre sont appelées.  
  
 Pour plus d’informations, consultez [EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]  
  
##  <a name="fmtlines"></a>  CEdit::FmtLines  
 Appelez cette fonction pour définir l’inclusion de caractères de saut de ligne conditionnel ou de désactiver au sein d’un contrôle d’édition de plusieurs lignes.  
  
```  
BOOL FmtLines(BOOL bAddEOL);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAddEOL*  
 Spécifie si les caractères de saut de ligne conditionnel doivent être insérées. La valeur **TRUE** insère les caractères ; une valeur de **FALSE** les supprime.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si toute mise en forme se produit ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un saut de ligne paramétré se compose de deux retours chariot et de saut de ligne insérée à la fin d’une ligne qui est interrompue en raison du retour. Un saut de ligne se compose d’un retour de chariot et un saut de ligne. Les lignes qui se terminent par un saut de ligne ne sont pas affectés par `FmtLines`.  
  
 Windows répondra uniquement si le `CEdit` l’objet est un contrôle d’édition de plusieurs lignes.  
  
 `FmtLines` affecte uniquement la mémoire tampon retournée par [GetHandle](#gethandle) et le texte retourné par [WM_GETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632627). Il n’a aucun impact sur l’affichage du texte dans le contrôle d’édition.  
  
 Pour plus d’informations, consultez [EM_FMTLINES](http://msdn.microsoft.com/library/windows/desktop/bb761570) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]  
  
##  <a name="getcuebanner"></a>  CEdit::GetCueBanner  
 Récupère le texte qui s’affiche en tant que l’indice de texte, ou Conseil, dans un contrôle d’édition lorsque le contrôle est vide.  
  
```  
BOOL GetCueBanner(
    LPWSTR lpszText,  
    int cchText) const;  
  
CString GetCueBanner() const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `lpszText`  
 Un pointeur vers une chaîne qui contient le texte de la file d’attente.  
  
 [in] `cchText`  
 Le nombre de caractères qui peuvent être reçus. Ce nombre comprend à la fin du `NULL` caractère.  
  
### <a name="return-value"></a>Valeur de retour  
 Pour la première surcharge, `true` si la méthode réussit ; sinon `false`.  
  
 Pour la seconde surcharge, une [CString](../../atl-mfc-shared/using-cstring.md) qui contient le texte d’indication si la méthode réussit ; sinon, une chaîne vide (« »).  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [EM_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761572) message, ce qui est décrit dans le Kit de développement logiciel Windows. Pour plus d’informations, consultez la [Edit_GetCueBannerText](http://msdn.microsoft.com/library/windows/desktop/bb761695) (macro).  
  
##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine  
 Appelez cette fonction pour déterminer la ligne visible au premier plan dans un contrôle d’édition.  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de la ligne affichée au premier plan. Pour les contrôles d’édition sur une ligne, la valeur de retour est 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]  
  
##  <a name="gethandle"></a>  CEdit::GetHandle  
 Appelez cette fonction pour récupérer un handle de la mémoire actuellement allouée à un contrôle d’édition de plusieurs lignes.  
  
```  
HLOCAL GetHandle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle de la mémoire locale qui identifie la mémoire tampon contenant le contenu du contrôle d’édition. Si une erreur se produit, par exemple envoyer le message à un contrôle d’édition sur une ligne, la valeur de retour est 0.  
  
### <a name="remarks"></a>Notes  
 Le handle est un handle de la mémoire locale et peut être utilisé par un de la **Local** gérer les fonctions de mémoire de Windows qui prennent une mémoire locale en tant que paramètre.  
  
 **GetHandle** est traité uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Appelez **GetHandle** pour un contrôle d’édition de plusieurs lignes dans une boîte de dialogue uniquement si la boîte de dialogue a été créée avec le **DS_LOCALEDIT** style d’indicateur est défini. Si le **DS_LOCALEDIT** style n’est pas défini, vous obtiendrez toujours une valeur de retour différente de zéro, mais vous ne serez pas en mesure d’utiliser la valeur retournée.  
  
> [!NOTE]
> **GetHandle** ne fonctionne pas avec Windows 95/98. Si vous appelez **GetHandle** dans Windows 95/98, elle retournera **NULL**. **GetHandle** fonctionnera comme indiqué sous Windows NT versions 3.51 et ultérieures.  
  
 Pour plus d’informations, consultez [EM_GETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761576) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]  
  
##  <a name="gethighlight"></a>  CEdit::GetHighlight  
 Obtient les index des premier et derniers caractères dans une plage de texte qui est mis en surbrillance dans le contrôle d’édition actuel.  
  
```  
BOOL GetHighlight(
    int* pichStart,   
    int* pichEnd) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[out] `pichStart`|Index de base zéro du premier caractère dans la plage de texte qui est mis en surbrillance.|  
|[out] `pichEnd`|Index de base zéro du dernier caractère de la plage de texte qui est mis en surbrillance.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [EM_GETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761578) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getlimittext"></a>  CEdit::GetLimitText  
 Appelez cette fonction membre pour obtenir la limite de texte pour ce `CEdit` objet.  
  
```  
UINT GetLimitText() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La limite texte actuelle, en octets, pour ce `CEdit` objet.  
  
### <a name="remarks"></a>Notes  
 La limite de texte est la quantité maximale de texte, en octets, que le contrôle d’édition peut accepter.  
  
> [!NOTE]
>  Cette fonction membre est disponible avec Windows 95 et Windows NT 4.0.  
  
 Pour plus d’informations, consultez [EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]  
  
##  <a name="getline"></a>  CEdit::GetLine  
 Appelez cette fonction pour récupérer une ligne de texte à partir d’un contrôle d’édition et le place dans `lpszBuffer`.  
  
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
 `nIndex`  
 Spécifie le numéro de ligne à récupérer à partir de plusieurs lignes contrôle d’édition. Numéros de ligne sont de base zéro ; la valeur 0 spécifie la première ligne. Ce paramètre est ignoré par un contrôle d’édition sur une ligne.  
  
 `lpszBuffer`  
 Pointe vers la mémoire tampon qui reçoit une copie de la ligne. Le premier mot de la mémoire tampon doit spécifier le nombre maximal de caractères qui peuvent être copiés dans la mémoire tampon.  
  
 `nMaxLength`  
 Spécifie le nombre maximal d’octets pouvant être copiée dans la mémoire tampon. `GetLine` place cette valeur dans le premier mot de `lpszBuffer` avant l’appel à Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’octets réellement copiés. La valeur de retour est 0 si le numéro de ligne spécifiée par `nIndex` est supérieur au nombre de lignes dans le contrôle d’édition.  
  
### <a name="remarks"></a>Notes  
 La ligne copiée ne contient pas un caractère de fin de la valeur null.  
  
 Pour plus d’informations, consultez [EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::GetLineCount](#getlinecount).  
  
##  <a name="getlinecount"></a>  CEdit::GetLineCount  
 Appelez cette fonction pour récupérer le nombre de lignes dans un contrôle d’édition de plusieurs lignes.  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Contrôle d’édition un entier contenant le nombre de lignes dans plusieurs lignes. Si aucun texte n’a été entré dans le contrôle d’édition, la valeur de retour est 1.  
  
### <a name="remarks"></a>Notes  
 `GetLineCount` est traité uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Pour plus d’informations, consultez [EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]  
  
##  <a name="getmargins"></a>  CEdit::GetMargins  
 Appelez cette fonction membre pour récupérer les marges gauche et droite de ce contrôle d’édition.  
  
```  
DWORD GetMargins() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur de la marge de gauche dans l’ordre de faible **WORD** et la largeur de la marge de droite dans l’ordre de haute **WORD**.  
  
### <a name="remarks"></a>Notes  
 Les marges sont mesurées en pixels.  
  
> [!NOTE]
>  Cette fonction membre est disponible avec Windows 95 et Windows NT 4.0.  
  
 Pour plus d’informations, consultez [EM_GETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761590) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="getmodify"></a>  CEdit::GetModify  
 Appelez cette fonction pour déterminer si le contenu d’un contrôle d’édition a été modifié.  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contenu de contrôle d’édition a été modifié ; 0 s’ils sont restés inchangés.  
  
### <a name="remarks"></a>Notes  
 Windows conserve un indicateur interne qui indique si le contenu du contrôle d’édition a été modifié. Cet indicateur est désactivé lorsque le contrôle d’édition est d’abord créé et peut également être désactivé en appelant le [SetModify](#setmodify) fonction membre.  
  
 Pour plus d’informations, consultez [EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]  
  
##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar  
 Appelez cette fonction pour récupérer le caractère de mot de passe s’affiche dans un contrôle d’édition lorsque l’utilisateur entre du texte.  
  
```  
TCHAR GetPasswordChar() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Spécifie le caractère à afficher au lieu du caractère entrés par l’utilisateur. La valeur de retour est `NULL` si aucun caractère de mot de passe n’existe.  
  
### <a name="remarks"></a>Notes  
 Si vous créez le contrôle d’édition avec le **ES_PASSWORD** style, la DLL qui prend en charge le contrôle détermine le caractère de mot de passe par défaut. Le manifeste ou la [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) méthode détermine les DLL prend en charge le contrôle d’édition. Si user32.dll prend en charge le contrôle d’édition, le caractère de mot de passe par défaut est astérisque (« * », U + 002 a). Si le fichier comctl32.dll version 6 prend en charge le contrôle d’édition, le caractère par défaut est noir cercle ('●', U + 25CF). Pour plus d’informations sur la DLL et la version prenant en charge les contrôles communs, consultez [interpréteur de commandes et les Versions de contrôles courants](http://msdn.microsoft.com/library/windows/desktop/bb776779).  
  
 Cette méthode envoie le [EM_GETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761594) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]  
  
##  <a name="getrect"></a>  CEdit::GetRect  
 Appelez cette fonction pour obtenir le rectangle de mise en forme d’un contrôle d’édition.  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `lpRect`  
 Pointe vers le `RECT` structure qui reçoit le rectangle de mise en forme.  
  
### <a name="remarks"></a>Notes  
 Le rectangle de mise en forme est le rectangle de limitation du texte, qui est indépendante de la taille de la fenêtre de contrôle d’édition.  
  
 Le rectangle de mise en forme d’un contrôle d’édition de plusieurs lignes peut être modifié par le [SetRect](#setrect) et [SetRectNP](#setrectnp) fonctions membres.  
  
 Pour plus d’informations, consultez [EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::LimitText](#limittext).  
  
##  <a name="getsel"></a>  CEdit::GetSel  
 Appelez cette fonction pour obtenir de début et fin de positions de caractère de la sélection actuelle (le cas échéant) dans un contrôle d’édition, à l’aide de la valeur de retour ou les paramètres.  
  
```  
DWORD GetSel() const;  
  
void GetSel(
    int& nStartChar,  
    int& nEndChar) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nStartChar`  
 Référence à un entier qui recevra la position du premier caractère dans la sélection actuelle.  
  
 `nEndChar`  
 Référence à un entier qui recevra la position du premier caractère non sélectionnée après la fin de la sélection actuelle.  
  
### <a name="return-value"></a>Valeur de retour  
 La version qui retourne un `DWORD` retourne une valeur qui contient la position de départ dans le mot de poids faible et de la position du premier caractère non sélectionnée après la fin de la sélection dans le mot de poids fort.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [EM_GETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761598) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]  
  
##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip  
 Masque les info-bulle associé au contrôle d’édition actuel.  
  
```  
BOOL HideBalloonTip();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette fonction envoie le [EM_HIDEBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761604) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="limittext"></a>  CEdit::LimitText  
 Appelez cette fonction pour limiter la longueur du texte que l’utilisateur peut entrer dans un contrôle d’édition.  
  
```  
void LimitText(int nChars = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nChars`  
 Spécifie la longueur (en octets) du texte que l’utilisateur peut entrer. Si ce paramètre est 0, la longueur de texte est définie sur **UINT_MAX** octets. Il s'agit du comportement par défaut.  
  
### <a name="remarks"></a>Notes  
 Modification de la limite de texte restreint uniquement le texte que l’utilisateur peut entrer. Il n’a aucun effet sur n’importe quel texte déjà dans le contrôle d’édition, ni n’affecte pas la longueur du texte copié dans le contrôle d’édition par le [SetWindowText](cwnd-class.md#setwindowtext) fonction membre dans `CWnd`. Si une application utilise le `SetWindowText` afin de placer davantage de texte dans un contrôle d’édition que celle spécifiée dans l’appel à `LimitText`, l’utilisateur peut supprimer le texte dans le contrôle d’édition. Toutefois, la limite de texte empêche l’utilisateur de remplacer le texte existant par un nouveau texte, à moins que la suppression de la sélection actuelle, le texte se situent en dessous de la limite de texte.  
  
> [!NOTE]
>  Dans Win32 (Windows NT et Windows 95/98), [SetLimitText](#setlimittext) remplace cette fonction.  
  
 Pour plus d’informations, consultez [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]  
  
##  <a name="linefromchar"></a>  CEdit::LineFromChar  
 Appelez cette fonction pour récupérer le numéro de ligne de la ligne qui contient l’index de caractère spécifié.  
  
```  
int LineFromChar(int nIndex = -1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Contient la valeur d’index de base zéro du caractère souhaité dans le texte du contrôle d’édition, ou -1. Si `nIndex` est -1, il spécifie la ligne actuelle, autrement dit, la ligne qui contient le point d’insertion.  
  
### <a name="return-value"></a>Valeur de retour  
 Le numéro de ligne de base zéro de la ligne contenant l’index de caractère spécifié par `nIndex`. Si `nIndex` est -1, le numéro de la ligne qui contient le premier caractère de la sélection est retourné. S’il n’existe pas de sélection, le numéro de ligne actuel est retourné.  
  
### <a name="remarks"></a>Notes  
 Un index de caractère est le nombre de caractères à partir du début du contrôle d’édition.  
  
 Cette fonction membre est utilisée uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Pour plus d’informations, consultez [EM_LINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761609) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]  
  
##  <a name="lineindex"></a>  CEdit::LineIndex  
 Appelez cette fonction pour récupérer l’index de caractère d’une ligne dans un contrôle d’édition de plusieurs lignes.  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nLine`  
 Contient la valeur d’index pour la ligne de votre choix dans le texte du contrôle d’édition, ou -1. Si `nLine` est -1, il spécifie la ligne actuelle, autrement dit, la ligne qui contient le point d’insertion.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de caractère de la ligne spécifiée dans `nLine` ou -1 si le numéro de ligne spécifié est supérieur au nombre de lignes dans le contrôle d’édition.  
  
### <a name="remarks"></a>Notes  
 L’index de caractère est le nombre de caractères à partir du début du contrôle d’édition de la ligne spécifiée.  
  
 Cette fonction membre est traitée uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Pour plus d’informations, consultez [EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]  
  
##  <a name="linelength"></a>  CEdit::LineLength  
 Récupère la longueur d’une ligne dans un contrôle d’édition.  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nLine`  
 Index de base zéro d’un caractère dans la ligne dont la longueur doit être récupéré. La valeur par défaut est -1.  
  
### <a name="return-value"></a>Valeur de retour  
 Pour les contrôles d’édition sur une ligne, la valeur de retour est la longueur, en `TCHAR`s, du texte dans le contrôle d’édition.  
  
 Pour les contrôles d’édition multiligne, la valeur de retour est la longueur, en `TCHAR`s, de la ligne spécifiée par la `nLine` paramètre. Pour [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] la longueur est le nombre d’octets dans la ligne de texte, pour le texte Unicode, la longueur est le nombre de caractères dans la ligne. La longueur n’inclut pas le caractère de retour chariot à la fin de la ligne.  
  
 Si le `nLine` paramètre est supérieur au nombre de caractères dans le contrôle, la valeur de retour est égale à zéro.  
  
 Si le `nLine` paramètre est -1, la valeur de retour est le nombre de caractères non sélectionnés dans les lignes qui contiennent des caractères sélectionnés. Par exemple, si la sélection s’étend à partir du quatrième caractère d’une ligne et le huitième caractère de la fin de la ligne suivante, la valeur de retour est 10. Autrement dit, trois caractères sur la première ligne et sept suivante.  
  
 Pour plus d’informations sur la `TCHAR` de type, consultez la `TCHAR` ligne dans la table [les Types de données Windows](http://msdn.microsoft.com/library/windows/desktop/aa383751).  
  
### <a name="remarks"></a>Notes  
 Cette méthode est prise en charge par le [EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::LineIndex](#lineindex).  
  
##  <a name="linescroll"></a>  CEdit::LineScroll  
 Appelez cette fonction pour faire défiler le texte d’un contrôle d’édition de plusieurs lignes.  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nLines`  
 Spécifie le nombre de lignes à faire défiler verticalement.  
  
 `nChars`  
 Spécifie le nombre de positions de caractère pour faire défiler horizontalement. Cette valeur est ignorée si le contrôle d’édition est la **ES_RIGHT** ou **ES_CENTER** style.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est traitée uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Le contrôle d’édition ne défile pas verticalement au-delà de la dernière ligne du texte dans le contrôle d’édition. Si la ligne en cours ainsi que le nombre de lignes spécifié par `nLines` dépasse le nombre total de lignes dans le contrôle d’édition, la valeur est ajustée afin que la dernière ligne du contrôle d’édition est l’objet d’un défilement vers le haut de la fenêtre de contrôle d’édition.  
  
 `LineScroll` peut être utilisé pour faire défiler horizontalement au-delà du dernier caractère de n’importe quelle ligne.  
  
 Pour plus d’informations, consultez [EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::GetFirstVisibleLine](#getfirstvisibleline).  
  
##  <a name="paste"></a>  CEdit::Paste  
 Appelez cette fonction pour insérer les données du Presse-papiers dans le `CEdit` au point d’insertion.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Notes  
 Les données sont insérées que si le Presse-papiers contient des données **CF_TEXT** format.  
  
 Pour plus d’informations, consultez [WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]  
  
##  <a name="posfromchar"></a>  CEdit::PosFromChar  
 Appelez cette fonction pour obtenir la position (angle supérieur gauche) d’un caractère donné dans cette `CEdit` objet.  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nChar`  
 Index de base zéro du caractère spécifié.  
  
### <a name="return-value"></a>Valeur de retour  
 Les coordonnées du coin supérieur gauche du caractère spécifié par `nChar`.  
  
### <a name="remarks"></a>Notes  
 Le caractère est spécifié en donnant sa valeur d’index de base zéro. Si `nChar` est supérieur à l’index du dernier caractère dans ce `CEdit` de l’objet, la valeur de retour spécifie les coordonnées de la position de caractère juste après le dernier caractère dans ce `CEdit` objet.  
  
> [!NOTE]
>  Cette fonction membre est disponible avec Windows 95 et Windows NT 4.0.  
  
 Pour plus d’informations, consultez [EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::LineFromChar](#linefromchar).  
  
##  <a name="replacesel"></a>  CEdit::ReplaceSel  
 Appelez cette fonction pour remplacer la sélection actuelle dans un contrôle d’édition avec le texte spécifié par `lpszNewText`.  
  
```  
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszNewText`  
 Pointe vers une chaîne terminée par le caractère null qui contient le texte de remplacement.  
  
 `bCanUndo`  
 Pour spécifier que cette fonction peut être annulée, définissez la valeur de ce paramètre pour **TRUE** . La valeur par défaut est **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Remplace uniquement une partie du texte dans un contrôle d’édition. Si vous souhaitez remplacer tout le texte, utilisez la [CWnd::SetWindowText](cwnd-class.md#setwindowtext) fonction membre.  
  
 S’il n’existe pas de sélection, le texte de remplacement est inséré à l’emplacement du curseur.  
  
 Pour plus d’informations, consultez [EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::LineIndex](#lineindex).  
  
##  <a name="setcuebanner"></a>  CEdit::SetCueBanner  
 Définit le texte qui s’affiche en tant que la pile de texte, ou Conseil, dans une modification de contrôle lorsque le contrôle est vide.  
  
```  
BOOL SetCueBanner(LPCWSTR lpszText);

 
BOOL SetCueBanner(
    LPCWSTR lpszText,   
    BOOL fDrawWhenFocused = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszText`  
 Pointeur vers une chaîne qui contient la file d’attente à afficher dans le contrôle d’édition.  
  
 [in] `fDrawWhenFocused`  
 Si `false`, la bannière de signal n’est pas dessinée lorsque l’utilisateur clique sur le contrôle d’édition et donne le contrôle le focus.  
  
 Si `true`, la bannière de signal est dessinée, même lorsque le contrôle a le focus. La bannière de signal disparaît lorsque l’utilisateur commence à taper dans le contrôle.  
  
 La valeur par défaut est `false`.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si la méthode a réussi ; dans le cas contraire `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [EM_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761639) message, ce qui est décrit dans le Kit de développement logiciel Windows. Pour plus d’informations, consultez la [Edit_SetCueBannerTextFocused](http://msdn.microsoft.com/library/windows/desktop/bb761703) (macro).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre la [CEdit::SetCueBanner](#setcuebanner) (méthode).  
  
 [!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]  
  
##  <a name="sethandle"></a>  CEdit::SetHandle  
 Appelez cette fonction pour définir le handle de la mémoire locale qui sera utilisée par un contrôle d’édition de plusieurs lignes.  
  
```  
void SetHandle(HLOCAL hBuffer);
```  
  
### <a name="parameters"></a>Paramètres  
 *hBuffer*  
 Contient un handle vers la mémoire locale. Ce handle doit avoir été créé par un appel précédent à la [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) (fonction) de Windows à l’aide du **LMEM_MOVEABLE** indicateur. La mémoire est censée pour contenir une chaîne se terminant par null. Si ce n’est pas le cas, le premier octet de la mémoire allouée doit être défini sur 0.  
  
### <a name="remarks"></a>Notes  
 Le contrôle d’édition utilise cette mémoire tampon pour stocker le texte actuellement affiché au lieu d’allouer de sa mémoire tampon.  
  
 Cette fonction membre est traitée uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Avant qu’une application définit un nouveau handle de mémoire, elle doit utiliser le [GetHandle](#gethandle) fonction membre pour obtenir le handle de la mémoire tampon en cours et libérer la mémoire à l’aide du **LocalFree** fonction Windows.  
  
 `SetHandle` Efface la mémoire tampon d’annulation (le [CanUndo](#canundo) puis, fonction membre retourne 0) et l’indicateur de modification interne (la [GetModify](#getmodify) puis, fonction membre retourne 0). La fenêtre de contrôle d’édition est redessinée.  
  
 Vous pouvez utiliser cette fonction membre dans un contrôle d’édition de plusieurs lignes dans une boîte de dialogue uniquement si vous avez créé la boîte de dialogue avec le **DS_LOCALEDIT** style d’indicateur est défini.  
  
> [!NOTE]
> **GetHandle** ne fonctionne pas avec Windows 95/98. Si vous appelez **GetHandle** dans Windows 95/98, elle retournera **NULL**. **GetHandle** fonctionnera comme indiqué sous Windows NT versions 3.51 et ultérieures.  
  
 Pour plus d’informations, consultez [EM_SETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761641), [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), et [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]  
  
##  <a name="sethighlight"></a>  CEdit::SetHighlight  
 Contrôle d’édition met en évidence une plage de texte qui s’affiche en cours.  
  
```  
void SetHighlight(
    int ichStart,   
    int ichEnd);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `ichStart`|Index de base zéro du premier caractère dans la plage de texte pour mettre en surbrillance.|  
|[in] `ichEnd`|Index de base zéro du dernier caractère dans la plage de texte pour mettre en surbrillance.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [EM_SETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761643) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="setlimittext"></a>  CEdit::SetLimitText  
 Appelez cette fonction membre pour définir la limite de texte pour ce `CEdit` objet.  
  
```  
void SetLimitText(UINT nMax);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMax`  
 La nouvelle limite de texte en caractères.  
  
### <a name="remarks"></a>Notes  
 La limite de texte est la quantité maximale de texte, en caractères, et que le contrôle d’édition peut accepter.  
  
 Modification de la limite de texte restreint uniquement le texte que l’utilisateur peut entrer. Il n’a aucun effet sur n’importe quel texte déjà dans le contrôle d’édition, ni n’affecte pas la longueur du texte copié dans le contrôle d’édition par le [SetWindowText](cwnd-class.md#setwindowtext) fonction membre dans `CWnd`. Si une application utilise le `SetWindowText` afin de placer davantage de texte dans un contrôle d’édition que celle spécifiée dans l’appel à `LimitText`, l’utilisateur peut supprimer le texte dans le contrôle d’édition. Toutefois, la limite de texte empêche l’utilisateur de remplacer le texte existant par un nouveau texte, à moins que la suppression de la sélection actuelle, le texte se situent en dessous de la limite de texte.  
  
 Cette fonction remplace [LimitText](#limittext) dans Win32.  
  
 Pour plus d’informations, consultez [EM_SETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761647) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="setmargins"></a>  CEdit::SetMargins  
 Appelez cette méthode pour définir les marges gauche et droite de ce contrôle d’édition.  
  
```  
void SetMargins(
    UINT nLeft,  
    UINT nRight);
```  
  
### <a name="parameters"></a>Paramètres  
 *nLeft*  
 La largeur de la marge de gauche, en pixels.  
  
 *nRight*  
 La largeur de la marge de droite, en pixels.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette fonction membre est disponible avec Windows 95 et Windows NT 4.0.  
  
 Pour plus d’informations, consultez [EM_SETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761649) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="setmodify"></a>  CEdit::SetModify  
 Appelez cette fonction pour définir ou supprimer l’indicateur modifié pour un contrôle d’édition.  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bModified`  
 La valeur **TRUE** indique que le texte a été modifié et la valeur **FALSE** indique qu’il est modifié. Par défaut, l’indicateur modifié est défini.  
  
### <a name="remarks"></a>Notes  
 L’indicateur modifié indique si le texte dans le contrôle d’édition a été modifié. Elle est définie automatiquement chaque fois que l’utilisateur modifie le texte. Sa valeur peut être récupérée avec la [GetModify](#getmodify) fonction membre.  
  
 Pour plus d’informations, consultez [EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::GetModify](#getmodify).  
  
##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar  
 Appelez cette fonction pour définir ou supprimer un caractère de mot de passe affiché dans un contrôle d’édition lorsque l’utilisateur tape du texte.  
  
```  
void SetPasswordChar(TCHAR ch);
```  
  
### <a name="parameters"></a>Paramètres  
 *ch*  
 Spécifie le caractère à afficher à la place le caractère tapé par l’utilisateur. Si *ch* est 0, les caractères tapés par l’utilisateur sont affichés.  
  
### <a name="remarks"></a>Notes  
 Quand un caractère de mot de passe est défini, ce caractère est affiché pour chaque caractère de l’utilisateur tape.  
  
 Cette fonction membre n’a aucun effet sur plusieurs lignes contrôle d’édition.  
  
 Lorsque le `SetPasswordChar` fonction membre est appelée, `CEdit` redessine tous les caractères visibles à l’aide du caractère spécifié par *ch*.  
  
 Si le contrôle d’édition est créé avec le [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) style, le caractère de mot de passe par défaut est défini à un astérisque ( **\***). Ce style est supprimé si `SetPasswordChar` est appelée avec *ch* définie sur 0.  
  
 Pour plus d’informations, consultez [EM_SETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761653) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]  
  
##  <a name="setreadonly"></a>  CEdit::SetReadOnly  
 Appelle cette fonction pour définir l’état en lecture seule d’un contrôle d’édition.  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bReadOnly`  
 Spécifie s’il faut définir ou supprimer l’état en lecture seule du contrôle d’édition. La valeur **TRUE** définit l’état en lecture seule ; la valeur **FALSE** définit l’état en lecture-écriture.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi, ou 0 si une erreur se produit.  
  
### <a name="remarks"></a>Notes  
 Le paramètre actuel se trouve en testant la [ES_READONLY](styles-used-by-mfc.md#edit-styles) indicateur dans la valeur de retour de [CWnd::GetStyle](cwnd-class.md#getstyle).  
  
 Pour plus d’informations, consultez [EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]  
  
##  <a name="setrect"></a>  CEdit::SetRect  
 Appelez cette fonction pour définir les dimensions d’un rectangle à l’aide des coordonnées spécifiées.  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpRect`  
 Pointe vers le `RECT` structure ou `CRect` objet qui spécifie les nouvelles dimensions du rectangle de mise en forme.  
  
### <a name="remarks"></a>Notes  
 Ce membre est traité uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Utilisez `SetRect` pour définir la mise en forme de contrôle d’édition rectangle de plusieurs lignes. Le rectangle de mise en forme est le rectangle de limitation du texte, qui est indépendante de la taille de la fenêtre de contrôle d’édition. Lorsque le contrôle d’édition est créé, le rectangle de mise en forme est identique à la zone cliente de la fenêtre de contrôle d’édition. À l’aide de la `SetRect` fonction membre, une application peut faire le rectangle de mise en forme supérieure ou inférieure à la fenêtre de contrôle d’édition.  
  
 Si le contrôle d’édition n’a aucune barre de défilement, texte sera découpé, ne pas encapsulé, si le rectangle de mise en forme est effectué en plus de la fenêtre. Si le contrôle d’édition contient une bordure, le rectangle de mise en forme est réduit par la taille de la bordure. Si vous ajustez le rectangle retourné par le `GetRect` fonction membre, vous devez supprimer la taille de la bordure avant de passer le rectangle à `SetRect`.  
  
 Lorsque `SetRect` est appelée, le contrôle d’édition de texte est également reformaté et affiche de nouveau.  
  
 Pour plus d’informations, consultez [EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]  
  
##  <a name="setrectnp"></a>  CEdit::SetRectNP  
 Appelez cette fonction pour définir le rectangle de mise en forme d’un contrôle d’édition de plusieurs lignes.  
  
```  
void SetRectNP(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpRect`  
 Pointe vers un `RECT` structure ou `CRect` objet qui spécifie les nouvelles dimensions du rectangle.  
  
### <a name="remarks"></a>Notes  
 Le rectangle de mise en forme est le rectangle de limitation du texte, qui est indépendante de la taille de la fenêtre de contrôle d’édition.  
  
 `SetRectNP` est identique à la `SetRect` fonction membre, sauf que la fenêtre de contrôle d’édition n’est pas redessinée.  
  
 Lorsque le contrôle d’édition est créé, le rectangle de mise en forme est identique à la zone cliente de la fenêtre de contrôle d’édition. En appelant le `SetRectNP` fonction membre, une application peut faire le rectangle de mise en forme supérieure ou inférieure à la fenêtre de contrôle d’édition.  
  
 Si le contrôle d’édition n’a aucune barre de défilement, texte sera découpé, ne pas encapsulé, si le rectangle de mise en forme est effectué en plus de la fenêtre.  
  
 Ce membre est traité uniquement par les contrôles d’édition de plusieurs lignes.  
  
 Pour plus d’informations, consultez [EM_SETRECTNP](http://msdn.microsoft.com/library/windows/desktop/bb761659) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::SetRect](#setrect).  
  
##  <a name="setsel"></a>  CEdit::SetSel  
 Appelez cette fonction pour sélectionner une plage de caractères dans un contrôle d’édition.  
  
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
 *dwSelection*  
 Spécifie la position de départ dans le mot de poids faible et la position de fin dans le mot de poids fort. Si le mot de poids faible est 0 et le mot de poids fort est -1, tout le texte du contrôle d’édition est sélectionné. Si le mot de poids faible est -1, la sélection actuelle est supprimée.  
  
 *bNoScroll*  
 Indique si le point d’insertion doit être atteint dans la vue. Si **FALSE**, le point d’insertion devient visible. Si **TRUE**, le point d’insertion ne défile pas dans la vue.  
  
 `nStartChar`  
 Spécifie la position de départ. Si `nStartChar` est égal à 0 et `nEndChar` est -1, tout le texte du contrôle d’édition est sélectionné. Si `nStartChar` est -1, une sélection en cours est supprimée.  
  
 `nEndChar`  
 Spécifie la position de fin.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [EM_SETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761661) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEdit::GetSel](#getsel).  
  
##  <a name="settabstops"></a>  CEdit::SetTabStops  
 Appelez cette fonction pour définir les taquets de tabulation dans un contrôle d’édition de plusieurs lignes.  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>Paramètres  
 `cxEachStop`  
 Spécifie que les taquets de tabulation doivent être définies à chaque `cxEachStop` unités de boîte de dialogue.  
  
 `nTabStops`  
 Spécifie le nombre de taquets de tabulation contenues dans `rgTabStops`. Ce nombre doit être supérieur à 1.  
  
 `rgTabStops`  
 Pointe vers un tableau d’entiers non signés, la spécification de l’onglet s’arrête en unités de boîte de dialogue. Une unité de boîte de dialogue est une distance horizontale ou verticale. Une unité de boîte de dialogue horizontale est égale à un quart de l’unité de largeur de base de dialogue actuelle et 1 unité de boîte de dialogue vertical est égale à un huitième de l’unité de base de hauteur de boîte de dialogue actuelle. Les unités de dialogue sont calculées en fonction de la hauteur et de la largeur de la police système actuelle. Le **GetDialogBaseUnits** fonction Windows retourne, unités de base, la boîte de dialogue active en pixels.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les onglets ont été définies ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Lorsque le texte est copié dans un contrôle d’édition de plusieurs lignes, n’importe quel caractère de tabulation dans le texte entraînera l’espace à générer jusqu'à la tabulation suivante.  
  
 Pour définir des taquets de tabulation à la taille par défaut de 32 unités de boîte de dialogue, appelez la version sans paramètre de cette fonction membre. Pour définir des taquets de tabulation sur une taille de 32, appelez la version avec le `cxEachStop` paramètre. Pour définir des taquets de tabulation dans un tableau de taille, utilisez la version avec deux paramètres.  
  
 Cette fonction membre est traitée uniquement par les contrôles d’édition de plusieurs lignes.  
  
 `SetTabStops` ne pas renouveler automatiquement la fenêtre d’édition. Si vous modifiez les taquets de tabulation du texte déjà dans le contrôle d’édition, appelez [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) pour redessiner la fenêtre d’édition.  
  
 Pour plus d’informations, consultez [EM_SETTABSTOPS](http://msdn.microsoft.com/library/windows/desktop/bb761663) et [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CEditView::SetTabStops](ceditview-class.md#settabstops).  
  
##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip  
 Affiche une info-bulle qui est associée avec le contrôle d’édition actuel.  
  
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
|[in] `pEditBalloonTip`|Pointeur vers un [EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466) structure qui décrit l’info-bulle.|  
|[in] `lpszTitle`|Pointeur vers une chaîne Unicode qui contient le titre de l’info-bulle.|  
|[in] `lpszText`|Pointeur vers une chaîne Unicode qui contient le texte d’info-bulle Info-bulle.|  
|[in] `ttiIcon`|Un `INT` qui spécifie le type d’icône à associer à l’info-bulle. La valeur par défaut est `TTI_NONE`. Pour plus d’informations, consultez la `ttiIcon` membre de la [EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466) structure.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette fonction envoie le [EM_SHOWBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761668) message, ce qui est décrit dans le Kit de développement logiciel Windows. Pour plus d’informations, consultez la [Edit_ShowBalloonTip](http://msdn.microsoft.com/library/windows/desktop/bb761707) (macro).  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit une variable, `m_cedit`, qui est utilisé pour accéder au contrôle d’édition actuel. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant affiche une info-bulle pour un contrôle d’édition. Le [CEdit::ShowBalloonTip](#showballoontip) méthode spécifie un texte d’info-bulle de titre et l’info-bulle.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]  
  
##  <a name="undo"></a>  CEdit::Undo  
 Appelez cette fonction pour annuler la dernière opération de contrôle d’édition.  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pour un contrôle d’édition sur une ligne, la valeur de retour est toujours différent de zéro. Pour un contrôle d’édition de plusieurs lignes, la valeur de retour est différent de zéro si l’opération d’annulation a réussi, ou 0 si l’opération de restauration échoue.  
  
### <a name="remarks"></a>Notes  
 Une opération d’annulation peut également être annulée. Par exemple, vous pouvez restaurer le texte supprimé avec le premier appel à **Annuler**. Tant qu’il n’existe aucune opération de modification intermédiaire, vous pouvez supprimer le texte en utilisant un deuxième appel à **Annuler**.  
  
 Pour plus d’informations, consultez [EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CALCDRIV](../../visual-cpp-samples.md)   
 [MFC exemple CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWnd (classe)](cwnd-class.md)   
 [Classe de CButton](cbutton-class.md)   
 [CComboBox (classe)](ccombobox-class.md)   
 [CListBox (classe)](clistbox-class.md)   
 [Classe de CScrollBar](cscrollbar-class.md)   
 [Classe de CStatic](cstatic-class.md)   
 [CDialog, classe](cdialog-class.md)
