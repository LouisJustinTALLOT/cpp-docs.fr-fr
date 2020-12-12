---
description: 'En savoir plus sur : classe CTaskDialog'
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
ms.openlocfilehash: 91cd3caec703f8e81116fccd75c0457abb69a3e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318583"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

Boîte de dialogue contextuelle qui fonctionne comme une boîte de message mais peut afficher des informations supplémentaires pour l'utilisateur. `CTaskDialog` inclut également les fonctionnalités nécessaires pour recueillir des informations auprès de l'utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[CTaskDialog :: CTaskDialog](#ctaskdialog)|Construit un objet `CTaskDialog`.|

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[CTaskDialog :: AddCommandControl](#addcommandcontrol)|Ajoute un contrôle de bouton de commande au `CTaskDialog` .|
|[CTaskDialog :: AddRadioButton](#addradiobutton)|Ajoute une case d’option à `CTaskDialog` .|
|[CTaskDialog :: ClickCommandControl](#clickcommandcontrol)|Clique sur un contrôle de bouton de commande ou un bouton commun par programmation.|
|[CTaskDialog :: ClickRadioButton](#clickradiobutton)|Clique sur une case d’option par programmation.|
|[CTaskDialog ::D oModal](#domodal)|Affiche la `CTaskDialog`.|
|[CTaskDialog :: GetCommonButtonCount](#getcommonbuttoncount)|Récupère le nombre de boutons courants disponibles.|
|[CTaskDialog :: GetCommonButtonFlag](#getcommonbuttonflag)|Convertit un bouton Windows standard en un type de bouton commun associé à la `CTaskDialog` classe.|
|[CTaskDialog :: GetCommonButtonId](#getcommonbuttonid)|Convertit l’un des types de boutons courants associés à la `CTaskDialog` classe en un bouton Windows standard.|
|[CTaskDialog :: GetOptions](#getoptions)|Retourne les indicateurs d’option pour ce `CTaskDialog` .|
|[CTaskDialog :: GetSelectedCommandControlID](#getselectedcommandcontrolid)|Retourne le contrôle de bouton de commande sélectionné.|
|[CTaskDialog :: GetSelectedRadioButtonID](#getselectedradiobuttonid)|Retourne la case d’option sélectionnée.|
|[CTaskDialog :: GetVerificationCheckboxState](#getverificationcheckboxstate)|Récupère l’état de la case à cocher vérification.|
|[CTaskDialog :: IsCommandControlEnabled](#iscommandcontrolenabled)|Détermine si un contrôle de bouton de commande ou un bouton commun est activé.|
|[CTaskDialog :: IsRadioButtonEnabled](#isradiobuttonenabled)|Détermine si une case d’option est activée.|
|[CTaskDialog :: IsSupported](#issupported)|Détermine si l’ordinateur qui exécute l’application prend en charge `CTaskDialog` .|
|[CTaskDialog :: LoadCommandControls](#loadcommandcontrols)|Ajoute des contrôles de bouton de commande à l’aide des données de la table de chaînes.|
|[CTaskDialog :: LoadRadioButtons](#loadradiobuttons)|Ajoute des cases d’option à l’aide des données de la table de chaînes.|
|[CTaskDialog :: NavigateTo](#navigateto)|Transfère le focus vers un autre `CTaskDialog` .|
|[CTaskDialog :: OnCommandControlClick](#oncommandcontrolclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un contrôle de bouton de commande.|
|[CTaskDialog :: OnCreate](#oncreate)|L’infrastructure appelle cette méthode après avoir créé le `CTaskDialog` .|
|[CTaskDialog :: OnDestroy](#ondestroy)|L’infrastructure appelle cette méthode immédiatement avant de détruire le `CTaskDialog` .|
|[CTaskDialog :: OnExpandButtonClick](#onexpandbuttonclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur le bouton d’expansion.|
|[CTaskDialog :: OnHelp](#onhelp)|L’infrastructure appelle cette méthode lorsque l’utilisateur demande de l’aide.|
|[CTaskDialog :: OnHyperlinkClick](#onhyperlinkclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un lien hypertexte.|
|[CTaskDialog :: OnInit](#oninit)|L’infrastructure appelle cette méthode lorsque le `CTaskDialog` est initialisé.|
|[CTaskDialog :: OnNavigatePage](#onnavigatepage)|L’infrastructure appelle cette méthode lorsque l’utilisateur déplace le focus sur les contrôles sur le `CTaskDialog` .|
|[CTaskDialog :: OnRadioButtonClick](#onradiobuttonclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur sélectionne un contrôle de case d’option.|
|[CTaskDialog :: OnTimer](#ontimer)|L’infrastructure appelle cette méthode lorsque le minuteur expire.|
|[CTaskDialog :: OnVerificationCheckboxClick](#onverificationcheckboxclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur la case à cocher vérification.|
|[CTaskDialog :: RemoveAllCommandControls](#removeallcommandcontrols)|Supprime tous les contrôles de commande de `CTaskDialog` .|
|[CTaskDialog :: RemoveAllRadioButtons](#removeallradiobuttons)|Supprime toutes les cases d’option du `CTaskDialog` .|
|[CTaskDialog :: SetCommandControlOptions](#setcommandcontroloptions)|Met à jour un contrôle de bouton de commande sur `CTaskDialog` .|
|[CTaskDialog :: SetCommonButtonOptions](#setcommonbuttonoptions)|Met à jour un sous-ensemble de boutons courants à activer et nécessitant une élévation UAC.|
|[CTaskDialog :: SetCommonButtons](#setcommonbuttons)|Ajoute des boutons courants à `CTaskDialog` .|
|[CTaskDialog :: SetContent](#setcontent)|Met à jour le contenu du `CTaskDialog` .|
|[CTaskDialog :: SetDefaultCommandControl](#setdefaultcommandcontrol)|Spécifie le contrôle de bouton de commande par défaut.|
|[CTaskDialog :: SetDefaultRadioButton](#setdefaultradiobutton)|Spécifie la case d’option par défaut.|
|[CTaskDialog :: SetDialogWidth](#setdialogwidth)|Ajuste la largeur du `CTaskDialog` .|
|[CTaskDialog :: SetExpansionArea](#setexpansionarea)|Met à jour la zone d’expansion du `CTaskDialog` .|
|[CTaskDialog :: SetFooterIcon](#setfootericon)|Met à jour l’icône de pied de page pour le `CTaskDialog` .|
|[CTaskDialog :: SetFooterText](#setfootertext)|Met à jour le texte sur le pied de page du `CTaskDialog` .|
|[CTaskDialog :: SetMainIcon](#setmainicon)|Met à jour l’icône principale de `CTaskDialog` .|
|[CTaskDialog :: SetMainInstruction](#setmaininstruction)|Met à jour l’instruction principale de `CTaskDialog` .|
|[CTaskDialog :: SetOptions](#setoptions)|Configure les options de `CTaskDialog` .|
|[CTaskDialog :: SetProgressBarMarquee](#setprogressbarmarquee)|Configure une barre de texte défilant pour le `CTaskDialog` et l’ajoute à la boîte de dialogue.|
|[CTaskDialog :: SetProgressBarPosition](#setprogressbarposition)|Ajuste la position de la barre de progression.|
|[CTaskDialog :: SetProgressBarRange](#setprogressbarrange)|Ajuste la plage de la barre de progression.|
|[CTaskDialog :: SetProgressBarState](#setprogressbarstate)|Définit l’état de la barre de progression et l’affiche sur le `CTaskDialog` .|
|[CTaskDialog :: SetRadioButtonOptions](#setradiobuttonoptions)|Active ou désactive une case d’option.|
|[CTaskDialog :: SetVerificationCheckbox](#setverificationcheckbox)|Définit l’état activé de la case à cocher vérification.|
|[CTaskDialog :: SetVerificationCheckboxText](#setverificationcheckboxtext)|Définit le texte sur le côté droit de la case à cocher vérification.|
|[CTaskDialog :: SetWindowTitle](#setwindowtitle)|Définit le titre de `CTaskDialog` .|
|[CTaskDialog :: ShowDialog](#showdialog)|Crée et affiche un `CTaskDialog` .|
|[CTaskDialog :: TaskDialogCallback](#taskdialogcallback)|L’infrastructure l’appelle en réponse à différents messages Windows.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|-|-|
|`m_aButtons`|Tableau de contrôles de bouton de commande pour `CTaskDialog` .|
|`m_aRadioButtons`|Tableau de contrôles de cases d’option pour `CTaskDialog` .|
|`m_bVerified`|`TRUE` indique que la case à cocher vérification est activée ; `FALSE` indique qu’il ne l’est pas.|
|`m_footerIcon`|Icône dans le pied de page du `CTaskDialog` .|
|`m_hWnd`|Handle de la fenêtre pour le `CTaskDialog` .|
|`m_mainIcon`|Icône principale de `CTaskDialog` .|
|`m_nButtonDisabled`|Masque qui indique les boutons les plus courants qui sont désactivés.|
|`m_nButtonElevation`|Masque qui indique les boutons courants qui requièrent l’élévation du contrôle de compte d’utilisateur.|
|`m_nButtonId`|ID du contrôle de bouton de commande sélectionné.|
|`m_nCommonButton`|Masque qui indique les boutons courants qui sont affichés sur le `CTaskDialog` .|
|`m_nDefaultCommandControl`|ID du contrôle de bouton de commande qui est sélectionné lorsque `CTaskDialog` est affiché.|
|`m_nDefaultRadioButton`|ID du contrôle de case d’option qui est sélectionné lorsque le `CTaskDialog` est affiché.|
|`m_nFlags`|Masque qui indique les options de `CTaskDialog` .|
|`m_nProgressPos`|Position actuelle de la barre de progression.  Cette valeur doit être comprise entre `m_nProgressRangeMin` et `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|Valeur maximale de la barre de progression.|
|`m_nProgressRangeMin`|Valeur minimale de la barre de progression.|
|`m_nProgressState`|État de la barre de progression. Pour plus d’informations, consultez [CTaskDialog :: SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|ID du contrôle de case d’option sélectionné.|
|`m_nWidth`|Largeur du `CTaskDialog` en pixels.|
|`m_strCollapse`|Chaîne `CTaskDialog` affichée à droite de la zone d’expansion lorsque les informations développées sont masquées.|
|`m_strContent`|Chaîne de contenu du `CTaskDialog` .|
|`m_strExpand`|Chaîne `CTaskDialog` qui s’affiche à droite de la zone d’expansion lorsque les informations développées sont affichées.|
|`m_strFooter`|Pied de page du `CTaskDialog` .|
|`m_strInformation`|Informations développées pour le `CTaskDialog` .|
|`m_strMainInstruction`|Instruction principale de `CTaskDialog` .|
|`m_strTitle`|Titre de la `CTaskDialog`.|
|`m_strVerification`|Chaîne que le `CTaskDialog` affiche à droite de la case à cocher de vérification.|

## <a name="remarks"></a>Notes

La `CTaskDialog` classe remplace la boîte de message Windows standard et possède des fonctionnalités supplémentaires telles que de nouveaux contrôles pour recueillir des informations auprès de l’utilisateur. Cette classe se trouve dans la bibliothèque MFC dans Visual Studio 2010 et versions ultérieures. Le `CTaskDialog` est disponible à partir de Windows Vista. Les versions antérieures de Windows ne peuvent pas afficher l' `CTaskDialog` objet. Utilisez `CTaskDialog::IsSupported` pour déterminer au moment de l’exécution si l’utilisateur actuel peut afficher la boîte de dialogue de tâches. La boîte de message Windows standard est toujours prise en charge.

La `CTaskDialog` est disponible uniquement lorsque vous générez votre application à l’aide de la bibliothèque Unicode.

Le `CTaskDialog` a deux constructeurs différents. Un constructeur vous permet de spécifier deux boutons de commande et un maximum de six contrôles de bouton standard. Vous pouvez ajouter d’autres boutons de commande après avoir créé le `CTaskDialog` . Le deuxième constructeur ne prend pas en charge les boutons de commande, mais vous pouvez ajouter un nombre illimité de contrôles de bouton standard. Pour plus d’informations sur les constructeurs, consultez [CTaskDialog :: CTaskDialog](#ctaskdialog).

L’illustration suivante montre un exemple `CTaskDialog` illustrant l’emplacement de certains contrôles.

![Exemple de CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Exemple de CTaskDialog") <br/>
Exemple CTaskDialog

## <a name="requirements"></a>Spécifications

**Système d’exploitation minimal requis :** Windows Vista

**En-tête :** afxtaskdialog. h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a> CTaskDialog :: AddCommandControl

Ajoute un nouveau contrôle de bouton de commande au `CTaskDialog` .

```cpp
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID*<br/>
dans Numéro d’identification du contrôle de commande.

*strCaption*<br/>
dans Chaîne que le `CTaskDialog` affiche à l’utilisateur. Utilisez cette chaîne pour expliquer l’objectif de la commande.

*bEnabled*<br/>
dans Paramètre booléen qui indique si le bouton nouveau est activé ou désactivé.

*bRequiresElevation*<br/>
dans Paramètre booléen qui indique si une commande requiert une élévation.

### <a name="remarks"></a>Notes

`CTaskDialog Class`Peut afficher un nombre illimité de contrôles de bouton de commande. Toutefois, si un `CTaskDialog` affiche des contrôles de bouton de commande, il peut afficher six boutons au maximum. Si un n' `CTaskDialog` a pas de contrôle de bouton de commande, il peut afficher un nombre illimité de boutons.

Lorsque l’utilisateur sélectionne un contrôle de bouton de commande, le `CTaskDialog` se ferme. Si votre application affiche la boîte de dialogue à l’aide de [CTaskDialog ::D omodal](#domodal), `DoModal` retourne le *nCommandControlID* du contrôle de bouton de commande sélectionné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a> CTaskDialog :: AddRadioButton

Ajoute une case d’option à `CTaskDialog` .

```cpp
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID*<br/>
dans Numéro d’identification de la case d’option.

*strCaption*<br/>
dans Chaîne `CTaskDialog` affichée à côté de la case d’option.

*bEnabled*<br/>
dans Paramètre booléen qui indique si la case d’option est activée.

### <a name="remarks"></a>Notes

Les cases d’option de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) vous permettent de recueillir des informations auprès de l’utilisateur. Utilisez la fonction [CTaskDialog :: GetSelectedRadioButtonID](#getselectedradiobuttonid) pour déterminer la case d’option qui est sélectionnée.

`CTaskDialog`Ne requiert pas que les paramètres *nRadioButtonID* soient uniques pour chaque case d’option. Toutefois, vous pouvez constater un comportement inattendu si vous n’utilisez pas d’identificateur distinct pour chaque case d’option.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a> CTaskDialog :: ClickCommandControl

Clique sur un contrôle de bouton de commande ou un bouton commun par programmation.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Paramètres

*nCommandControlID*<br/>
dans ID de commande du contrôle à cliquer.

### <a name="remarks"></a>Notes

Cette méthode génère le TDM_CLICK_BUTTON de message Windows.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a> CTaskDialog :: ClickRadioButton

Clique sur une case d’option par programmation.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID*<br/>
dans ID de la case d’option à cliquer.

### <a name="remarks"></a>Notes

Cette méthode génère le TDM_CLICK_RADIO_BUTTON de message Windows.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a> CTaskDialog :: CTaskDialog

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
dans Chaîne à utiliser pour le contenu du `CTaskDialog` .

*strMainInstruction*<br/>
dans Instruction principale de `CTaskDialog` .

*strTitle*<br/>
dans Titre du `CTaskDialog` .

*nCommonButtons*<br/>
dans Masque des boutons courants à ajouter à `CTaskDialog` .

*nTaskDialogOptions*<br/>
dans Ensemble d’options à utiliser pour `CTaskDialog` .

*strFooter*<br/>
dans Chaîne à utiliser en tant que pied de page.

*nIDCommandControlsFirst*<br/>
dans ID de chaîne de la première commande.

*nIDCommandControlsLast*<br/>
dans ID de chaîne de la dernière commande.

### <a name="remarks"></a>Notes

Vous pouvez ajouter un `CTaskDialog` à votre application de deux manières. La première consiste à utiliser l’un des constructeurs pour créer un `CTaskDialog` et l’afficher à l’aide de [CTaskDialog ::D omodal](#domodal). La seconde consiste à utiliser la fonction statique [CTaskDialog :: ShowDialog](#showdialog), qui vous permet d’afficher un `CTaskDialog` sans créer explicitement un `CTaskDialog` objet.

Le deuxième constructeur crée des contrôles de bouton de commande en utilisant les données du fichier de ressources de votre application. La table de chaînes du fichier de ressources contient plusieurs chaînes avec des ID de chaîne associés. Cette méthode ajoute un contrôle de bouton de commande pour chaque entrée valide dans la table de chaînes entre *nIDCommandControlsFirst* et *nCommandControlsLast*, inclus. Pour ces contrôles de bouton de commande, la chaîne dans la table de chaînes est la légende du contrôle et l’ID de chaîne est l’ID du contrôle.

Pour obtenir la liste des options valides, consultez [CTaskDialog :: SetOptions](#setoptions) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a> CTaskDialog ::D oModal

Affiche `CTaskDialog` et le rend modal.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Paramètres

*hParent*<br/>
dans Fenêtre parente de `CTaskDialog` .

### <a name="return-value"></a>Valeur renvoyée

Entier qui correspond à la sélection effectuée par l’utilisateur.

### <a name="remarks"></a>Notes

Affiche cette instance du [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). L’application attend ensuite que l’utilisateur ferme la boîte de dialogue.

`CTaskDialog`Se ferme lorsque l’utilisateur sélectionne un bouton commun, un contrôle de lien de commande ou ferme le `CTaskDialog` . La valeur de retour est l’identificateur qui indique la façon dont l’utilisateur a fermé la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a> CTaskDialog :: GetCommonButtonCount

Récupère le nombre de boutons courants.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de boutons courants disponibles.

### <a name="remarks"></a>Notes

Les boutons courants sont les boutons par défaut que vous fournissez à [CTaskDialog :: CTaskDialog](#ctaskdialog). La [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) affiche les boutons situés en bas de la boîte de dialogue.

La liste énumérée des boutons est fournie dans CommCtrl. h.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a> CTaskDialog :: GetCommonButtonFlag

Convertit un bouton Windows standard en un type de bouton commun associé à la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Paramètres

*nButtonId*<br/>
dans Valeur du bouton Windows standard.

### <a name="return-value"></a>Valeur renvoyée

Valeur du `CTaskDialog` bouton commun correspondant. S’il n’existe aucun bouton commun correspondant, cette méthode retourne 0.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a> CTaskDialog :: GetCommonButtonId

Convertit l’un des types de boutons courants associés à la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) en un bouton Windows standard.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Paramètres

*Tous*<br/>
dans Type de bouton commun associé à la `CTaskDialog` classe.

### <a name="return-value"></a>Valeur renvoyée

Valeur du bouton Windows standard correspondant. S’il n’existe aucun bouton Windows correspondant, la méthode retourne 0.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a> CTaskDialog :: GetOptions

Retourne les indicateurs d’option pour ce `CTaskDialog` .

```
int GetOptions() const;
```

### <a name="return-value"></a>Valeur renvoyée

Indicateurs de `CTaskDialog` .

### <a name="remarks"></a>Notes

Pour plus d’informations sur les options disponibles pour la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md), consultez [CTaskDialog :: SetOptions](#setoptions).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a> CTaskDialog :: GetSelectedCommandControlID

Retourne le contrôle de bouton de commande sélectionné.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Valeur renvoyée

ID du contrôle de bouton de commande actuellement sélectionné.

### <a name="remarks"></a>Notes

Vous n’avez pas besoin d’utiliser cette méthode pour récupérer l’ID du bouton de commande que l’utilisateur a sélectionné. Cet ID est retourné par [CTaskDialog ::D omodal](#domodal) ou [CTaskDialog :: ShowDialog](#showdialog).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a> CTaskDialog :: GetSelectedRadioButtonID

Retourne la case d’option sélectionnée.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Valeur renvoyée

ID de la case d’option sélectionnée.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette méthode une fois que l’utilisateur a fermé la boîte de dialogue pour récupérer la case d’option sélectionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a> CTaskDialog :: GetVerificationCheckboxState

Récupère l’état de la case à cocher vérification.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la case à cocher est activée, FALSe dans le cas contraire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a> CTaskDialog :: IsCommandControlEnabled

Détermine si un contrôle ou un bouton de bouton de commande est activé.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Paramètres

*nCommandControlID*<br/>
dans ID du contrôle de bouton de commande ou du bouton à tester.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le contrôle est activé, FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette méthode pour déterminer la disponibilité des deux contrôles de bouton de commande et des boutons courants de la `CTaskDialog` classe *.

Si *nCommandControlID* n’est pas un identificateur valide pour un bouton courant `CTaskDialog` ou un contrôle de bouton de commande, cette méthode lève une exception.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a> CTaskDialog :: IsRadioButtonEnabled

Détermine si une case d’option est activée.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID*<br/>
dans ID de la case d’option à tester.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la case d’option est activée, FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Si *nRadioButtonID* n’est pas un identificateur valide pour une case d’option, cette méthode lève une exception.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a> CTaskDialog :: IsSupported

Détermine si l’ordinateur qui exécute l’application prend en charge `CTaskDialog` .

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’ordinateur prend en charge le `CTaskDialog` ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour déterminer au moment de l’exécution si l’ordinateur qui exécute votre application prend en charge la `CTaskDialog` classe. Si l’ordinateur ne prend pas en charge le `CTaskDialog` , vous devez fournir une autre méthode de communication des informations à l’utilisateur. Votre application se bloque si elle tente d’utiliser un `CTaskDialog` sur un ordinateur qui ne prend pas en charge la `CTaskDialog` classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a> CTaskDialog :: LoadCommandControls

Ajoute des contrôles de bouton de commande à l’aide des données de la table de chaînes.

```cpp
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Paramètres

*nIDCommandControlsFirst*<br/>
dans ID de chaîne de la première commande.

*nIDCommandControlsLast*<br/>
dans ID de chaîne de la dernière commande.

### <a name="remarks"></a>Notes

Cette méthode crée des contrôles de bouton de commande en utilisant les données du fichier de ressources de votre application. La table de chaînes du fichier de ressources contient plusieurs chaînes avec des ID de chaîne associés. Les nouveaux contrôles de bouton de commande ajoutés à l’aide de cette méthode utilisent la chaîne pour la légende du contrôle et l’ID de chaîne de l’ID du contrôle. La plage de chaînes sélectionnée est fournie par *nIDCommandControlsFirst* et *nCommandControlsLast*, inclus. S’il existe une entrée vide dans la plage, la méthode n’ajoute pas de contrôle de bouton de commande pour cette entrée.

Par défaut, les nouveaux contrôles de bouton de commande sont activés et ne nécessitent pas d’élévation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a> CTaskDialog :: LoadRadioButtons

Ajoute des contrôles de case d’option à l’aide des données de la table de chaînes.

```cpp
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Paramètres

*nIDRadioButtonsFirst*<br/>
dans ID de chaîne de la première case d’option.

*nIDRadioButtonsLast*<br/>
dans ID de chaîne de la dernière case d’option.

### <a name="remarks"></a>Notes

Cette méthode crée des cases d’option à l’aide des données du fichier de ressources de votre application. La table de chaînes du fichier de ressources contient plusieurs chaînes avec des ID de chaîne associés. Les nouvelles cases d’option ajoutées à l’aide de cette méthode utilisent la chaîne pour la légende de la case d’option et l’ID de chaîne de l’ID de la case d’option. La plage de chaînes sélectionnée est fournie par *nIDRadioButtonsFirst* et *nRadioButtonsLast*, inclus. S’il existe une entrée vide dans la plage, la méthode n’ajoute pas de case d’option pour cette entrée.

Par défaut, les nouvelles cases d’option sont activées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a> CTaskDialog :: NavigateTo

Transfère le focus vers un autre `CTaskDialog` .

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Paramètres

*oTaskDialog*<br/>
dans `CTaskDialog` Qui reçoit le focus.

### <a name="remarks"></a>Notes

Cette méthode masque le actuel `CTaskDialog` lorsqu’il affiche *oTaskDialog*. Le *oTaskDialog* est affiché dans le même emplacement que le actuel `CTaskDialog` .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a> CTaskDialog :: OnCommandControlClick

L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un contrôle de bouton de commande.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID*<br/>
dans ID du contrôle de bouton de commande que l’utilisateur a sélectionné.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a> CTaskDialog :: OnCreate

L’infrastructure appelle cette méthode après avoir créé le `CTaskDialog` .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a> CTaskDialog :: OnDestroy

L’infrastructure appelle cette méthode immédiatement avant de détruire le `CTaskDialog` .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a> CTaskDialog :: OnExpandButtonClick

L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur le bouton d’expansion.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Paramètres

*a été revelopper*<br/>
dans Une valeur différente de zéro indique que les informations supplémentaires sont affichées. 0 indique que les informations supplémentaires sont masquées.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a> CTaskDialog :: OnHelp

L’infrastructure appelle cette méthode lorsque l’utilisateur demande de l’aide.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a> CTaskDialog :: OnHyperlinkClick

L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un lien hypertexte.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Paramètres

*strHref*<br/>
dans Chaîne qui représente le lien hypertexte.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Cette méthode appelle [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) avant de retourner S_OK.

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a> CTaskDialog :: OnInit

L’infrastructure appelle cette méthode lorsque le `CTaskDialog` est initialisé.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a> CTaskDialog :: OnNavigatePage

L’infrastructure appelle cette méthode en réponse à la méthode [CTaskDialog :: NavigateTo](#navigateto) .

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a> CTaskDialog :: OnRadioButtonClick

L’infrastructure appelle cette méthode lorsque l’utilisateur sélectionne un contrôle de case d’option.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID*<br/>
dans ID du contrôle de case d’option sur lequel l’utilisateur a cliqué.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a> CTaskDialog :: OnTimer

L’infrastructure appelle cette méthode lorsque le minuteur expire.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Paramètres

*lTime*<br/>
dans Durée en millisecondes depuis la `CTaskDialog` création du ou de la réinitialisation de la minuterie.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a> CTaskDialog :: OnVerificationCheckboxClick

L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur la case à cocher vérification.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Paramètres

*bChecked*<br/>
dans La valeur TRUE indique que la case à cocher vérification est activée ; FALSe indique qu’il ne l’est pas.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a> CTaskDialog :: RemoveAllCommandControls

Supprime tous les contrôles de bouton de commande de `CTaskDialog` .

```cpp
void RemoveAllCommandControls();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a> CTaskDialog :: RemoveAllRadioButtons

Supprime toutes les cases d’option du `CTaskDialog` .

```cpp
void RemoveAllRadioButtons();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a> CTaskDialog :: SetCommandControlOptions

Met à jour un contrôle de bouton de commande sur `CTaskDialog` .

```cpp
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID*<br/>
dans ID du contrôle de commande à mettre à jour.

*bEnabled*<br/>
dans Paramètre booléen qui indique si le contrôle de bouton de commande spécifié est activé ou désactivé.

*bRequiresElevation*<br/>
dans Paramètre booléen qui indique si le contrôle de bouton de commande spécifié requiert une élévation.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour modifier si un contrôle de bouton de commande est activé ou nécessite une élévation après qu’il a été ajouté à la `CTaskDialog` classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a> CTaskDialog :: SetCommonButtonOptions

Met à jour un sous-ensemble de boutons courants à activer et pour exiger l’élévation UAC.

```cpp
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Paramètres

*nDisabledButtonMask*<br/>
dans Masque pour les boutons courants à désactiver.

*nElevationButtonMask*<br/>
dans Masque pour les boutons courants qui requièrent une élévation.

### <a name="remarks"></a>Notes

Vous pouvez définir les boutons courants disponibles pour une instance de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) en utilisant le constructeur [CTaskDialog :: CTaskDialog](#ctaskdialog) et la méthode [CTaskDialog :: SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` ne prend pas en charge l’ajout de nouveaux boutons courants.

Si vous utilisez cette méthode pour désactiver ou élever un bouton commun qui n’est pas disponible pour cela `CTaskDialog` , cette méthode lève une exception à l’aide de la macro [garantir](diagnostic-services.md#ensure) .

Cette méthode active tout bouton disponible pour `CTaskDialog` , mais n’est pas dans le *nDisabledButtonMask*, même s’il a été précédemment désactivé. Cette méthode traite l’élévation de la même manière : elle enregistre les boutons courants comme ne nécessitant pas d’élévation si le bouton commun est disponible mais n’est pas inclus dans *nElevationButtonMask*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a> CTaskDialog :: SetCommonButtons

Ajoute des boutons courants à `CTaskDialog` .

```cpp
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Paramètres

*nButtonMask*<br/>
dans Masque des boutons à ajouter à `CTaskDialog` .

*nDisabledButtonMask*<br/>
dans Masque des boutons à désactiver.

*nElevationButtonMask*<br/>
dans Masque des boutons qui requièrent une élévation.

### <a name="remarks"></a>Notes

Vous ne pouvez pas appeler cette méthode après la création de la fenêtre d’affichage pour cette instance de la `CTaskDialog` classe. Si vous le faites, cette méthode lève une exception.

Les boutons indiqués par *nButtonMask* remplacent tous les boutons courants précédemment ajoutés à `CTaskDialog` . Seuls les boutons indiqués dans *nButtonMask* sont disponibles.

Si *nDisabledButtonMask* ou *nElevationButtonMask* contiennent un bouton qui n’est pas dans *nButtonMask*, cette méthode lève une exception à l’aide de la macro [garantir](diagnostic-services.md#ensure) .

Par défaut, tous les boutons courants sont activés et ne nécessitent pas d’élévation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a> CTaskDialog :: SetContent

Met à jour le contenu du `CTaskDialog` .

```cpp
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Paramètres

*strContent*<br/>
dans Chaîne à afficher à l’utilisateur.

### <a name="remarks"></a>Notes

Le contenu de la `CTaskDialog` classe est le texte qui est affiché à l’utilisateur dans la section principale de la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a> CTaskDialog :: SetDefaultCommandControl

Spécifie le contrôle de bouton de commande par défaut.

```cpp
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Paramètres

*nCommandControlID*<br/>
dans ID du contrôle de bouton de commande par défaut.

### <a name="remarks"></a>Notes

Le contrôle de bouton de commande par défaut est le contrôle qui est sélectionné lorsque le `CTaskDialog` s’affiche pour la première fois à l’utilisateur.

Cette méthode lève une exception si elle ne peut pas trouver le contrôle de bouton de commande spécifié par *nCommandControlID*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a> CTaskDialog :: SetDefaultRadioButton

Spécifie la case d’option par défaut.

```cpp
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID*<br/>
dans ID de la case d’option à utiliser comme valeur par défaut.

### <a name="remarks"></a>Notes

La case d’option par défaut est le bouton qui est sélectionné lorsque le `CTaskDialog` est affiché pour la première fois à l’utilisateur.

Cette méthode lève une exception si elle ne peut pas trouver la case d’option spécifiée par *nRadioButtonID*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a> CTaskDialog :: SetDialogWidth

Ajuste la largeur du `CTaskDialog` .

```cpp
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
dans Largeur de la boîte de dialogue, en pixels.

### <a name="remarks"></a>Notes

Le paramètre *nWidth* doit être supérieur ou égal à 0. Sinon, cette méthode lève une exception.

Si *nWidth* a la valeur 0, cette méthode affecte à la boîte de dialogue la taille par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a> CTaskDialog :: SetExpansionArea

Met à jour la zone d’expansion du `CTaskDialog` .

```cpp
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Paramètres

*strExpandedInformation*<br/>
dans Chaîne que le `CTaskDialog` affiche dans le corps principal de la boîte de dialogue lorsque l’utilisateur clique sur le bouton d’expansion.

*strCollapsedLabel*<br/>
dans Chaîne que le `CTaskDialog` affiche à côté du bouton d’expansion lorsque la zone développée est réduite.

*strExpandedLabel*<br/>
dans Chaîne que le `CTaskDialog` affiche à côté du bouton d’expansion lorsque la zone développée est affichée.

### <a name="remarks"></a>Notes

La zone d’expansion de la `CTaskDialog` classe vous permet de fournir des informations supplémentaires à l’utilisateur. La zone d’expansion est dans la partie principale du `CTaskDialog` , située immédiatement sous le titre et la chaîne de contenu.

Lorsque `CTaskDialog` est affiché pour la première fois, il n’affiche pas les informations développées et les place `strCollapsedLabel` en regard du bouton d’expansion. Quand l’utilisateur clique sur le bouton d’expansion, le `CTaskDialog` affiche *strExpandedInformation* et remplace l’étiquette par *strExpandedLabel*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a> CTaskDialog :: SetFooterIcon

Met à jour l’icône de pied de page du `CTaskDialog` .

```cpp
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Paramètres

*hFooterIcon*<br/>
dans Nouvelle icône pour `CTaskDialog` .

*lpszFooterIcon*<br/>
dans Nouvelle icône pour `CTaskDialog` .

### <a name="remarks"></a>Notes

L’icône de pied de page est affichée en bas de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Il peut avoir un texte de pied de page associé. Vous pouvez modifier le texte de pied de page avec [CTaskDialog :: SetFooterText](#setfootertext).

Cette méthode lève une exception avec [la macro s'](diagnostic-services.md#ensure) afficher si le `CTaskDialog` est affiché ou si le paramètre d’entrée a la valeur null.

Un `CTaskDialog` peut uniquement accepter un `HICON` ou `LPCWSTR` une icône de pied de page. Cela est configuré en définissant l’option TDF_USE_HICON_FOOTER dans le constructeur ou [CTaskDialog :: SetOptions](#setoptions). Par défaut, le `CTaskDialog` est configuré pour utiliser `LPCWSTR` comme type d’entrée pour l’icône de pied de page. Cette méthode génère une exception si vous essayez de définir l’icône à l’aide du type inapproprié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a> CTaskDialog :: SetFooterText

Met à jour le texte sur le pied de page du `CTaskDialog` .

```cpp
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Paramètres

*strFooterText*<br/>
dans Nouveau texte du pied de page.

### <a name="remarks"></a>Notes

L’icône de pied de page apparaît en regard du texte de pied de page en bas de la `CTaskDialog` . Vous pouvez modifier l’icône de pied de page avec [CTaskDialog :: SetFooterIcon](#setfootericon).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a> CTaskDialog :: SetMainIcon

Met à jour l’icône principale de `CTaskDialog` .

```cpp
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Paramètres

*hMainIcon*<br/>
dans Nouvelle icône.

*lpszMainIcon*<br/>
dans Nouvelle icône.

### <a name="remarks"></a>Notes

Cette méthode lève une exception avec [la macro s'](diagnostic-services.md#ensure) afficher si le `CTaskDialog` est affiché ou si le paramètre d’entrée a la valeur null.

Un `CTaskDialog` peut uniquement accepter un `HICON` ou `LPCWSTR` une icône principale. Vous pouvez configurer cela en définissant l’option TDF_USE_HICON_MAIN dans le constructeur ou dans la méthode [CTaskDialog :: SetOptions](#setoptions) . Par défaut, `CTaskDialog` est configuré pour utiliser `LPCWSTR` comme type d’entrée pour l’icône principale. Cette méthode génère une exception si vous essayez de définir l’icône à l’aide du type inapproprié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a> CTaskDialog :: SetMainInstruction

Met à jour l’instruction principale de `CTaskDialog` .

```cpp
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Paramètres

*strInstructions*<br/>
dans Nouvelle instruction principale.

### <a name="remarks"></a>Notes

L’instruction principale de la `CTaskDialog` classe est le texte affiché à l’utilisateur dans une grande police en gras. Il se trouve dans la boîte de dialogue sous la barre de titre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a> CTaskDialog :: SetOptions

Configure les options de `CTaskDialog` .

```cpp
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Paramètres

*nOptionFlag*<br/>
dans Jeu d’indicateurs à utiliser pour `CTaskDialog` .

### <a name="remarks"></a>Notes

Cette méthode efface toutes les options actuelles pour le `CTaskDialog` . Pour conserver les options actuelles, vous devez d’abord les récupérer avec [CTaskDialog :: GetOptions](#getoptions) et les combiner avec les options que vous souhaitez définir.

Le tableau suivant répertorie toutes les options valides.

|Nom|Description|
|-|-|
|TDF_ENABLE_HYPERLINKS|Active les liens hypertexte dans `CTaskDialog` .|
|TDF_USE_HICON_MAIN|Configure le `CTaskDialog` pour utiliser un `HICON` pour l’icône principale. L’alternative consiste à utiliser un `LPCWSTR` .|
|TDF_USE_HICON_FOOTER|Configure le `CTaskDialog` pour utiliser un `HICON` pour l’icône de pied de page. L’alternative consiste à utiliser un `LPCWSTR` .|
|TDF_ALLOW_DIALOG_CANCELLATION|Permet à l’utilisateur de fermer le `CTaskDialog` à l’aide du clavier ou à l’aide de l’icône située dans l’angle supérieur droit de la boîte de dialogue, même si le bouton **Annuler** n’est pas activé. Si cet indicateur n’est pas défini et que le bouton **Annuler** n’est pas activé, l’utilisateur ne peut pas fermer la boîte de dialogue en utilisant Alt + F4, la touche Échap ou le bouton fermer de la barre de titre.|
|TDF_USE_COMMAND_LINKS|Configure le `CTaskDialog` pour utiliser les contrôles de bouton de commande.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Configure le `CTaskDialog` pour utiliser des contrôles de bouton de commande sans afficher d’icône en regard du contrôle. TDF_USE_COMMAND_LINKS remplace TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Indique que la zone d’expansion est actuellement développée.|
|TDF_EXPANDED_BY_DEFAULT|Détermine si la zone d’expansion est développée par défaut.|
|TDF_VERIFICATION_FLAG_CHECKED|Indique que la case à cocher vérification est actuellement activée.|
|TDF_SHOW_PROGRESS_BAR|Configure `CTaskDialog` pour afficher une barre de progression.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Configure la barre de progression pour qu’elle soit une barre de progression défilant. Si vous activez cette option, vous devez définir TDF_SHOW_PROGRESS_BAR pour obtenir le comportement attendu.|
|TDF_CALLBACK_TIMER|Indique que l' `CTaskDialog` intervalle de rappel est défini à environ 200 millisecondes.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Configure le `CTaskDialog` à centrer par rapport à la fenêtre parente. Si cet indicateur n’est pas activé, le `CTaskDialog` est centré par rapport à l’analyse.|
|TDF_RTL_LAYOUT|Configure le `CTaskDialog` pour une disposition de lecture de droite à gauche.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Indique qu’aucune case d’option n’est sélectionnée lorsque le `CTaskDialog` s’affiche.|
|TDF_CAN_BE_MINIMIZED|Permet à l’utilisateur de réduire le `CTaskDialog` . Pour prendre en charge cette option, le `CTaskDialog` ne peut pas être modal. MFC ne prend pas en charge cette option, car MFC ne prend pas en charge le mode non modal `CTaskDialog` .|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a> CTaskDialog :: SetProgressBarMarquee

Configure une barre de texte défilant pour le `CTaskDialog` et l’ajoute à la boîte de dialogue.

```cpp
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Paramètres

*bEnabled*<br/>
dans TRUE pour activer la barre de sélection ; FALSe pour désactiver la barre de sélection et la supprimer de la `CTaskDialog` .

*nMarqueeSpeed*<br/>
dans Entier qui indique la vitesse de la barre de sélection.

### <a name="remarks"></a>Notes

La barre de sélection apparaît sous le texte principal de la `CTaskDialog` classe.

Utilisez *nMarqueeSpeed* pour définir la vitesse de la barre de sélection ; des valeurs plus élevées indiquent une vitesse plus lente. La valeur 0 pour *nMarqueeSpeed* fait passer la barre de sélection à la vitesse par défaut pour Windows.

Cette méthode lève une exception avec la macro [s’assurer](diagnostic-services.md#ensure) si *nMarqueeSpeed* est inférieur à 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a> CTaskDialog :: SetProgressBarPosition

Ajuste la position de la barre de progression.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Paramètres

*nProgressPos*<br/>
dans Position de la barre de progression.

### <a name="remarks"></a>Notes

Cette méthode lève une exception avec la macro [s’assurer](diagnostic-services.md#ensure) si *nProgressPos* n’est pas dans la plage de la barre de progression. Vous pouvez modifier la plage de la barre de progression avec [CTaskDialog :: SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a> CTaskDialog :: SetProgressBarRange

Ajuste la plage de la barre de progression.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Paramètres

*nRangeMin*<br/>
dans Limite inférieure de la barre de progression.

*nRangeMax*<br/>
dans Limite supérieure de la barre de progression.

### <a name="remarks"></a>Notes

La position de la barre de progression est relative à *nRangeMin* et *nRangeMax*. Par exemple, si *nRangeMin* est 50 et *nRangeMax* est 100, une position de 75 est à mi-chemin sur la barre de progression. Utilisez [CTaskDialog :: SetProgressBarPosition](#setprogressbarposition) pour définir la position de la barre de progression.

Pour afficher la barre de progression, l’option TDF_SHOW_PROGRESS_BAR doit être activée et TDF_SHOW_MARQUEE_PROGRESS_BAR ne doit pas être activée. Cette méthode définit automatiquement TDF_SHOW_PROGRESS_BAR et efface TDF_SHOW_MARQUEE_PROGRESS_BAR. Utilisez [CTaskDialog :: SetOptions](#setoptions) pour modifier manuellement les options de cette instance de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Cette méthode lève une exception avec la macro [s’assurer](diagnostic-services.md#ensure) si *nRangeMin* n’est pas inférieur à *nRangeMax*. Cette méthode lève également une exception si le `CTaskDialog` est déjà affiché et comporte une barre de progression défilant.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a> CTaskDialog :: SetProgressBarState

Définit l’état de la barre de progression et l’affiche sur le `CTaskDialog` .

```cpp
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Paramètres

*nState*<br/>
dans État de la barre de progression. Consultez la section Notes pour connaître les valeurs possibles.

### <a name="remarks"></a>Notes

Cette méthode lève une exception avec la macro [garantir](diagnostic-services.md#ensure) si le `CTaskDialog` est déjà affiché et comporte une barre de progression défilant.

Le tableau suivant répertorie les valeurs possibles pour *nState*. Dans tous ces cas, la barre de progression se remplit avec la couleur normale jusqu’à ce qu’elle atteigne la position d’arrêt désignée. À ce stade, il change de couleur en fonction de l’État.

|Nom|Description|
|-|-|
|PBST_NORMAL|Une fois la barre de progression remplie, le `CTaskDialog` ne modifie pas la couleur de la barre. Par défaut, la couleur normale est verte.|
|PBST_ERROR|Une fois la barre de progression remplie, la `CTaskDialog` couleur de la barre est remplacée par la couleur de l’erreur. Par défaut, il s’agit du rouge.|
|PBST_PAUSED|Une fois la barre de progression remplie, le remplace la couleur `CTaskDialog` de la barre par la couleur suspendue. Par défaut, il s’agit de la couleur jaune.|

Vous pouvez définir l’emplacement où la barre de progression s’arrête avec [CTaskDialog :: SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a> CTaskDialog :: SetRadioButtonOptions

Active ou désactive une case d’option.

```cpp
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Paramètres

*nRadioButtonID*<br/>
dans ID du contrôle de case d’option.

*bEnabled*<br/>
dans TRUE pour activer la case d’option ; FALSe pour désactiver la case d’option.

### <a name="remarks"></a>Notes

Cette méthode lève une exception avec la macro [s’assurer](diagnostic-services.md#ensure) si *nRadioButtonID* n’est pas un ID valide pour une case d’option.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a> CTaskDialog :: SetVerificationCheckbox

Définit l’état activé de la case à cocher vérification.

```cpp
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Paramètres

*bChecked*<br/>
dans TRUE pour que la case à cocher de vérification `CTaskDialog` soit activée lorsque est affiché ; FALSe pour que la case à cocher vérification soit désactivée lorsque le `CTaskDialog` s’affiche.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a> CTaskDialog :: SetVerificationCheckboxText

Définit le texte affiché à droite de la case à cocher vérification.

```cpp
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Paramètres

*strVerificationText*<br/>
dans Texte que cette méthode affiche à côté de la case à cocher vérification.

### <a name="remarks"></a>Notes

Cette méthode lève une exception avec la macro [s’assurer](diagnostic-services.md#ensure) si cette instance de la `CTaskDialog` classe est déjà affichée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a> CTaskDialog :: SetWindowTitle

Définit le titre de `CTaskDialog` .

```cpp
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Paramètres

*strWindowTitle*<br/>
dans Nouveau titre de `CTaskDialog` .

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a> CTaskDialog :: ShowDialog

Crée et affiche un `CTaskDialog` .

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
dans Chaîne à utiliser pour le contenu du `CTaskDialog` .

*strMainInstruction*<br/>
dans Instruction principale de `CTaskDialog` .

*strTitle*<br/>
dans Titre du `CTaskDialog` .

*nIDCommandControlsFirst*<br/>
dans ID de chaîne de la première commande.

*nIDCommandControlsLast*<br/>
dans ID de chaîne de la dernière commande.

*nCommonButtons*<br/>
dans Masque des boutons à ajouter à `CTaskDialog` .

*nTaskDialogOptions*<br/>
dans Ensemble d’options à utiliser pour `CTaskDialog` .

*strFooter*<br/>
dans Chaîne à utiliser en tant que pied de page.

### <a name="return-value"></a>Valeur renvoyée

Entier qui correspond à la sélection effectuée par l’utilisateur.

### <a name="remarks"></a>Notes

Cette méthode statique vous permet de créer une instance de la `CTaskDialog` classe sans créer explicitement un `CTaskDialog` objet dans votre code. Étant donné qu’il n’y a pas d' `CTaskDialog` objet, vous ne pouvez pas appeler d’autres méthodes du `CTaskDialog` si vous utilisez cette méthode pour afficher un `CTaskDialog` à l’utilisateur.

Cette méthode crée des contrôles de bouton de commande en utilisant les données du fichier de ressources de votre application. La table de chaînes du fichier de ressources contient plusieurs chaînes avec des ID de chaîne associés. Cette méthode ajoute un contrôle de bouton de commande pour chaque entrée valide dans la table de chaînes entre *nIDCommandControlsFirst* et *nCommandControlsLast*, inclus. Pour ces contrôles de bouton de commande, la chaîne dans la table de chaînes est la légende du contrôle et l’ID de chaîne est l’ID du contrôle.

Pour obtenir la liste des options valides, consultez [CTaskDialog :: SetOptions](#setoptions) .

`CTaskDialog`Se ferme lorsque l’utilisateur sélectionne un bouton commun, un contrôle de lien de commande ou ferme le `CTaskDialog` . La valeur de retour est l’identificateur qui indique la façon dont l’utilisateur a fermé la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a> CTaskDialog :: TaskDialogCallback

L’infrastructure appelle cette méthode en réponse à différents messages Windows.

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

*HWND*<br/>
dans Handle de la `m_hWnd` structure de `CTaskDialog` .

*uNotification*<br/>
dans Code de notification qui spécifie le message généré.

*wParam*<br/>
dans Plus d’informations sur le message.

*lParam*<br/>
dans Plus d’informations sur le message.

*dwRefData*<br/>
dans Pointeur vers l' `CTaskDialog` objet auquel s’applique le message de rappel.

### <a name="return-value"></a>Valeur renvoyée

Dépend du code de notification spécifique. Pour plus d'informations, consultez la section Notes.

### <a name="remarks"></a>Notes

L’implémentation par défaut de `TaskDialogCallback` gère le message spécifique, puis appelle la méthode appropriée sur la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Par exemple, en réponse au message TDN_BUTTON_CLICKED, `TaskDialogCallback` appelle [CTaskDialog :: OnCommandControlClick](#oncommandcontrolclick).

Les valeurs de *wParam* et *lParam* dépendent du message généré spécifique. Il est possible que l’une ou l’autre de ces valeurs soit vide. Le tableau suivant répertorie les notifications par défaut qui sont prises en charge et les valeurs de *wParam* et *lParam* . Si vous substituez cette méthode dans une classe dérivée, vous devez implémenter le code de rappel pour chaque message dans le tableau suivant.

|Message de notification|*wParam* Ajoutée|*lParam* Ajoutée|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Non utilisé.|Non utilisé.|
|TDN_NAVIGATED|Non utilisé.|Non utilisé.|
|TDN_BUTTON_CLICKED|ID du contrôle de bouton de commande.|Non utilisé.|
|TDN_HYPERLINK_CLICKED|Non utilisé.|Structure [LPCWSTR](/windows/win32/WinProg/windows-data-types) qui contient le lien.|
|TDN_TIMER|Durée en millisecondes depuis la `CTaskDialog` création du ou de la réinitialisation de la minuterie.|Non utilisé.|
|TDN_DESTROYED|Non utilisé.|Non utilisé.|
|TDN_RADIO_BUTTON_CLICKED|ID de la case d’option.|Non utilisé.|
|TDN_DIALOG_CONSTRUCTED|Non utilisé.|Non utilisé.|
|TDN_VERIFICATION_CLICKED|1 si la case à cocher est activée, 0 dans le cas contraire.|Non utilisé.|
|TDN_HELP|Non utilisé.|Non utilisé.|
|TDN_EXPANDO_BUTTON_CLICKED|0 si la zone d’expansion est réduite ; valeur différente de zéro si le texte d’expansion est affiché.|Non utilisé.|

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Procédure pas à pas : ajout d’un CTaskDialog à une application](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
