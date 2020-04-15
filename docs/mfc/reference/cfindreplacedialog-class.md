---
title: Classe CFindReplaceDialog
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 7a12d0520d070d74afd9fa91e828970d14c82700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373869"
---
# <a name="cfindreplacedialog-class"></a>Classe CFindReplaceDialog

Vous permet de mettre en œuvre des boîtes de dialogue de type Chaîne/Remplacer dans votre application.

## <a name="syntax"></a>Syntaxe

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Appelez cette fonction `CFindReplaceDialog` pour construire un objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog::Créer](#create)|Crée et `CFindReplaceDialog` affiche une boîte de dialogue.|
|[CFindReplaceDialog::FindNext](#findnext)|Appelez cette fonction pour déterminer si l’utilisateur veut trouver la prochaine occurrence de la chaîne de recherche.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Appelez cette fonction pour récupérer la chaîne de recherche actuelle.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Appelez cette fonction `FINDREPLACE` pour récupérer la structure dans votre gestionnaire de message enregistré.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Appelez cette fonction pour récupérer la chaîne de remplacement actuelle.|
|[CFindReplaceDialog::Est-Ce qu’il s’agit d’une détermination](#isterminating)|Appelez cette fonction pour déterminer si la boîte de dialogue se termine.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Appelez cette fonction pour déterminer si l’utilisateur veut correspondre au cas de la chaîne de recherche exactement.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Appelez cette fonction pour déterminer si l’utilisateur veut correspondre à des mots entiers seulement.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Appelez cette fonction pour déterminer si l’utilisateur souhaite que tous les événements de la chaîne soient remplacés.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Appelez cette fonction pour déterminer si l’utilisateur souhaite que le mot actuel soit remplacé.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Appelez cette fonction pour déterminer si l’utilisateur souhaite que la recherche se déroule dans une direction descendante.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Une structure utilisée pour `CFindReplaceDialog` personnaliser un objet.|

## <a name="remarks"></a>Notes

Contrairement aux autres boîtes de `CFindReplaceDialog` dialogue communes de Windows, les objets sont sans mode, permettant aux utilisateurs d’interagir avec d’autres fenêtres pendant qu’ils sont à l’écran. Il existe deux `CFindReplaceDialog` types d’objets : trouver des boîtes de dialogue et trouver/remplacer les boîtes de dialogue. Bien que les boîtes de dialogue permettent à l’utilisateur d’entrer les chaînes de recherche et de recherche/remplacement, ils n’exécutent aucune des fonctions de recherche ou de remplacement. Vous devez les ajouter à l’application.

Pour construire `CFindReplaceDialog` un objet, utilisez le constructeur fourni (qui n’a pas d’arguments). Puisqu’il s’agit d’une boîte de dialogue sans mode, allouez l’objet sur le tas à l’aide du **nouvel** opérateur, plutôt que sur la pile.

Une `CFindReplaceDialog` fois qu’un objet a été construit, vous devez appeler la fonction membre [Create](#create) pour créer et afficher la boîte de dialogue.

Utilisez la structure [m_fr](#m_fr) pour initialiser la boîte `Create`de dialogue avant d’appeler . La `m_fr` structure est de type [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Pour plus d’informations sur cette structure, voir le SDK Windows.

Pour que la fenêtre parente soit notifiée des demandes de recherche/remplacement, vous devez utiliser la fonction Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) et utiliser la macro [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) carte de message dans votre fenêtre d’image qui gère ce message enregistré.

Vous pouvez déterminer si l’utilisateur a décidé `IsTerminating` de mettre fin à la boîte de dialogue avec la fonction membre.

`CFindReplaceDialog`s’appuie sur le COMMDLG. Fichier DLL qui expédie avec les versions Windows 3.1 et plus tard.

Pour personnaliser la boîte de dialogue, `CFindReplaceDialog`dérivez une classe, fournissez un modèle de dialogue personnalisé et ajoutez une carte de message pour traiter les messages de notification à partir des contrôles étendus. Tous les messages non traités doivent être transmis à la classe de base.

Personnaliser la fonction de crochet n’est pas nécessaire.

Pour plus d’informations sur l’utilisation `CFindReplaceDialog`, voir Classes de dialogue [commun](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog

Construit un objet `CFindReplaceDialog`.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Notes

Parce `CFindReplaceDialog` que l’objet est une boîte de dialogue sans mode, vous devez le construire sur le tas en utilisant le **nouvel** opérateur.

Pendant la destruction, le cadre tente d’effectuer une suppression de **ce** sur le pointeur à la boîte de dialogue. Si vous avez créé la boîte de dialogue sur la pile, **le** pointeur n’existe pas et un comportement indéfini peut en résulter.

Pour plus d’informations `CFindReplaceDialog` sur la construction d’objets, voir la vue d’ensemble [CFindReplaceDialog.](../../mfc/reference/cfindreplacedialog-class.md) Utilisez le [CFindReplaceDialog: :Créer](#create) la fonction membre pour afficher la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFindReplaceDialog::Créer

Crée et affiche soit un objet de boîte de dialogue `bFindDialogOnly`Trouver ou trouver/remplacer, selon la valeur de .

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*bFindDialogDély*<br/>
Définissez ce paramètre à TRUE pour afficher une boîte de dialogue **Find.** Réglez-le à FALSE pour afficher une boîte de dialogue **Trouver/Remplacer.**

*lpszFindQu’est-ce que*<br/>
Pointeur vers la chaîne de recherche par défaut lorsque la boîte de dialogue apparaît. Si NULL, la boîte de dialogue ne contient pas de chaîne de recherche par défaut.

*lpszReplaceAvec*<br/>
Pointeur vers la chaîne de remplacement par défaut lorsque la boîte de dialogue apparaît. Si NULL, la boîte de dialogue ne contient pas de chaîne de remplacement par défaut.

*dwFlags*<br/>
Un ou plusieurs drapeaux que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinés à l’aide de l’opérateur BITwise OU. La valeur par défaut est FR_DOWN, ce qui précise que la recherche doit se dérouler dans une direction descendante. Consultez la structure [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) dans le Windows SDK pour plus d’informations sur ces drapeaux.

*pParentWnd*<br/>
Un pointeur à la fenêtre parent ou propriétaire de la boîte de dialogue. Il s’agit de la fenêtre qui recevra le message spécial indiquant qu’une action de recherche/remplacement est demandée. Si NULL, la fenêtre principale de l’application est utilisée.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet de boîte de dialogue a été créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Pour que la fenêtre parente soit notifiée des demandes de recherche/remplacement, vous devez utiliser la fonction Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) dont la valeur de retour est un numéro de message unique à l’instance de l’application. Votre fenêtre de trame doit avoir une entrée `OnFindReplace` de carte de message qui déclare la fonction de rappel (dans l’exemple qui suit) qui gère ce message enregistré. Le fragment de code suivant est un exemple de `CMyRichEditView`la façon de le faire pour une classe de fenêtre cadre nommée :

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

Dans `OnFindReplace` votre fonction, vous interprétez les intentions de l’utilisateur en utilisant le [CFindReplaceDialog::FindNext](#findnext) et [CFindReplaceDialog::IsTerminating](#isterminating) methods and you create the code for the find/replace operations.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFindReplaceDialog::FindNext

Appelez cette fonction à partir de votre fonction de rappel pour déterminer si l’utilisateur veut trouver la prochaine occurrence de la chaîne de recherche.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur veut trouver la prochaine occurrence de la chaîne de recherche; sinon 0.

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFindReplaceDialog::GetFindString

Appelez cette fonction à partir de votre fonction de rappel pour récupérer la chaîne par défaut à trouver.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Valeur de retour

La chaîne par défaut à trouver.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFindReplaceDialog::GetNotifier

Appelez cette fonction pour récupérer un pointeur dans la boîte de dialogue Trouver remplacer.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*lParam*<br/>
La valeur *lparam* est passée `OnFindReplace` à la fonction de membre de la fenêtre de cadre.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la boîte de dialogue actuelle.

### <a name="remarks"></a>Notes

Il doit être utilisé dans votre fonction de rappel pour accéder à la `m_fr` boîte de dialogue actuelle, appeler ses fonctions membres et accéder à la structure.

### <a name="example"></a>Exemple

Voir [CFindReplaceDialog::Créer](#create) par exemple de la façon d’enregistrer le gestionnaire OnFindReplace pour recevoir des notifications à partir de la boîte de dialogue Find Replace.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString

Appelez cette fonction pour récupérer la chaîne de remplacement actuelle.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Valeur de retour

La chaîne par défaut avec laquelle remplacer les cordes trouvées.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFindReplaceDialog::Est-Ce qu’il s’agit d’une détermination

Appelez cette fonction dans votre fonction de rappel pour déterminer si l’utilisateur a décidé de mettre fin à la boîte de dialogue.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur a décidé de mettre fin à la boîte de dialogue; sinon 0.

### <a name="remarks"></a>Notes

Si cette fonction renvoie nonzero, vous devez appeler la `DestroyWindow` fonction membre de la boîte de dialogue actuelle et définir n’importe quelle variable de pointeur de boîte de dialogue à NULL. En option, vous pouvez également stocker le texte de recherche/remplacer pour la dernière fois entré et l’utiliser pour initialiser la prochaine boîte de dialogue de recherche/remplacer.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFindReplaceDialog::m_fr

Utilisé pour personnaliser `CFindReplaceDialog` un objet.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Notes

`m_fr`est une structure de type [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Ses membres stockent les caractéristiques de l’objet de la boîte de dialogue. Après la `CFindReplaceDialog` construction d’un `m_fr` objet, vous pouvez utiliser pour modifier différentes valeurs dans la boîte de dialogue.

Pour plus d’informations sur `FINDREPLACE` cette structure, voir la structure dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFindReplaceDialog::MatchCase

Appelez cette fonction pour déterminer si l’utilisateur veut correspondre au cas de la chaîne de recherche exactement.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur veut trouver des occurrences de la chaîne de recherche qui correspondent exactement au cas de la chaîne de recherche; sinon 0.

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord

Appelez cette fonction pour déterminer si l’utilisateur veut correspondre à des mots entiers seulement.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur veut correspondre uniquement à l’ensemble des mots de la chaîne de recherche; sinon 0.

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFindReplaceDialog::ReplaceAll

Appelez cette fonction pour déterminer si l’utilisateur souhaite que tous les événements de la chaîne soient remplacés.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur a demandé que toutes les chaînes correspondant à la chaîne de remplacement soient remplacées; sinon 0.

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent

Appelez cette fonction pour déterminer si l’utilisateur souhaite que le mot actuel soit remplacé.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur a demandé que la chaîne actuellement sélectionnée soit remplacée par la chaîne de remplacement; sinon 0.

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFindReplaceDialog::SearchDown

Appelez cette fonction pour déterminer si l’utilisateur souhaite que la recherche se déroule dans une direction descendante.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur veut que la recherche se déroule dans une direction descendante; 0 si l’utilisateur veut que la recherche se déroule dans une direction ascendante.

## <a name="see-also"></a>Voir aussi

[Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
