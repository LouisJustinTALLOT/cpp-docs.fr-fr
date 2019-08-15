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
ms.openlocfilehash: 71234adec214bcbf5d42090edb582a7e5dd552b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506526"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog, classe

Vous permet d’implémenter des boîtes de dialogue de recherche/remplacement de chaînes standard dans votre application.

## <a name="syntax"></a>Syntaxe

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog)|Appelez cette fonction pour construire un `CFindReplaceDialog` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog:: Create](#create)|Crée et affiche une `CFindReplaceDialog` boîte de dialogue.|
|[CFindReplaceDialog:: FindNext](#findnext)|Appelez cette fonction pour déterminer si l’utilisateur souhaite Rechercher l’occurrence suivante de la chaîne de recherche.|
|[CFindReplaceDialog:: GetFindString](#getfindstring)|Appelez cette fonction pour récupérer la chaîne de recherche actuelle.|
|[CFindReplaceDialog:: GetNotifier](#getnotifier)|Appelez cette fonction pour récupérer la `FINDREPLACE` structure dans votre gestionnaire de messages inscrits.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Appelez cette fonction pour récupérer la chaîne de remplacement actuelle.|
|[CFindReplaceDialog:: IsTerminating](#isterminating)|Appelez cette fonction pour déterminer si la boîte de dialogue s’arrête.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Appelez cette fonction pour déterminer si l’utilisateur souhaite faire correspondre exactement la casse de la chaîne de recherche.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Appelez cette fonction pour déterminer si l’utilisateur souhaite faire correspondre uniquement des mots entiers.|
|[CFindReplaceDialog:: ReplaceAll](#replaceall)|Appelez cette fonction pour déterminer si l’utilisateur souhaite que toutes les occurrences de la chaîne soient remplacées.|
|[CFindReplaceDialog:: ReplaceCurrent](#replacecurrent)|Appelez cette fonction pour déterminer si l’utilisateur souhaite remplacer le mot actuel.|
|[CFindReplaceDialog:: SearchDown](#searchdown)|Appelez cette fonction pour déterminer si l’utilisateur souhaite que la recherche s’effectue dans une direction vers le bas.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Structure utilisée pour personnaliser un `CFindReplaceDialog` objet.|

## <a name="remarks"></a>Notes

Contrairement aux autres boîtes de dialogue courantes de `CFindReplaceDialog` Windows, les objets sont non modals, ce qui permet aux utilisateurs d’interagir avec d’autres fenêtres lorsqu’ils sont à l’écran. Il existe deux types d' `CFindReplaceDialog` objets: Rechercher les boîtes de dialogue et les boîtes de dialogue Rechercher/Remplacer. Bien que les boîtes de dialogue permettent à l’utilisateur d’entrer des chaînes de recherche et de recherche/remplacement, elles n’effectuent aucune des fonctions de recherche ou de remplacement. Vous devez les ajouter à l’application.

Pour construire un `CFindReplaceDialog` objet, utilisez le constructeur fourni (qui n’a pas d’arguments). Étant donné qu’il s’agit d’une boîte de dialogue non modale, allouez l’objet sur le tas à l’aide de l’opérateur **New** , plutôt que sur la pile.

Une fois `CFindReplaceDialog` qu’un objet a été construit, vous devez appeler la fonction membre [Create](#create) pour créer et afficher la boîte de dialogue.

Utilisez la structure [m_fr](#m_fr) pour initialiser la boîte de dialogue avant `Create`d’appeler. La `m_fr` structure est de type [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Pour plus d’informations sur cette structure, consultez la SDK Windows.

Pour que la fenêtre parente soit notifiée des demandes de recherche/remplacement, vous devez utiliser la fonction [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) de Windows et utiliser la macro de table des messages [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) dans votre fenêtre frame qui gère ce message enregistré.

Vous pouvez déterminer si l’utilisateur a décidé de fermer la boîte de dialogue avec `IsTerminating` la fonction membre.

`CFindReplaceDialog`s’appuie sur le COMMDLG. Fichier DLL fourni avec Windows versions 3,1 et ultérieures.

Pour personnaliser la boîte de dialogue, dérivez `CFindReplaceDialog`une classe de, fournissez un modèle de boîte de dialogue personnalisé et ajoutez une table des messages pour traiter les messages de notification des contrôles étendus. Tous les messages non traités doivent être passés à la classe de base.

La personnalisation de la fonction de raccordement n’est pas obligatoire.

Pour plus d’informations sur `CFindReplaceDialog`l’utilisation de, consultez [classes de boîtes de dialogue communes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxdlgs. h

##  <a name="cfindreplacedialog"></a>CFindReplaceDialog:: CFindReplaceDialog

Construit un objet `CFindReplaceDialog`.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Notes

Étant donné `CFindReplaceDialog` que l’objet est une boîte de dialogue non modale, vous devez le construire sur le segment de mémoire à l’aide de l’opérateur **New** .

Pendant la destruction, le Framework tente d’effectuer une **Suppression de ce** sur le pointeur vers la boîte de dialogue. Si vous avez créé la boîte de dialogue sur la pile, le pointeur **This** n’existe pas et un comportement non défini peut se produire.

Pour plus d’informations sur la construction `CFindReplaceDialog` d’objets, consultez la vue d’ensemble de [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) . Utilisez la fonction membre [CFindReplaceDialog:: Create](#create) pour afficher la boîte de dialogue.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

Crée et affiche un objet de boîte de dialogue Rechercher ou rechercher/remplacer, en fonction de la valeur `bFindDialogOnly`de.

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
Affectez la valeur TRUE à ce paramètre pour afficher une boîte de dialogue **Rechercher** . Affectez-lui la valeur FALSe pour afficher une boîte de dialogue **Rechercher/Remplacer** .

*lpszFindWhat*<br/>
Pointeur vers la chaîne de recherche par défaut lorsque la boîte de dialogue s’affiche. Si la valeur est NULL, la boîte de dialogue ne contient pas de chaîne de recherche par défaut.

*lpszReplaceWith*<br/>
Pointeur vers la chaîne de remplacement par défaut lorsque la boîte de dialogue s’affiche. Si la valeur est NULL, la boîte de dialogue ne contient pas de chaîne de remplacement par défaut.

*dwFlags*<br/>
Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinés à l’aide de l’opérateur de bits or. La valeur par défaut est FR_DOWN, qui spécifie que la recherche doit se poursuivre dans le sens inverse. Pour plus d’informations sur ces indicateurs, consultez la structure [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) dans le SDK Windows.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue. Il s’agit de la fenêtre qui recevra le message spécial indiquant qu’une action rechercher/remplacer est demandée. Si la valeur est NULL, la fenêtre principale de l’application est utilisée.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet de boîte de dialogue a été créé avec succès; Sinon, 0.

### <a name="remarks"></a>Notes

Pour que la fenêtre parente soit notifiée des demandes de recherche/remplacement, vous devez utiliser la fonction [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) de Windows dont la valeur de retour est un numéro de message unique à l’instance de l’application. Votre fenêtre frame doit avoir une entrée de table des messages qui déclare la fonction de `OnFindReplace` rappel (dans l’exemple ci-dessous) qui gère ce message inscrit. Le fragment de code suivant est un exemple de la manière de procéder pour une classe de fenêtre `CMyRichEditView`Frame nommée:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

Dans votre `OnFindReplace` fonction, vous interprétez les intentions de l’utilisateur à l’aide des méthodes [CFindReplaceDialog:: FindNext](#findnext) et [CFindReplaceDialog:: IsTerminating](#isterminating) , et vous créez le code pour les opérations de recherche/remplacement.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog).

##  <a name="findnext"></a>CFindReplaceDialog:: FindNext

Appelez cette fonction à partir de votre fonction de rappel pour déterminer si l’utilisateur souhaite Rechercher l’occurrence suivante de la chaîne recherchée.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur souhaite Rechercher l’occurrence suivante de la chaîne recherchée; Sinon, 0.

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

Appelez cette fonction à partir de votre fonction de rappel pour récupérer la chaîne par défaut à rechercher.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne par défaut à rechercher.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>CFindReplaceDialog:: GetNotifier

Appelez cette fonction pour récupérer un pointeur vers la boîte de dialogue de recherche de remplacement en cours.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*lParam*<br/>
Valeur *lParam* passée à la fonction membre de `OnFindReplace` la fenêtre frame.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la boîte de dialogue active.

### <a name="remarks"></a>Notes

Elle doit être utilisée dans votre fonction de rappel pour accéder à la boîte de dialogue active, appeler ses fonctions membres et `m_fr` accéder à la structure.

### <a name="example"></a>Exemples

Pour obtenir un exemple d’inscription du gestionnaire OnFindReplace pour recevoir des notifications à partir de la boîte de dialogue Rechercher et remplacer, consultez [CFindReplaceDialog:: Create](#create) .

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

Appelez cette fonction pour récupérer la chaîne de remplacement actuelle.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne par défaut à utiliser pour remplacer les chaînes trouvées.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFindReplaceDialog:: GetFindString](#getfindstring).

##  <a name="isterminating"></a>CFindReplaceDialog:: IsTerminating

Appelez cette fonction dans votre fonction de rappel pour déterminer si l’utilisateur a décidé de fermer la boîte de dialogue.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a décidé de fermer la boîte de dialogue; Sinon, 0.

### <a name="remarks"></a>Notes

Si cette fonction retourne une valeur différente de zéro, vous `DestroyWindow` devez appeler la fonction membre de la boîte de dialogue active et affecter la valeur null à toute variable de pointeur de boîte de dialogue. Si vous le souhaitez, vous pouvez également stocker le dernier texte de recherche/remplacement entré et l’utiliser pour initialiser la boîte de dialogue Rechercher/Remplacer suivante.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CFindReplaceDialog:: GetFindString](#getfindstring).

##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr

Utilisé pour personnaliser un `CFindReplaceDialog` objet.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Notes

`m_fr`est une structure de type [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Ses membres stockent les caractéristiques de l’objet de boîte de dialogue. Après avoir construit un `CFindReplaceDialog` objet, vous pouvez utiliser `m_fr` pour modifier différentes valeurs dans la boîte de dialogue.

Pour plus d’informations sur cette structure, consultez `FINDREPLACE` la structure dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog).

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

Appelez cette fonction pour déterminer si l’utilisateur souhaite faire correspondre exactement la casse de la chaîne de recherche.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur souhaite rechercher des occurrences de la chaîne de recherche qui correspondent exactement à la casse de la chaîne de recherche; Sinon, 0.

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

Appelez cette fonction pour déterminer si l’utilisateur souhaite faire correspondre uniquement des mots entiers.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur souhaite faire correspondre uniquement les mots entiers de la chaîne recherchée; Sinon, 0.

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

Appelez cette fonction pour déterminer si l’utilisateur souhaite que toutes les occurrences de la chaîne soient remplacées.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a demandé que toutes les chaînes correspondant à la chaîne de remplacement soient remplacées; Sinon, 0.

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

Appelez cette fonction pour déterminer si l’utilisateur souhaite remplacer le mot actuel.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a demandé que la chaîne actuellement sélectionnée soit remplacée par la chaîne de remplacement; Sinon, 0.

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

Appelez cette fonction pour déterminer si l’utilisateur souhaite que la recherche s’effectue dans une direction vers le bas.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’utilisateur veut que la recherche se déroule dans une direction vers le bas; 0 si l’utilisateur veut que la recherche s’effectue dans une direction vers le haut.

## <a name="see-also"></a>Voir aussi

[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
