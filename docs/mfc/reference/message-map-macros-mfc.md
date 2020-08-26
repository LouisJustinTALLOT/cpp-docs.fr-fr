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
ms.openlocfilehash: 33b5d2eaefa11f9ccf6459aa05b4e24138731e80
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840269"
---
# <a name="message-map-macros-mfc"></a>Macros de table des messages (MFC)

Pour prendre en charge les tables de messages, MFC fournit les macros suivantes :

### <a name="message-map-declaration-and-demarcation-macros"></a>Déclaration de table de messages et macros de délimitation

|Nom|Description|
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Déclare qu’une table des messages sera utilisée dans une classe pour mapper des messages à des fonctions (doit être utilisé dans la déclaration de classe).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Commence la définition d’une table des messages (doit être utilisée dans l’implémentation de la classe).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Commence la définition d’une table des messages sur un type de classe contenant un argument de modèle unique. |
|[END_MESSAGE_MAP](#end_message_map)|Termine la définition d’une table des messages (doit être utilisée dans l’implémentation de la classe).|

### <a name="message-mapping-macros"></a>Macros de mappage de message

|Nom|Description|
|-|-|
|[ON_COMMAND](#on_command)|Indique quelle fonction gérera un message de commande spécifié.|
|[ON_COMMAND_EX](#on_command_ex)|Indique quelle fonction gérera un message de commande spécifié.|
|[ON_CONTROL](#on_control)|Indique quelle fonction gérera un message de notification de contrôle spécifié.|
|[ON_MESSAGE](#on_message)|Indique quelle fonction gérera un message défini par l’utilisateur.|
|[ON_OLECMD](#on_olecmd)|Indique quelle fonction gère une commande de menu à partir d’un DocObject ou de son conteneur.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Indique quelle fonction gérera un message enregistré défini par l’utilisateur.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Indique quelle fonction gérera un message enregistré défini par l’utilisateur lorsque vous avez une `CWinThread` classe.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Indique quelle fonction gérera un message défini par l’utilisateur lorsque vous avez une `CWinThread` classe.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Indique quelle fonction doit gérer un message de commande de mise à jour d’interface utilisateur spécifié.|

### <a name="message-map-range-macros"></a>Macros de plage de la table des messages

|Nom|Description|
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Indique quelle fonction gérera la plage d’ID de commandes spécifiée dans les deux premiers paramètres de la macro.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Indique le gestionnaire de mise à jour qui gérera la plage d’ID de commandes spécifiée dans les deux premiers paramètres de la macro.|
|[ON_CONTROL_RANGE](#on_control_range)|Indique quelle fonction gérera les notifications à partir de la plage d’ID de contrôle spécifiée dans les deuxième et troisième paramètres à la macro. Le premier paramètre est un message de notification de contrôle, tel que BN_CLICKED.|

Pour plus d’informations sur les tables de messages, sur les macros de déclaration et de délimitation de table des messages, ainsi que sur les macros de mappage de message, consultez les rubriques [tables](../../mfc/reference/message-maps-mfc.md) des messages et [gestion des messages et mappage](../../mfc/message-handling-and-mapping.md). Pour plus d’informations sur les plages de la table des messages, consultez [gestionnaires pour les plages de la table des messages](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a><a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

Commence la définition de votre table des messages.

### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Spécifie le nom de la classe dont la table des messages est.

*baseClass*<br/>
Spécifie le nom de la classe de base de *les*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (. cpp) qui définit les fonctions membres pour votre classe, démarrez la table des messages avec la macro BEGIN_MESSAGE_MAP, puis ajoutez des entrées de macro pour chacune de vos fonctions de gestionnaire de messages et complétez la table des messages avec la macro END_MESSAGE_MAP.

Pour plus d’informations sur les tables des messages, consultez [tables des messages](message-maps-mfc.md) .

### <a name="example"></a>Exemple

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a> BEGIN_TEMPLATE_MESSAGE_MAP

Commence la définition d’une table des messages sur un type de classe contenant un argument de modèle unique.

### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Spécifie le nom de la classe dont la table des messages est.

*TYPE_NAME*<br/>
Nom du paramètre de modèle spécifié pour la classe.

*baseClass*<br/>
Spécifie le nom de la classe de base de *les*.

### <a name="remarks"></a>Notes

Cette macro est similaire à la macro [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) ; Toutefois, cette macro est destinée aux classes contenant un argument de modèle unique.

Dans la section implémentation de méthode de votre classe, démarrez la table des messages avec la macro BEGIN_TEMPLATE_MESSAGE_MAP ; Ajoutez ensuite des entrées de macro pour chacune de vos méthodes de gestionnaire de messages, comme vous le feriez pour une table des messages standard. Comme pour la macro BEGIN_MESSAGE_MAP, complétez la table des messages de modèle avec la macro [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) .

Pour plus d’informations sur l’implémentation des tables des messages pour les classes de modèle, consultez [Comment : créer une table des messages pour une classe de modèle](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a> DECLARE_MESSAGE_MAP

Déclare que la classe définit une table des messages. Chaque `CCmdTarget` classe dérivée de votre programme doit fournir une table des messages pour gérer les messages.

### <a name="syntax"></a>Syntaxe

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Notes

Utilisez la macro DECLARE_MESSAGE_MAP à la fin de votre déclaration de classe. Ensuite, dans le fichier. cpp qui définit les fonctions membres de la classe, utilisez la macro BEGIN_MESSAGE_MAP, les entrées de macro pour chacune de vos fonctions de gestionnaire de messages et la macro END_MESSAGE_MAP.

> [!NOTE]
> Si vous déclarez un membre après DECLARE_MESSAGE_MAP, vous devez spécifier un nouveau type d’accès ( **`public`** , **`private`** ou **`protected`** ) pour ceux-ci.

Pour plus d’informations sur les tables des messages et la macro DECLARE_MESSAGE_MAP, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a> END_MESSAGE_MAP

Termine la définition de votre table des messages.

### <a name="syntax"></a>Syntaxe

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les tables des messages et la macro END_MESSAGE_MAP, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="on_command"></a><a name="on_command"></a> ON_COMMAND

Cette macro mappe un message de commande à une fonction membre.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*commandId*<br/>
ID de la commande.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

### <a name="remarks"></a>Notes

Elle indique quelle fonction gérera un message de commande à partir d’un objet d’interface utilisateur de commande comme un élément de menu ou un bouton de barre d’outils.

Lorsqu’un objet cible de commande reçoit un message de WM_COMMAND Windows avec l’ID spécifié, ON_COMMAND appelle la fonction membre `memberFxn` pour gérer le message.

Utilisez ON_COMMAND pour mapper une commande unique à une fonction membre. Utilisez [ON_COMMAND_RANGE](#on_command_range) pour mapper une plage d’ID de commandes à une fonction membre. Une seule entrée de table des messages peut correspondre à un ID de commande donné. Autrement dit, vous ne pouvez pas mapper une commande à plus d’un gestionnaire. Pour plus d’informations et d’exemples, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_. h

## <a name="on_command_ex"></a><a name="on_command_ex"></a> ON_COMMAND_EX

Fonction membre du gestionnaire de commandes étendue.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Paramètres

*commandId*<br/>
ID de la commande.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

### <a name="remarks"></a>Notes

Une forme étendue de gestionnaires de messages de commande est disponible pour des utilisations avancées. La macro ON_COMMAND_EX est utilisée pour ces gestionnaires de messages et fournit un sur-ensemble de la fonctionnalité de [ON_COMMAND](message-map-macros-mfc.md#on_command) . Les fonctions membres du gestionnaire de commandes étendu acceptent un seul paramètre, un UINT contenant l’ID de commande et retournent une valeur BOOLÉENNE. La valeur de retour doit être TRUE pour indiquer que la commande a été gérée ; Sinon, le routage continue vers d’autres objets de la cible de commande.

Pour plus d’informations, consultez Technical note [TN006 : messages Maps] tm006-message-maps.md).

### <a name="requirements"></a>Configuration requise

Fichier d’en-tête : afxmsg_. h

## <a name="on_control"></a><a name="on_control"></a> ON_CONTROL

Indique quelle fonction doit gérer un message de notification de contrôle personnalisé.

### <a name="syntax"></a>Syntaxe

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*wNotifyCode*<br/>
Code de notification du contrôle.

*commandId*<br/>
ID de la commande.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

### <a name="remarks"></a>Notes

Les messages de notification de contrôle sont ceux envoyés à partir d’un contrôle à sa fenêtre parente.

Il doit y avoir exactement une ON_CONTROL instruction de macro dans votre table des messages pour chaque message de notification de contrôle qui doit être mappé à une fonction de gestionnaire de messages.

Pour plus d’informations et d’exemples, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_. h

## <a name="on_message"></a><a name="on_message"></a> ON_MESSAGE

Indique quelle fonction gérera un message défini par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Paramètres

*message*<br/>
ID de message.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle le message est mappé.

Le type de la fonction doit être `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)` .

### <a name="remarks"></a>Notes

Les messages définis par l’utilisateur sont des messages qui ne sont pas des messages Windows WM_MESSAGE standard. Lors de la sélection d’un ID de message, vous devez utiliser des valeurs comprises dans la plage de WM_USER (0x0400) à 0x7FFF ou WM_APP (0x8000) à 0xBFFF. Pour plus d’informations sur les ID de message, consultez [WM_APP](/windows/win32/winmsg/wm-app).

Il doit y avoir exactement une ON_MESSAGE instruction de macro dans votre table des messages pour chaque message défini par l’utilisateur qui doit être mappé à une fonction de gestionnaire de messages.

> [!NOTE]
> En plus des messages définis par l’utilisateur, ON_MESSAGE gère les messages Windows moins courants. Pour plus d’informations, consultez [tables des messages](../../mfc/tn006-message-maps.md).

Pour plus d’informations et d’exemples, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md) et les [gestionnaires définis par l’utilisateur](user-defined-handlers.md) .

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

**En-tête :** afxmsg_. h

## <a name="on_olecmd"></a><a name="on_olecmd"></a> ON_OLECMD

Achemine les commandes par le biais de l’interface de dispatch de commande `IOleCommandTarget` .

### <a name="syntax"></a>Syntaxe

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Paramètres

*pguid*<br/>
Identificateur du groupe de commandes auquel appartient la commande. Utilisez la valeur NULL pour le groupe standard.

*olecmdid*<br/>
Identificateur de la commande OLE.

*commandId*<br/>
L’ID de menu, l’ID de barre d’outils, l’ID de bouton ou un autre ID de la ressource ou de l’objet qui émet la commande.

### <a name="remarks"></a>Notes

`IOleCommandTarget` permet à un conteneur de recevoir des commandes qui proviennent de l’interface utilisateur d’un DocObject, et permet au conteneur d’envoyer les mêmes commandes (telles que New, Open, SaveAs et Print dans le menu File, et de copier, coller, annuler, etc. dans le menu Edition) à un DocObject.

`IOleCommandTarget` est plus simple que OLE Automation `IDispatch` . `IOleCommandTarget` repose entièrement sur un ensemble standard de commandes qui ont rarement des arguments, et aucune information de type n’est impliquée (la sécurité de type est également réduite pour les arguments de commande). Si vous devez distribuer des commandes avec des arguments, utilisez [COleServerDoc :: OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

Les `IOleCommandTarget` commandes de menu standard ont été implémentées par MFC dans les macros suivantes :

**ON_OLECMD_CLEARSELECTION ()**

Distribue la commande Edit Clear. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY ()**

Distribue la commande modifier la copie. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT ()**

Distribue la commande Modifier Cut. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW ()**

Distribue la nouvelle commande file. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN ()**

Distribue la commande fichier ouvrir. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP ()**

Distribue la commande de mise en page de fichier. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE ()**

Distribue la commande Modifier coller. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL ()**

Distribue la commande Modifier Collage spécial. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT ()**

Distribue la commande d’impression de fichier. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW ()**

Distribue la commande Aperçu avant impression du fichier. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO ()**

Distribue la commande Edit Redo. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE ()**

Distribue la commande d’enregistrement de fichier. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS ()**

Distribue la commande fichier enregistrer sous. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS ()**

Distribue la commande Enregistrer la copie sous. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL ()**

Distribue la commande Modifier sélectionner tout. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO ()**

Distribue la commande modifier annuler. Implémentée en tant que :

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Configuration requise

**En-tête :** AfxDocOb. h

## <a name="on_registered_message"></a><a name="on_registered_message"></a> ON_REGISTERED_MESSAGE

La `RegisterWindowMessage` fonction Windows est utilisée pour définir un nouveau message de fenêtre qui est garanti comme étant unique dans tout le système.

### <a name="syntax"></a>Syntaxe

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Paramètres

*nMessageVariable*<br/>
Variable d’ID de message de fenêtre inscrite.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle le message est mappé.

### <a name="remarks"></a>Notes

Cette macro indique quelle fonction va gérer le message inscrit.

Pour plus d’informations et d’exemples, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_. h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a> ON_REGISTERED_THREAD_MESSAGE

Indique quelle fonction gère le message enregistré par la fonction RegisterWindowMessage de Windows.

### <a name="syntax"></a>Syntaxe

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Paramètres

*nMessageVariable*<br/>
Variable d’ID de message de fenêtre inscrite.

*memberFxn*<br/>
Nom de la fonction CWinThread-Message-Handler à laquelle le message est mappé.

### <a name="remarks"></a>Notes

RegisterWindowMessage est utilisé pour définir un nouveau message de fenêtre qui est garanti comme étant unique dans tout le système. ON_REGISTERED_THREAD_MESSAGE doit être utilisé à la place de ON_REGISTERED_MESSAGE quand vous avez une classe CWinThread.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_. h

## <a name="on_thread_message"></a><a name="on_thread_message"></a> ON_THREAD_MESSAGE

Indique quelle fonction gérera un message défini par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Paramètres

*message*<br/>
ID de message.

*memberFxn*<br/>
Nom de la `CWinThread` fonction de gestionnaire de messages à laquelle le message est mappé.

### <a name="remarks"></a>Notes

ON_THREAD_MESSAGE doit être utilisé à la place de ON_MESSAGE quand vous avez une `CWinThread` classe. Les messages définis par l’utilisateur sont des messages qui ne sont pas des messages Windows WM_MESSAGE standard. Il doit y avoir exactement une ON_THREAD_MESSAGE instruction de macro dans votre table des messages pour chaque message défini par l’utilisateur qui doit être mappé à une fonction de gestionnaire de messages.

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXOLE. h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a> ON_UPDATE_COMMAND_UI

Cette macro indique quelle fonction doit gérer un message de commande de mise à jour de l’interface utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
ID de message.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle le message est mappé.

### <a name="remarks"></a>Notes

Il doit y avoir exactement une instruction de macro ON_UPDATE_COMMAND_UI dans votre table des messages pour chaque commande de mise à jour d’interface utilisateur qui doit être mappée à une fonction de gestionnaire de messages.

Pour plus d’informations et d’exemples, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXOLE. h

## <a name="on_command_range"></a><a name="on_command_range"></a> ON_COMMAND_RANGE

Utilisez cette macro pour mapper une plage contiguë d’ID de commandes à une fonction de gestionnaire de messages unique.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*ID1*<br/>
ID de commande au début d’une plage contiguë d’ID de commande.

*ID2*<br/>
ID de commande à la fin d’une plage contiguë d’ID de commande.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

La plage d’ID commence par *ID1* et se termine par *ID2*.

Utilisez ON_COMMAND_RANGE pour mapper une plage d’ID de commandes à une fonction membre. Utilisez [ON_COMMAND](#on_command) pour mapper une commande unique à une fonction membre. Une seule entrée de table des messages peut correspondre à un ID de commande donné. Autrement dit, vous ne pouvez pas mapper une commande à plus d’un gestionnaire. Pour plus d’informations sur le mappage des plages de messages, consultez [gestionnaires pour les plages de la table des messages](../../mfc/handlers-for-message-map-ranges.md).

Il n’existe pas de prise en charge automatique des plages de la table des messages. vous devez donc placer la macro vous-même.

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

**En-tête :** afxmsg_. h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a> ON_UPDATE_COMMAND_UI_RANGE

Mappe une plage contiguë d’ID de commande à une seule fonction de gestionnaire de messages de mise à jour.

### <a name="syntax"></a>Syntaxe

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*ID1*<br/>
ID de commande au début d’une plage contiguë d’ID de commande.

*ID2*<br/>
ID de commande à la fin d’une plage contiguë d’ID de commande.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de message de mise à jour à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Mettre à jour les gestionnaires de messages met à jour l’état des éléments de menu et des boutons de barre d’outils associés à la commande. La plage d’ID commence par *ID1* et se termine par *ID2*.

Il n’existe pas de prise en charge automatique des plages de la table des messages. vous devez donc placer la macro vous-même.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_. h

## <a name="on_control_range"></a><a name="on_control_range"></a> ON_CONTROL_RANGE

Utilisez cette macro pour mapper une plage contiguë d’ID de contrôle à une fonction de gestionnaire de messages unique pour un message de notification Windows spécifié, tel que BN_CLICKED.

### <a name="syntax"></a>Syntaxe

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*wNotifyCode*<br/>
Code de notification auquel votre gestionnaire répond.

*ID1*<br/>
ID de commande au début d’une plage contiguë d’ID de contrôle.

*ID2*<br/>
ID de commande à la fin d’une plage contiguë d’ID de contrôle.

*memberFxn*<br/>
Nom de la fonction de gestionnaire de messages à laquelle les contrôles sont mappés.

### <a name="remarks"></a>Notes

La plage d’ID commence par *ID1* et se termine par *ID2*. Le gestionnaire est appelé pour la notification spécifiée provenant de l’un des contrôles mappés.

Il n’existe pas de prise en charge automatique des plages de la table des messages. vous devez donc placer la macro vous-même.

Pour plus d’informations sur l’implémentation des fonctions de gestionnaire pour une plage d’ID de contrôle, consultez [gestionnaires pour les plages de table de messages](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmsg_. h

## <a name="see-also"></a>Voir aussi

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006 : tables des messages](../tn006-message-maps.md)<br/>
[COleCmdUI, classe](colecmdui-class.md)<br/>
[COleServerDoc :: OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Gestionnaires définis par l’utilisateur](user-defined-handlers.md)<br/>
[CCmdUI, classe](ccmdui-class.md)
