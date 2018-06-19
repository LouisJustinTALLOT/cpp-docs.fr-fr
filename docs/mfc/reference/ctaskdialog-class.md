---
title: Classe CTaskDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 096423e08b470efea55e790e7ad038eb04715ccb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379006"
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
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Ajoute un contrôle de bouton de commande pour le `CTaskDialog`.|  
|[CTaskDialog::AddRadioButton](#addradiobutton)|Ajoute un bouton radio pour le `CTaskDialog`.|  
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Clique sur un bouton de commande ou commun par programme.|  
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Clique sur un bouton radio par programme.|  
|[CTaskDialog::DoModal](#domodal)|Affiche la `CTaskDialog`.|  
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Récupère le nombre de boutons courants disponibles.|  
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Convertit un standard associé à un bouton de Windows pour le type de bouton commun la `CTaskDialog` classe.|  
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Convertit un des types courants de bouton associés à la `CTaskDialog` classe pour un bouton Windows standard.|  
|[CTaskDialog::GetOptions](#getoptions)|Retourne les indicateurs d’option pour ce `CTaskDialog`.|  
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Retourne le contrôle de bouton de commande sélectionnée.|  
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Retourne la case d’option sélectionnée.|  
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Récupère l’état de la case à cocher de vérification.|  
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Détermine si un bouton de commande ou d’un bouton commune est activée.|  
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Détermine si une case d’option est activée.|  
|[CTaskDialog::IsSupported](#issupported)|Détermine si l’ordinateur qui exécute l’application prend en charge la `CTaskDialog`.|  
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Ajoute des contrôles de bouton de commande à l’aide de données à partir de la table de chaînes.|  
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Ajoute des cases d’option à l’aide de données à partir de la table de chaînes.|  
|[CTaskDialog::NavigateTo](#navigateto)|Transfère le focus vers un autre `CTaskDialog`.|  
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un contrôle de bouton de commande.|  
|[CTaskDialog::OnCreate](#oncreate)|L’infrastructure appelle cette méthode après avoir créé le `CTaskDialog`.|  
|[CTaskDialog::OnDestroy](#ondestroy)|L’infrastructure appelle cette méthode immédiatement avant elle détruit le `CTaskDialog`.|  
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur le bouton de développement.|  
|[CTaskDialog::OnHelp](#onhelp)|L’infrastructure appelle cette méthode lorsque l’utilisateur demande l’aide.|  
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un lien hypertexte.|  
|[CTaskDialog::OnInit](#oninit)|L’infrastructure appelle cette méthode lorsque le `CTaskDialog` est initialisé.|  
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|L’infrastructure appelle cette méthode lorsque l’utilisateur déplace le focus en ce qui concerne les contrôles le `CTaskDialog`.|  
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur sélectionne un contrôle case d’option.|  
|[CTaskDialog::OnTimer](#ontimer)|L’infrastructure appelle cette méthode lorsque le minuteur expire.|  
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur la case à cocher de vérification.|  
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Supprime tous les contrôles de commande à partir de la `CTaskDialog`.|  
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Supprime tous les boutons de case d’option à partir de la `CTaskDialog`.|  
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Met à jour un contrôle de bouton de commande sur le `CTaskDialog`.|  
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Met à jour un sous-ensemble des boutons courants pour être activé et requièrent une élévation de compte d’utilisateur.|  
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Ajoute des boutons courantes à le `CTaskDialog`.|  
|[CTaskDialog::SetContent](#setcontent)|Met à jour le contenu de la `CTaskDialog`.|  
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Spécifie le contrôle de bouton de commande par défaut.|  
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Spécifie la case d’option par défaut.|  
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Ajuste la largeur de la `CTaskDialog`.|  
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Met à jour la zone d’extension de la `CTaskDialog`.|  
|[CTaskDialog::SetFooterIcon](#setfootericon)|Met à jour l’icône de pied de page pour le `CTaskDialog`.|  
|[CTaskDialog::SetFooterText](#setfootertext)|Met à jour le texte dans le pied de page de la `CTaskDialog`.|  
|[CTaskDialog::SetMainIcon](#setmainicon)|Met à jour l’icône principale de la `CTaskDialog`.|  
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Met à jour l’instruction principale de la `CTaskDialog`.|  
|[CTaskDialog::SetOptions](#setoptions)|Configure les options pour le `CTaskDialog`.|  
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Configure une barre de sélection pour la `CTaskDialog` et l’ajoute à la boîte de dialogue.|  
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ajuste la position de la barre de progression.|  
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Ajuste la plage de la barre de progression.|  
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Définit l’état de la barre de progression et l’affiche sur la `CTaskDialog`.|  
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Active ou désactive une case d’option.|  
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Définit l’état activé de la case à cocher de vérification.|  
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Définit le texte sur le côté droit de la case à cocher de vérification.|  
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Définit le titre de la `CTaskDialog`.|  
|[CTaskDialog::ShowDialog](#showdialog)|Crée et affiche un `CTaskDialog`.|  
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|L’infrastructure appelle cette en réponse à différents messages de Windows.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|`m_aButtons`|Le tableau de contrôles de bouton de commande pour le `CTaskDialog`.|  
|`m_aRadioButtons`|Le tableau de contrôles de bouton radio pour le `CTaskDialog`.|  
|`m_bVerified`|`TRUE` Indique la vérification case à cocher est activée ; `FALSE` indique qu’il n’est pas.|  
|`m_footerIcon`|L’icône dans le pied de page de la `CTaskDialog`.|  
|`m_hWnd`|Un handle de fenêtre pour le `CTaskDialog`.|  
|`m_mainIcon`|L’icône principale de la `CTaskDialog`.|  
|`m_nButtonDisabled`|Un masque qui indique les boutons courants sont désactivées.|  
|`m_nButtonElevation`|Un masque qui indique les boutons courants nécessitent élévation UAC.|  
|`m_nButtonId`|L’ID du contrôle de bouton de commande sélectionnée.|  
|`m_nCommonButton`|Un masque indiquant les boutons courantes sont affichés sur la `CTaskDialog`.|  
|`m_nDefaultCommandControl`|Contrôle de l’ID du bouton de commande qui est sélectionné lorsque le `CTaskDialog` s’affiche.|  
|`m_nDefaultRadioButton`|L’ID de la case d’un contrôle est sélectionné lorsque le `CTaskDialog` s’affiche.|  
|`m_nFlags`|Un masque qui indique les options pour le `CTaskDialog`.|  
|`m_nProgressPos`|La position actuelle de la barre de progression.  Cette valeur doit être comprise entre `m_nProgressRangeMin` et `m_nProgressRangeMax`.|  
|`m_nProgressRangeMax`|La valeur maximale pour la barre de progression.|  
|`m_nProgressRangeMin`|La valeur minimale pour la barre de progression.|  
|`m_nProgressState`|L’état de la barre de progression. Pour plus d’informations, consultez [CTaskDialog::SetProgressBarState](#setprogressbarstate).|  
|`m_nRadioId`|L’ID du contrôle de bouton de case d’option sélectionnée.|  
|`m_nWidth`|La largeur de la `CTaskDialog` en pixels.|  
|`m_strCollapse`|La chaîne de la `CTaskDialog` affiche à droite de la zone d’extension lorsque les informations étendues sont masquées.|  
|`m_strContent`|La chaîne de contenu de la `CTaskDialog`.|  
|`m_strExpand`|La chaîne de la `CTaskDialog` affiche à droite de la zone d’extension lorsque les informations étendues s’affiche.|  
|`m_strFooter`|Le pied de page de la `CTaskDialog`.|  
|`m_strInformation`|Les informations étendues pour la `CTaskDialog`.|  
|`m_strMainInstruction`|L’instruction principale de la `CTaskDialog`.|  
|`m_strTitle`|Le titre de la `CTaskDialog`.|  
|`m_strVerification`|La chaîne que le `CTaskDialog` affiche à droite de la case à cocher de vérification.|  
  
## <a name="remarks"></a>Notes  
 La `CTaskDialog` classe remplace la boîte de message Windows standard et comporte des fonctionnalités supplémentaires telles que de nouveaux contrôles pour recueillir des informations à partir de l’utilisateur. Cette classe se trouve dans la bibliothèque MFC dans [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]. Le `CTaskDialog` est disponible à partir de Windows Vista. Les versions antérieures de Windows ne peut pas afficher le `CTaskDialog` objet. Utilisez `CTaskDialog::IsSupported` pour déterminer à l’exécution si l’utilisateur actuel peut afficher la boîte de dialogue de tâche. La boîte de message Windows standard est toujours pris en charge dans [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)].  
  
 Le `CTaskDialog` est disponible uniquement lorsque vous générez votre application à l’aide de la bibliothèque Unicode.  
  
 Le `CTaskDialog` a deux constructeurs différents. Un constructeur permet de spécifier les deux boutons de commande et un maximum de six contrôles bouton normal. Vous pouvez ajouter des boutons de commande plus après avoir créé le `CTaskDialog`. Le deuxième constructeur ne prend pas en charge des boutons de commande, mais vous pouvez ajouter un nombre illimité de contrôles de bouton normal. Pour plus d’informations sur les constructeurs, consultez [CTaskDialog::CTaskDialog](#ctaskdialog).  
  
 L’illustration suivante montre un exemple `CTaskDialog` pour illustrer l’emplacement de certains de ces contrôles.  
  
 ![Exemple de CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "ctaskdialogsample")  
Exemple de CTaskDialog  
  
## <a name="requirements"></a>Spécifications  
 **Valeur minimale de système d’exploitation requis :** Windows Vista  
  
 **En-tête :** afxtaskdialog.h  
  
##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl  
 Ajoute un nouveau contrôle de bouton de commande pour le `CTaskDialog`.  
  
```  
void AddCommandControl(
    int nCommandControlID,  
    const CString& strCaption,  
    BOOL bEnabled = TRUE,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nCommandControlID`  
 Numéro d’identification de contrôle de commande.  
  
 [in] `strCaption`  
 La chaîne que le `CTaskDialog` affiche à l’utilisateur. Utilisez cette chaîne pour expliquer l’objectif de la commande.  
  
 [in] `bEnabled`  
 Un paramètre booléen qui indique si le bouton est activé ou désactivé.  
  
 [in] `bRequiresElevation`  
 Un paramètre booléen qui indique si une commande nécessite des privilèges élevés.  
  
### <a name="remarks"></a>Notes  
 Le `CTaskDialog Class` peut afficher un nombre illimité de contrôles de bouton de commande. Toutefois, si un `CTaskDialog` contrôle l’affiche un bouton de commande, il peut afficher un maximum de six boutons. Si un `CTaskDialog` ne contient aucun contrôle de bouton de commande, il peut afficher un nombre illimité de boutons.  
  
 Lorsque l’utilisateur sélectionne un contrôle de bouton de commande, le `CTaskDialog` se ferme. Si votre application affiche la boîte de dialogue à l’aide de [CTaskDialog::DoModal](#domodal), `DoModal` retourne le `nCommandControlID` du contrôle de bouton de commande sélectionnée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="addradiobutton"></a>  CTaskDialog::AddRadioButton  
 Ajoute un bouton radio pour le `CTaskDialog`.  
  
```  
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,  
    const CString& strCaption,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nRadioButtonID`  
 Numéro d’identification de la case d’option.  
  
 [in] `strCaption`  
 La chaîne que le `CTaskDialog` s’affiche en regard de la case d’option.  
  
 [in] `bEnabled`  
 Un paramètre booléen qui indique si la case d’option est activée.  
  
### <a name="remarks"></a>Notes  
 Boutons de la case d’option pour le [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) vous permettent de recueillir des informations à partir de l’utilisateur. Utilisez la fonction [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) pour déterminer quel bouton de case d’option est sélectionnée.  
  
 Le `CTaskDialog` n’exige pas que le `nRadioButtonID` paramètres sont uniques pour chaque case d’option. Toutefois, vous pouvez rencontrer un comportement inattendu si vous n’utilisez pas un identificateur distinct pour chaque case d’option.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="clickcommandcontrol"></a>  CTaskDialog::ClickCommandControl  
 Clique sur un bouton de commande ou commun par programme.  
  
```  
protected:  
void ClickCommandControl(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nCommandControlID`  
 L’ID de commande du contrôle de cliquer sur.  
  
### <a name="remarks"></a>Notes  
 Cette méthode génère le message windows `TDM_CLICK_BUTTON`.  
  
##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton  
 Clique sur un bouton radio par programme.  
  
```  
protected:  
void ClickRadioButton(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nRadioButtonID`  
 ID de cliquer sur le bouton d’option.  
  
### <a name="remarks"></a>Notes  
 Cette méthode génère le message windows `TDM_CLICK_RADIO_BUTTON`.  
  
##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog  
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
 [in] `strContent`  
 La chaîne à utiliser pour le contenu de la `CTaskDialog`.  
  
 [in] `strMainInstruction`  
 L’instruction principale de la `CTaskDialog`.  
  
 [in] `strTitle`  
 Le titre de la `CTaskDialog`.  
  
 [in] `nCommonButtons`  
 Un masque des boutons courantes à ajouter à la `CTaskDialog`.  
  
 [in] `nTaskDialogOptions`  
 Le jeu d’options à utiliser pour le `CTaskDialog`.  
  
 [in] `strFooter`  
 La chaîne à utiliser dans le pied de page.  
  
 [in] `nIDCommandControlsFirst`  
 L’ID de chaîne de la première commande.  
  
 [in] `nIDCommandControlsLast`  
 L’ID de chaîne de la dernière commande.  
  
### <a name="remarks"></a>Notes  
 Il existe deux manières que vous pouvez ajouter un `CTaskDialog` à votre application. La première consiste à utiliser un des constructeurs pour créer un `CTaskDialog` et l’afficher à l’aide de [CTaskDialog::DoModal](#domodal). La seconde consiste à utiliser la fonction statique [CTaskDialog::ShowDialog](#showdialog), ce qui vous permet d’afficher un `CTaskDialog` sans créer explicitement un `CTaskDialog` objet.  
  
 Le deuxième constructeur crée des contrôles de bouton de commande à l’aide des données à partir du fichier de ressources de votre application. La table de chaînes dans le fichier de ressources a plusieurs chaînes avec l’ID de chaîne associé. Cette méthode ajoute un contrôle de bouton de commande pour chaque entrée valide dans la table de chaînes entre `nIDCommandControlsFirst` et `nCommandControlsLast`(inclus). Pour ces contrôles de bouton de commande, la chaîne de la table de chaînes est la légende du contrôle et l’ID de chaîne ID de. du contrôle  
  
 Consultez [CTaskDialog::SetOptions](#setoptions) pour obtenir la liste des options valides.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="domodal"></a>  CTaskDialog::DoModal  
 Affiche le `CTaskDialog` et rend modal.  
  
```  
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hParent`  
 La fenêtre parente de la `CTaskDialog`.  
  
### <a name="return-value"></a>Valeur de retour  
 Entier qui correspond à la sélection effectuée par l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 Affiche cette instance de la [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). L’application, puis attend que l’utilisateur de fermer la boîte de dialogue.  
  
 Le `CTaskDialog` se ferme lorsque l’utilisateur sélectionne un bouton commun, un contrôle de lien de commande, ou ferme le `CTaskDialog`. La valeur de retour est l’identificateur qui indique la façon dont l’utilisateur a fermé la boîte de dialogue.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getcommonbuttoncount"></a>  CTaskDialog::GetCommonButtonCount  
 Récupère le nombre de boutons courants.  
  
```  
int GetCommonButtonCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de boutons courants disponibles.  
  
### <a name="remarks"></a>Notes  
 Les boutons courants sont les boutons par défaut que vous fournissez à [CTaskDialog::CTaskDialog](#ctaskdialog). Le [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) affiche les boutons au bas de la boîte de dialogue.  
  
 La liste énumérée des boutons est fournie dans CommCtrl.h.  
  
##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag  
 Convertit un standard associé à un bouton de Windows pour le type de bouton commun le [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md).  
  
```  
int GetCommonButtonFlag(int nButtonId) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nButtonId`  
 La valeur de bouton Windows standard.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur correspondantes `CTaskDialog` bouton courantes. S’il n’existe aucun bouton commun correspondant, cette méthode retourne 0.  
  
##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId  
 Convertit un des types courants de bouton associés à la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) à un bouton Windows standard.  
  
```  
int GetCommonButtonId(int nFlag);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nFlag`  
 Le type de bouton courantes liées à la `CTaskDialog` classe.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur du bouton Windows standard correspondant. S’il n’existe aucun bouton Windows correspondant, la méthode retourne 0.  
  
##  <a name="getoptions"></a>  CTaskDialog::GetOptions  
 Retourne les indicateurs d’option pour ce `CTaskDialog`.  
  
```  
int GetOptions() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Les indicateurs de le `CTaskDialog`.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les options disponibles pour le [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md), consultez [CTaskDialog::SetOptions](#setoptions).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getselectedcommandcontrolid"></a>  CTaskDialog::GetSelectedCommandControlID  
 Retourne le contrôle de bouton de commande sélectionnée.  
  
```  
int GetSelectedCommandControlID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID du contrôle de bouton de commande actuellement sélectionnée.  
  
### <a name="remarks"></a>Notes  
 Il est inutile d’utiliser cette méthode pour récupérer l’ID du bouton de commande que l’utilisateur sélectionné. Cet ID est retourné par [CTaskDialog::DoModal](#domodal) ou [CTaskDialog::ShowDialog](#showdialog).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="getselectedradiobuttonid"></a>  CTaskDialog::GetSelectedRadioButtonID  
 Retourne la case d’option sélectionnée.  
  
```  
int GetSelectedRadioButtonID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 ID de la case d’option sélectionnée.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser cette méthode une fois que l’utilisateur ferme la boîte de dialogue pour récupérer la case d’option sélectionnée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="getverificationcheckboxstate"></a>  CTaskDialog::GetVerificationCheckboxState  
 Récupère l’état de la case à cocher de vérification.  
  
```  
BOOL GetVerificationCheckboxState() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la case à cocher est activée, `FALSE` si elle n’est pas.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled  
 Détermine si un bouton de commande ou un bouton est activé.  
  
```  
BOOL IsCommandControlEnabled(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nCommandControlID`  
 ID de bouton de commande ou du bouton à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le contrôle est activé, `FALSE` si elle n’est pas.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser cette méthode pour déterminer la disponibilité des deux contrôles de bouton de commande et les boutons courants de la `CTaskDialog Class`.  
  
 Si `nCommandControlID` n'est pas un identificateur valide pour une commune `CTaskDialog` bouton ou un contrôle de bouton de commande, cette méthode lève une exception.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled  
 Détermine si une case d’option est activée.  
  
```  
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nRadioButtonID`  
 ID de la case à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la case d’option est activée, `FALSE` si elle n’est pas.  
  
### <a name="remarks"></a>Notes  
 Si `nRadioButtonID` n’est pas un identificateur valide pour un bouton radio, cette méthode lève une exception.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="issupported"></a>  CTaskDialog::IsSupported  
 Détermine si l’ordinateur qui exécute l’application prend en charge la `CTaskDialog`.  
  
```  
static BOOL IsSupported();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si l’ordinateur prend en charge la `CTaskDialog`; `FALSE` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction pour déterminer lors de l’exécution si l’ordinateur qui exécute votre application prend en charge la `CTaskDialog Class`. Si l’ordinateur ne prend pas en charge la `CTaskDialog`, vous devez fournir une autre méthode de communication des informations à l’utilisateur. Votre application se bloque si elle tente d’utiliser un `CTaskDialog` sur un ordinateur qui ne prend pas en charge la `CTaskDialog` classe.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="loadcommandcontrols"></a>  CTaskDialog::LoadCommandControls  
 Ajoute des contrôles de bouton de commande à l’aide de données à partir de la table de chaînes.  
  
```  
void LoadCommandControls(
    int nIDCommandControlsFirst,  
    int nIDCommandControlsLast);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nIDCommandControlsFirst`  
 L’ID de chaîne de la première commande.  
  
 [in] `nIDCommandControlsLast`  
 L’ID de chaîne de la dernière commande.  
  
### <a name="remarks"></a>Notes  
 Cette méthode crée des contrôles de bouton de commande à l’aide des données à partir du fichier de ressources de votre application. La table de chaînes dans le fichier de ressources a plusieurs chaînes avec l’ID de chaîne associé. Nouveaux contrôles de bouton de commande ajoutés à l’aide de cette méthode utilisent la chaîne pour la légende du contrôle et l’ID de chaîne pour l’ID de. du contrôle La plage de chaînes sélectionné est fournie par `nIDCommandControlsFirst` et `nCommandControlsLast`(inclus). S’il existe une entrée vide dans la plage, la méthode n’ajoute pas de contrôle de bouton de commande pour cette entrée.  
  
 Par défaut, les nouveaux contrôles de bouton de commande sont activés et ne nécessitent pas d’élévation.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons  
 Ajoute des contrôles de bouton radio en utilisant des données à partir de la table de chaînes.  
  
```  
void LoadRadioButtons(
    int nIDRadioButtonsFirst,  
    int nIDRadioButtonsLast);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nIDRadioButtonsFirst`  
 L’ID de chaîne du premier bouton radio.  
  
 [in] `nIDRadioButtonsLast`  
 L’ID de chaîne de la dernière case.  
  
### <a name="remarks"></a>Notes  
 Cette méthode crée des cases d’option à l’aide des données à partir du fichier de ressources de votre application. La table de chaînes dans le fichier de ressources a plusieurs chaînes avec l’ID de chaîne associé. Des boutons radio ajoutés à l’aide de cette méthode utilisent ID de la case d’option la chaîne pour la légende du bouton de la case d’option et l’ID de chaîne La plage de chaînes sélectionné est fournie par `nIDRadioButtonsFirst` et `nRadioButtonsLast`(inclus). S’il existe une entrée vide dans la plage, la méthode n’ajoute pas d’une case d’option pour cette entrée.  
  
 Par défaut, des boutons radio sont activés.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="navigateto"></a>  CTaskDialog::NavigateTo  
 Transfère le focus vers un autre `CTaskDialog`.  
  
```  
protected:  
void NavigateTo(CTaskDialog& oTaskDialog) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `oTaskDialog`  
 Le `CTaskDialog` qui reçoit le focus.  
  
### <a name="remarks"></a>Notes  
 Cette méthode masque actuel `CTaskDialog` lorsqu’il affiche la `oTaskDialog`. Le `oTaskDialog` s’affiche dans le même emplacement qu’actuel `CTaskDialog`.  
  
##  <a name="oncommandcontrolclick"></a>  CTaskDialog::OnCommandControlClick  
 L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un contrôle de bouton de commande.  
  
```  
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nCommandControlID`  
 L’ID du contrôle de bouton de commande que l’utilisateur sélectionné.  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="oncreate"></a>  CTaskDialog::OnCreate  
 L’infrastructure appelle cette méthode après avoir créé le `CTaskDialog`.  
  
```  
virtual HRESULT OnCreate();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy  
 L’infrastructure appelle cette méthode immédiatement avant elle détruit le `CTaskDialog`.  
  
```  
virtual HRESULT OnDestroy();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="onexpandbuttonclick"></a>  CTaskDialog::OnExpandButtonClick  
 L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur le bouton de développement.  
  
```  
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bExpanded`  
 Une valeur différente de zéro indique que les informations supplémentaires s’affiche. 0 indique que les informations supplémentaires sont masquées.  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="onhelp"></a>  CTaskDialog::OnHelp  
 L’infrastructure appelle cette méthode lorsque l’utilisateur demande l’aide.  
  
```  
virtual HRESULT OnHelp();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick  
 L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur un lien hypertexte.  
  
```  
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strHref`  
 Chaîne qui représente le lien hypertexte.  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) avant de retourner `S_OK`.  
  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="oninit"></a>  CTaskDialog::OnInit  
 L’infrastructure appelle cette méthode lorsque le `CTaskDialog` est initialisé.  
  
```  
virtual HRESULT OnInit();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage  
 L’infrastructure appelle cette méthode en réponse à la [CTaskDialog::NavigateTo](#navigateto) (méthode).  
  
```  
virtual HRESULT OnNavigatePage();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick  
 L’infrastructure appelle cette méthode lorsque l’utilisateur sélectionne un contrôle case d’option.  
  
```  
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nRadioButtonID`  
 L’ID du contrôle de bouton radio que l’utilisateur a cliqué.  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="ontimer"></a>  CTaskDialog::OnTimer  
 L’infrastructure appelle cette méthode lorsque le minuteur expire.  
  
```  
virtual HRESULT OnTimer(long lTime);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lTime`  
 Durée en millisecondes depuis le `CTaskDialog` a été créé ou le minuteur a été réinitialisé.  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="onverificationcheckboxclick"></a>  CTaskDialog::OnVerificationCheckboxClick  
 L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur la case à cocher de vérification.  
  
```  
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bChecked`  
 `TRUE` Indique la vérification est activée ; `FALSE` indique qu’il n’est pas.  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour implémenter un comportement personnalisé.  
  
##  <a name="removeallcommandcontrols"></a>  CTaskDialog::RemoveAllCommandControls  
 Supprime tous les contrôles de bouton de commande à partir de la `CTaskDialog`.  
  
```  
void RemoveAllCommandControls();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="removeallradiobuttons"></a>  CTaskDialog::RemoveAllRadioButtons  
 Supprime tous les boutons de case d’option à partir de la `CTaskDialog`.  
  
```  
void RemoveAllRadioButtons();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setcommandcontroloptions"></a>  CTaskDialog::SetCommandControlOptions  
 Met à jour un contrôle de bouton de commande sur le `CTaskDialog`.  
  
```  
void SetCommandControlOptions(
    int nCommandControlID,  
    BOOL bEnabled,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nCommandControlID`  
 L’ID du contrôle de commande pour mettre à jour.  
  
 [in] `bEnabled`  
 Un paramètre booléen qui indique si le contrôle de bouton de commande spécifiée est activé ou désactivé.  
  
 [in] `bRequiresElevation`  
 Un paramètre booléen qui indique si le contrôle de bouton de commande spécifiée requiert une élévation.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour modifier un contrôle de bouton de commande est activé ou qu’il nécessite des privilèges élevés après qu’il a été ajouté à la `CTaskDialog Class`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions  
 Met à jour un sous-ensemble des boutons courants pour être activé et requièrent une élévation de compte d’utilisateur.  
  
```  
void SetCommonButtonOptions(
    int nDisabledButtonMask,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nDisabledButtonMask`  
 Un masque pour les boutons courantes à désactiver.  
  
 [in] `nElevationButtonMask`  
 Un masque pour les boutons courantes qui requièrent une élévation.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez définir les boutons courants disponibles à une instance de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md) à l’aide du constructeur [CTaskDialog::CTaskDialog](#ctaskdialog) et la méthode [CTaskDialog::SetCommonButtons ](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` ne prend pas en charge l’ajout de nouveaux boutons courants.  
  
 Si vous utilisez cette méthode pour désactiver ou élever un bouton commun qui n’est pas disponible pour ce `CTaskDialog`, cette méthode lève une exception à l’aide de la [Vérifiez](diagnostic-services.md#ensure) (macro).  
  
 Cette méthode permet de n’importe quel bouton est disponible pour le `CTaskDialog` mais ne figure pas dans le `nDisabledButtonMask`, même si elle a été précédemment désactivée. Cette méthode traite une élévation de la même manière : il enregistre les boutons courants comme ne nécessitant ne pas d’élévation si le bouton commun est disponible mais non inclus dans `nElevationButtonMask`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons  
 Ajoute des boutons courantes à le `CTaskDialog`.  
  
```  
void SetCommonButtons(
    int nButtonMask,  
    int nDisabledButtonMask = 0,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nButtonMask`  
 Un masque des boutons à ajouter à la `CTaskDialog`.  
  
 [in] `nDisabledButtonMask`  
 Un masque des boutons pour le désactiver.  
  
 [in] `nElevationButtonMask`  
 Un masque des boutons qui requièrent une élévation.  
  
### <a name="remarks"></a>Notes  
 Vous ne pouvez pas appeler cette méthode après la fenêtre d’affichage pour cette instance de la `CTaskDialog Class` est créé. Si vous le faites, cette méthode lève une exception.  
  
 Les boutons indiquaient par `nButtonMask` remplacer des boutons courantes précédemment ajoutés à la `CTaskDialog`. Seuls les boutons figurant `nButtonMask` sont disponibles.  
  
 Si le paramètre `nDisabledButtonMask` ou `nElevationButtonMask` contient un bouton qui n’est pas `nButtonMask`, cette méthode lève une exception à l’aide de la [Vérifiez](diagnostic-services.md#ensure) (macro).  
  
 Par défaut, tous les boutons courantes sont activés et ne nécessitent pas d’élévation.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcontent"></a>  CTaskDialog::SetContent  
 Met à jour le contenu de la `CTaskDialog`.  
  
```  
void SetContent(const CString& strContent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strContent`  
 Chaîne à afficher à l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 Le contenu de la `CTaskDialog Class` est le texte qui s’affiche à l’utilisateur dans la section principale de la boîte de dialogue.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setdefaultcommandcontrol"></a>  CTaskDialog::SetDefaultCommandControl  
 Spécifie le contrôle de bouton de commande par défaut.  
  
```  
void SetDefaultCommandControl(int nCommandControlID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nCommandControlID`  
 ID du contrôle de bouton de commande à la valeur par défaut.  
  
### <a name="remarks"></a>Notes  
 Le contrôle de bouton de commande par défaut est le contrôle qui est sélectionné lorsque le `CTaskDialog` est d’abord affiché à l’utilisateur.  
  
 Cette méthode lève une exception si elle ne peut pas trouver le contrôle de bouton de commande spécifié par `nCommandControlID`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setdefaultradiobutton"></a>  CTaskDialog::SetDefaultRadioButton  
 Spécifie la case d’option par défaut.  
  
```  
void SetDefaultRadioButton(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nRadioButtonID`  
 ID de la case d’option par défaut.  
  
### <a name="remarks"></a>Notes  
 La case d’option par défaut est le bouton est sélectionné lorsque le `CTaskDialog` est d’abord affiché à l’utilisateur.  
  
 Cette méthode lève une exception s’il ne trouve pas la case d’option spécifiée par `nRadioButtonID`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth  
 Ajuste la largeur de la `CTaskDialog`.  
  
```  
void SetDialogWidth(int nWidth = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nWidth`  
 La largeur de la boîte de dialogue, en pixels.  
  
### <a name="remarks"></a>Notes  
 Le paramètre `nWidth` doit être supérieur ou égal à 0. Sinon, cette méthode lève une exception.  
  
 Si `nWidth` est définie sur 0, cette méthode définit la boîte de dialogue à la taille par défaut.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setexpansionarea"></a>  CTaskDialog::SetExpansionArea  
 Met à jour la zone d’extension de la `CTaskDialog`.  
  
```  
void SetExpansionArea(
    const CString& strExpandedInformation,  
    const CString& strCollapsedLabel = _T(""),  
    const CString& strExpandedLabel = _T(""));
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strExpandedInformation`  
 La chaîne que le `CTaskDialog` affiche dans le corps principal de la boîte de dialogue lorsque l’utilisateur clique sur le bouton de développement.  
  
 [in] `strCollapsedLabel`  
 La chaîne que le `CTaskDialog` affiche en regard du bouton d’extension lors de la zone étendue est réduite.  
  
 [in] `strExpandedLabel`  
 La chaîne que le `CTaskDialog` affiche en regard du bouton d’extension lors de la zone étendue s’affiche.  
  
### <a name="remarks"></a>Notes  
 La zone d’extension de la `CTaskDialog Class` vous permet de fournir des informations supplémentaires à l’utilisateur. La zone d’extension est dans la partie principale de la `CTaskDialog`, qui se trouve immédiatement en dessous de la chaîne de titre et le contenu.  
  
 Lorsque le `CTaskDialog` est le premier affiché, il n’affiche pas les informations étendues et place `strCollapsedLabel` en regard du bouton d’extension. Lorsque l’utilisateur clique sur le bouton de développement, le `CTaskDialog` affiche `strExpandedInformation` et modifie l’étiquette à `strExpandedLabel`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon  
 Met à jour l’icône de pied de page de la `CTaskDialog`.  
  
```  
void SetFooterIcon(HICON hFooterIcon);  
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hFooterIcon`  
 L’icône Nouveau pour le `CTaskDialog`.  
  
 [in] `lpszFooterIcon`  
 L’icône Nouveau pour le `CTaskDialog`.  
  
### <a name="remarks"></a>Notes  
 L’icône de pied de page s’affiche au bas de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Peut avoir associé à pied de page. Vous pouvez modifier le texte de pied de page avec [CTaskDialog::SetFooterText](#setfootertext).  
  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) (macro) si le `CTaskDialog` est affiché ou le paramètre d’entrée est `NULL`.  
  
 A `CTaskDialog` accepte uniquement un `HICON` ou `LPCWSTR` sous forme d’une icône de pied de page. Ceci est configuré en définissant l’option `TDF_USE_HICON_FOOTER` dans le constructeur ou [CTaskDialog::SetOptions](#setoptions). Par défaut, le `CTaskDialog` est configuré pour utiliser `LPCWSTR` comme type d’entrée pour l’icône de pied de page. Cette méthode génère une exception si vous essayez de définir l’icône de l’aide du type inapproprié.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText  
 Met à jour le texte dans le pied de page de la `CTaskDialog`.  
  
```  
void SetFooterText(const CString& strFooterText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strFooterText`  
 Le nouveau texte du pied de page.  
  
### <a name="remarks"></a>Notes  
 L’icône de pied de page s’affiche en regard du texte de pied de page au bas de la `CTaskDialog`. Vous pouvez modifier l’icône de pied de page avec [CTaskDialog::SetFooterIcon](#setfootericon).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmainicon"></a>  CTaskDialog::SetMainIcon  
 Met à jour l’icône principale de la `CTaskDialog`.  
  
```  
void SetMainIcon(HICON hMainIcon);  
void SetMainIcon(LPCWSTR lpszMainIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hMainIcon`  
 L’icône Nouveau.  
  
 [in] `lpszMainIcon`  
 L’icône Nouveau.  
  
### <a name="remarks"></a>Notes  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) (macro) si le `CTaskDialog` est affiché ou le paramètre d’entrée est `NULL`.  
  
 A `CTaskDialog` accepte uniquement un `HICON` ou `LPCWSTR` sous forme d’icône principal. Vous pouvez configurer cela en définissant le `TDF_USE_HICON_MAIN` option dans le constructeur ou en la [CTaskDialog::SetOptions](#setoptions) (méthode). Par défaut, le `CTaskDialog` est configuré pour utiliser `LPCWSTR` comme type d’entrée pour l’icône principale. Cette méthode génère une exception si vous essayez de définir l’icône de l’aide du type inapproprié.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmaininstruction"></a>  CTaskDialog::SetMainInstruction  
 Met à jour l’instruction principale de la `CTaskDialog`.  
  
```  
void SetMainInstruction(const CString& strInstructions);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strInstructions`  
 La nouvelle instruction principale.  
  
### <a name="remarks"></a>Notes  
 L’instruction principale de la `CTaskDialog Class` est le texte affiché à l’utilisateur dans une grande taille de police en gras. Il se trouve dans la boîte de dialogue en dessous de la barre de titre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setoptions"></a>  CTaskDialog::SetOptions  
 Configure les options pour le `CTaskDialog`.  
  
```  
void SetOptions(int nOptionFlag);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nOptionFlag`  
 Le jeu d’indicateurs à utiliser pour le `CTaskDialog`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode efface toutes les options actuelles pour le `CTaskDialog`. Pour conserver les options actuelles, vous devez les récupérer tout d’abord avec [CTaskDialog::GetOptions](#getoptions) et de les combiner avec les options que vous souhaitez définir.  
  
 Le tableau suivant répertorie toutes les options valides.  
  
 `TDF_ENABLE_HYPERLINKS`  
 Permet à des liens hypertexte dans le `CTaskDialog`.  
  
 `TDF_USE_HICON_MAIN`  
 Configure le `CTaskDialog` à utiliser un `HICON` pour l’icône principale. L’alternative consiste à utiliser un `LPCWSTR`.  
  
 `TDF_USE_HICON_FOOTER`  
 Configure le `CTaskDialog` à utiliser un `HICON` pour l’icône de pied de page. L’alternative consiste à utiliser un `LPCWSTR`.  
  
 `TDF_ALLOW_DIALOG_CANCELLATION`  
 Permet à l’utilisateur fermer la `CTaskDialog` à l’aide du clavier ou à l’aide de l’icône dans le coin supérieur droit de la boîte de dialogue, même si le **Annuler** bouton n’est pas activé. Si cet indicateur n’est pas défini et la **Annuler** bouton n’est pas activé, l’utilisateur ne peut pas fermer la boîte de dialogue à l’aide de Alt + F4, la touche ÉCHAP, ou bouton de fermeture de la barre de titre.  
  
 `TDF_USE_COMMAND_LINKS`  
 Configure le `CTaskDialog` à utiliser les contrôles de bouton de commande.  
  
 `TDF_USE_COMMAND_LINKS_NO_ICON`  
 Configure le `CTaskDialog` à utiliser les contrôles de bouton de commande sans affichage d’une icône en regard du contrôle. `TDF_USE_COMMAND_LINKS` se substitue à `TDF_USE_COMMAND_LINKS_NO_ICON`.  
  
 `TDF_EXPAND_FOOTER_AREA`  
 Indique la zone d’extension est actuellement développée.  
  
 `TDF_EXPANDED_BY_DEFAULT`  
 Détermine si la zone d’extension est développée par défaut.  
  
 `TDF_VERIFICATION_FLAG_CHECKED`  
 Indique que la case à cocher de vérification est actuellement sélectionnée.  
  
 `TDF_SHOW_PROGRESS_BAR`  
 Configure le `CTaskDialog` pour afficher une barre de progression.  
  
 `TDF_SHOW_MARQUEE_PROGRESS_BAR`  
 Configure la barre de progression à une barre de progression texte défilant. Si vous activez cette option, vous devez définir `TDF_SHOW_PROGRESS_BAR` pour que le comportement attendu.  
  
 `TDF_CALLBACK_TIMER`  
 Indique que le `CTaskDialog` intervalle de rappel est défini sur environ 200 millisecondes.  
  
 `TDF_POSITION_RELATIVE_TO_WINDOW`  
 Configure le `CTaskDialog` sera centré par rapport à la fenêtre parente. Si cet indicateur n’est pas activé, le `CTaskDialog` est centrée par rapport à l’analyse.  
  
 `TDF_RTL_LAYOUT`  
 Configure le `CTaskDialog` pour une lecture de droite à gauche.  
  
 `TDF_NO_DEFAULT_RADIO_BUTTON`  
 Indique qu’aucune case d’option n’est sélectionnée lorsque le `CTaskDialog` s’affiche.  
  
 `TDF_CAN_BE_MINIMIZED`  
 Permet à l’utilisateur afin de réduire le `CTaskDialog`. Pour prendre en charge cette option, le `CTaskDialog` ne peut pas être modal. MFC ne prend pas en charge cette option, car les MFC ne prend pas en charge un non modal `CTaskDialog`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee  
 Configure une barre de sélection pour la `CTaskDialog` et l’ajoute à la boîte de dialogue.  
  
```  
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,  
    int nMarqueeSpeed = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnabled`  
 `TRUE` Pour activer la barre de texte défilant. `FALSE` pour désactiver la barre de sélection et la supprimer à partir de la `CTaskDialog`.  
  
 [in] `nMarqueeSpeed`  
 Entier qui indique la vitesse de la barre de texte défilant.  
  
### <a name="remarks"></a>Notes  
 La barre de sélection apparaît sous le texte principal de la `CTaskDialog Class`.  
  
 Utilisez `nMarqueeSpeed` pour définir la vitesse de la barre de texte défilant ; des valeurs supérieures indiquent une vitesse plus lente. La valeur 0 pour `nMarqueeSpeed` déplace la barre de sélection à la vitesse de la valeur par défaut pour Windows.  
  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) macro si `nMarqueeSpeed` est inférieur à 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarposition"></a>  CTaskDialog::SetProgressBarPosition  
 Ajuste la position de la barre de progression.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nProgressPos`  
 La position de la barre de progression.  
  
### <a name="remarks"></a>Notes  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) macro si `nProgressPos` n’est pas dans la plage de barre de progression. Vous pouvez modifier la plage de barre de progression avec [CTaskDialog::SetProgressBarRange](#setprogressbarrange).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarrange"></a>  CTaskDialog::SetProgressBarRange  
 Ajuste la plage de la barre de progression.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nRangeMin`  
 La limite inférieure de la barre de progression.  
  
 [in] `nRangeMax`  
 La limite supérieure de la barre de progression.  
  
### <a name="remarks"></a>Notes  
 La position de la barre de progression est relatif au `nRangeMin` et `nRangeMax`. Par exemple, si `nRangeMin` est 50 et `nRangeMax` est 100, une position de 75 se trouve à mi-chemin entre la barre de progression. Utilisez [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) pour définir la position de la barre de progression.  
  
 Pour afficher la progression de la barre, l’option `TDF_SHOW_PROGRESS_BAR` doit être activé et `TDF_SHOW_MARQUEE_PROGRESS_BAR` ne doit pas être activé. Cette méthode définit automatiquement `TDF_SHOW_PROGRESS_BAR` et efface `TDF_SHOW_MARQUEE_PROGRESS_BAR`. Utilisez [CTaskDialog::SetOptions](#setoptions) pour modifier manuellement les options de cette instance de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md).  
  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) macro si `nRangeMin` est au moins `nRangeMax`. Cette méthode lève également une exception si la `CTaskDialog` est déjà affichée et a une barre de progression texte défilant.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState  
 Définit l’état de la barre de progression et l’affiche sur la `CTaskDialog`.  
  
```  
void SetProgressBarState(int nState = PBST_NORMAL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nState`  
 L’état de la barre de progression. Consultez la section Notes pour les valeurs possibles.  
  
### <a name="remarks"></a>Notes  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) macro si la `CTaskDialog` est déjà affichée et a une barre de progression texte défilant.  
  
 Le tableau suivant répertorie les valeurs possibles pour `nState`. Dans tous ces cas, la barre de progression est renseignées avec la couleur normale jusqu'à atteindre la position d’arrêt désigné. À ce stade il change de couleur en fonction de l’état.  
  
 PBST_NORMAL  
 Après la progression barre se remplit, le `CTaskDialog` ne modifie pas la couleur de la barre. Par défaut, la couleur normale est verte.  
  
 PBST_ERROR  
 Après la progression barre se remplit, le `CTaskDialog` modifie la couleur de la barre de la couleur de l’erreur. Par défaut, il s’agit rouge.  
  
 PBST_PAUSED  
 Après la progression barre se remplit, le `CTaskDialog` modifie la couleur de la barre de la couleur en pause. Par défaut, il s’agit jaune.  
  
 Vous pouvez définir où la barre de progression s’arrête avec [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setradiobuttonoptions"></a>  CTaskDialog::SetRadioButtonOptions  
 Active ou désactive une case d’option.  
  
```  
void SetRadioButtonOptions(
    int nRadioButtonID,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nRadioButtonID`  
 L’ID du contrôle de bouton radio.  
  
 [in] `bEnabled`  
 `TRUE` Pour activer le bouton radio ; `FALSE` pour désactiver la case d’option.  
  
### <a name="remarks"></a>Notes  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) macro si `nRadioButtonID` n’est pas un ID valid pour une case d’option.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setverificationcheckbox"></a>  CTaskDialog::SetVerificationCheckbox  
 Définit l’état activé de la case à cocher de vérification.  
  
```  
void SetVerificationCheckbox(BOOL bChecked);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bChecked`  
 `TRUE` Pour que la vérification de la case à cocher activée lorsque le `CTaskDialog` est affichée ; `FALSE` pour que la vérification de la case à cocher désactivée lorsque le `CTaskDialog` s’affiche.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setverificationcheckboxtext"></a>  CTaskDialog::SetVerificationCheckboxText  
 Définit le texte qui s’affiche à droite de la case à cocher de vérification.  
  
```  
void SetVerificationCheckboxText(CString& strVerificationText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strVerificationText`  
 Le texte que cette méthode s’affiche en regard de la case à cocher de vérification.  
  
### <a name="remarks"></a>Notes  
 Cette méthode lève une exception avec le [Vérifiez](diagnostic-services.md#ensure) macro si cette instance de la `CTaskDialog Class` est déjà affichée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setwindowtitle"></a>  CTaskDialog::SetWindowTitle  
 Définit le titre de la `CTaskDialog`.  
  
```  
void SetWindowTitle(CString& strWindowTitle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strWindowTitle`  
 Le nouveau titre pour le `CTaskDialog`.  
  
### <a name="remarks"></a>Notes  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="showdialog"></a>  CTaskDialog::ShowDialog  
 Crée et affiche un `CTaskDialog`.  
  
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
 [in] `strContent`  
 La chaîne à utiliser pour le contenu de la `CTaskDialog`.  
  
 [in] `strMainInstruction`  
 L’instruction principale de la `CTaskDialog`.  
  
 [in] `strTitle`  
 Le titre de la `CTaskDialog`.  
  
 [in] `nIDCommandControlsFirst`  
 L’ID de chaîne de la première commande.  
  
 [in] `nIDCommandControlsLast`  
 L’ID de chaîne de la dernière commande.  
  
 [in] `nCommonButtons`  
 Un masque des boutons à ajouter à la `CTaskDialog`.  
  
 [in] `nTaskDialogOptions`  
 Le jeu d’options à utiliser pour le `CTaskDialog`.  
  
 [in] `strFooter`  
 La chaîne à utiliser dans le pied de page.  
  
### <a name="return-value"></a>Valeur de retour  
 Entier qui correspond à la sélection effectuée par l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 Cette méthode statique permet de créer une instance de la `CTaskDialog Class` sans créer explicitement un `CTaskDialog` objet dans votre code. Étant donné qu’aucun `CTaskDialog` de l’objet, vous ne pouvez pas appeler d’autres méthodes de la `CTaskDialog` si vous utilisez cette méthode pour afficher un `CTaskDialog` à l’utilisateur.  
  
 Cette méthode crée des contrôles de bouton de commande à l’aide des données à partir du fichier de ressources de votre application. La table de chaînes dans le fichier de ressources a plusieurs chaînes avec l’ID de chaîne associé. Cette méthode ajoute un contrôle de bouton de commande pour chaque entrée valide dans la table de chaînes entre `nIDCommandControlsFirst` et `nCommandControlsLast`(inclus). Pour ces contrôles de bouton de commande, la chaîne de la table de chaînes est la légende du contrôle et l’ID de chaîne ID de. du contrôle  
  
 Consultez [CTaskDialog::SetOptions](#setoptions) pour obtenir la liste des options valides.  
  
 Le `CTaskDialog` se ferme lorsque l’utilisateur sélectionne un bouton commun, un contrôle de lien de commande, ou ferme le `CTaskDialog`. La valeur de retour est l’identificateur qui indique la façon dont l’utilisateur a fermé la boîte de dialogue.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback  
 L’infrastructure appelle cette méthode en réponse à différents messages de Windows.  
  
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
 [in] `hwnd`  
 Un handle vers le `m_hWnd` la structure de la `CTaskDialog`.  
  
 [in] `uNotification`  
 Le code de notification qui spécifie le message généré.  
  
 [in] `wParam`  
 Plus d’informations sur le message.  
  
 [in] `lParam`  
 Plus d’informations sur le message.  
  
 [in] `dwRefData`  
 Un pointeur vers le `CTaskDialog` objet auquel s’applique le message de rappel.  
  
### <a name="return-value"></a>Valeur de retour  
 Dépend du code de notification spécifique. Pour plus d'informations, consultez la section Notes.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de `TaskDialogCallback` gère le message spécifique, puis appelle approprié sur la méthode de la [classe CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Par exemple, en réponse à la `TDN_BUTTON_CLICKED` message, `TaskDialogCallback` appelle [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).  
  
 Les valeurs de `wParam` et `lParam` dépendent du message généré spécifique. Il est possible pour un ou les deux de ces valeurs est vide. Le tableau suivant répertorie les notifications par défaut qui sont prises en charge et ce que les valeurs de `wParam` et `lParam` représentent. Si vous substituez cette méthode dans une classe dérivée, vous devez implémenter le code de rappel pour chaque message dans le tableau suivant.  
  
|Message de notification|Valeur `wParam`|Valeur `lParam`|  
|--------------------------|--------------------|--------------------|  
|`TDN_CREATED`|Non utilisé.|Non utilisé.|  
|`TDN_NAVIGATED`|Non utilisé.|Non utilisé.|  
|`TDN_BUTTON_CLICKED`|ID de contrôle de bouton de commande|Non utilisé.|  
|`TDN_HYPERLINK_CLICKED`|Non utilisé.|A [LPCWSTR](http://msdn.microsoft.com/library/windows/desktop/aa383751) structure qui contient le lien.|  
|`TDN_TIMER`|Durée en millisecondes depuis le `CTaskDialog` a été créé ou le minuteur a été réinitialisé.|Non utilisé.|  
|`TDN_DESTROYED`|Non utilisé.|Non utilisé.|  
|`TDN_RADIO_BUTTON_CLICKED`|L’ID de bouton radio.|Non utilisé.|  
|`TDN_DIALOG_CONSTRUCTED`|Non utilisé.|Non utilisé.|  
|`TDN_VERIFICATION_CLICKED`|1 si la case à cocher est activée, 0 si elle n’est pas.|Non utilisé.|  
|`TDN_HELP`|Non utilisé.|Non utilisé.|  
|`TDN_EXPANDO_BUTTON_CLICKED`|0 si la zone d’expansion est réduite ; différent de zéro si le texte de l’expansion est affiché.|Non utilisé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Procédure pas à pas : ajout d’une classe CTaskDialog à une application](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)



