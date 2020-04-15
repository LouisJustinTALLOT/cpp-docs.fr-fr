---
title: Classe CDialog
ms.date: 09/07/2019
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
ms.openlocfilehash: cad762f426012d9d1931b96d54d8a53c9bab465d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375644"
---
# <a name="cdialog-class"></a>Classe CDialog

La classe de base utilisée pour afficher des boîtes de dialogue sur l’écran.

## <a name="syntax"></a>Syntaxe

```
class CDialog : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Construit un objet `CDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDialog::Créer](#create)|Initialise l'objet `CDialog`. Crée une boîte de dialogue sans mode `CDialog` et la fixe à l’objet.|
|[CDialog::CreateIndirect](#createindirect)|Crée une boîte de dialogue sans mode à partir d’un modèle de boîte de dialogue dans la mémoire (pas basé sur les ressources).|
|[CDialog::DoModal](#domodal)|Appelle une boîte de dialogue modal et revient une fois terminé.|
|[CDialog::EndDialog](#enddialog)|Ferme une boîte de dialogue modal.|
|[CDialog::GetDefID](#getdefid)|Obtient l’ID du contrôle par défaut pushbutton pour une boîte de dialogue.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Déplace l’accent vers un contrôle spécifié de la boîte de dialogue dans la boîte de dialogue.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Crée une boîte de dialogue modal à partir d’un modèle de boîte de dialogue dans la mémoire (pas basé sur les ressources). Les paramètres sont stockés `DoModal` jusqu’à ce que la fonction soit appelée.|
|[CDialog::MapDialogRect](#mapdialogrect)|Convertit les unités de boîte de dialogue d’un rectangle en unités d’écran.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Déplace l’accent vers le prochain contrôle de la boîte de dialogue dans la boîte de dialogue.|
|[CDialog::OnInitDialog](#oninitdialog)|Remplacer pour augmenter l’initialisation de la boîte de dialogue.|
|[CDialog::OnSetFont](#onsetfont)|Remplacer pour spécifier la police qu’un contrôle de la boîte de dialogue doit utiliser lorsqu’il tire du texte.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Déplace l’accent sur le contrôle précédent de la boîte de dialogue dans la boîte de dialogue.|
|[CDialog::SetDefID](#setdefid)|Modifie le contrôle par défaut du pushbutton pour une boîte de dialogue à un pushbutton spécifié.|
|[CDialog::SetHelpID](#sethelpid)|Définit une pièce d’identité d’aide sensible au contexte pour la boîte de dialogue.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Remplacement pour effectuer le bouton Annuler ou l’action clé ESC. La valeur par défaut ferme `DoModal` la boîte de dialogue et renvoie IDCANCEL.|
|[CDialog::OnOK](#onok)|Remplacer pour effectuer l’action bouton OK dans une boîte de dialogue modal. La valeur par défaut ferme `DoModal` la boîte de dialogue et renvoie IDOK.|

## <a name="remarks"></a>Notes

Les boîtes de dialogue sont de deux types : modales et sans mode. Une boîte de dialogue modal doit être fermée par l’utilisateur avant que l’application ne se poursuive. Une boîte de dialogue sans mode permet à l’utilisateur d’afficher la boîte de dialogue et de revenir à une autre tâche sans annuler ou supprimer la boîte de dialogue.

Un `CDialog` objet est une combinaison d’un modèle de dialogue et d’une `CDialog`classe dérivée. Utilisez l’éditeur de dialogue pour créer le modèle de dialogue et le stocker dans `CDialog`une ressource, puis utilisez le magicien de classe Add pour créer une classe dérivée de .

Une boîte de dialogue, comme toute autre fenêtre, reçoit des messages de Windows. Dans une boîte de dialogue, vous êtes particulièrement intéressé à traiter les messages de notification à partir des contrôles de la boîte de dialogue puisque c’est ainsi que l’utilisateur interagit avec votre boîte de dialogue. Utilisez [l’assistant de classe](mfc-class-wizard.md) pour sélectionner les messages que vous souhaitez gérer et il ajoutera les entrées de carte de message appropriées et les fonctions des membres de message-gestionnaire à la classe pour vous. Vous n’avez qu’à écrire du code spécifique à l’application dans les fonctions des membres du gestionnaire.

Si vous préférez, vous pouvez toujours écrire des entrées de carte de message et des fonctions de membre manuellement.

Dans toutes les cases de dialogue, sauf les plus triviales, vous ajoutez des variables de membre à votre classe de dialogue dérivée pour stocker les données saisies dans les contrôles de la boîte de dialogue par l’utilisateur ou pour afficher les données pour l’utilisateur. Vous pouvez utiliser l’assistant Add Variable pour créer des variables membres et les associer à des contrôles. En même temps, vous choisissez un type variable et une gamme de valeurs permise pour chaque variable. L’assistant de code ajoute les variables du membre à votre classe de dialogue dérivée.

Une carte de données est générée pour gérer automatiquement l’échange de données entre les variables du membre et les contrôles de la boîte de dialogue. La carte des données fournit des fonctions qui initialisent les contrôles dans la boîte de dialogue avec les valeurs appropriées, récupèrent les données et valident les données.

Pour créer une boîte de dialogue modal, construisez un objet sur la pile `DoModal` à l’aide du constructeur pour votre classe de dialogue dérivée, puis appelez pour créer la fenêtre de dialogue et ses commandes. Si vous souhaitez créer un dialogue `Create` sans mode, faites appel au constructeur de votre classe de dialogue.

Vous pouvez également créer un modèle en mémoire en utilisant une structure de données [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) telle que décrite dans le SDK Windows. Après avoir `CDialog` construit un objet, appelez [CreateIndirect](#createindirect) pour créer une boîte de dialogue sans mode, ou appelez [InitModalIndirect](#initmodalindirect) et [DoModal](#domodal) pour créer une boîte de dialogue modal.

La carte des données d’échange et `CWnd::DoDataExchange` de validation est écrite dans un remplacement de ce qui est ajouté à votre nouvelle classe de dialogue. Consultez la fonction membre [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) pour en savoir `CWnd` plus sur les fonctionnalités d’échange et de validation.

Le programmeur et le `DoDataExchange` cadre appellent indirectement par un appel à [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Le cadre `UpdateData` appelle lorsque l’utilisateur clique sur le bouton OK pour fermer une boîte de dialogue modal. (Les données ne sont pas récupérées si le bouton Annuler est cliqué.) La mise en œuvre par `UpdateData` défaut d’OnInitDialog appelle également à définir les valeurs initiales des contrôles. [OnInitDialog](#oninitdialog) Vous remplacez `OnInitDialog` généralement pour initialiser davantage les contrôles. `OnInitDialog`est appelé après tous les contrôles de dialogue sont créés et juste avant la boîte de dialogue est affiché.

Vous pouvez `CWnd::UpdateData` appeler à tout moment lors de l’exécution d’une boîte de dialogue modale ou sans mode.

Si vous développez une boîte de dialogue à la main, vous ajoutez les variables nécessaires aux variables nécessaires à la classe de boîte de dialogue dérivée vous-même, et vous ajoutez des fonctions de membre pour définir ou obtenir ces valeurs.

Une boîte de dialogue modal se ferme automatiquement lorsque l’utilisateur appuie sur `EndDialog` les boutons OK ou Annuler ou lorsque votre code appelle la fonction du membre.

Lorsque vous implémentez une boîte de `OnCancel` dialogue sans `DestroyWindow` mode, remplacez toujours la fonction du membre et appelez de l’intérieur. N’appelez pas la `CDialog::OnCancel`classe de `EndDialog`base, parce qu’il appelle , ce qui rendra la boîte de dialogue invisible, mais ne sera pas le détruire. Vous devez également `PostNcDestroy` remplacer les boîtes de dialogue sans mode afin de supprimer **cela**, puisque les boîtes de dialogue sans mode sont généralement alloués avec **de nouvelles**. Les boîtes de dialogue modal sont généralement `PostNcDestroy` construites sur le cadre et n’ont pas besoin de nettoyage.

Pour plus `CDialog`d’informations sur , voir [Boîtes De dialogue](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cdialogcdialog"></a><a name="cdialog"></a>CDialog::CDialog

Pour construire une boîte de dialogue modal basée sur les ressources, appelez l’une ou l’autre forme publique du constructeur.

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne non terminée qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate (en)*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

*pParentWnd*<br/>
Points à l’objet de fenêtre du parent ou du propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Une forme du constructeur donne accès à la ressource de dialogue par nom de modèle. L’autre constructeur donne accès par numéro d’identification de modèle, généralement avec un préfixe **IDD_** (par exemple, IDD_DIALOG1).

Pour construire une boîte de dialogue modal à partir d’un modèle en `InitModalIndirect`mémoire, d’abord invoquer le constructeur sans paramètres et protégé, puis appeler .

Après avoir construit une boîte de dialogue modal `DoModal`avec l’une des méthodes ci-dessus, appelez .

Pour construire une boîte de dialogue sans mode, utilisez la forme protégée du `CDialog` constructeur. Le constructeur est protégé parce que vous devez dériver votre propre classe de boîte de dialogue pour implémenter une boîte de dialogue sans mode. La construction d’une boîte de dialogue sans mode est un processus en deux étapes. Appelez d’abord le constructeur; ensuite appelez `Create` la fonction membre pour créer une boîte `CreateIndirect` de dialogue basée sur les ressources, ou appelez pour créer la boîte de dialogue à partir d’un modèle dans la mémoire.

## <a name="cdialogcreate"></a><a name="create"></a>CDialog::Créer

Appelez `Create` pour créer une boîte de dialogue sans mode à l’aide d’un modèle de boîte de dialogue à partir d’une ressource.

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne non terminée qui est le nom d’une ressource de modèle de boîte de dialogue.

*pParentWnd*<br/>
Points à l’objet de fenêtre parent (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

*nIDTemplate (en)*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Les deux formes reviennent nonzero si la création et l’initialisation de la boîte de dialogue ont été couronnées de succès; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez mettre `Create` l’appel à l’intérieur du constructeur ou l’appeler après que le constructeur est invoqué.

Deux formes `Create` de la fonction membre sont fournies pour l’accès à la ressource de modèle de boîte de dialogue par nom de modèle ou numéro d’identification de modèle (par exemple, IDD_DIALOG1).

Pour l’une ou l’autre forme, passez un pointeur à l’objet de fenêtre parent. Si *pParentWnd* est NULL, la boîte de dialogue sera créée avec sa fenêtre parente ou propriétaire réglée sur la fenêtre d’application principale.

La `Create` fonction du membre revient immédiatement après qu’elle crée la boîte de dialogue.

Utilisez le style WS_VISIBLE dans le modèle de boîte de dialogue si la boîte de dialogue doit apparaître lorsque la fenêtre parente est créée. Sinon, vous `ShowWindow`devez appeler . Pour d’autres styles de dialogue-box et leur application, voir la structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) dans le Windows SDK et [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles) dans la *référence MFC*.

Utilisez `CWnd::DestroyWindow` la fonction pour détruire une `Create` boîte de dialogue créée par la fonction.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

## <a name="cdialogcreateindirect"></a><a name="createindirect"></a>CDialog::CreateIndirect

Appelez cette fonction de membre pour créer une boîte de dialogue sans mode à partir d’un modèle de boîte de dialogue dans la mémoire.

```
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*lpDialogTemplate*<br/>
Points à la mémoire qui contient un modèle de boîte de dialogue utilisé pour créer la boîte de dialogue. Ce modèle est sous la forme d’une structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) et des informations de contrôle, comme décrit dans le SDK Windows.

*pParentWnd*<br/>
Points à l’objet de fenêtre parent de l’objet de dialogue (de type [CWnd](../../mfc/reference/cwnd-class.md)). S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

*lpDialogInit*<br/>
Indique une ressource DLGINIT.

*hDialogTemplate*<br/>
Contient une poignée à la mémoire globale contenant un modèle de boîte de dialogue. Ce modèle est sous `DLGTEMPLATE` la forme d’une structure et de données pour chaque contrôle dans la boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Nonzero si la boîte de dialogue a été créée et paralysée avec succès; sinon 0.

### <a name="remarks"></a>Notes

La `CreateIndirect` fonction du membre revient immédiatement après qu’elle crée la boîte de dialogue.

Utilisez le style WS_VISIBLE dans le modèle de boîte de dialogue si la boîte de dialogue doit apparaître lorsque la fenêtre parente est créée. Sinon, vous `ShowWindow` devez appeler pour le faire apparaître. Pour plus d’informations sur la façon dont vous pouvez spécifier d’autres styles de boîte de dialogue dans le modèle, voir la structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) dans le SDK Windows.

Utilisez `CWnd::DestroyWindow` la fonction pour détruire une `CreateIndirect` boîte de dialogue créée par la fonction.

Les boîtes de dialogue qui contiennent des contrôles ActiveX nécessitent des informations supplémentaires fournies dans une ressource DLGINIT.

## <a name="cdialogdomodal"></a><a name="domodal"></a>CDialog::DoModal

Appelez cette fonction de membre pour invoquer la boîte de dialogue modal et retourner le résultat de la boîte de dialogue une fois fait.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

Une valeur **int** qui spécifie la valeur du paramètre *nResult* qui a été passé au [CDialog::EndDialog](#enddialog) fonction membre, qui est utilisé pour fermer la boîte de dialogue. La valeur de retour est de -1 si la fonction ne pouvait pas créer la boîte de dialogue, ou IDABORT si une autre erreur s’est produite, auquel cas la fenêtre de sortie contiendra des informations d’erreur de [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Cette fonction de membre gère toute interaction avec l’utilisateur pendant que la boîte de dialogue est active. C’est ce qui rend la boîte de dialogue modale; c’est-à-dire que l’utilisateur ne peut pas interagir avec d’autres fenêtres jusqu’à ce que la boîte de dialogue soit fermée.

Si l’utilisateur clique sur l’un des pushbuttons dans la boîte de dialogue, comme OK ou Annuler, une fonction de membre de message-gestionnaire, comme [OnOK](#onok) ou [OnCancel](#oncancel), est appelé pour tenter de fermer la boîte de dialogue. La `OnOK` fonction de membre par défaut validera et mettra à jour les données de `OnCancel` la boîte de dialogue et fermera la boîte de dialogue avec le résultat IDOK, et la fonction de membre par défaut fermera la boîte de dialogue avec résultat IDCANCEL sans valider ou mettre à jour les données de la boîte de dialogue. Vous pouvez remplacer ces fonctions de gestionnaire de messages pour modifier leur comportement.

> [!NOTE]
> `PreTranslateMessage`est maintenant appelé pour le traitement des messages boîte de dialogue modal.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

## <a name="cdialogenddialog"></a><a name="enddialog"></a>CDialog::EndDialog

Appelez cette fonction de membre pour mettre fin à une boîte de dialogue modal.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Paramètres

*nResult*<br/>
Contient la valeur à retourner de la boîte `DoModal`de dialogue à l’appelant de .

### <a name="remarks"></a>Notes

Cette fonction de membre renvoie *nResult* comme la valeur de retour de `DoModal`. Vous devez `EndDialog` utiliser la fonction pour terminer le traitement chaque fois qu’une boîte de dialogue modal est créée.

Vous pouvez `EndDialog` appeler à tout moment, même dans [OnInitDialog](#oninitdialog), auquel cas vous devez fermer la boîte de dialogue avant qu’il ne soit affiché ou avant que la mise au point d’entrée est définie.

`EndDialog`ne ferme pas immédiatement la boîte de dialogue. Au lieu de cela, il définit un drapeau qui dirige la boîte de dialogue à fermer dès que le gestionnaire de message actuel revient.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

## <a name="cdialoggetdefid"></a><a name="getdefid"></a>CDialog::GetDefID

Appelez `GetDefID` la fonction membre pour obtenir l’ID du contrôle par défaut pushbutton pour une boîte de dialogue.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur 32 `DWORD`bits (). Si le pushbutton par défaut a une valeur d’identification, le mot de haute commande contient DC_HASDEFID et le mot de faible ordre contient la valeur d’identification. Si le pushbutton par défaut n’a pas de valeur d’identification, la valeur de retour est de 0.

### <a name="remarks"></a>Notes

Il s’agit généralement d’un bouton OK.

## <a name="cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl

Déplace la mise au point vers le contrôle spécifié dans la boîte de dialogue.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Paramètres

*pWndCtrl*<br/>
Identifie la fenêtre (contrôle) qui doit recevoir la mise au point.

### <a name="remarks"></a>Notes

Pour obtenir un pointeur au contrôle (fenêtre enfant) pour passer `CWnd::GetDlgItem` comme *pWndCtrl*, appelez la fonction membre, qui renvoie un pointeur à un objet [CWnd.](../../mfc/reference/cwnd-class.md)

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

## <a name="cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog::InitModalIndirect

Appelez cette fonction de membre pour initialiser un objet de dialogue modal à l’aide d’un modèle de boîte de dialogue que vous construisez en mémoire.

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*lpDialogTemplate*<br/>
Points à la mémoire qui contient un modèle de boîte de dialogue utilisé pour créer la boîte de dialogue. Ce modèle est sous la forme d’une structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) et des informations de contrôle, comme décrit dans le SDK Windows.

*hDialogTemplate*<br/>
Contient une poignée à la mémoire globale contenant un modèle de boîte de dialogue. Ce modèle est sous `DLGTEMPLATE` la forme d’une structure et de données pour chaque contrôle dans la boîte de dialogue.

*pParentWnd*<br/>
Points à l’objet de fenêtre du parent ou du propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

*lpDialogInit*<br/>
Indique une ressource DLGINIT.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet de dialogue a été créé et paralysé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Pour créer indirectement une boîte de dialogue modal, d’abord allouer un bloc de mémoire global et le remplir avec le modèle de boîte de dialogue. Appelez ensuite `CDialog` le constructeur vide pour construire l’objet de la boîte de dialogue. Ensuite, `InitModalIndirect` appelez pour stocker votre poignée sur le modèle de boîte de dialogue en mémoire. La boîte de dialogue Windows est créée et affichée plus tard, lorsque la fonction membre [DoModal](#domodal) est appelée.

Les boîtes de dialogue qui contiennent des contrôles ActiveX nécessitent des informations supplémentaires fournies dans une ressource DLGINIT.

## <a name="cdialogmapdialogrect"></a><a name="mapdialogrect"></a>CDialog::MapDialogRect

Appelez pour convertir les unités de boîte de dialogue d’un rectangle en unités d’écran.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient les coordonnées de la boîte de dialogue à convertir.

### <a name="remarks"></a>Notes

Les unités de la boîte de dialogue sont indiquées en termes d’unité de base actuelle de boîte de dialogue dérivée de la largeur moyenne et de la hauteur des caractères dans la police utilisée pour le texte de la boîte de dialogue. Une unité horizontale est un quart de l’unité de largeur de base de boîte de dialogue, et une unité verticale est un huitième de l’unité de hauteur de base de boîte de dialogue.

La `GetDialogBaseUnits` fonction Windows renvoie des informations de taille pour la police système, mais vous pouvez spécifier une police différente pour chaque boîte de dialogue si vous utilisez le style DS_SETFONT dans le fichier de définition des ressources. La `MapDialogRect` fonction Windows utilise la police appropriée pour cette boîte de dialogue.

La `MapDialogRect` fonction membre remplace les unités de boîte de dialogue en *lpRect* par des unités d’écran (pixels) de sorte que le rectangle peut être utilisé pour créer une boîte de dialogue ou positionner un contrôle dans une boîte.

## <a name="cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog::NextDlgCtrl

Déplace l’accent vers le contrôle suivant dans la boîte de dialogue.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Notes

Si l’accent est mis sur le dernier contrôle dans la boîte de dialogue, il se déplace vers le premier contrôle.

## <a name="cdialogoncancel"></a><a name="oncancel"></a>CDialog::OnCancel

Le cadre appelle cette méthode lorsque l’utilisateur clique **annuler** ou appuyer sur la clé ESC dans une boîte de dialogue modale ou sans mode.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Notes

Remplacez cette méthode pour effectuer des actions (telles que la restauration de vieilles données) lorsqu’un utilisateur ferme la boîte de dialogue en cliquant sur **Annuler** ou en frappant la clé ESC. La valeur par défaut ferme une boîte de dialogue modal en appelant [EndDialog](#enddialog) et en faisant retourner [DoModal](#domodal) à IDCANCEL.

Si vous implémentez le bouton **Annuler** dans une `OnCancel` boîte de dialogue sans mode, vous devez remplacer la méthode et appeler [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) à l’intérieur. N’appelez pas la méthode de `EndDialog`la classe de base, parce qu’elle appelle , ce qui rendra la boîte de dialogue invisible mais ne la détruira pas.

> [!NOTE]
> Vous ne pouvez pas remplacer `CFileDialog` cette méthode lorsque vous utilisez un objet dans un programme qui est compilé sous Windows XP. Pour plus `CFileDialog`d’informations sur , voir [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

## <a name="cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog::OnInitDialog

Cette méthode est appelée `WM_INITDIALOG` en réponse au message.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Précise si l’application a défini l’accent sur l’entrée à l’un des contrôles dans la boîte de dialogue. Si `OnInitDialog` les retours non zéro, Windows définit la mise au point de l’entrée à l’emplacement par défaut, le premier contrôle dans la boîte de dialogue. L’application ne peut retourner 0 que si elle a explicitement défini l’accent sur l’entrée à l’un des contrôles dans la boîte de dialogue.

### <a name="remarks"></a>Notes

Windows envoie `WM_INITDIALOG` le message à la boîte de dialogue pendant les appels [Create,](#create) [CreateIndirect](#createindirect), ou [DoModal,](#domodal) qui se produisent immédiatement avant que la boîte de dialogue est affichée.

Remplacez cette méthode si vous souhaitez effectuer un traitement spécial lorsque la boîte de dialogue est paralysée. Dans la version préconcée, `OnInitDialog` appelez d’abord la classe de base, mais ignorez sa valeur de retour. Vous reviendrez `TRUE` généralement de votre méthode de dépassement.

Windows appelle `OnInitDialog` la fonction en utilisant la procédure de dialogue-boîte globale standard commune à toutes les boîtes de dialogue Microsoft Foundation Class Library. Il n’appelle pas cette fonction à travers votre carte de message, et donc vous n’avez pas besoin d’une entrée de carte de message pour cette méthode.

> [!NOTE]
> Vous ne pouvez pas remplacer `CFileDialog` cette méthode lorsque vous utilisez un objet dans un programme qui est compilé sous Windows Vista ou des systèmes d’exploitation ultérieurs. Pour plus d’informations sur les changements à `CFileDialog` sous Windows Vista et plus tard, voir [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

## <a name="cdialogonok"></a><a name="onok"></a>CDialog::OnOK

Appelé lorsque l’utilisateur clique sur le bouton **OK** (le bouton avec un ID d’IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

Remplacez cette méthode pour effectuer des actions lorsque le bouton **OK** est activé. Si la boîte de dialogue comprend la validation et l’échange automatiques de données, la mise en œuvre par défaut de cette méthode valide les données de la boîte de dialogue et met à jour les variables appropriées dans votre application.

Si vous implémentez le bouton **OK** dans une `OnOK` boîte de dialogue sans mode, vous devez remplacer la méthode et appeler [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) à l’intérieur. N’appelez pas la méthode de la classe de base, car elle appelle [EndDialog](#enddialog) qui rend la boîte de dialogue invisible mais ne la détruit pas.

> [!NOTE]
> Vous ne pouvez pas remplacer `CFileDialog` cette méthode lorsque vous utilisez un objet dans un programme qui est compilé sous Windows XP. Pour plus `CFileDialog`d’informations sur , voir [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

## <a name="cdialogonsetfont"></a><a name="onsetfont"></a>CDialog::OnSetFont

Spécifie la police qu’un contrôle de la boîte de dialogue utilisera lors du dessin du texte.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[dans] Spécifie un pointeur à la police qui sera utilisé comme police par défaut pour tous les contrôles dans cette boîte de dialogue.

### <a name="remarks"></a>Notes

La boîte de dialogue utilisera la police spécifiée comme défaut pour tous ses contrôles.

L’éditeur de dialogue définit généralement la police de la boîte de dialogue dans le cadre de la ressource de modèle de boîte de dialogue.

> [!NOTE]
> Vous ne pouvez pas remplacer `CFileDialog` cette méthode lorsque vous utilisez un objet dans un programme qui est compilé sous Windows Vista ou des systèmes d’exploitation ultérieurs. Pour plus d’informations sur les changements à `CFileDialog` sous Windows Vista et plus tard, voir [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

## <a name="cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl

Met l’accent sur le contrôle précédent dans la boîte de dialogue.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Notes

Si l’accent est mis sur le premier contrôle dans la boîte de dialogue, il se déplace vers le dernier contrôle dans la boîte.

## <a name="cdialogsetdefid"></a><a name="setdefid"></a>CDialog::SetDefID

Modifie le contrôle par défaut du pushbutton pour une boîte de dialogue.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Spécifie l’ID du contrôle du pushbutton qui deviendra la valeur par défaut.

## <a name="cdialogsethelpid"></a><a name="sethelpid"></a>CDialog::SetHelpID

Définit une pièce d’identité d’aide sensible au contexte pour la boîte de dialogue.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Paramètres

*nIDR (en)*<br/>
Spécifie l’ID d’aide sensible au contexte.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
