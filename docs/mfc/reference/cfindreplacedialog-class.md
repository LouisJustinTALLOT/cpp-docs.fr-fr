---
title: CFindReplaceDialog, classe
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
ms.openlocfilehash: de48d8f495802bdf1c5f69e7a4edc41153c9599f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264623"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog, classe

Vous permet d’implémenter des boîtes de dialogue Rechercher/Remplacer de chaîne standard dans votre application.

## <a name="syntax"></a>Syntaxe

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Appelez cette fonction pour construire un `CFindReplaceDialog` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|Crée et affiche un `CFindReplaceDialog` boîte de dialogue.|
|[CFindReplaceDialog::FindNext](#findnext)|Appelez cette fonction pour déterminer si l’utilisateur souhaite rechercher l’occurrence suivante de la chaîne de recherche.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Appelez cette fonction pour récupérer la chaîne de recherche actuelle.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Appelez cette fonction pour récupérer le `FINDREPLACE` structure dans votre gestionnaire de messages inscrits.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Appelez cette fonction pour récupérer la chaîne de remplacement en cours.|
|[CFindReplaceDialog::IsTerminating](#isterminating)|Appelez cette fonction pour déterminer si la boîte de dialogue se termine.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Appelez cette fonction pour déterminer si l’utilisateur souhaite correspond exactement à la casse de la chaîne de recherche.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Appelez cette fonction pour déterminer si l’utilisateur veut faire correspondre les mots entiers uniquement.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Appelez cette fonction pour déterminer si l’utilisateur souhaite obtenir toutes les occurrences de la chaîne à remplacer.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Appelez cette fonction pour déterminer si l’utilisateur veut le mot actuel à remplacer.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Appelez cette fonction pour déterminer si l’utilisateur souhaite que la recherche continue dans une direction vers le bas.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Une structure utilisée pour personnaliser un `CFindReplaceDialog` objet.|

## <a name="remarks"></a>Notes

Contrairement à d’autres Windows courantes boîtes de dialogue, `CFindReplaceDialog` objets sont non modales, ce qui permet aux utilisateurs d’interagir avec d’autres fenêtres pendant qu’ils se trouvent sur l’écran. Il existe deux types de `CFindReplaceDialog` objets : Trouvez des boîtes de dialogue et les boîtes de dialogue Rechercher/Remplacer. Bien que les boîtes de dialogue Autoriser l’utilisateur à la recherche d’entrée et les chaînes de recherche/remplacement, elles n’effectuent pas un de la recherche ou du remplacement des fonctions. Vous devez les ajouter à l’application.

Pour construire un `CFindReplaceDialog` d’objet, utilisez le constructeur fourni (qui n’a aucun argument). Dans la mesure où il s’agit d’une boîte de dialogue non modale, allouer l’objet sur le tas en utilisant le **nouveau** opérateur, plutôt que sur la pile.

Une fois un `CFindReplaceDialog` objet a été construit, vous devez appeler la [créer](#create) fonction membre pour créer et afficher la boîte de dialogue.

Utilisez le [m_fr](#m_fr) structure pour initialiser la boîte de dialogue avant d’appeler `Create`. Le `m_fr` structure est de type [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea). Pour plus d’informations sur cette structure, consultez le Kit de développement Windows.

Dans l’ordre de la fenêtre parente à être informé des demandes de recherche/remplacement, vous devez utiliser le Windows [RegisterWindowMessage](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea) de fonction et utiliser le [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) macro de table des messages dans le cadre de votre fenêtre qui gère ce message enregistré.

Vous pouvez déterminer si l’utilisateur a décidé de mettre fin à la boîte de dialogue avec le `IsTerminating` fonction membre.

`CFindReplaceDialog` s’appuie sur le COMMDLG. Fichier DLL qui est livré avec Windows 3.1 et versions ultérieures.

Pour personnaliser la boîte de dialogue, dérivez une classe de `CFindReplaceDialog`, de fournir un modèle de boîte de dialogue personnalisée et ajouter une table des messages pour traiter les messages de notification à partir de contrôles étendus. Tous les messages non traités doivent être passés à la classe de base.

Personnalisation de la fonction de raccordement n’est pas nécessaire.

Pour plus d’informations sur l’utilisation de `CFindReplaceDialog`, consultez [des Classes de boîte de dialogue communes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdlgs.h

##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog

Construit un objet `CFindReplaceDialog`.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Notes

Étant donné que le `CFindReplaceDialog` objet est une boîte de dialogue non modale, vous devez construire sur le tas à l’aide de la **nouveau** opérateur.

Au cours de destruction, l’infrastructure essaie d’exécuter un **supprimer cette** sur le pointeur vers la boîte de dialogue. Si vous avez créé la boîte de dialogue sur la pile, le **cela** pointeur n’existe pas et un comportement non défini peut aboutir.

Pour plus d’informations sur la construction de `CFindReplaceDialog` , voir la [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) vue d’ensemble. Utilisez le [CFindReplaceDialog::Create](#create) fonction membre pour afficher la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

Crée et affiche un rechercher ou rechercher/remplacer objet boîte de dialogue, selon la valeur de `bFindDialogOnly`.

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*bFindDialogOnly*<br/>
Définissez ce paramètre sur TRUE pour afficher un **trouver** boîte de dialogue. Affectez-lui la valeur FALSE pour afficher un **rechercher/remplacer** boîte de dialogue.

*lpszFindWhat*<br/>
Pointeur vers la chaîne de recherche par défaut lorsque la boîte de dialogue s’affiche. Si NULL, la boîte de dialogue ne contient pas une chaîne de recherche par défaut.

*lpszReplaceWith*<br/>
Pointeur vers la chaîne de remplacement par défaut lorsque la boîte de dialogue s’affiche. Si NULL, la boîte de dialogue ne contient pas une chaîne de remplacement par défaut.

*dwFlags*<br/>
Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinées à l’aide de l’opérateur OR au niveau du bit. La valeur par défaut est FR_DOWN, qui spécifie que la recherche doit continuer vers le bas. Consultez le [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea) structure dans le SDK Windows pour plus d’informations sur ces indicateurs.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue. Il s’agit de la fenêtre qui reçoit le message spécial qui indique qu’une action de recherche/remplacement est demandée. Si NULL, la fenêtre principale de l’application est utilisée.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet de boîte de dialogue a été créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Dans l’ordre de la fenêtre parente à être informé des demandes de recherche/remplacement, vous devez utiliser le Windows [RegisterWindowMessage](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea) dont la valeur renvoyée est un message unique à l’instance de l’application de fonction. Votre fenêtre frame doit avoir une entrée de mappage de message qui déclare la fonction de rappel ( `OnFindReplace` dans l’exemple qui suit) qui gère ce message enregistré. Le fragment de code suivant est un exemple de procédure à suivre pour une classe de fenêtre frame nommée `CMyRichEditView`:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

Au sein de votre `OnFindReplace` (fonction), vous interprétez les intentions de l’utilisateur à l’aide de la [CFindReplaceDialog::FindNext](#findnext) et [CFindReplaceDialog::IsTerminating](#isterminating) méthodes et que vous créez le code pour les opérations Rechercher/Remplacer.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

##  <a name="findnext"></a>  CFindReplaceDialog::FindNext

Appelez cette fonction à partir de votre fonction de rappel pour déterminer si l’utilisateur souhaite rechercher l’occurrence suivante de la chaîne recherchée.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur souhaite rechercher l’occurrence suivante de la chaîne de recherche. sinon 0.

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

Appelez cette fonction à partir de votre fonction de rappel pour récupérer la chaîne par défaut à rechercher.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Valeur de retour

La chaîne par défaut à rechercher.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier

Appelez cette fonction pour récupérer un pointeur vers la boîte de dialogue Rechercher et remplacer en cours.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*lParam*<br/>
Le *lparam* la valeur passée à la fenêtre frame `OnFindReplace` fonction membre.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la boîte de dialogue actuelle.

### <a name="remarks"></a>Notes

Il doit être utilisé pour accéder à la boîte de dialogue, appeler son membre, fonctions et des accès dans votre fonction de rappel le `m_fr` structure.

### <a name="example"></a>Exemple

Consultez [CFindReplaceDialog::Create](#create) pour obtenir un exemple montrant comment inscrire le Gestionnaire de OnFindReplace pour recevoir des notifications à partir de la boîte de dialogue Rechercher et remplacer.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

Appelez cette fonction pour récupérer la chaîne de remplacement en cours.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Valeur de retour

La chaîne par défaut avec laquelle remplacer des chaînes est trouvés.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFindReplaceDialog::GetFindString](#getfindstring).

##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating

Appelez cette fonction au sein de votre fonction de rappel pour déterminer si l’utilisateur a décidé de mettre fin à la boîte de dialogue.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a décidé de mettre fin à la boîte de dialogue ; sinon 0.

### <a name="remarks"></a>Notes

Si cette fonction retourne une valeur différente de zéro, vous devez appeler la `DestroyWindow` fonction membre de la boîte de dialogue actuelle zone et à n’importe quelle variable de pointeur de boîte dialogue avec la valeur NULL. Si vous le souhaitez, vous pouvez également stocker le texte de recherche/remplacement entré la dernière fois et l’utiliser pour initialiser la boîte de dialogue Rechercher/Remplacer suivante.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFindReplaceDialog::GetFindString](#getfindstring).

##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr

Utilisé pour personnaliser un `CFindReplaceDialog` objet.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Notes

`m_fr` est une structure de type [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea). Ses membres stockent les caractéristiques de l’objet de la boîte de dialogue. Après avoir construit un `CFindReplaceDialog` de l’objet, vous pouvez utiliser `m_fr` pour modifier des valeurs différentes dans la boîte de dialogue.

Pour plus d’informations sur cette structure, consultez le `FINDREPLACE` structure dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

Appelez cette fonction pour déterminer si l’utilisateur souhaite correspond exactement à la casse de la chaîne de recherche.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur souhaite rechercher des occurrences de la chaîne de recherche qui correspondent exactement à la casse de la chaîne de recherche ; sinon 0.

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

Appelez cette fonction pour déterminer si l’utilisateur veut faire correspondre les mots entiers uniquement.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur veut faire correspondre uniquement les mots entiers de la chaîne de recherche. sinon 0.

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

Appelez cette fonction pour déterminer si l’utilisateur souhaite obtenir toutes les occurrences de la chaîne à remplacer.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a demandé que toutes les chaînes correspondant à la chaîne de remplacement remplacé ; sinon 0.

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

Appelez cette fonction pour déterminer si l’utilisateur veut le mot actuel à remplacer.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a demandé que la chaîne sélectionnée actuellement être remplacé par la chaîne de remplacement ; sinon 0.

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

Appelez cette fonction pour déterminer si l’utilisateur souhaite que la recherche continue dans une direction vers le bas.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur souhaite que la recherche continue dans une direction vers le bas ; 0 si l’utilisateur souhaite rechercher vers le haut.

## <a name="see-also"></a>Voir aussi

[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
