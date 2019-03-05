---
title: CDialog (classe)
ms.date: 11/04/2016
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
ms.openlocfilehash: d3c3bca7932b9e9c7e7723b286c83ca3694a9968
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305092"
---
# <a name="cdialog-class"></a>CDialog (classe)

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
|[CDialog::Create](#create)|Initialise le `CDialog` objet. Crée une boîte de dialogue non modale et l’attache à la `CDialog` objet.|
|[CDialog::CreateIndirect](#createindirect)|Crée une boîte de dialogue non modale à partir d’un modèle de boîte de dialogue en mémoire (non-basée sur les ressources).|
|[CDialog::DoModal](#domodal)|Appelle une boîte de dialogue modale et retourne lorsque vous avez terminé.|
|[CDialog::EndDialog](#enddialog)|Ferme la boîte de dialogue modale.|
|[CDialog::GetDefID](#getdefid)|Obtient l’ID du contrôle bouton-poussoir par défaut pour une boîte de dialogue.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Déplace le focus à un contrôle de boîte de dialogue spécifié dans la boîte de dialogue.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Crée une boîte de dialogue modale à partir d’un modèle de boîte de dialogue en mémoire (non-basée sur les ressources). Les paramètres sont stockées jusqu'à ce que la fonction `DoModal` est appelée.|
|[CDialog::MapDialogRect](#mapdialogrect)|Convertit les unités de boîte de dialogue d’un rectangle en unités de l’écran.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Déplace le focus vers le contrôle suivant de la boîte de dialogue dans la boîte de dialogue.|
|[CDialog::OnInitDialog](#oninitdialog)|Méthode override pour augmenter l’initialisation de la boîte de dialogue.|
|[CDialog::OnSetFont](#onsetfont)|Méthode override pour indiquer la police à un contrôle de boîte de dialogue consiste à utiliser lorsqu’il dessine le texte.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Déplace le focus vers le contrôle précédent de la boîte de dialogue dans la boîte de dialogue.|
|[CDialog::SetDefID](#setdefid)|Remplace le contrôle de commande par défaut pour une boîte de dialogue un bouton de commande spécifié.|
|[CDialog::SetHelpID](#sethelpid)|Définit un ID d’aide contextuelle pour la boîte de dialogue.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Méthode override pour effectuer l’action de clé d’ÉCHAP ou un bouton Annuler. La valeur par défaut ferme la boîte de dialogue et `DoModal` retourne IDCANCEL.|
|[CDialog::OnOK](#onok)|Méthode override pour effectuer l’action du bouton OK dans la boîte de dialogue modale. La valeur par défaut ferme la boîte de dialogue et `DoModal` retourne IDOK.|

## <a name="remarks"></a>Notes

Boîtes de dialogue sont de deux types : modales et non modales. Une boîte de dialogue modale doit être fermée par l’utilisateur avant que l’application continue. Une boîte de dialogue non modale permet à l’utilisateur afficher la boîte de dialogue et revenir à une autre tâche sans l’annulation ou la suppression de la boîte de dialogue.

Un `CDialog` objet est une combinaison d’un modèle de boîte de dialogue et un `CDialog`-classe dérivée. Utiliser l’éditeur de boîtes de dialogue pour créer le modèle de boîte de dialogue et les stocker dans une ressource, puis utiliser l’Assistant Ajouter une classe pour créer une classe dérivée de `CDialog`.

Une boîte de dialogue, comme toute autre fenêtre reçoit des messages à partir de Windows. Une boîte de dialogue vous intéresse particulièrement dans le traitement des messages de notification à partir de contrôles de la boîte de dialogue, c'est-à-dire la façon dont l’utilisateur interagit avec votre boîte de dialogue. Utilisez la fenêtre Propriétés pour sélectionner les messages que vous le souhaitez pour gérer et il ajoute les entrées de mappage de message approprié et les fonctions de membre de gestionnaire de messages à la classe pour vous. Vous devez uniquement écrire du code spécifique à l’application dans les fonctions membres de gestionnaire.

Si vous préférez, vous pouvez toujours écrire les entrées de table des messages et les fonctions membres manuellement.

Dans tous les la plus simple de la boîte de dialogue, vous ajoutez des variables membres à votre classe de boîte de dialogue dérivée pour stocker les données entrées par l’utilisateur dans les contrôles de la boîte de dialogue ou pour afficher des données pour l’utilisateur. Vous pouvez utiliser l’Assistant Ajouter une Variable à créer des variables de membre et les associer à des contrôles. En même temps, vous choisissez un type de variable et la plage autorisée de valeurs pour chaque variable. L’Assistant code ajoute les variables de membre à votre classe de boîte de dialogue dérivée.

Un mappage de données est généré pour gérer automatiquement l’échange de données entre les variables de membre et les contrôles de la boîte de dialogue. Le mappage de données fournit des fonctions pour initialiser les contrôles dans la boîte de dialogue avec les valeurs appropriées, de récupèrent les données et de valident les données.

Pour créer une boîte de dialogue modale, construisez un objet sur la pile à l’aide du constructeur pour votre classe dérivée de boîte de dialogue, puis appelez `DoModal` pour créer la fenêtre de la boîte de dialogue et ses contrôles. Si vous souhaitez créer une boîte de dialogue non modale, appelez `Create` dans le constructeur de votre classe de boîte de dialogue.

Vous pouvez également créer un modèle en mémoire en utilisant un [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) structure de données comme décrit dans le SDK Windows. Après avoir construit un `CDialog` de l’objet, appelez [CreateIndirect](#createindirect) pour créer un non modal boîte de dialogue ou appel [InitModalIndirect](#initmodalindirect) et [DoModal](#domodal) pour créer une fenêtre modale boîte de dialogue.

Le mappage de données exchange et la validation est écrit dans une substitution de `CWnd::DoDataExchange` qui est ajouté à votre nouvelle classe de boîte de dialogue. Consultez le [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) fonction membre dans `CWnd` pour plus d’informations sur la fonctionnalité d’échange et validation.

Le programmeur et l’appel de framework `DoDataExchange` indirectement via un appel à [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Le framework appelle `UpdateData` lorsque l’utilisateur clique sur le bouton OK pour fermer la boîte de dialogue modale. (Les données ne sont pas récupérées si l’utilisateur clique sur le bouton Annuler.) L’implémentation par défaut de [OnInitDialog](#oninitdialog) appelle également `UpdateData` pour définir les valeurs initiales des contrôles. Vous substituez généralement `OnInitDialog` pour initialiser des contrôles. `OnInitDialog` est appelée une fois que tous les contrôles de boîte de dialogue sont créés et juste avant la boîte de dialogue s’affiche.

Vous pouvez appeler `CWnd::UpdateData` à tout moment pendant l’exécution d’une boîte de dialogue modale ou non modale.

Si vous développez une boîte de dialogue à la main, vous ajoutez les variables de membre nécessaire à la classe de boîte de dialogue dérivée vous-même, et vous ajoutez des fonctions membres pour définir ou obtenir ces valeurs.

Une boîte de dialogue modale ferme automatiquement lorsque l’utilisateur appuie sur le bouton OK ou annuler ou lorsque votre code appelle la `EndDialog` fonction membre.

Lorsque vous implémentez une boîte de dialogue non modale, vous devez toujours remplacer le `OnCancel` fonction membre et appelez `DestroyWindow` à partir de qu’il contient. N’appelez pas la classe de base `CDialog::OnCancel`, car il appelle `EndDialog`, qui rendent la boîte de dialogue invisibles mais pas détruira ce dernier. Vous devez également substituer `PostNcDestroy` pour les boîtes de dialogue non modale afin de pouvoir supprimer **cela**, étant donné que les boîtes de dialogue non modales sont généralement attribués avec **nouveau**. Boîtes de dialogue modales sont généralement construits sur le frame et n’avez pas besoin de `PostNcDestroy` nettoyage.

Pour plus d’informations sur `CDialog`, consultez [boîtes de dialogue](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="cdialog"></a>  CDialog::CDialog

Pour construire une boîte de dialogue basée sur les ressources, appelez des deux formes public du constructeur.

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
Contient une chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Une forme du constructeur fournit l’accès à la ressource de boîte de dialogue par le nom du modèle. L’autre constructeur fournit l’accès par numéro d’ID de modèle, généralement avec un **IDD_** préfixe (par exemple, IDD_DIALOG1).

Pour construire une boîte de dialogue modale à partir d’un modèle en mémoire, tout d’abord appeler le constructeur sans paramètre, protégé, puis appelez `InitModalIndirect`.

Une fois que vous construisez une boîte de dialogue modale avec l’une des méthodes ci-dessus, appelez `DoModal`.

Pour construire une boîte de dialogue non modale, utilisez la forme protégée de la `CDialog` constructeur. Le constructeur est protégé, car vous devez dériver votre propre classe de boîte de dialogue pour implémenter une boîte de dialogue non modale. Construction d’une boîte de dialogue non modale est un processus en deux étapes. Tout d’abord appeler le constructeur ; Appelez ensuite la `Create` fonction membre pour créer une boîte de dialogue basée sur les ressources, ou appelez `CreateIndirect` pour créer la boîte de dialogue à partir d’un modèle en mémoire.

##  <a name="create"></a>  CDialog::Create

Appelez `Create` pour créer une boîte de dialogue non modale à l’aide d’un modèle de boîte de dialogue à partir d’une ressource.

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
Contient une chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.

*nIDTemplate*<br/>
Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Les deux formes retournent différent de zéro si l’initialisation et la création de la boîte de dialogue ont réussi ; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez placer l’appel à `Create` dans le constructeur ou un appel après le constructeur est appelé.

Deux formes de la `Create` fonction membre sont fournis pour accéder à la ressource de modèle de boîte de dialogue par le nom du modèle ou numéro d’ID de modèle (par exemple, IDD_DIALOG1).

Pour des deux formes, passer un pointeur vers l’objet de fenêtre parent. Si *pParentWnd* est NULL, la boîte de dialogue sera créée avec sa fenêtre parente ou propriétaire défini dans la fenêtre principale de l’application.

Le `Create` fonction membre retourne immédiatement après avoir créé la boîte de dialogue.

Utiliser le style WS_VISIBLE dans le modèle de boîte de dialogue si la boîte de dialogue doit s’afficher lors de la création de la fenêtre parente. Sinon, vous devez appeler `ShowWindow`. Pour davantage les styles de boîte de dialogue et leur application, consultez le [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) structure dans le SDK Windows et [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) dans le *référence MFC*.

Utilisez le `CWnd::DestroyWindow` fonction pour détruire une boîte de dialogue créée par le `Create` (fonction).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>  CDialog::CreateIndirect

Appelez cette fonction membre pour créer une boîte de dialogue non modale à partir d’un modèle de boîte de dialogue en mémoire.

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
Pointe vers la mémoire qui contient un modèle de boîte de dialogue permet de créer la boîte de dialogue. Ce modèle est sous la forme d’un [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) informations de structure et de contrôle, comme décrit dans le SDK Windows.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent de l’objet de la boîte de dialogue (de type [CWnd](../../mfc/reference/cwnd-class.md)). Si sa valeur est NULL, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.

*lpDialogInit*<br/>
Pointe vers une ressource DLGINIT.

*hDialogTemplate*<br/>
Contient un handle de mémoire globale qui contient un modèle de boîte de dialogue. Ce modèle est sous la forme d’un `DLGTEMPLATE` structure et les données pour chaque contrôle dans la boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la boîte de dialogue a été créée et initialisée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Le `CreateIndirect` fonction membre retourne immédiatement après avoir créé la boîte de dialogue.

Utiliser le style WS_VISIBLE dans le modèle de boîte de dialogue si la boîte de dialogue doit s’afficher lors de la création de la fenêtre parente. Sinon, vous devez appeler `ShowWindow` pour qu’elle apparaisse. Pour plus d’informations sur la façon dont vous pouvez spécifier les autres styles de boîte de dialogue dans le modèle, consultez la [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) structure dans le SDK Windows.

Utilisez le `CWnd::DestroyWindow` fonction pour détruire une boîte de dialogue créée par le `CreateIndirect` (fonction).

Les boîtes de dialogue qui contiennent des contrôles ActiveX nécessitent des informations supplémentaires fournies dans une ressource DLGINIT.

##  <a name="domodal"></a>  CDialog::DoModal

Appelez cette fonction membre pour appeler la boîte de dialogue modale et retournent le résultat de la boîte de dialogue lorsque vous avez terminé.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

Un **int** valeur qui spécifie la valeur de la *%nrésultat* paramètre qui a été transmis à la [CDialog::EndDialog](#enddialog) fonction membre, ce qui est utilisée pour fermer la boîte de dialogue. La valeur de retour est -1 si la fonction Impossible de créer la boîte de dialogue, ou IDABORT si une autre erreur s’est produite, auquel cas la fenêtre de sortie contiendra des informations d’erreur à partir de [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Notes

Cette fonction membre gère toutes les interactions avec l’utilisateur pendant que la boîte de dialogue est active. C’est ce qui rend la boîte de dialogue modale ; Autrement dit, l’utilisateur ne peut pas interagir avec d’autres fenêtres jusqu'à ce que la boîte de dialogue est fermée.

Si l’utilisateur clique sur un des boutons de commande dans la boîte de dialogue, tel que OK ou annuler, une fonction membre de gestionnaire de messages, tel que [OnOK](#onok) ou [OnCancel](#oncancel), est appelé pour tenter de fermer la boîte de dialogue. La valeur par défaut `OnOK` fonction membre valider et mettre à jour les données de la boîte de dialogue et fermez la boîte de dialogue avec un résultat IDOK et la valeur par défaut `OnCancel` fonction membre ferme la boîte de dialogue avec un résultat IDCANCEL sans validation ou de la mise à jour le données de la boîte de dialogue. Vous pouvez remplacer ces fonctions de gestionnaire de messages pour modifier leur comportement.

> [!NOTE]
> `PreTranslateMessage` est maintenant appelé pour le traitement de message boîte de dialogue modale.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>  CDialog::EndDialog

Appelez cette fonction membre pour mettre fin à une boîte de dialogue modale.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Paramètres

*nResult*<br/>
Contient la valeur à retourner à partir de la boîte de dialogue à l’appelant de `DoModal`.

### <a name="remarks"></a>Notes

Cette fonction membre retourne *%nrésultat* en tant que valeur de retour de `DoModal`. Vous devez utiliser le `EndDialog` fonction terminer le traitement de chaque fois qu’une boîte de dialogue modale est créée.

Vous pouvez appeler `EndDialog` à tout moment, même dans les [OnInitDialog](#oninitdialog), auquel cas vous devez fermer la boîte de dialogue avant qu’il est indiquée ou avant de définir le focus d’entrée.

`EndDialog` ne fermez pas la boîte de dialogue immédiatement. Au lieu de cela, il définit un indicateur qui dirige la boîte de dialogue pour fermer dès que retourne le Gestionnaire de messages en cours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>  CDialog::GetDefID

Appelez le `GetDefID` fonction membre à obtenir l’ID du contrôle bouton-poussoir par défaut pour une boîte de dialogue.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur 32 bits ( `DWORD`). Si le bouton de commande par défaut a une valeur d’ID, le mot de poids fort contient DC_HASDEFID et le mot de poids faible contient la valeur d’ID. Si le bouton de commande par défaut n’a pas une valeur d’ID, la valeur de retour est 0.

### <a name="remarks"></a>Notes

Il s’agit généralement d’un bouton OK.

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

Déplace le focus vers le contrôle spécifié dans la boîte de dialogue.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Paramètres

*pWndCtrl*<br/>
Identifie la fenêtre (contrôle) qui doit recevoir le focus.

### <a name="remarks"></a>Notes

Pour obtenir un pointeur vers le contrôle (fenêtre enfant) à passer comme *pWndCtrl*, appelez le `CWnd::GetDlgItem` fonction membre, qui retourne un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

Appelez cette fonction membre pour initialiser un objet de la boîte de dialogue modale à l’aide d’un modèle de boîte de dialogue que vous construisez dans la mémoire.

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
Pointe vers la mémoire qui contient un modèle de boîte de dialogue permet de créer la boîte de dialogue. Ce modèle est sous la forme d’un [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) informations de structure et de contrôle, comme décrit dans le SDK Windows.

*hDialogTemplate*<br/>
Contient un handle de mémoire globale qui contient un modèle de boîte de dialogue. Ce modèle est sous la forme d’un `DLGTEMPLATE` structure et les données pour chaque contrôle dans la boîte de dialogue.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.

*lpDialogInit*<br/>
Pointe vers une ressource DLGINIT.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet de la boîte de dialogue a été créé et initialisé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Pour créer une boîte de dialogue modale indirectement, tout d’abord d’allouer un bloc global de mémoire et de le remplir avec le modèle de boîte de dialogue. Appelez ensuite la vider `CDialog` constructeur pour construire l’objet de la boîte de dialogue. Ensuite, appelez `InitModalIndirect` pour stocker votre handle vers le modèle de boîte de dialogue en mémoire. La boîte de dialogue Windows est créée et affichée ensuite, lorsque le [DoModal](#domodal) fonction membre est appelée.

Les boîtes de dialogue qui contiennent des contrôles ActiveX nécessitent des informations supplémentaires fournies dans une ressource DLGINIT.

##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect

L’appel à convertir les unités de boîte de dialogue d’un rectangle en unités de l’écran.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) structure ou [CRect](../../atl-mfc-shared/reference/crect-class.md) coordonne d’objet qui contient la boîte de dialogue à convertir.

### <a name="remarks"></a>Notes

Unités de boîte de dialogue sont exprimées dans l’unité de base de la boîte de dialogue actuel dérivée de la largeur moyenne et la hauteur des caractères de la police utilisée pour le texte de la boîte de dialogue. Une unité horizontale correspond à un quart de l’unité de la largeur de la base de la boîte de dialogue et une unité verticale est un huitième de l’unité de base de hauteur de la boîte de dialogue.

Le `GetDialogBaseUnits` (fonction) Windows retourne des informations sur la taille de la police système, mais vous pouvez spécifier une autre police pour chaque boîte de dialogue si vous utilisez le style DS_SETFONT dans le fichier de définition de ressource. Le `MapDialogRect` fonction de Windows utilise la police appropriée pour cette boîte de dialogue.

Le `MapDialogRect` fonction membre remplace les unités de boîte de dialogue dans *lpRect* avec écran unités (pixels) afin que le rectangle peut être utilisé pour créer une boîte de dialogue ou positionner un contrôle dans une zone.

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

Déplace le focus au contrôle suivant dans la boîte de dialogue.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Notes

Si le focus est sur le dernier contrôle dans la boîte de dialogue, il se déplace vers le premier contrôle.

##  <a name="oncancel"></a>  CDialog::OnCancel

L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur **Annuler** ou appuie sur la touche ÉCHAP dans une boîte de dialogue modale ou non modale.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Notes

Substituez cette méthode pour effectuer des actions (par exemple, la restauration des données anciennes) lorsqu’un utilisateur ferme la boîte de dialogue en cliquant sur **Annuler** ou appuyant sur la touche ÉCHAP. La valeur par défaut ferme la boîte de dialogue modale en appelant [EndDialog](#enddialog) et à l’origine [DoModal](#domodal) pour renvoyer IDCANCEL.

Si vous implémentez le **Annuler** bouton dans une boîte de dialogue non modale, vous devez substituer la `OnCancel` méthode et appel [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) qu’il contient. N’appelez pas la méthode de classe de base, parce qu’il appelle `EndDialog`, qui sera rendre la boîte de dialogue invisible mais pas la détruire.

> [!NOTE]
>  Vous ne pouvez pas substituer cette méthode lorsque vous utilisez un `CFileDialog` objet dans un programme qui est compilé sous Windows XP. Pour plus d’informations sur `CFileDialog`, consultez [classe CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>  CDialog::OnInitDialog

Cette méthode est appelée en réponse à la `WM_INITDIALOG` message.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Spécifie si l’application a défini le focus d’entrée à un des contrôles dans la boîte de dialogue. Si `OnInitDialog` retourne une valeur différente de zéro, Windows définit le focus d’entrée à l’emplacement par défaut, le premier contrôle dans la boîte de dialogue. L’application peut retourner 0 uniquement si elle a défini le focus d’entrée explicitement à un des contrôles dans la boîte de dialogue.

### <a name="remarks"></a>Notes

Windows envoie les `WM_INITDIALOG` message à la boîte de dialogue pendant les [créer](#create), [CreateIndirect](#createindirect), ou [DoModal](#domodal) appels, qui se produisent immédiatement avant la boîte de dialogue s’affiche.

Substituez cette méthode si vous souhaitez effectuer un traitement spécial lors de l’initialisation de la boîte de dialogue. Dans la version substituée, tout d’abord appeler la classe de base `OnInitDialog` mais sa valeur de retour de l’ignorer. Vous renverrez généralement `TRUE` à partir de votre méthode substituée.

Appels de Windows le `OnInitDialog` fonction à l’aide de la procédure standard global-boîte de dialogue commune à toutes les boîtes de dialogue Bibliothèque Microsoft Foundation Class. Il n’appelle pas cette fonction via votre table des messages, et par conséquent, il est inutile une entrée de mappage de message pour cette méthode.

> [!NOTE]
> Vous ne pouvez pas substituer cette méthode lorsque vous utilisez un `CFileDialog` objet dans un programme qui est compilé sous Windows Vista ou des systèmes d’exploitation ultérieurs. Pour plus d’informations sur les modifications apportées aux `CFileDialog` sous Windows Vista et versions ultérieures, consultez [classe CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>  CDialog::OnOK

Appelée lorsque l’utilisateur clique sur le **OK** bouton (avec un ID de IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

Substituez cette méthode pour effectuer des actions lorsque les **OK** bouton est activé. Si la boîte de dialogue inclut exchange et validation automatique des données, l’implémentation par défaut de cette méthode valide les données de boîte de dialogue et met à jour les variables appropriées dans votre application.

Si vous implémentez le **OK** bouton dans une boîte de dialogue non modale, vous devez substituer la `OnOK` méthode et appel [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) qu’il contient. N’appelez pas la méthode de classe de base, parce qu’il appelle [EndDialog](#enddialog) qui rend la boîte de dialogue invisible, mais ne la supprime pas.

> [!NOTE]
>  Vous ne pouvez pas substituer cette méthode lorsque vous utilisez un `CFileDialog` objet dans un programme qui est compilé sous Windows XP. Pour plus d’informations sur `CFileDialog`, consultez [classe CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>  CDialog::OnSetFont

Spécifie la police de qu'un contrôle de boîte de dialogue utilise pour dessiner du texte.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[in] Spécifie un pointeur vers la police qui sera utilisé comme police par défaut pour tous les contrôles dans cette boîte de dialogue.

### <a name="remarks"></a>Notes

La boîte de dialogue utilisera la police spécifiée en tant que la valeur par défaut pour tous ses contrôles.

L’éditeur de boîtes de dialogue définit généralement la police de la boîte de dialogue dans le cadre de la ressource de modèle de boîte de dialogue.

> [!NOTE]
> Vous ne pouvez pas substituer cette méthode lorsque vous utilisez un `CFileDialog` objet dans un programme qui est compilé sous Windows Vista ou des systèmes d’exploitation ultérieurs. Pour plus d’informations sur les modifications apportées aux `CFileDialog` sous Windows Vista et versions ultérieures, consultez [classe CFileDialog](../../mfc/reference/cfiledialog-class.md).

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

Définit le focus au contrôle précédent dans la boîte de dialogue.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Notes

Si le focus est sur le premier contrôle dans la boîte de dialogue, il déplace au dernier contrôle dans la zone.

##  <a name="setdefid"></a>  CDialog::SetDefID

Remplace le contrôle de commande par défaut pour une boîte de dialogue.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Spécifie l’ID du contrôle bouton-poussoir qui deviendra la valeur par défaut.

##  <a name="sethelpid"></a>  CDialog::SetHelpID

Définit un ID d’aide contextuelle pour la boîte de dialogue.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Paramètres

*nIDR*<br/>
Spécifie l’ID de l’aide contextuelle.

## <a name="see-also"></a>Voir aussi

[MFC exemple DLGCBR32](../../visual-cpp-samples.md)<br/>
[Exemple MFC DLGTEMPL](../../visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
