---
title: Macros de table des messages (MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: ec6e638a1099db8baeefe220215485b6480c30e4
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174765"
---
# <a name="message-map-macros-mfc"></a>Macros de table des messages (MFC)

Pour prendre en charge les tables des messages, la bibliothèque MFC fournit les macros suivantes :

### <a name="message-map-declaration-and-demarcation-macros"></a>Déclaration de la table des messages et des Macros de démarcation

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Déclare qu’une table des messages servira dans une classe pour mapper les messages à des fonctions (doit être utilisé dans la déclaration de classe).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Commence la définition d’une table des messages (doit être utilisé dans l’implémentation de classe).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Commence la définition d’une table des messages sur un type de classe contenant un seul argument de modèle. |
|[END_MESSAGE_MAP](#end_message_map)|Termine la définition d’une table des messages (doit être utilisé dans l’implémentation de classe).|

### <a name="message-mapping-macros"></a>Macros de mappage des messages

|||
|-|-|
|[ON_COMMAND](#on_command)|Indique la fonction qui gérera un message de commande spécifiée.|
|[ON_COMMAND_EX](#on_command_ex)|Indique la fonction qui gérera un message de commande spécifiée.|
|[ON_CONTROL](#on_control)|Indique la fonction qui gérera un message de notification de contrôle spécifié.|
|[ON_MESSAGE](#on_message)|Indique la fonction qui gérera un message défini par l’utilisateur.|
|[ON_OLECMD](#on_olecmd)|Indique la fonction qui gérera une commande de menu à partir de DocObject ou son conteneur.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Indique la fonction qui gérera un message défini par l’utilisateur inscrit.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Indique la fonction qui gérera un message défini par l’utilisateur inscrit lorsque vous avez un `CWinThread` classe.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Indique la fonction qui gérera un message défini par l’utilisateur lorsque vous avez un `CWinThread` classe.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Indique la fonction qui gérera un message de commande de mise à jour spécifié de l’interface utilisateur.|

### <a name="message-map-range-macros"></a>Macros de la plage de la table des messages

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Indique la fonction qui gérera la plage d’ID de commande spécifié dans les deux premiers paramètres dans la macro.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Indique quel gestionnaire de mise à jour gère la plage d’ID de commande spécifié dans les deux premiers paramètres dans la macro.|
|[ON_CONTROL_RANGE](#on_control_range)|Indique la fonction qui gérera les notifications à partir de la plage d’ID spécifiées dans les deuxième et troisième paramètres à la macro de contrôle. Le premier paramètre est un message de notification de contrôle, telles que BN_CLICKED.|

Pour plus d’informations sur les tables des messages, la déclaration de la table des messages et les macros de démarcation et les macros de mappage des messages, consultez [tables des messages](../../mfc/reference/message-maps-mfc.md) et [rubriques de mappage et de gestion des messages](../../mfc/message-handling-and-mapping.md). Pour plus d’informations sur les plages de table des messages, consultez [gestionnaires pour les plages de la table des messages](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

Commence la définition de votre table des messages.

### <a name="syntax"></a>Syntaxe

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Spécifie le nom de la classe dont le message mapper.

*baseClass*<br/>
Spécifie le nom de la classe de base de *theClass*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (.cpp) qui définit les fonctions membres pour votre classe, démarrer la table des messages avec la macro BEGIN_MESSAGE_MAP, puis ajouter des entrées de macro pour chacune de vos fonctions de gestionnaire de messages et terminer la table des messages avec le END_MESSAGE_MAP macro.

Pour plus d’informations sur les tables des messages, consultez [tables des messages](message-maps-mfc.md)

### <a name="example"></a>Exemple

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="begin_template_message_map"></a> BEGIN_TEMPLATE_MESSAGE_MAP

Commence la définition d’une table des messages sur un type de classe contenant un seul argument de modèle.

### <a name="syntax"></a>Syntaxe

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Spécifie le nom de la classe dont le message mapper.

*type_name*<br/>
Le nom du paramètre de modèle spécifié pour la classe.

*baseClass*<br/>
Spécifie le nom de la classe de base de *theClass*.

### <a name="remarks"></a>Notes

Cette macro est semblable à la [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) macro ; Toutefois, cette macro est conçue pour les classes contenant un seul argument de modèle.

Dans la section d’implémentation de méthode de votre classe, démarrez la table des messages avec la macro BEGIN_TEMPLATE_MESSAGE_MAP ; puis ajoutez les entrées de macro pour chacune de vos méthodes de gestionnaire de messages comme vous le feriez pour un mappage de message standard. Comme avec la macro BEGIN_MESSAGE_MAP, effectuer un mappage de message de modèle avec le [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) (macro).

Pour plus d’informations sur l’implémentation des tables des messages pour les classes de modèle, consultez [Comment : Créer une table des messages pour une classe de modèle](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="declare_message_map"></a>  DECLARE_MESSAGE_MAP

Déclare que la classe définit une table des messages. Chaque `CCmdTarget`-classe dérivée dans votre programme doit fournir une table des messages pour gérer les messages.

### <a name="syntax"></a>Syntaxe

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Notes

Utilisez la macro DECLARE_MESSAGE_MAP à la fin de votre déclaration de classe. Puis, dans le fichier .cpp qui définit les fonctions membres pour la classe, utilisez le BEGIN_MESSAGE_MAP (macro), les entrées de la macro pour chacun de vos fonctions de gestionnaire de messages et l’END_MESSAGE_MAP (macro).

> [!NOTE]
>  Si vous déclarez un membre après DECLARE_MESSAGE_MAP, vous devez spécifier un nouveau type d’accès (**public**, **privé**, ou **protégé**) pour eux.

Pour plus d’informations sur les tables des messages et le DECLARE_MESSAGE_MAP (macro), consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="end_message_map"></a>  END_MESSAGE_MAP

Met fin à la définition de votre table des messages.

### <a name="syntax"></a>Syntaxe

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les tables des messages et l’END_MESSAGE_MAP (macro), consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="on_command"></a>  ON_COMMAND

Cette macro est mappé à un message de commande à une fonction membre.

### <a name="syntax"></a>Syntaxe

```
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*commandId*<br/>
ID de la commande.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

### <a name="remarks"></a>Notes

Il indique la fonction qui gérera un message de commande à partir d’un objet d’interface utilisateur de commande tel qu’un bouton de barre d’outils ou élément de menu.

Lorsqu’un objet cible de commande reçoit un message WM_COMMAND de Windows avec l’ID spécifié, ON_COMMAND appelle la fonction membre `memberFxn` pour gérer le message.

ON_COMMAND permet de mapper une seule commande à une fonction membre. Utilisez [ON_COMMAND_RANGE](#on_command_range) pour mapper une plage d’ID de commande à fonction d’un seul membre. Qu’une seule entrée de table des messages peut correspondre à un ID de commande donné. Autrement dit, vous ne pouvez pas mapper une commande à plusieurs gestionnaires. Pour plus d’informations et des exemples, consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="on_command_ex"></a>  ON_COMMAND_EX

Étendue de fonction membre de gestionnaire de commandes.

### <a name="syntax"></a>Syntaxe

```
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Paramètres

*commandId*<br/>
ID de la commande.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

### <a name="remarks"></a>Notes

Une forme étendue de gestionnaires de messages de commande est disponible pour les utilisations avancées. La macro ON_COMMAND_EX est utilisée pour ces gestionnaires de messages, et il fournit un sur-ensemble de la [ON_COMMAND](message-map-macros-mfc.md#on_command) fonctionnalité. Fonctions membres de gestionnaire de commandes étendue acceptent un seul paramètre, UINT contenant l’ID de commande et retournent une valeur Booléenne. La valeur de retour doit être TRUE pour indiquer que la commande a été gérée ; routage dans le cas contraire, il continuera à d’autres objets de cible de commande.

Pour plus d’informations, consultez la Note technique [TN006 : Tables des messages] tm006-message-maps.md).

### <a name="requirements"></a>Configuration requise

Fichier d’en-tête : afxmsg_.h

## <a name="on_control"></a>  ON_CONTROL

Indique la fonction qui gérera un message de notification de contrôles personnalisés.

### <a name="syntax"></a>Syntaxe

```
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*wNotifyCode*<br/>
Le code de notification du contrôle.

*commandId*<br/>
ID de la commande.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

### <a name="remarks"></a>Notes

Messages de notification de contrôle sont ceux envoyés à partir d’un contrôle à sa fenêtre parente.

Il doit y avoir exactement une instruction de macro ON_CONTROL dans votre table des messages pour chaque message de notification de contrôle qui doit être mappée à une fonction de gestionnaire de messages.

Pour plus d’informations et des exemples, consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="on_message"></a>  ON_MESSAGE

Indique la fonction qui gérera un message défini par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Paramètres

*message*<br/>
ID de message.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages auquel le message est mappé.

Le type de la fonction doit être `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.

### <a name="remarks"></a>Notes

Messages définis par l’utilisateur sont ceux qui ne sont pas les messages Windows WM_MESSAGE standard. Lorsque vous sélectionnez un ID de message, vous devez utiliser des valeurs dans la plage de WM_USER (0 x 0400) 0x7FFF ou WM_APP (0 x 8000) pour 0xBFFF. Pour plus d’informations sur l’ID de message, consultez [WM_APP](/windows/desktop/winmsg/wm-app).

Il doit y avoir exactement une instruction de macro ON_MESSAGE dans votre table des messages pour tous les messages définis par l’utilisateur qui doivent être mappé à une fonction de gestionnaire de messages.

> [!NOTE]
>  En plus des messages définis par l’utilisateur, ON_MESSAGE gère les messages Windows moins courantes. Pour plus d’informations, consultez [tables des messages](../../mfc/tn006-message-maps.md).

Pour plus d’informations et des exemples, consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md) et [les gestionnaires définis par l’utilisateur](user-defined-handlers.md)

### <a name="example"></a>Exemple

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="on_olecmd"></a>  ON_OLECMD

Achemine les commandes via l’interface de dispatch de commande `IOleCommandTarget`.

### <a name="syntax"></a>Syntaxe

```
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Paramètres

*pguid*<br/>
Identificateur du groupe de commandes auquel appartient la commande. Utilisez NULL pour le groupe standard.

*olecmdid*<br/>
L’identificateur de la commande OLE.

*commandId*<br/>
L’ID de menu, ID de la barre d’outils, ID de bouton ou autres ID de la ressource ou un objet émettant la commande.

### <a name="remarks"></a>Notes

`IOleCommandTarget` permet à un conteneur de recevoir des commandes provenant de l’interface utilisateur de DocObject et permet au conteneur envoyer les mêmes commandes (telles que nouveau, ouvrir, enregistrer sous et impression dans le menu fichier ; et copier, coller, Annuler, et ainsi de suite dans le menu Edition) pour DocObject.

`IOleCommandTarget` est plus simple que OLE Automation `IDispatch`. `IOleCommandTarget` repose entièrement sur un ensemble standard de commandes ont que rarement des arguments, et aucune information de type n’est impliquée (sécurité de type est également réduite pour les arguments de commande). Si vous n’avez pas besoin de distribuer des commandes avec des arguments, utilisez [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

Le `IOleCommandTarget` des commandes de menu standard ont été implémentées par MFC dans les macros suivantes :

**ON_OLECMD_CLEARSELECTION( )**

Distribue la commande Modifier clair. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Distribue la commande modifier la copie. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Distribue la commande Modifier Couper. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

Distribue la commande fichier nouveau. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

Distribue la commande fichier ouvrir. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

Distribue la commande de mise en Page. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Distribue la commande Coller modifier. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Distribue la commande modifier le collage spécial. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

Distribue la commande Imprimer du fichier. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

Distribue la commande Aperçu avant impression de fichier. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

Distribue la commande modifier la restauration par progression. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

Distribue la commande de l’enregistrement du fichier. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

Distribue la commande Fichier Enregistrer sous. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

Distribue la commande fichier enregistrer une copie sous. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Distribue la commande Sélectionner tout de la modifier. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

Distribue la commande Modifier Annuler. Implémenté en tant que :

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdocob.h

## <a name="on_registered_message"></a>  ON_REGISTERED_MESSAGE

Le Windows `RegisterWindowMessage` fonction est utilisée pour définir un nouveau message de fenêtre est garanti être unique dans tout le système.

### <a name="syntax"></a>Syntaxe

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Paramètres

*nMessageVariable*<br/>
La variable ID de message de fenêtre inscrits.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages auquel le message est mappé.

### <a name="remarks"></a>Notes

Cette macro indique la fonction qui gérera le message enregistré.

Pour plus d’informations et des exemples, consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="on_registered_thread_message"></a>  ON_REGISTERED_THREAD_MESSAGE

Indique la fonction qui gérera le message enregistré par la fonction RegisterWindowMessage de Windows.

### <a name="syntax"></a>Syntaxe

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Paramètres

*nMessageVariable*<br/>
La variable ID de message de fenêtre inscrits.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages CWinThread auquel le message est mappé.

### <a name="remarks"></a>Notes

RegisterWindowMessage est utilisé pour définir un nouveau message de fenêtre est garanti être unique dans tout le système. ON_REGISTERED_THREAD_MESSAGE doit être utilisé au lieu de ON_REGISTERED_MESSAGE lorsque vous avez une classe CWinThread.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="on_thread_message"></a>  ON_THREAD_MESSAGE

Indique la fonction qui gérera un message défini par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Paramètres

*message*<br/>
ID de message.

*memberFxn*<br/>
Le nom de la `CWinThread`-message-fonction de gestionnaire à laquelle le message est mappé.

### <a name="remarks"></a>Notes

ON_THREAD_MESSAGE doit être utilisé au lieu de ON_MESSAGE lorsque vous avez un `CWinThread` classe. Messages définis par l’utilisateur sont ceux qui ne sont pas les messages Windows WM_MESSAGE standard. Il doit y avoir exactement une instruction de macro ON_THREAD_MESSAGE dans votre table des messages pour tous les messages définis par l’utilisateur qui doivent être mappé à une fonction de gestionnaire de messages.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxole.h

## <a name="on_update_command_ui"></a>  ON_UPDATE_COMMAND_UI

Cette macro indique la fonction qui gérera un message de commande de mise à jour de l’interface utilisateur.

### <a name="syntax"></a>Syntaxe

```
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*messageId*<br/>
ID de message.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages auquel le message est mappé.

### <a name="remarks"></a>Notes

Il doit y avoir exactement une instruction de macro ON_UPDATE_COMMAND_UI dans votre table des messages pour chaque commande de mise à jour d’interface utilisateur qui doit être mappée à une fonction de gestionnaire de messages.

Pour plus d’informations et des exemples, consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxole.h

## <a name="on_command_range"></a>  ON_COMMAND_RANGE

Utilisez cette macro pour mapper une plage contiguë d’ID de commande à une fonction de gestionnaire de message unique.

### <a name="syntax"></a>Syntaxe

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*id1*<br/>
ID de commande au début d’une plage contiguë d’ID de commande.

*id2*<br/>
ID de commande à la fin d’une plage contiguë d’ID de commande.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

La plage des identificateurs commence par *id1* et se termine par *id2*.

Utilisez ON_COMMAND_RANGE pour mapper une plage d’ID de commande à fonction d’un seul membre. Utilisez [ON_COMMAND](#on_command) pour mapper une seule commande à une fonction membre. Qu’une seule entrée de table des messages peut correspondre à un ID de commande donné. Autrement dit, vous ne pouvez pas mapper une commande à plusieurs gestionnaires. Pour plus d’informations sur les plages de message de mappage, consultez [gestionnaires pour les plages de la table des messages](../../mfc/handlers-for-message-map-ranges.md).

Il n’existe aucune prise en charge automatique des plages de table de message, vous devez placer la macro vous-même.

### <a name="example"></a>Exemple

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="on_update_command_ui_range"></a>  ON_UPDATE_COMMAND_UI_RANGE

Mappe une plage contiguë d’ID de commande à une fonction de gestionnaire de messages de mise à jour unique.

### <a name="syntax"></a>Syntaxe

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*id1*<br/>
ID de commande au début d’une plage contiguë d’ID de commande.

*id2*<br/>
ID de commande à la fin d’une plage contiguë d’ID de commande.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages de mise à jour à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Gestionnaires de messages de mise à jour de mettre à jour l’état des éléments de menu et boutons de barre d’outils associés à la commande. La plage des identificateurs commence par *id1* et se termine par *id2*.

Il n’existe aucune prise en charge automatique des plages de table de message, vous devez placer la macro vous-même.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="on_control_range"></a>  ON_CONTROL_RANGE

Utilisez cette macro pour mapper une plage contiguë d’ID de contrôle à une fonction de gestionnaire de message unique pour un message de notification Windows spécifié, tel que BN_CLICKED.

### <a name="syntax"></a>Syntaxe

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*wNotifyCode*<br/>
Le code de notification à laquelle répond votre gestionnaire.

*id1*<br/>
ID de commande au début d’une plage contiguë d’ID de contrôle.

*id2*<br/>
ID de commande à la fin d’une plage contiguë d’ID de contrôle.

*memberFxn*<br/>
Le nom de la fonction de gestionnaire de messages auquel les contrôles sont mappés.

### <a name="remarks"></a>Notes

La plage des identificateurs commence par *id1* et se termine par *id2*. Le gestionnaire est appelé pour la notification spécifiée en provenance des contrôles mappés.

Il n’existe aucune prise en charge automatique des plages de table de message, vous devez placer la macro vous-même.

Pour plus d’informations sur l’implémentation des fonctions du gestionnaire pour une plage d’ID de contrôle, consultez [gestionnaires pour les plages de la table des messages](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_.h

## <a name="see-also"></a>Voir aussi

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006 : Tables des messages](../tn006-message-maps.md)<br/>
[COleCmdUI, classe](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)<br/>
[Gestionnaires définis par l’utilisateur](user-defined-handlers.md)<br/>
[CCmdUI, classe](ccmdui-class.md)
