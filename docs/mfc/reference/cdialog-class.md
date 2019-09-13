---
title: CDialog (classe)
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
ms.openlocfilehash: b07190c70fb11950b25aff45fb10e850c0e81b24
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907605"
---
# <a name="cdialog-class"></a>CDialog (classe)

Classe de base utilisée pour afficher des boîtes de dialogue à l’écran.

## <a name="syntax"></a>Syntaxe

```
class CDialog : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDialog :: CDialog](#cdialog)|Construit un objet `CDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDialog :: Create](#create)|Initialise l' `CDialog` objet. Crée une boîte de dialogue non modale et l’attache à `CDialog` l’objet.|
|[CDialog :: CreateIndirect](#createindirect)|Crée une boîte de dialogue non modale à partir d’un modèle de boîte de dialogue en mémoire (non basé sur les ressources).|
|[CDialog::DoModal](#domodal)|Appelle une boîte de dialogue modale et retourne une valeur quand elle est terminée.|
|[CDialog::EndDialog](#enddialog)|Ferme une boîte de dialogue modale.|
|[CDialog::GetDefID](#getdefid)|Obtient l’ID du contrôle PUSHBUTTON par défaut d’une boîte de dialogue.|
|[CDialog :: GotoDlgCtrl](#gotodlgctrl)|Déplace le focus vers un contrôle de boîte de dialogue spécifié dans la boîte de dialogue.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Crée une boîte de dialogue modale à partir d’un modèle de boîte de dialogue en mémoire (non basé sur les ressources). Les paramètres sont stockés jusqu’à ce `DoModal` que la fonction soit appelée.|
|[CDialog::MapDialogRect](#mapdialogrect)|Convertit les unités de boîte de dialogue d’un rectangle en unités d’écran.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Déplace le focus vers le contrôle de boîte de dialogue suivant dans la boîte de dialogue.|
|[CDialog::OnInitDialog](#oninitdialog)|Substituez pour augmenter l’initialisation de la boîte de dialogue.|
|[CDialog::OnSetFont](#onsetfont)|Substituez pour spécifier la police qu’un contrôle de boîte de dialogue doit utiliser lorsqu’il dessine du texte.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Déplace le focus vers le contrôle de boîte de dialogue précédent dans la boîte de dialogue.|
|[CDialog::SetDefID](#setdefid)|Remplace le contrôle PUSHBUTTON par défaut d’une boîte de dialogue par un bouton de commande spécifié.|
|[CDialog::SetHelpID](#sethelpid)|Définit un ID d’aide contextuelle pour la boîte de dialogue.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDialog :: OnCancel](#oncancel)|Substituez pour exécuter le bouton Annuler ou l’action touche ÉCHAP. La valeur par défaut ferme la boîte `DoModal` de dialogue et retourne IDCANCEL.|
|[CDialog::OnOK](#onok)|Substituez pour exécuter l’action du bouton OK dans une boîte de dialogue modale. La valeur par défaut ferme la boîte `DoModal` de dialogue et retourne IDOK.|

## <a name="remarks"></a>Notes

Les boîtes de dialogue sont de deux types : modal et non modal. Une boîte de dialogue modale doit être fermée par l’utilisateur avant que l’application continue. Une boîte de dialogue non modale permet à l’utilisateur d’afficher la boîte de dialogue et de revenir à une autre tâche sans annuler ou supprimer la boîte de dialogue.

Un `CDialog` objet est une combinaison d’un modèle de boîte de `CDialog`dialogue et d’une classe dérivée de. Utilisez l’éditeur de boîtes de dialogue pour créer le modèle de boîte de dialogue et le stocker dans une ressource, puis utilisez l’Assistant Ajouter une `CDialog`classe pour créer une classe dérivée de.

Une boîte de dialogue, comme toute autre fenêtre, reçoit des messages de Windows. Dans une boîte de dialogue, vous êtes particulièrement intéressé par la gestion des messages de notification à partir des contrôles de la boîte de dialogue, car il s’agit de la façon dont l’utilisateur interagit avec votre boîte de dialogue. Utilisez l' [Assistant classe](mfc-class-wizard.md) pour sélectionner les messages que vous souhaitez gérer et ajouter les entrées de table de messages et les fonctions membres du gestionnaire de messages appropriées à la classe pour vous. Vous devez uniquement écrire du code spécifique à l’application dans les fonctions membres du gestionnaire.

Si vous préférez, vous pouvez toujours écrire manuellement les entrées et les fonctions membres de la table des messages.

Dans toutes les boîtes de dialogue sauf la plus triviale, vous ajoutez des variables membres à votre classe de boîte de dialogue dérivée pour stocker les données entrées dans les contrôles de la boîte de dialogue par l’utilisateur ou pour afficher les données de l’utilisateur. Vous pouvez utiliser l’Assistant Ajouter une variable pour créer des variables membres et les associer à des contrôles. En même temps, vous choisissez un type de variable et une plage de valeurs autorisée pour chaque variable. L’Assistant code ajoute les variables membres à votre classe de boîte de dialogue dérivée.

Un mappage de données est généré pour gérer automatiquement l’échange de données entre les variables membres et les contrôles de la boîte de dialogue. Le mappage de données fournit des fonctions qui initialisent les contrôles dans la boîte de dialogue avec les valeurs appropriées, récupèrent les données et valident les données.

Pour créer une boîte de dialogue modale, construisez un objet sur la pile à l’aide du constructeur de votre classe `DoModal` de boîte de dialogue dérivée, puis appelez pour créer la fenêtre de boîte de dialogue et ses contrôles. Si vous souhaitez créer une boîte de dialogue non modale `Create` , appelez dans le constructeur de votre classe de boîte de dialogue.

Vous pouvez également créer un modèle en mémoire à l’aide d’une structure de données [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) , comme décrit dans la SDK Windows. Après avoir construit un `CDialog` objet, appelez [CreateIndirect](#createindirect) pour créer une boîte de dialogue non modale, ou appelez [InitModalIndirect](#initmodalindirect) [et DoModal](#domodal) pour créer une boîte de dialogue modale.

Le mappage de données d’échange et de validation est écrit dans une `CWnd::DoDataExchange` substitution de qui est ajoutée à votre nouvelle classe de dialogue. `CWnd` Pour plus d’informations sur les fonctionnalités d’Exchange et de validation, consultez la fonction membre [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) .

Le programmeur et le Framework appellent `DoDataExchange` indirectement par le biais d’un appel à [CWnd :: UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Le Framework appelle `UpdateData` lorsque l’utilisateur clique sur le bouton OK pour fermer une boîte de dialogue modale. (Les données ne sont pas récupérées si vous cliquez sur le bouton Annuler.) L’implémentation par défaut de [OnInitDialog](#oninitdialog) appelle `UpdateData` également pour définir les valeurs initiales des contrôles. En général, vous `OnInitDialog` substituez pour initialiser les contrôles. `OnInitDialog`est appelé après que tous les contrôles de boîte de dialogue ont été créés et juste avant que la boîte de dialogue ne s’affiche.

Vous pouvez appeler `CWnd::UpdateData` à tout moment pendant l’exécution d’une boîte de dialogue modale ou non modale.

Si vous développez une boîte de dialogue manuellement, vous ajoutez vous-même les variables membres nécessaires à la classe de boîte de dialogue dérivée, et vous ajoutez des fonctions membres pour définir ou obtenir ces valeurs.

Une boîte de dialogue modale se ferme automatiquement lorsque l’utilisateur appuie sur les boutons OK ou annuler ou lorsque votre `EndDialog` code appelle la fonction membre.

Lorsque vous implémentez une boîte de dialogue non modale, substituez toujours la `OnCancel` fonction membre et appelez `DestroyWindow` à partir de celle-ci. N’appelez pas la classe `CDialog::OnCancel`de base, car `EndDialog`elle appelle, ce qui rendra la boîte de dialogue invisible, mais ne la détruira pas. Vous devez également substituer `PostNcDestroy` les boîtes de dialogue non modales afin de supprimer **cela**, car les boîtes de dialogue non modales sont généralement allouées avec **New**. Les boîtes de dialogue modales sont généralement construites sur le frame `PostNcDestroy` et n’ont pas besoin d’être nettoyées.

Pour plus d’informations `CDialog`sur, consultez [boîtes de dialogue](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cdialog"></a>CDialog :: CDialog

Pour construire une boîte de dialogue modale basée sur les ressources, appelez l’une des formes publiques du constructeur.

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
Contient une chaîne terminée par le caractère null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Une forme du constructeur permet d’accéder à la ressource de boîte de dialogue par nom de modèle. L’autre constructeur fournit l’accès par numéro d’ID de modèle, généralement avec un préfixe **IDD_** (par exemple, IDD_DIALOG1).

Pour construire une boîte de dialogue modale à partir d’un modèle en mémoire, appelez d’abord le constructeur protégé sans `InitModalIndirect`paramètre, puis appelez.

Après avoir construit une boîte de dialogue modale avec l’une des méthodes ci `DoModal`-dessus, appelez.

Pour construire une boîte de dialogue non modale, utilisez la forme protégée `CDialog` du constructeur. Le constructeur est protégé, car vous devez dériver votre propre classe de boîte de dialogue pour implémenter une boîte de dialogue non modale. La création d’une boîte de dialogue non modale est un processus en deux étapes. Appelez d’abord le constructeur. Appelez ensuite la `Create` fonction membre pour créer une boîte de dialogue basée sur les ressources, `CreateIndirect` ou appelez pour créer la boîte de dialogue à partir d’un modèle en mémoire.

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
Contient une chaîne terminée par le caractère null qui est le nom d’une ressource de modèle de boîte de dialogue.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

*nIDTemplate*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Les deux formulaires retournent une valeur différente de zéro si la création et l’initialisation de la boîte de dialogue ont réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez placer l’appel à `Create` l’intérieur du constructeur ou l’appeler une fois le constructeur appelé.

Deux formes de la `Create` fonction membre sont fournies pour accéder à la ressource de modèle de boîte de dialogue par le biais d’un nom de modèle ou d’un numéro d’ID de modèle (par exemple, IDD_DIALOG1).

Pour l’un ou l’autre formulaire, transmettez un pointeur vers l’objet de fenêtre parente. Si *pParentWnd* a la valeur null, la boîte de dialogue est créée avec sa fenêtre parente ou propriétaire définie sur la fenêtre d’application principale.

La `Create` fonction membre retourne immédiatement après avoir créé la boîte de dialogue.

Utilisez le style WS_VISIBLE dans le modèle de boîte de dialogue si la boîte de dialogue doit s’afficher lors de la création de la fenêtre parente. Sinon, vous devez appeler `ShowWindow`. Pour obtenir d’autres styles de boîtes de dialogue et leur application, consultez la structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) dans le SDK Windows et les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) dans la *référence MFC*.

Utilisez la `CWnd::DestroyWindow` fonction pour détruire une boîte de dialogue créée par `Create` la fonction.

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
Pointe vers la mémoire qui contient un modèle de boîte de dialogue utilisé pour créer la boîte de dialogue. Ce modèle se présente sous la forme d’une structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) et d’informations de contrôle, comme décrit dans la SDK Windows.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent de l’objet Dialog (de type [CWnd](../../mfc/reference/cwnd-class.md)). Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

*lpDialogInit*<br/>
Pointe vers une ressource DLGINIT.

*hDialogTemplate*<br/>
Contient un handle de mémoire globale contenant un modèle de boîte de dialogue. Ce modèle se présente sous la forme d' `DLGTEMPLATE` une structure et de données pour chaque contrôle dans la boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la boîte de dialogue a été créée et initialisée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

La `CreateIndirect` fonction membre retourne immédiatement après avoir créé la boîte de dialogue.

Utilisez le style WS_VISIBLE dans le modèle de boîte de dialogue si la boîte de dialogue doit s’afficher lors de la création de la fenêtre parente. Dans le cas contraire, `ShowWindow` vous devez appeler pour qu’il apparaisse. Pour plus d’informations sur la façon dont vous pouvez spécifier d’autres styles de boîte de dialogue dans le modèle, consultez la structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) dans le SDK Windows.

Utilisez la `CWnd::DestroyWindow` fonction pour détruire une boîte de dialogue créée par `CreateIndirect` la fonction.

Les boîtes de dialogue qui contiennent des contrôles ActiveX requièrent des informations supplémentaires fournies dans une ressource DLGINIT.

##  <a name="domodal"></a>  CDialog::DoModal

Appelez cette fonction membre pour appeler la boîte de dialogue modale et retourner le résultat de la boîte de dialogue lorsque vous avez terminé.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

Valeur **int** qui spécifie la valeur du paramètre *nrésultat* qui a été passé à la fonction membre [CDialog :: EndDialog](#enddialog) , qui est utilisée pour fermer la boîte de dialogue. La valeur de retour est-1 si la fonction n’a pas pu créer la boîte de dialogue, ou IDABORT si une autre erreur s’est produite, auquel cas la fenêtre de sortie contiendra des informations d’erreur de [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Cette fonction membre gère toute l’interaction avec l’utilisateur pendant que la boîte de dialogue est active. C’est ce qui rend la boîte de dialogue modale ; autrement dit, l’utilisateur ne peut pas interagir avec d’autres fenêtres tant que la boîte de dialogue n’est pas fermée.

Si l’utilisateur clique sur l’un des boutons de la boîte de dialogue, par exemple OK ou annuler, une fonction membre du gestionnaire de messages, telle que [OnOK](#onok) ou [OnCancel](#oncancel), est appelée pour tenter de fermer la boîte de dialogue. La fonction `OnOK` membre par défaut valide et met à jour les données de boîte de dialogue, puis ferme la boîte de dialogue avec le `OnCancel` résultat IDOK, et la fonction membre par défaut ferme la boîte de dialogue avec le résultat IDCANCEL sans valider ou mettre à jour le données de boîte de dialogue. Vous pouvez remplacer ces fonctions de gestionnaire de messages pour modifier leur comportement.

> [!NOTE]
> `PreTranslateMessage`est maintenant appelé pour le traitement des messages de boîte de dialogue modale.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>  CDialog::EndDialog

Appelez cette fonction membre pour mettre fin à une boîte de dialogue modale.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Paramètres

*nResult*<br/>
Contient la valeur à retourner de la boîte de dialogue à l’appelant de `DoModal`.

### <a name="remarks"></a>Notes

Cette fonction membre retourne *nrésultat* comme valeur de retour de `DoModal`. Vous devez utiliser la `EndDialog` fonction pour terminer le traitement chaque fois qu’une boîte de dialogue modale est créée.

Vous pouvez appeler `EndDialog` à tout moment, même dans [OnInitDialog](#oninitdialog). dans ce cas, vous devez fermer la boîte de dialogue avant qu’elle ne soit affichée ou avant que le focus d’entrée soit défini.

`EndDialog`ne ferme pas la boîte de dialogue immédiatement. Au lieu de cela, il définit un indicateur qui dirige la boîte de dialogue pour qu’elle se ferme dès que le gestionnaire de messages actuel retourne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>  CDialog::GetDefID

Appelez la `GetDefID` fonction membre pour obtenir l’ID du contrôle PUSHBUTTON par défaut d’une boîte de dialogue.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur 32 bits ( `DWORD`). Si le bouton de commande par défaut a une valeur d’ID, le mot de poids fort contient DC_HASDEFID et le mot de poids faible contient la valeur d’ID. Si le PUSHBUTTON par défaut n’a pas de valeur d’ID, la valeur de retour est 0.

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

Pour obtenir un pointeur vers le contrôle (fenêtre enfant) à passer en tant que *pWndCtrl*, `CWnd::GetDlgItem` appelez la fonction membre, qui retourne un pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) .

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd :: GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

Appelez cette fonction membre pour initialiser un objet de boîte de dialogue modale à l’aide d’un modèle de boîte de dialogue que vous construisez en mémoire.

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
Pointe vers la mémoire qui contient un modèle de boîte de dialogue utilisé pour créer la boîte de dialogue. Ce modèle se présente sous la forme d’une structure [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) et d’informations de contrôle, comme décrit dans la SDK Windows.

*hDialogTemplate*<br/>
Contient un handle de mémoire globale contenant un modèle de boîte de dialogue. Ce modèle se présente sous la forme d' `DLGTEMPLATE` une structure et de données pour chaque contrôle dans la boîte de dialogue.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

*lpDialogInit*<br/>
Pointe vers une ressource DLGINIT.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet de boîte de dialogue a été créé et initialisé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour créer une boîte de dialogue modale de manière indirecte, vous devez d’abord allouer un bloc de mémoire global et le remplir avec le modèle de boîte de dialogue. Appelez ensuite le constructeur `CDialog` vide pour construire l’objet de boîte de dialogue. Ensuite, appelez `InitModalIndirect` pour stocker votre handle dans le modèle de boîte de dialogue en mémoire. La boîte de dialogue Windows est créée et affichée ultérieurement, lorsque la fonction membre [DoModal](#domodal) est appelée.

Les boîtes de dialogue qui contiennent des contrôles ActiveX requièrent des informations supplémentaires fournies dans une ressource DLGINIT.

##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect

Appelez pour convertir les unités de boîte de dialogue d’un rectangle en unités d’écran.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient les coordonnées de la boîte de dialogue à convertir.

### <a name="remarks"></a>Notes

Les unités de boîte de dialogue sont exprimées en termes de l’unité de base de boîte de dialogue actuelle dérivée de la largeur et de la hauteur moyennes des caractères de la police utilisée pour le texte de la boîte de dialogue. Une unité horizontale est un quart de l’unité de largeur de base de la boîte de dialogue, et une unité verticale est un huitième de l’unité de hauteur de base de la boîte de dialogue.

La `GetDialogBaseUnits` fonction Windows retourne des informations sur la taille de la police système, mais vous pouvez spécifier une police différente pour chaque boîte de dialogue si vous utilisez le style DS_SETFONT dans le fichier de définition de ressource. La `MapDialogRect` fonction Windows utilise la police appropriée pour cette boîte de dialogue.

La `MapDialogRect` fonction membre remplace les unités de boîte de dialogue dans *lpRect* par des unités d’écran (pixels) afin que le rectangle puisse être utilisé pour créer une boîte de dialogue ou positionner un contrôle dans une zone.

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

Déplace le focus vers le contrôle suivant dans la boîte de dialogue.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Notes

Si le focus se trouve au dernier contrôle de la boîte de dialogue, il passe au premier contrôle.

##  <a name="oncancel"></a>  CDialog::OnCancel

L’infrastructure appelle cette méthode lorsque l’utilisateur clique sur **Annuler** ou appuie sur la touche Échap dans une boîte de dialogue modale ou non modale.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Notes

Substituez cette méthode pour effectuer des actions (telles que la restauration d’anciennes données) quand un utilisateur ferme la boîte de dialogue en cliquant sur **Annuler** ou en appuyant sur la touche ÉCHAP. La valeur par défaut ferme une boîte de dialogue modale en appelant [EndDialog](#enddialog) et provoquant le retour de IDCANCEL par [DoModal](#domodal) .

Si vous implémentez le bouton **Annuler** dans une boîte de dialogue non modale, vous devez `OnCancel` substituer la méthode et appeler [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) à l’intérieur de celle-ci. N’appelez pas la méthode de la classe de base, car `EndDialog`elle appelle, ce qui rendra la boîte de dialogue invisible, mais ne la détruira pas.

> [!NOTE]
>  Vous ne pouvez pas substituer cette méthode quand vous `CFileDialog` utilisez un objet dans un programme qui est compilé sous Windows XP. Pour plus d’informations `CFileDialog`sur, consultez [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>  CDialog::OnInitDialog

Cette méthode est appelée en réponse au `WM_INITDIALOG` message.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Spécifie si l’application a défini le focus d’entrée sur l’un des contrôles de la boîte de dialogue. Si `OnInitDialog` retourne une valeur différente de zéro, Windows définit le focus d’entrée sur l’emplacement par défaut, le premier contrôle de la boîte de dialogue. L’application peut retourner 0 uniquement si elle a explicitement défini le focus d’entrée sur l’un des contrôles de la boîte de dialogue.

### <a name="remarks"></a>Notes

Windows envoie le `WM_INITDIALOG` message à la boîte de dialogue pendant les appels [Create](#create), [CreateIndirect](#createindirect)ou [DoModal](#domodal) , qui se produisent immédiatement avant l’affichage de la boîte de dialogue.

Substituez cette méthode si vous souhaitez effectuer un traitement spécial lorsque la boîte de dialogue est initialisée. Dans la version substituée, appelez d’abord la classe `OnInitDialog` de base, mais ignorez sa valeur de retour. En général, vous `TRUE` revenez de votre méthode substituée.

Windows appelle la `OnInitDialog` fonction à l’aide de la procédure de boîte de dialogue globale standard commune à toutes les boîtes de dialogue de bibliothèque MFC (Microsoft Foundation Class). Elle n’appelle pas cette fonction par le biais de votre table des messages. par conséquent, vous n’avez pas besoin d’une entrée de la table des messages pour cette méthode.

> [!NOTE]
> Vous ne pouvez pas substituer cette méthode quand vous `CFileDialog` utilisez un objet dans un programme qui est compilé sous Windows Vista ou des systèmes d’exploitation ultérieurs. Pour plus d’informations sur les `CFileDialog` modifications apportées à sous Windows Vista et versions ultérieures, consultez [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>  CDialog::OnOK

Appelé lorsque l’utilisateur clique sur le bouton **OK** (le bouton avec l’ID IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

Substituez cette méthode pour exécuter des actions lorsque le bouton **OK** est activé. Si la boîte de dialogue comprend la validation automatique des données et Exchange, l’implémentation par défaut de cette méthode valide les données de la boîte de dialogue et met à jour les variables appropriées dans votre application.

Si vous implémentez le bouton **OK** dans une boîte de dialogue non modale, vous devez `OnOK` substituer la méthode et appeler [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) à l’intérieur de celle-ci. N’appelez pas la méthode de la classe de base, car elle appelle [EndDialog](#enddialog) qui rend la boîte de dialogue invisible, mais ne la détruit pas.

> [!NOTE]
>  Vous ne pouvez pas substituer cette méthode quand vous `CFileDialog` utilisez un objet dans un programme qui est compilé sous Windows XP. Pour plus d’informations `CFileDialog`sur, consultez [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>  CDialog::OnSetFont

Spécifie la police qui sera utilisée par un contrôle de boîte de dialogue pour dessiner du texte.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
dans Spécifie un pointeur vers la police qui sera utilisée comme police par défaut pour tous les contrôles de cette boîte de dialogue.

### <a name="remarks"></a>Notes

La boîte de dialogue utilise la police spécifiée comme valeur par défaut pour tous ses contrôles.

L’éditeur de boîtes de dialogue définit généralement la police de la boîte de dialogue dans le cadre de la ressource de modèle de boîte de dialogue.

> [!NOTE]
> Vous ne pouvez pas substituer cette méthode quand vous `CFileDialog` utilisez un objet dans un programme qui est compilé sous Windows Vista ou des systèmes d’exploitation ultérieurs. Pour plus d’informations sur les `CFileDialog` modifications apportées à sous Windows Vista et versions ultérieures, consultez [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

Définit le focus sur le contrôle précédent dans la boîte de dialogue.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Notes

Si le focus se trouve au premier contrôle de la boîte de dialogue, il passe au dernier contrôle dans la zone.

##  <a name="setdefid"></a>  CDialog::SetDefID

Modifie le contrôle PUSHBUTTON par défaut d’une boîte de dialogue.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Spécifie l’ID du contrôle PUSHBUTTON qui devient la valeur par défaut.

##  <a name="sethelpid"></a>  CDialog::SetHelpID

Définit un ID d’aide contextuelle pour la boîte de dialogue.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Paramètres

*nIDR*<br/>
Spécifie l’ID de l’aide contextuelle.

## <a name="see-also"></a>Voir aussi

[Exemple MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
