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
ms.openlocfilehash: 6e9291f0f39057403bc27c7fe4ff5ca5a82dfe3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356584"
---
# <a name="message-map-macros-mfc"></a>Macros de table des messages (MFC)

Pour étayer les cartes de messages, MFC fournit les macros suivantes :

### <a name="message-map-declaration-and-demarcation-macros"></a>Déclaration de carte de message et macros de démarcation

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Déclare qu’une carte de message sera utilisée dans une classe pour cartographier les messages aux fonctions (doit être utilisée dans la déclaration de classe).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Commence la définition d’une carte de message (doit être utilisée dans la mise en œuvre de la classe).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Commence la définition d’une carte de message sur un type de classe contenant un seul argument de modèle. |
|[END_MESSAGE_MAP](#end_message_map)|Termine la définition d’une carte de message (doit être utilisée dans la mise en œuvre de la classe).|

### <a name="message-mapping-macros"></a>Macros de cartographie des messages

|||
|-|-|
|[ON_COMMAND](#on_command)|Indique quelle fonction traitera un message de commande spécifié.|
|[ON_COMMAND_EX](#on_command_ex)|Indique quelle fonction traitera un message de commande spécifié.|
|[ON_CONTROL](#on_control)|Indique quelle fonction traitera un message de notification de contrôle spécifié.|
|[ON_MESSAGE](#on_message)|Indique quelle fonction gérera un message défini par l’utilisateur.|
|[ON_OLECMD](#on_olecmd)|Indique quelle fonction gérera une commande de menu à partir d’un DocObject ou de son conteneur.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Indique quelle fonction traitera un message enregistré défini par l’utilisateur.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Indique quelle fonction traitera un message enregistré `CWinThread` défini par l’utilisateur lorsque vous avez une classe.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Indique quelle fonction gérera un message défini `CWinThread` par l’utilisateur lorsque vous avez une classe.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Indique quelle fonction gérera un message de commande de mise à jour utilisateur-interface spécifié.|

### <a name="message-map-range-macros"></a>Macros de portée Message-Map

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Indique quelle fonction gérera la gamme d’ID de commande spécifiée dans les deux premiers paramètres de la macro.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Indique quel gestionnaire de mise à jour gérera la gamme d’informations de commande spécifiées dans les deux premiers paramètres de la macro.|
|[ON_CONTROL_RANGE](#on_control_range)|Indique quelle fonction traitera les notifications de la gamme d’ID de contrôle spécifiée dans les deuxième et troisième paramètres à la macro. Le premier paramètre est un message de notification de contrôle, tel que BN_CLICKED.|

Pour plus d’informations sur les cartes de messages, la déclaration de carte de message et les macros de démarcation, et les macros de cartographie des messages, voir [cartes de messages](../../mfc/reference/message-maps-mfc.md) et sujets de traitement et de cartographie des [messages](../../mfc/message-handling-and-mapping.md). Pour plus d’informations sur les plages de cartes de messages, voir [Handlers for Message-Map Ranges](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Commence la définition de votre carte de message.

### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Spécifie le nom de la classe dont il s’agit de la carte de message.

*Baseclass*<br/>
Spécifie le nom de la classe de base de *la Classe*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (.cpp) qui définit les fonctions des membres pour votre classe, démarrez la carte de message avec la BEGIN_MESSAGE_MAP macro, puis ajoutez des entrées macro pour chacune de vos fonctions de gestionnaire de message, et remplissez la carte de message avec la END_MESSAGE_MAP macro.

Pour plus d’informations sur les cartes de messages, voir [Cartes des messages](message-maps-mfc.md)

### <a name="example"></a>Exemple

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Commence la définition d’une carte de message sur un type de classe contenant un seul argument de modèle.

### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Spécifie le nom de la classe dont il s’agit de la carte de message.

*type_name*<br/>
Le nom du paramètre du modèle spécifié pour la classe.

*Baseclass*<br/>
Spécifie le nom de la classe de base de *la Classe*.

### <a name="remarks"></a>Notes

Cette macro est similaire à la [macro BEGIN_MESSAGE_MAP;](message-map-macros-mfc.md#begin_message_map) cependant, cette macro est destinée aux classes contenant un seul argument de modèle.

Dans la section d’implémentation de la méthode de votre classe, commencez la carte de message avec la macro BEGIN_TEMPLATE_MESSAGE_MAP; puis ajoutez des entrées macro pour chacune de vos méthodes de gestionnaire de messages comme vous le feriez pour une carte de message standard. Comme avec la macro BEGIN_MESSAGE_MAP, complétez la carte de message de modèle avec la macro [END_MESSAGE_MAP.](message-map-macros-mfc.md#end_message_map)

Pour plus d’informations sur la mise en œuvre des cartes de messages pour les classes de modèles, consultez [Comment créer une carte de message pour une classe de gabarit](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Déclare que la classe définit une carte de message. Chaque `CCmdTarget`classe dérivée de votre programme doit fournir une carte de message pour traiter les messages.

### <a name="syntax"></a>Syntaxe

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Notes

Utilisez la macro DECLARE_MESSAGE_MAP à la fin de votre déclaration de classe. Ensuite, dans le fichier .cpp qui définit les fonctions du membre pour la classe, utilisez les BEGIN_MESSAGE_MAP macro, les entrées macro pour chacune de vos fonctions de gestionnaire de messages, et la macro END_MESSAGE_MAP.

> [!NOTE]
> Si vous déclarez un membre après DECLARE_MESSAGE_MAP, vous devez spécifier un nouveau type d’accès **(public,** **privé**ou **protégé)** pour eux.

Pour plus d’informations sur les cartes de messages et la macro DECLARE_MESSAGE_MAP, voir [Message Handling and Mapping Topics](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

Termine la définition de votre carte de message.

### <a name="syntax"></a>Syntaxe

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les cartes de messages et la macro END_MESSAGE_MAP, voir [Message Handling and Mapping Topics](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>ON_COMMAND

Cette macro cartographie un message de commande à une fonction de membre.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*Commandid*<br/>
ID de la commande.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de message à laquelle la commande est cartographiée.

### <a name="remarks"></a>Notes

Il indique quelle fonction gérera un message de commande à partir d’un objet de commande utilisateur-interface tel qu’un élément de menu ou un bouton de barre d’outils.

Lorsqu’un objet cible de commande reçoit un message Windows WM_COMMAND avec l’ID `memberFxn` spécifié, ON_COMMAND appelle la fonction membre pour gérer le message.

Utilisez ON_COMMAND pour cartographier une seule commande à une fonction de membre. Utilisez [ON_COMMAND_RANGE](#on_command_range) pour cartographier une gamme d’informations de commande à une fonction de membre. Une seule entrée de carte de message peut correspondre à une pièce d’identité de commande donnée. Autrement dit, vous ne pouvez pas cartographier une commande à plus d’un gestionnaire. Pour plus d’informations et d’exemples, voir [Les sujets de traitement et de cartographie des messages](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

Fonction élargie de membre de commande-handler.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Paramètres

*Commandid*<br/>
ID de la commande.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de message à laquelle la commande est cartographiée.

### <a name="remarks"></a>Notes

Une forme étendue de gestionnaires de messages de commande est disponible pour des utilisations avancées. La macro ON_COMMAND_EX est utilisée pour ces gestionnaires de messages, et il fournit un superset de la [fonctionnalité ON_COMMAND.](message-map-macros-mfc.md#on_command) Les fonctions élargies de membre de commande-handler prennent un seul paramètre, un UINT contenant l’ID de commande, et renvoient un BOOL. La valeur de retour devrait être VRAI pour indiquer que la commande a été manipulée; sinon le routage continuera à d’autres objets cibles de commande.

Pour plus d’informations, voir Note technique [TN006: Message Maps]tm006-message-maps.md).

### <a name="requirements"></a>Spécifications

Fichier d’en-tête: afxmsg_.h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

Indique quelle fonction gérera un message de notification sur mesure.

### <a name="syntax"></a>Syntaxe

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*wNotifyCode (en)*<br/>
Le code de notification du contrôle.

*Commandid*<br/>
ID de la commande.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de message à laquelle la commande est cartographiée.

### <a name="remarks"></a>Notes

Les messages de notification de contrôle sont ceux envoyés d’un contrôle à sa fenêtre parente.

Il doit y avoir exactement une ON_CONTROL macro dans votre carte de message pour chaque message de notification de contrôle qui doit être cartographié à une fonction de gestionnaire de message.

Pour plus d’informations et d’exemples, voir [Les sujets de traitement et de cartographie des messages](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

Indique quelle fonction gérera un message défini par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Paramètres

*Message*<br/>
ID de message.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle le message est cartographié.

Le type de la `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`fonction doit être .

### <a name="remarks"></a>Notes

Les messages définis par l’utilisateur sont des messages qui ne sont pas des messages de WM_MESSAGE Windows standard. Lors de la sélection d’un ID de message, vous devez utiliser des valeurs dans la gamme de WM_USER (0x0400) à 0x7FFF ou WM_APP (0x8000) à 0xBFFF. Pour plus d’informations sur les demandes d’informations sur les messages d’information, voir [WM_APP](/windows/win32/winmsg/wm-app).

Il devrait y avoir exactement une ON_MESSAGE macro-énoncé dans votre carte de message pour chaque message défini par l’utilisateur qui doit être cartographié à une fonction de gestionnaire de message.

> [!NOTE]
> En plus des messages définis par l’utilisateur, ON_MESSAGE gère des messages Windows moins courants. Pour plus d’informations, voir [Cartes de message](../../mfc/tn006-message-maps.md).

Pour plus d’informations et d’exemples, consultez [les sujets de traitement et de cartographie des messages](../../mfc/message-handling-and-mapping.md) et les gestionnaires [définis par les utilisateurs](user-defined-handlers.md)

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

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

Itinéraires commandes à travers `IOleCommandTarget`l’interface de commande de répartition .

### <a name="syntax"></a>Syntaxe

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Paramètres

*pguid*<br/>
Identification du groupe de commandement auquel appartient la commande. Utilisez NULL pour le groupe standard.

*olecmdid*<br/>
L’identifiant de la commande OLE.

*Commandid*<br/>
L’ID du menu, l’ID de la barre d’outils, l’id bouton ou toute autre pièce d’identité de la ressource ou de l’objet émettant la commande.

### <a name="remarks"></a>Notes

`IOleCommandTarget`permet à un conteneur de recevoir des commandes provenant de l’interface utilisateur d’un DocObject, et permet au conteneur d’envoyer les mêmes commandes (telles que New, Open, SaveAs, et Print sur le menu Fichier; et Copier, pâte, Annuler, et ainsi de suite sur le menu Edit) à un DocObject.

`IOleCommandTarget`est plus simple que OLE Automation `IDispatch`. `IOleCommandTarget`s’appuie entièrement sur un ensemble standard de commandes qui ont rarement des arguments, et aucune information type n’est impliquée (la sécurité de type est diminuée pour les arguments de commande aussi bien). Si vous avez besoin d’envoyer des commandes avec des arguments, utilisez [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

Les `IOleCommandTarget` commandes de menu standard ont été mises en œuvre par MFC dans les macros suivantes :

**ON_OLECMD_CLEARSELECTION)**

Envoie la commande Edit Clear. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY)**

Dépêche la commande Modifier la copie. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT)**

Envoie la commande Edit Cut. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW)**

Dépêche la commande Du fichier Nouveau. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN)**

Envoie la commande File Open. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP)**

Envoie la commande de configuration de la page de fichiers. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE)**

Dépêche la commande Edit Paste. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL)**

Dépêche la commande spéciale Edit Paste. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT)**

Dépêche la commande d’impression de fichiers. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW)**

Dépêche la commande d’aperçu d’impression de fichiers. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO)**

Envoie la commande Edit Redo. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE)**

Envoie la commande De l’enregistrement de fichiers. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS)**

Dépêche le fichier Enregistrer comme commande. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS)**

Dépêche la copie d’enregistrement de fichier comme commande. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL)**

Envoie la commande Edit Select All. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO)**

Envoie la commande Edit Undo. Implémenté comme:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Spécifications

**En-tête:** afxdocob.h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

La `RegisterWindowMessage` fonction Windows est utilisée pour définir un nouveau message de fenêtre qui est garanti pour être unique dans l’ensemble du système.

### <a name="syntax"></a>Syntaxe

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Paramètres

*nMessageVariable*<br/>
La variable d’identification de message de fenêtre enregistrée.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle le message est cartographié.

### <a name="remarks"></a>Notes

Cette macro indique quelle fonction traitera le message enregistré.

Pour plus d’informations et d’exemples, voir [Les sujets de traitement et de cartographie des messages](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Exemple

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Indique quelle fonction gérera le message enregistré par la fonction Windows RegisterWindowMessage.

### <a name="syntax"></a>Syntaxe

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Paramètres

*nMessageVariable*<br/>
La variable d’identification de message de fenêtre enregistrée.

*membreFxn*<br/>
Le nom de la fonction CWinThread-message-handler à laquelle le message est cartographié.

### <a name="remarks"></a>Notes

RegisterWindowMessage est utilisé pour définir un nouveau message de fenêtre qui est garanti pour être unique dans l’ensemble du système. ON_REGISTERED_THREAD_MESSAGE doit être utilisé au lieu de ON_REGISTERED_MESSAGE lorsque vous avez un cours CWinThread.

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

Indique quelle fonction gérera un message défini par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Paramètres

*Message*<br/>
ID de message.

*membreFxn*<br/>
Le nom `CWinThread`de la fonction -message-gestionnaire à laquelle le message est cartographié.

### <a name="remarks"></a>Notes

ON_THREAD_MESSAGE doit être utilisé au lieu de ON_MESSAGE lorsque `CWinThread` vous avez un cours. Les messages définis par l’utilisateur sont des messages qui ne sont pas des messages de WM_MESSAGE Windows standard. Il devrait y avoir exactement une ON_THREAD_MESSAGE macro-énoncé dans votre carte de message pour chaque message défini par l’utilisateur qui doit être cartographié à une fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

Cette macro indique quelle fonction gérera un message de commande de mise à jour utilisateur-interface.

### <a name="syntax"></a>Syntaxe

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Paramètres

*Messageid*<br/>
ID de message.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle le message est cartographié.

### <a name="remarks"></a>Notes

Il devrait y avoir exactement une ON_UPDATE_COMMAND_UI macro-énoncé dans votre carte de message pour chaque commande de mise à jour utilisateur-interface qui doit être cartographiée à une fonction de gestionnaire de message.

Pour plus d’informations et d’exemples, voir [Les sujets de traitement et de cartographie des messages](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

Utilisez cette macro pour cartographier une gamme contigus d’ID de commande à une seule fonction de gestionnaire de message.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*id1 (en)*<br/>
Carte ID au début d’une gamme contigue de pièces d’identité de commande.

*id2*<br/>
Carte ID à la fin d’une gamme contigue de pièces d’identité de commande.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle les commandes sont cartographiées.

### <a name="remarks"></a>Notes

La gamme d’ID commence par *id1* et se termine par *id2*.

Utilisez ON_COMMAND_RANGE pour cartographier une gamme d’informations de commande à une fonction de membre. Utilisez [ON_COMMAND](#on_command) pour cartographier une seule commande à une fonction de membre. Une seule entrée de carte de message peut correspondre à une pièce d’identité de commande donnée. Autrement dit, vous ne pouvez pas cartographier une commande à plus d’un gestionnaire. Pour plus d’informations sur la cartographie des plages de messages, voir [Handlers for Message-Map Ranges](../../mfc/handlers-for-message-map-ranges.md).

Il n’y a pas de support automatique pour les plages de carte de message, donc vous devez placer le macro vous-même.

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

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

Cartographiez une gamme contigus d’ID de commande à une seule fonction de gestionnaire de message de mise à jour.

### <a name="syntax"></a>Syntaxe

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*id1 (en)*<br/>
Carte ID au début d’une gamme contigue de pièces d’identité de commande.

*id2*<br/>
Carte ID à la fin d’une gamme contigue de pièces d’identité de commande.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de message de mise à jour à laquelle les commandes sont cartographiées.

### <a name="remarks"></a>Notes

Mettre à jour les gestionnaires de messages mettre à jour l’état des éléments de menu et des boutons de barre d’outils associés à la commande. La gamme d’ID commence par *id1* et se termine par *id2*.

Il n’y a pas de support automatique pour les plages de carte de message, donc vous devez placer le macro vous-même.

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

Utilisez cette macro pour cartographier une gamme contigus d’IDs de contrôle à une seule fonction de gestionnaire de message pour un message de notification Windows spécifié, comme BN_CLICKED.

### <a name="syntax"></a>Syntaxe

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Paramètres

*wNotifyCode (en)*<br/>
Le code de notification auquel votre gestionnaire répond.

*id1 (en)*<br/>
Id de commande au début d’une gamme contigue d’identifications de contrôle.

*id2*<br/>
Id de commande à la fin d’une gamme contigus de pièces d’identité de contrôle.

*membreFxn*<br/>
Le nom de la fonction de gestionnaire de messages à laquelle les commandes sont cartographiées.

### <a name="remarks"></a>Notes

La gamme d’ID commence par *id1* et se termine par *id2*. Le gestionnaire est appelé pour la notification spécifiée provenant de l’un des contrôles cartographiés.

Il n’y a pas de support automatique pour les plages de carte de message, donc vous devez placer le macro vous-même.

Pour plus d’informations sur la mise en œuvre des fonctions de gestionnaire pour une gamme d’ID de contrôle, consultez [Handlers pour les gammes de cartes de message](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxmsg_.h

## <a name="see-also"></a>Voir aussi

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006 : tables des messages](../tn006-message-maps.md)<br/>
[Classe COleCmdUI](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[EnregistrerWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Handlers définis par l’utilisateur](user-defined-handlers.md)<br/>
[CCmdUI, classe](ccmdui-class.md)
