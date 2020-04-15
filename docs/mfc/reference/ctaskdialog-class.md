---
title: CTaskDialog Class
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: e9aeee31d2952d5362c983934ce85f0332f553fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366632"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

Boîte de dialogue contextuelle qui fonctionne comme une boîte de message mais peut afficher des informations supplémentaires pour l'utilisateur. `CTaskDialog` inclut également les fonctionnalités nécessaires pour recueillir des informations auprès de l'utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|Construit un objet `CTaskDialog`.|

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Ajoute un contrôle de `CTaskDialog`bouton de commande à la .|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Ajoute un bouton `CTaskDialog`radio à la .|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Clique sur un contrôle de bouton de commande ou un bouton commun programmatiquement.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Clique sur un bouton radio programmatiquement.|
|[CTaskDialog::DoModal](#domodal)|Affiche la `CTaskDialog`.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Récupère le nombre de boutons courants disponibles.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Convertit un bouton Windows standard au type `CTaskDialog` de bouton commun associé à la classe.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Convertit l’un des types `CTaskDialog` de boutons courants associés à la classe en un bouton Windows standard.|
|[CTaskDialog::GetOptions](#getoptions)|Retourne les drapeaux `CTaskDialog`d’option pour cela .|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Retourne le contrôle de bouton de commande sélectionné.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Retourne le bouton radio sélectionné.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Récupère l’état de la case à cocher de vérification.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Détermine si un contrôle de bouton de commande ou un bouton commun est activé.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Détermine si un bouton radio est activé.|
|[CTaskDialog::IsSupported](#issupported)|Détermine si l’ordinateur qui exécute `CTaskDialog`l’application prend en charge le .|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Ajoute des commandes de bouton de commande en utilisant les données de la table à cordes.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Ajoute des boutons radio en utilisant les données de la table à cordes.|
|[CTaskDialog::NavigateTo](#navigateto)|Transfère l’accent à un autre `CTaskDialog`.|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Le cadre appelle cette méthode lorsque l’utilisateur clique sur un contrôle de bouton de commande.|
|[CTaskDialog::OnCreate](#oncreate)|Le cadre appelle cette méthode `CTaskDialog`après qu’elle crée le .|
|[CTaskDialog::OnDestroy](#ondestroy)|Le cadre appelle cette méthode immédiatement `CTaskDialog`avant qu’elle ne détruise le .|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|Le cadre appelle cette méthode lorsque l’utilisateur clique sur le bouton d’extension.|
|[CTaskDialog::OnHelp](#onhelp)|Le cadre appelle cette méthode lorsque l’utilisateur demande de l’aide.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Le cadre appelle cette méthode lorsque l’utilisateur clique sur un lien hypertexte.|
|[CTaskDialog::OnInit](#oninit)|Le cadre appelle cette `CTaskDialog` méthode lorsque l’est parascé.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Le cadre appelle cette méthode lorsque l’utilisateur déplace `CTaskDialog`l’accent en ce qui concerne les contrôles sur le .|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Le cadre appelle cette méthode lorsque l’utilisateur sélectionne un contrôle de bouton radio.|
|[CTaskDialog::OnTimer](#ontimer)|Le cadre appelle cette méthode lorsque la minuterie expire.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Le cadre appelle cette méthode lorsque l’utilisateur clique sur la case à cocher de vérification.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Supprime tous les contrôles `CTaskDialog`de commande de la .|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Supprime tous les boutons radio `CTaskDialog`de la .|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Mise à jour d’un contrôle de bouton de commande sur le `CTaskDialog`.|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Mise à jour d’un sous-ensemble de boutons communs à activer et nécessitent une élévation UAC.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Ajoute des boutons `CTaskDialog`communs à la .|
|[CTaskDialog::SetContent](#setcontent)|Mises à jour `CTaskDialog`le contenu de la .|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Spécifie le contrôle par défaut du bouton de commande.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Spécifie le bouton radio par défaut.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Ajuste la `CTaskDialog`largeur de la .|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Mises à jour `CTaskDialog`de la zone d’expansion de la .|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Mises à jour de `CTaskDialog`l’icône de pied pour le .|
|[CTaskDialog::SetFooterText](#setfootertext)|Mises à jour du texte `CTaskDialog`sur le pied de la .|
|[CTaskDialog::SetMainIcon](#setmainicon)|Mises à jour `CTaskDialog`de l’icône principale de la .|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Mises à jour `CTaskDialog`de l’instruction principale de la .|
|[CTaskDialog::SetOptions](#setoptions)|Configure les options `CTaskDialog`pour le .|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Configure une barre de `CTaskDialog` chapiteau pour le et l’ajoute à la boîte de dialogue.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ajuste la position de la barre de progression.|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Ajuste la portée de la barre de progression.|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Définit l’état de la barre `CTaskDialog`de progression et l’affiche sur le .|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Permet ou désactive un bouton radio.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Définit l’état coché de la case à cocher de vérification.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Définit le texte sur le côté droit de la case à cocher de vérification.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Définit le titre `CTaskDialog`de la .|
|[CTaskDialog::ShowDialog](#showdialog)|Crée et `CTaskDialog`affiche un .|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|Le cadre appelle cela en réponse à divers messages Windows.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|`m_aButtons`|La gamme de commandes `CTaskDialog`de boutons de commande pour le .|
|`m_aRadioButtons`|La gamme de commandes `CTaskDialog`de bouton radio pour le .|
|`m_bVerified`|`TRUE`indique que la case à cocher de vérification est cochée; `FALSE` indique qu’il ne l’est pas.|
|`m_footerIcon`|L’icône dans le `CTaskDialog`pied de la .|
|`m_hWnd`|Une poignée à la `CTaskDialog`fenêtre pour le .|
|`m_mainIcon`|L’icône principale `CTaskDialog`de la .|
|`m_nButtonDisabled`|Un masque qui indique lequel des boutons courants sont désactivés.|
|`m_nButtonElevation`|Un masque qui indique lequel des boutons courants nécessite l’élévation de l’UAC.|
|`m_nButtonId`|L’ID du contrôle de bouton de commande sélectionné.|
|`m_nCommonButton`|Un masque qui indique quels boutons `CTaskDialog`communs sont affichés sur le .|
|`m_nDefaultCommandControl`|L’ID du bouton de commande `CTaskDialog` qui est sélectionné lorsque l’est affiché.|
|`m_nDefaultRadioButton`|L’ID du bouton radio qui `CTaskDialog` est sélectionné lorsque l’est affiché.|
|`m_nFlags`|Un masque qui indique `CTaskDialog`les options pour le .|
|`m_nProgressPos`|La position actuelle pour la barre de progression.  Cette valeur doit être comprise entre `m_nProgressRangeMin` et `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|La valeur maximale pour la barre de progression.|
|`m_nProgressRangeMin`|La valeur minimale pour la barre de progression.|
|`m_nProgressState`|L’état de la barre de progression. Pour plus d’informations, voir [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|L’ID du contrôle du bouton radio sélectionné.|
|`m_nWidth`|Largeur du `CTaskDialog` en pixels.|
|`m_strCollapse`|La chaîne `CTaskDialog` les écrans à droite de la boîte d’extension lorsque l’information élargie est cachée.|
|`m_strContent`|La chaîne de `CTaskDialog`contenu de la .|
|`m_strExpand`|La chaîne `CTaskDialog` les écrans à droite de la boîte d’extension lorsque l’information élargie est affichée.|
|`m_strFooter`|Le pied de `CTaskDialog`la .|
|`m_strInformation`|L’information élargie `CTaskDialog`pour le .|
|`m_strMainInstruction`|L’instruction principale `CTaskDialog`de la .|
|`m_strTitle`|Titre de la `CTaskDialog`.|
|`m_strVerification`|La chaîne `CTaskDialog` que les écrans à droite de la case à cocher de vérification.|

## <a name="remarks"></a>Notes

La `CTaskDialog` classe remplace la boîte de message Windows standard et dispose de fonctionnalités supplémentaires telles que de nouveaux contrôles pour recueillir des informations auprès de l’utilisateur. Cette classe est dans la bibliothèque MFC à Visual Studio 2010 et plus tard. Le `CTaskDialog` est disponible en commençant par Windows Vista. Les versions antérieures de `CTaskDialog` Windows ne peuvent pas afficher l’objet. Utilisez `CTaskDialog::IsSupported` pour déterminer au moment de l’exécution si l’utilisateur actuel peut afficher la boîte de dialogue de tâches. La boîte de message Windows standard est toujours prise en charge.

Le `CTaskDialog` n’est disponible que lorsque vous construisez votre application en utilisant la bibliothèque Unicode.

Le `CTaskDialog` a deux constructeurs différents. Un constructeur vous permet de spécifier deux boutons de commande et un maximum de six commandes régulières de bouton. Vous pouvez ajouter plus de boutons `CTaskDialog`de commande après avoir créé le . Le deuxième constructeur ne prend en charge aucun bouton de commande, mais vous pouvez ajouter un nombre illimité de commandes régulières de boutons. Pour plus d’informations sur les constructeurs, voir [CTaskDialog::CTaskDialog](#ctaskdialog).

L’image suivante `CTaskDialog` montre un échantillon pour illustrer l’emplacement de certains des contrôles.

![Exemple de CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Exemple de CTaskDialog") <br/>
Échantillon de CTaskDialog

## <a name="requirements"></a>Spécifications

**Système d’exploitation minimum requis :** Windows Vista

**En-tête:** afxtaskdialog.h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a>CTaskDialog::AddCommandControl

Ajoute un nouveau contrôle `CTaskDialog`de bouton de commande à la .

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID (en)*<br/>
[dans] Le numéro d’identification du contrôle de commande.

*strCaption (en)*<br/>
[dans] La chaîne `CTaskDialog` que les affiches à l’utilisateur. Utilisez cette chaîne pour expliquer le but de la commande.

*bEnabled*<br/>
[dans] Un paramètre Boolean qui indique si le nouveau bouton est activé ou désactivé.

*bRequiresElevation (en)*<br/>
[dans] Un paramètre Boolean qui indique si une commande nécessite une élévation.

### <a name="remarks"></a>Notes

Le `CTaskDialog Class` peut afficher un nombre illimité de commandes de boutons de commande. Toutefois, si `CTaskDialog` un bouton de commande affiche des commandes, il peut afficher un maximum de six boutons. Si `CTaskDialog` un n’a pas de commandes de bouton de commande, il peut afficher un nombre illimité de boutons.

Lorsque l’utilisateur sélectionne un contrôle `CTaskDialog` de bouton de commande, le se ferme. Si votre application affiche la boîte de dialogue en utilisant [CTaskDialog::DoModal](#domodal), `DoModal` renvoie le *nCommandControlID* du contrôle de bouton de commande sélectionné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a>CTaskDialog::AddRadioButton

Ajoute un bouton `CTaskDialog`radio à la .

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID (en anglais seulement)*<br/>
[dans] Le numéro d’identification du bouton radio.

*strCaption (en)*<br/>
[dans] La chaîne `CTaskDialog` que les écrans à côté du bouton radio.

*bEnabled*<br/>
[dans] Un paramètre Boolean qui indique si le bouton radio est activé.

### <a name="remarks"></a>Notes

Les boutons radio de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) vous permettent de recueillir des informations auprès de l’utilisateur. Utilisez la fonction [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) pour déterminer quel bouton radio est sélectionné.

Le `CTaskDialog` n’exige pas que les paramètres *nRadioButtonID* sont uniques pour chaque bouton radio. Cependant, vous pouvez éprouver un comportement inattendu si vous n’utilisez pas un identifiant distinct pour chaque bouton radio.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a>CTaskDialog::ClickCommandControl

Clique sur un contrôle de bouton de commande ou un bouton commun programmatiquement.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Paramètres

*nCommandControlID (en)*<br/>
[dans] L’ID de commande du contrôle pour cliquer.

### <a name="remarks"></a>Notes

Cette méthode génère le message Windows TDM_CLICK_BUTTON.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a>CTaskDialog::ClickRadioButton

Clique sur un bouton radio programmatiquement.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID (en anglais seulement)*<br/>
[dans] L’ID du bouton radio pour cliquer.

### <a name="remarks"></a>Notes

Cette méthode génère le message Windows TDM_CLICK_RADIO_BUTTON.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a>CTaskDialog::CTaskDialog

Crée une instance de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Paramètres

*strContent*<br/>
[dans] La chaîne à utiliser pour `CTaskDialog`le contenu de la .

*strMainInstruction*<br/>
[dans] L’instruction principale `CTaskDialog`de la .

*strTitle (strTitle)*<br/>
[dans] Le titre `CTaskDialog`de la .

*nCommonButtons*<br/>
[dans] Un masque des boutons communs à `CTaskDialog`ajouter à la .

*nTaskDialogOptions*<br/>
[dans] L’ensemble d’options `CTaskDialog`à utiliser pour le .

*strFooter (en)*<br/>
[dans] La ficelle à utiliser comme pied.

*nIDCommandControlsFirst*<br/>
[dans] L’ID de chaîne de la première commande.

*nIDCommandControlsLast*<br/>
[dans] L’ID de chaîne de la dernière commande.

### <a name="remarks"></a>Notes

Il y a deux façons `CTaskDialog` d’ajouter un à votre application. La première façon est d’utiliser l’un des constructeurs pour créer un `CTaskDialog` et l’afficher à l’aide de [CTaskDialog::DoModal](#domodal). La deuxième façon est d’utiliser la fonction statique [CTaskDialog::ShowDialog](#showdialog), qui vous permet d’afficher un `CTaskDialog` sans créer explicitement un `CTaskDialog` objet.

Le deuxième constructeur crée des commandes de boutons de commande en utilisant les données du fichier de ressources de votre application. La table de chaîne dans le fichier de ressources a plusieurs chaînes avec des ID de chaîne associés. Cette méthode ajoute un contrôle de bouton de commande pour chaque entrée valide dans la table de chaîne entre *nIDCommandControlsFirst* et *nCommandControlsLast*, inclusivement. Pour ces commandes de bouton de commande, la chaîne dans la table de chaîne est la légende du contrôle et l’ID de la chaîne est l’ID du contrôle.

Voir [CTaskDialog:SetOptions](#setoptions) pour une liste d’options valides.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a>CTaskDialog::DoModal

Montre `CTaskDialog` le et le rend modal.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Paramètres

*hParent*<br/>
[dans] La fenêtre parente pour le `CTaskDialog`.

### <a name="return-value"></a>Valeur de retour

Un intégrant qui correspond à la sélection faite par l’utilisateur.

### <a name="remarks"></a>Notes

Affiche cette instance du [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). L’application attend alors que l’utilisateur ferme la boîte de dialogue.

Le `CTaskDialog` se ferme lorsque l’utilisateur sélectionne un bouton commun, `CTaskDialog`un contrôle de lien de commande, ou ferme le . La valeur de retour est l’identifiant qui indique comment l’utilisateur a fermé la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a>CTaskDialog::GetCommonButtonCount

Récupère le nombre de boutons courants.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de boutons courants disponibles.

### <a name="remarks"></a>Notes

Les boutons communs sont les boutons par défaut que vous fournissez à [CTaskDialog::CTaskDialog](#ctaskdialog). La [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) affiche les boutons le long du bas de la boîte de dialogue.

La liste des boutons énumérés est fournie dans CommCtrl.h.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a>CTaskDialog::GetCommonButtonFlag

Convertit un bouton Windows standard au type de bouton commun associé à la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Paramètres

*nButtonId (en)*<br/>
[dans] La valeur standard du bouton Windows.

### <a name="return-value"></a>Valeur de retour

La valeur du `CTaskDialog` bouton commun correspondant. S’il n’y a pas de bouton commun correspondant, cette méthode renvoie 0.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a>CTaskDialog::GetCommonButtonId

Convertit l’un des types de boutons courants associés à la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) en un bouton Windows standard.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Paramètres

*nFlag*<br/>
[dans] Le type de bouton `CTaskDialog` commun associé à la classe.

### <a name="return-value"></a>Valeur de retour

La valeur du bouton Windows standard correspondant. S’il n’y a pas de bouton Windows correspondant, la méthode renvoie 0.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a>CTaskDialog::GetOptions

Retourne les drapeaux `CTaskDialog`d’option pour cela .

```
int GetOptions() const;
```

### <a name="return-value"></a>Valeur de retour

Les drapeaux `CTaskDialog`pour le .

### <a name="remarks"></a>Notes

Pour plus d’informations sur les options disponibles pour la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md), voir [CTaskDialog::SetOptions](#setoptions).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a>CTaskDialog::GetSelectedCommandControlID

Retourne le contrôle de bouton de commande sélectionné.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Valeur de retour

L’ID du contrôle de bouton de commande actuellement sélectionné.

### <a name="remarks"></a>Notes

Vous n’avez pas besoin d’utiliser cette méthode pour récupérer l’ID du bouton de commande que l’utilisateur a choisi. Cette pièce d’identité est retournée soit par [CTaskDialog::DoModal](#domodal) ou [CTaskDialog::ShowDialog](#showdialog).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a>CTaskDialog::GetSelectedRadioButtonID

Retourne le bouton radio sélectionné.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Valeur de retour

L’ID du bouton radio sélectionné.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette méthode après que l’utilisateur ferme la boîte de dialogue pour récupérer le bouton radio sélectionné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a>CTaskDialog::GetVerificationCheckboxState

Récupère l’état de la case à cocher de vérification.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la case à cocher est cochée, FALSE si elle n’est pas.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a>CTaskDialog::IsCommandControlEnabled

Détermine si un bouton de commande ou un bouton est activé.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Paramètres

*nCommandControlID (en)*<br/>
[dans] L’ID du contrôle ou du bouton de commande pour tester.

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôle est activé, FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette méthode pour déterminer la disponibilité des commandes `CTaskDialog` des boutons de commande et des boutons courants de la Classe.

Si *nCommandControlID* n’est pas un `CTaskDialog` identifiant valide pour un bouton commun ou un contrôle de bouton de commande, cette méthode lance une exception.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a>CTaskDialog::IsRadioButtonEnabled

Détermine si un bouton radio est activé.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID (en anglais seulement)*<br/>
[dans] L’ID du bouton radio à tester.

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton radio est activé, FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

Si *nRadioButtonID* n’est pas un identifiant valide pour un bouton radio, cette méthode jette une exception.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a>CTaskDialog::IsSupported

Détermine si l’ordinateur qui exécute `CTaskDialog`l’application prend en charge le .

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Valeur de retour

VRAI si l’ordinateur prend en charge le `CTaskDialog`; FALSE autrement.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour déterminer au moment de l’exécution si l’ordinateur qui exécute votre application prend en charge la `CTaskDialog` classe. Si l’ordinateur ne `CTaskDialog`prend pas en charge le , vous devez fournir une autre méthode de communication des informations à l’utilisateur. Votre application se plantera si `CTaskDialog` elle essaie d’utiliser `CTaskDialog` un ordinateur sur un ordinateur qui ne prend pas en charge la classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a>CTaskDialog::LoadCommandControls

Ajoute des commandes de bouton de commande en utilisant les données de la table à cordes.

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Paramètres

*nIDCommandControlsFirst*<br/>
[dans] L’ID de chaîne de la première commande.

*nIDCommandControlsLast*<br/>
[dans] L’ID de chaîne de la dernière commande.

### <a name="remarks"></a>Notes

Cette méthode crée des contrôles de bouton de commande en utilisant les données du fichier de ressources de votre application. La table de chaîne dans le fichier de ressources a plusieurs chaînes avec des ID de chaîne associés. Les nouveaux contrôles de bouton de commande ajoutés en utilisant cette méthode utilisent la chaîne pour la légende du contrôle et l’ID de chaîne pour l’ID du contrôle. La gamme de cordes sélectionnées est fournie par *nIDCommandControlsFirst* et *nCommandControlsLast*, inclusivement. S’il y a une entrée vide dans la plage, la méthode n’ajoute pas un contrôle de bouton de commande pour cette entrée.

Par défaut, les nouvelles commandes de boutons de commande sont activées et ne nécessitent pas d’altitude.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a>CTaskDialog::LoadRadioButtons

Ajoute des commandes de bouton radio en utilisant les données de la table de chaîne.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Paramètres

*nIDRadioButtonsFirst*<br/>
[dans] L’ID de chaîne du premier bouton radio.

*nIDRadioButtonsLast*<br/>
[dans] L’ID de chaîne du dernier bouton radio.

### <a name="remarks"></a>Notes

Cette méthode crée des boutons radio en utilisant les données du fichier de ressources de votre application. La table de chaîne dans le fichier de ressources a plusieurs chaînes avec des ID de chaîne associés. Les nouveaux boutons radio ajoutés en utilisant cette méthode utilisent la chaîne pour la légende du bouton radio et l’ID de chaîne pour l’ID du bouton radio. La gamme de cordes sélectionnées est fournie par *nIDRadioButtonsFirst* et *nRadioButtonsLast*, inclusivement. S’il y a une entrée vide dans la plage, la méthode n’ajoute pas un bouton radio pour cette entrée.

Par défaut, de nouveaux boutons radio sont activés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a>CTaskDialog::NavigateTo

Transfère l’accent à un autre `CTaskDialog`.

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Paramètres

*oTaskDialog (en anglais seulement)*<br/>
[dans] Le `CTaskDialog` qui reçoit l’accent.

### <a name="remarks"></a>Notes

Cette méthode cache `CTaskDialog` le courant quand il affiche l’oTaskDialog . *oTaskDialog* *L’oTaskDialog* est affiché au même `CTaskDialog`endroit que le courant .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a>CTaskDialog::OnCommandControlClick

Le cadre appelle cette méthode lorsque l’utilisateur clique sur un contrôle de bouton de commande.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID (en)*<br/>
[dans] L’ID du bouton de commande que l’utilisateur a choisi.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a>CTaskDialog::OnCreate

Le cadre appelle cette méthode `CTaskDialog`après qu’elle crée le .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a>CTaskDialog::OnDestroy

Le cadre appelle cette méthode immédiatement `CTaskDialog`avant qu’elle ne détruise le .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a>CTaskDialog::OnExpandButtonClick

Le cadre appelle cette méthode lorsque l’utilisateur clique sur le bouton d’extension.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Paramètres

*bExpanded*<br/>
[dans] Une valeur non zéro indique que les informations supplémentaires sont affichées; 0 indique que les informations supplémentaires sont cachées.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a>CTaskDialog::OnHelp

Le cadre appelle cette méthode lorsque l’utilisateur demande de l’aide.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a>CTaskDialog::OnHyperlinkClick

Le cadre appelle cette méthode lorsque l’utilisateur clique sur un lien hypertexte.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Paramètres

*strHref*<br/>
[dans] La chaîne qui représente l’hyperlien.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Cette méthode appelle [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) avant qu’elle ne revienne S_OK.

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a>CTaskDialog::OnInit

Le cadre appelle cette `CTaskDialog` méthode lorsque l’est parascé.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a>CTaskDialog::OnNavigatePage

Le cadre appelle cette méthode en réponse à la [méthode CTaskDialog::NavigateTo](#navigateto) méthode.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a>CTaskDialog::OnRadioButtonClick

Le cadre appelle cette méthode lorsque l’utilisateur sélectionne un contrôle de bouton radio.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID (en anglais seulement)*<br/>
[dans] L’ID du bouton radio contrôle que l’utilisateur a cliqué.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a>CTaskDialog::OnTimer

Le cadre appelle cette méthode lorsque la minuterie expire.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Paramètres

*lTime (en)*<br/>
[dans] Temps en millisecondes `CTaskDialog` depuis la création ou la minuterie a été réinitialisée.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a>CTaskDialog::OnVerificationCheckboxClick

Le cadre appelle cette méthode lorsque l’utilisateur clique sur la case à cocher de vérification.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Paramètres

*bChecked*<br/>
[dans] TRUE indique que la case à cocher de vérification est sélectionnée; FALSE indique que ce n’est pas le cas.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre par défaut S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre un comportement personnalisé.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a>CTaskDialog::RemoveAllCommandControls

Supprime toutes les commandes du `CTaskDialog`bouton de commande .

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a>CTaskDialog::RemoveAllRadioButtons

Supprime tous les boutons radio `CTaskDialog`de la .

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a>CTaskDialog::SetCommandControlOptions

Mise à jour d’un contrôle de bouton de commande sur le `CTaskDialog`.

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID (en)*<br/>
[dans] L’ID du contrôle de commande à mettre à jour.

*bEnabled*<br/>
[dans] Un paramètre Boolean qui indique si le contrôle spécifié du bouton de commande est activé ou désactivé.

*bRequiresElevation (en)*<br/>
[dans] Un paramètre Boolean qui indique si le contrôle spécifié du bouton de commande nécessite une élévation.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour changer si un contrôle de bouton de `CTaskDialog` commande est activé ou nécessite l’élévation après qu’il a été ajouté à la classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a>CTaskDialog::SetCommonButtonOptions

Mise à jour d’un sous-ensemble de boutons communs à activer et à exiger l’élévation de l’UAC.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Paramètres

*nDisabledButtonMask*<br/>
[dans] Un masque pour que les boutons communs désactive.

*nElevationButtonMask*<br/>
[dans] Un masque pour les boutons communs qui nécessitent l’élévation.

### <a name="remarks"></a>Notes

Vous pouvez définir les boutons communs disponibles à une instance de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) en utilisant le constructeur [CTaskDialog::CTaskDialog](#ctaskdialog) et la méthode [CTaskDialog::SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions`ne prend pas en charge l’ajout de nouveaux boutons communs.

Si vous utilisez cette méthode pour désactiver ou élever un bouton `CTaskDialog`commun qui n’est pas disponible pour cela, cette méthode jette une exception en utilisant la macro [ENSURE.](diagnostic-services.md#ensure)

Cette méthode permet n’importe `CTaskDialog` quel bouton qui est disponible pour le mais n’est pas dans le *nDisabledButtonMask*, même si elle a déjà été désactivée. Cette méthode traite l’élévation d’une manière similaire: il enregistre les boutons communs comme ne nécessitant pas d’élévation si le bouton commun est disponible, mais pas inclus dans *nElevationButtonMask*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a>CTaskDialog::SetCommonButtons

Ajoute des boutons `CTaskDialog`communs à la .

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Paramètres

*nButtonMask (en)*<br/>
[dans] Un masque des boutons à `CTaskDialog`ajouter à la .

*nDisabledButtonMask*<br/>
[dans] Un masque des boutons à désactiver.

*nElevationButtonMask*<br/>
[dans] Un masque des boutons qui nécessitent une élévation.

### <a name="remarks"></a>Notes

Vous ne pouvez pas appeler cette méthode `CTaskDialog` après la création de la fenêtre d’affichage pour cet exemple de la classe. Si vous le faites, cette méthode jette une exception.

Les boutons indiqués par *nButtonMask* remplacent tous `CTaskDialog`les boutons courants précédemment ajoutés à la . Seuls les boutons indiqués dans *nButtonMask* sont disponibles.

Si *nDisabledButtonMask* ou *nElevationButtonMask* contiennent un bouton qui n’est pas dans *nButtonMask*, cette méthode jette une exception en utilisant la macro [ENSURE.](diagnostic-services.md#ensure)

Par défaut, tous les boutons courants sont activés et ne nécessitent pas d’élévation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a>CTaskDialog::SetContent

Mises à jour `CTaskDialog`le contenu de la .

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Paramètres

*strContent*<br/>
[dans] La chaîne à afficher à l’utilisateur.

### <a name="remarks"></a>Notes

Le contenu `CTaskDialog` de la classe est le texte qui est affiché à l’utilisateur dans la section principale de la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a>CTaskDialog::SetDefaultCommandControl

Spécifie le contrôle par défaut du bouton de commande.

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID (en)*<br/>
[dans] L’ID du contrôle du bouton de commande pour être la valeur par défaut.

### <a name="remarks"></a>Notes

Le contrôle par défaut du bouton de `CTaskDialog` commande est le contrôle qui est sélectionné lorsque l’est affiché pour la première fois à l’utilisateur.

Cette méthode jette une exception si elle ne peut pas trouver le contrôle de bouton de commande spécifié par *nCommandControlID*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a>CTaskDialog::SetDefaultRadioButton

Spécifie le bouton radio par défaut.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID (en anglais seulement)*<br/>
[dans] L’ID du bouton radio pour être la valeur par défaut.

### <a name="remarks"></a>Notes

Le bouton radio par défaut est `CTaskDialog` le bouton qui est sélectionné lorsque le premier est affiché à l’utilisateur.

Cette méthode jette une exception si elle ne peut pas trouver le bouton radio spécifié par *nRadioButtonID*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a>CTaskDialog::SetDialogWidth

Ajuste la `CTaskDialog`largeur de la .

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Paramètres

*nWidth (en)*<br/>
[dans] La largeur de la boîte de dialogue, en pixels.

### <a name="remarks"></a>Notes

Le paramètre *nWidth* doit être supérieur ou égal à 0. Sinon, cette méthode jette une exception.

Si *nWidth* est réglé à 0, cette méthode définit la boîte de dialogue à la taille par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a>CTaskDialog::SetExpansionArea

Mises à jour `CTaskDialog`de la zone d’expansion de la .

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Paramètres

*strExpandedInformation*<br/>
[dans] La chaîne `CTaskDialog` que les écrans dans le corps principal de la boîte de dialogue lorsque l’utilisateur clique sur le bouton d’expansion.

*strCollapsedLabel*<br/>
[dans] La chaîne `CTaskDialog` que les écrans à côté du bouton d’expansion lorsque la zone élargie est effondrée.

*strExpandedLabel*<br/>
[dans] La chaîne `CTaskDialog` que les écrans à côté du bouton d’expansion lorsque la zone élargie est affichée.

### <a name="remarks"></a>Notes

La zone d’expansion de la `CTaskDialog` classe vous permet de fournir des informations supplémentaires à l’utilisateur. La zone d’expansion est `CTaskDialog`dans la partie principale de la , situé immédiatement sous le titre et la chaîne de contenu.

Lorsque `CTaskDialog` l’est affiché pour la première fois, il ne montre pas les informations élargies et met `strCollapsedLabel` à côté du bouton d’expansion. Lorsque l’utilisateur clique sur `CTaskDialog` le bouton d’extension, les affiches *strExpandedInformation* et change l’étiquette en *strExpandedLabel*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a>CTaskDialog::SetFooterIcon

Mises à jour de `CTaskDialog`l’icône de pied de la .

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Paramètres

*hFooterIcon (en)*<br/>
[dans] La nouvelle icône `CTaskDialog`pour le .

*lpszFooterIcon*<br/>
[dans] La nouvelle icône `CTaskDialog`pour le .

### <a name="remarks"></a>Notes

L’icône de pied est affichée sur le bas de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Il peut avoir associé le texte de pied. Vous pouvez modifier le texte du pied avec [CTaskDialog:SetFooterText](#setfootertext).

Cette méthode fait une [ENSURE](diagnostic-services.md#ensure) exception avec `CTaskDialog` la macro ENSURE si le paramètre d’entrée est affiché ou si le paramètre d’entrée est NULL.

A `CTaskDialog` ne peut `HICON` `LPCWSTR` accepter qu’une icône de pied ou comme une icône. Ceci est configuré en définissant l’option TDF_USE_HICON_FOOTER dans le constructeur ou [CTaskDialog:SetOptions](#setoptions). Par défaut, `CTaskDialog` le est `LPCWSTR` configuré pour utiliser comme le type d’entrée pour l’icône de pied. Cette méthode génère une exception si vous essayez de définir l’icône en utilisant le type inapproprié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a>CTaskDialog::SetFooterText

Mises à jour du texte `CTaskDialog`sur le pied de la .

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Paramètres

*strFooterText*<br/>
[dans] Le nouveau texte pour le pied.

### <a name="remarks"></a>Notes

L’icône de pied apparaît à côté du `CTaskDialog`texte de pied sur le fond de la . Vous pouvez changer l’icône de pied avec [CTaskDialog:SetFooterIcon](#setfootericon).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a>CTaskDialog::SetMainIcon

Mises à jour `CTaskDialog`de l’icône principale de la .

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Paramètres

*hMainIcon (en)*<br/>
[dans] La nouvelle icône.

*lpszMainIcon*<br/>
[dans] La nouvelle icône.

### <a name="remarks"></a>Notes

Cette méthode fait une [ENSURE](diagnostic-services.md#ensure) exception avec `CTaskDialog` la macro ENSURE si le paramètre d’entrée est affiché ou si le paramètre d’entrée est NULL.

A `CTaskDialog` ne peut `HICON` `LPCWSTR` accepter qu’une icône principale ou comme une icône principale. Vous pouvez configurer cela en définissant l’option TDF_USE_HICON_MAIN dans le constructeur ou dans le [CTaskDialog: :SetOptions](#setoptions) méthode. Par défaut, `CTaskDialog` le est `LPCWSTR` configuré pour utiliser comme type d’entrée pour l’icône principale. Cette méthode génère une exception si vous essayez de définir l’icône en utilisant le type inapproprié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a>CTaskDialog::SetMainInstruction

Mises à jour `CTaskDialog`de l’instruction principale de la .

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Paramètres

*strInstructions*<br/>
[dans] La nouvelle instruction principale.

### <a name="remarks"></a>Notes

L’instruction principale `CTaskDialog` de la classe est le texte affiché à l’utilisateur dans une grande police audacieuse. Il est situé dans la boîte de dialogue sous la barre de titre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a>CTaskDialog::SetOptions

Configure les options `CTaskDialog`pour le .

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Paramètres

*nOptionFlag (en)*<br/>
[dans] L’ensemble de drapeaux `CTaskDialog`à utiliser pour le .

### <a name="remarks"></a>Notes

Cette méthode efface toutes les `CTaskDialog`options actuelles pour le . Pour préserver les options actuelles, vous devez les récupérer d’abord avec [CTaskDialog: :GetOptions](#getoptions) et les combiner avec les options que vous souhaitez définir.

Le tableau suivant répertorie toutes les options valides.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Permet les hyperliens dans le `CTaskDialog`.|
|TDF_USE_HICON_MAIN|Configure le `CTaskDialog` pour `HICON` utiliser un pour l’icône principale. L’alternative est `LPCWSTR`d’utiliser un .|
|TDF_USE_HICON_FOOTER|Configure le `CTaskDialog` pour `HICON` utiliser un pour l’icône de pied. L’alternative est `LPCWSTR`d’utiliser un .|
|TDF_ALLOW_DIALOG_CANCELLATION|Permet à l’utilisateur de fermer le `CTaskDialog` en utilisant le clavier ou en utilisant l’icône dans le coin supérieur droit de la boîte de dialogue, même si le bouton **Annuler** n’est pas activé. Si ce drapeau n’est pas défini et que le bouton **Annuler** n’est pas activé, l’utilisateur ne peut pas fermer la boîte de dialogue en utilisant Alt-F4, la clé Escape ou le bouton proche de la barre de titre.|
|TDF_USE_COMMAND_LINKS|Configure le `CTaskDialog` bouton de commande pour utiliser.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Configure le `CTaskDialog` pour utiliser les commandes de bouton de commande sans afficher une icône à côté du contrôle. TDF_USE_COMMAND_LINKS l’emporte sur TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Indique que la zone d’expansion est actuellement agrandie.|
|TDF_EXPANDED_BY_DEFAULT|Détermine si la zone d’expansion est agrandie par défaut.|
|TDF_VERIFICATION_FLAG_CHECKED|Indique que la case à cocher de vérification est actuellement sélectionnée.|
|TDF_SHOW_PROGRESS_BAR|Configure le `CTaskDialog` pour afficher une barre de progression.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Configure la barre de progression pour être une barre de progression de chapiteau. Si vous activez cette option, vous devez définir TDF_SHOW_PROGRESS_BAR d’avoir le comportement attendu.|
|TDF_CALLBACK_TIMER|Indique que `CTaskDialog` l’intervalle de rappel est réglé à environ 200 millisecondes.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Configure le `CTaskDialog` centre à centre par rapport à la fenêtre parente. Si ce drapeau n’est pas activé, le `CTaskDialog` est centré par rapport au moniteur.|
|TDF_RTL_LAYOUT|Configure la `CTaskDialog` mise en page pour une lecture de droite à gauche.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Indique qu’aucun bouton radio `CTaskDialog` n’est sélectionné lorsque l’apparaît.|
|TDF_CAN_BE_MINIMIZED|Permet à l’utilisateur de minimiser le `CTaskDialog`. Pour soutenir cette `CTaskDialog` option, le ne peut pas être modal. MFC ne prend pas en charge cette option `CTaskDialog`parce que MFC ne prend pas en charge un modeless .|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a>CTaskDialog::SetProgressBarMarquee

Configure une barre de `CTaskDialog` chapiteau pour le et l’ajoute à la boîte de dialogue.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Paramètres

*bEnabled*<br/>
[dans] VRAI pour permettre la barre de chapiteau; FALSE pour désactiver la barre de chapiteau `CTaskDialog`et l’enlever de la .

*nMarqueeSpeed*<br/>
[dans] Un intégrant qui indique la vitesse de la barre de chapiteau.

### <a name="remarks"></a>Notes

La barre de chapiteau apparaît sous `CTaskDialog` le texte principal de la classe.

Utilisez *nMarqueeSpeed* pour définir la vitesse de la barre de chapiteau; de plus grandes valeurs indiquent une vitesse plus lente. Une valeur de 0 pour *nMarqueeSpeed* fait bouger la barre de chapiteau à la vitesse par défaut de Windows.

Cette méthode jette une exception avec la macro [ENSURE](diagnostic-services.md#ensure) si *nMarqueeSpeed* est inférieur à 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a>CTaskDialog::SetProgressBarPosition

Ajuste la position de la barre de progression.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Paramètres

*nProgressPos*<br/>
[dans] La position de la barre de progression.

### <a name="remarks"></a>Notes

Cette méthode jette une exception avec la macro [ENSURE](diagnostic-services.md#ensure) si *nProgressPos* n’est pas dans la gamme de barres de progression. Vous pouvez modifier la plage de barres de progression avec [CTaskDialog:SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a>CTaskDialog::SetProgressBarRange

Ajuste la portée de la barre de progression.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Paramètres

*nRangeMin (en)*<br/>
[dans] La limite inférieure de la barre de progression.

*nRangeMax (en)*<br/>
[dans] La limite supérieure de la barre de progression.

### <a name="remarks"></a>Notes

La position de la barre de progression est relative à *nRangeMin* et *nRangeMax*. Par exemple, si *nRangeMin* est de 50 et *nRangeMax* est de 100, une position de 75 est à mi-chemin à travers la barre de progression. Utilisez [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) pour définir la position de la barre de progression.

Pour afficher la barre de progression, l’option TDF_SHOW_PROGRESS_BAR doit être activée et TDF_SHOW_MARQUEE_PROGRESS_BAR ne doit pas être activée. Cette méthode définit automatiquement TDF_SHOW_PROGRESS_BAR et efface TDF_SHOW_MARQUEE_PROGRESS_BAR. Utilisez [CTaskDialog::SetOptions](#setoptions) pour modifier manuellement les options pour cette instance de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Cette méthode jette une exception avec la macro [ENSURE](diagnostic-services.md#ensure) si *nRangeMin* n’est pas moins de *nRangeMax*. Cette méthode jette également une `CTaskDialog` exception si l’est déjà affiché et a une barre de progression de chapiteau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a>CTaskDialog::SetProgressBarState

Définit l’état de la barre `CTaskDialog`de progression et l’affiche sur le .

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Paramètres

*nState (États-Unis)*<br/>
[dans] L’état de la barre de progression. Voir la section Remarques pour les valeurs possibles.

### <a name="remarks"></a>Notes

Cette méthode jette une [ENSURE](diagnostic-services.md#ensure) exception avec `CTaskDialog` la macro ENSURE si le est déjà affiché et a une barre de progression de chapiteau.

Le tableau suivant énumère les valeurs possibles pour *nState*. Dans tous ces cas, la barre de progression se remplira de la couleur régulière jusqu’à ce qu’elle atteigne la position d’arrêt désignée. À ce stade, il va changer de couleur en fonction de l’état.

|||
|-|-|
|PBST_NORMAL|Après la barre de `CTaskDialog` progression se remplit, le ne change pas la couleur de la barre. Par défaut, la couleur régulière est verte.|
|PBST_ERROR|Après la barre de `CTaskDialog` progression se remplit, les changements de la couleur de la barre à la couleur d’erreur. Par défaut, c’est rouge.|
|PBST_PAUSED|Après la barre de `CTaskDialog` progression se remplit, les changements de la couleur de la barre à la couleur en pause. Par défaut, c’est jaune.|

Vous pouvez définir où la barre de progression s’arrête avec [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a>CTaskDialog::SetRadioButtonOptions

Permet ou désactive un bouton radio.

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID (en anglais seulement)*<br/>
[dans] L’ID du contrôle du bouton radio.

*bEnabled*<br/>
[dans] VRAI pour activer le bouton radio; FALSE pour désactiver le bouton radio.

### <a name="remarks"></a>Notes

Cette méthode jette une exception avec la macro [ENSURE](diagnostic-services.md#ensure) si *nRadioButtonID* n’est pas un ID valide pour un bouton radio.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a>CTaskDialog::SetVerificationCheckbox

Définit l’état coché de la case à cocher de vérification.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Paramètres

*bChecked*<br/>
[dans] VRAI d’avoir la case `CTaskDialog` à cocher de vérification sélectionnée lorsque l’affichage est affiché; FALSE d’avoir la case à cocher de vérification non sélectionnée lorsque l’est `CTaskDialog` affiché.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a>CTaskDialog::SetVerificationCheckboxText

Définit le texte qui s’affiche à droite de la case à cocher de vérification.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Paramètres

*strVerificationText*<br/>
[dans] Le texte que cette méthode affiche à côté de la case à cocher de vérification.

### <a name="remarks"></a>Notes

Cette méthode jette une [ENSURE](diagnostic-services.md#ensure) exception avec la macro `CTaskDialog` ENSURE si cette instance de la classe est déjà affichée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a>CTaskDialog::SetWindowTitle

Définit le titre `CTaskDialog`de la .

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Paramètres

*strWindowTitle (en)*<br/>
[dans] Le nouveau titre `CTaskDialog`pour le .

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a>CTaskDialog::ShowDialog

Crée et `CTaskDialog`affiche un .

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Paramètres

*strContent*<br/>
[dans] La chaîne à utiliser pour `CTaskDialog`le contenu de la .

*strMainInstruction*<br/>
[dans] L’instruction principale `CTaskDialog`de la .

*strTitle (strTitle)*<br/>
[dans] Le titre `CTaskDialog`de la .

*nIDCommandControlsFirst*<br/>
[dans] L’ID de chaîne de la première commande.

*nIDCommandControlsLast*<br/>
[dans] L’ID de chaîne de la dernière commande.

*nCommonButtons*<br/>
[dans] Un masque des boutons à `CTaskDialog`ajouter à la .

*nTaskDialogOptions*<br/>
[dans] L’ensemble d’options `CTaskDialog`à utiliser pour le .

*strFooter (en)*<br/>
[dans] La ficelle à utiliser comme pied.

### <a name="return-value"></a>Valeur de retour

Un intégrant qui correspond à la sélection faite par l’utilisateur.

### <a name="remarks"></a>Notes

Cette méthode statique vous permet de `CTaskDialog` créer une `CTaskDialog` instance de la classe sans créer explicitement un objet dans votre code. Parce qu’il n’y a pas `CTaskDialog` `CTaskDialog` d’objet, vous ne `CTaskDialog` pouvez pas appeler d’autres méthodes de la si vous utilisez cette méthode pour montrer un à l’utilisateur.

Cette méthode crée des contrôles de bouton de commande en utilisant les données du fichier de ressources de votre application. La table de chaîne dans le fichier de ressources a plusieurs chaînes avec des ID de chaîne associés. Cette méthode ajoute un contrôle de bouton de commande pour chaque entrée valide dans la table de chaîne entre *nIDCommandControlsFirst* et *nCommandControlsLast*, inclusivement. Pour ces commandes de bouton de commande, la chaîne dans la table de chaîne est la légende du contrôle et l’ID de la chaîne est l’ID du contrôle.

Voir [CTaskDialog:SetOptions](#setoptions) pour une liste d’options valides.

Le `CTaskDialog` se ferme lorsque l’utilisateur sélectionne un bouton commun, `CTaskDialog`un contrôle de lien de commande, ou ferme le . La valeur de retour est l’identifiant qui indique comment l’utilisateur a fermé la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a>CTaskDialog::TaskDialogCallback

Le cadre appelle cette méthode en réponse à divers messages Windows.

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>Paramètres

*Hwnd*<br/>
[dans] Une poignée `m_hWnd` à la `CTaskDialog`structure pour le .

*uNotification*<br/>
[dans] Le code de notification qui spécifie le message généré.

*wParam*<br/>
[dans] Plus d’informations sur le message.

*lParam*<br/>
[dans] Plus d’informations sur le message.

*dwRefData*<br/>
[dans] Un pointeur `CTaskDialog` sur l’objet à qui le message de rappel s’applique.

### <a name="return-value"></a>Valeur de retour

Dépend du code de notification spécifique. Pour plus d'informations, consultez la section Remarques.

### <a name="remarks"></a>Notes

La mise `TaskDialogCallback` en œuvre par défaut de gère le message spécifique, puis appelle la méthode appropriée On de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Par exemple, en réponse au message `TaskDialogCallback` TDN_BUTTON_CLICKED, appelle [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).

Les valeurs de *wParam* et *lParam* dépendent du message généré spécifique. Il est possible que l’une ou l’autre de ces valeurs soit vide. Le tableau suivant répertorie les notifications par défaut qui sont prises en charge et ce que représentent les valeurs de *wParam* et *lParam.* Si vous remplacez cette méthode dans une classe dérivée, vous devez implémenter le code de rappel pour chaque message dans le tableau suivant.

|Notification Message|*wParam (en)* Valeur|*lParam (en)* Valeur|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Non utilisé.|Non utilisé.|
|TDN_NAVIGATED|Non utilisé.|Non utilisé.|
|TDN_BUTTON_CLICKED|L’ID de commande de commande.|Non utilisé.|
|TDN_HYPERLINK_CLICKED|Non utilisé.|Une structure [LPCWSTR](/windows/win32/WinProg/windows-data-types) qui contient le lien.|
|TDN_TIMER|Temps en millisecondes `CTaskDialog` depuis la création ou la minuterie a été réinitialisée.|Non utilisé.|
|TDN_DESTROYED|Non utilisé.|Non utilisé.|
|TDN_RADIO_BUTTON_CLICKED|L’ID du bouton radio.|Non utilisé.|
|TDN_DIALOG_CONSTRUCTED|Non utilisé.|Non utilisé.|
|TDN_VERIFICATION_CLICKED|1 si la case à cocher est cochée, 0 si elle n’est pas.|Non utilisé.|
|TDN_HELP|Non utilisé.|Non utilisé.|
|TDN_EXPANDO_BUTTON_CLICKED|0 si la zone d’expansion est effondrée; nonzero si le texte d’extension est affiché.|Non utilisé.|

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Procédure pas à pas : ajout d’une classe CTaskDialog à une application](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
