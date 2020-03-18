---
title: Interface ICommandSource
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: a57ca6f36546a17b9a35ebea875ff01b43de1332
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445714"
---
# <a name="icommandsource-interface"></a>Interface ICommandSource

Gère les commandes envoyées à partir d’un objet source de commande à un contrôle utilisateur.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandSource
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[ICommandSource :: AddCommandHandler](#addcommandhandler)|Ajoute un gestionnaire de commandes à un objet source de commande.|
|[ICommandSource :: AddCommandRangeHandler](#addcommandrangehandler)|Ajoute un groupe de gestionnaires de commandes à un objet source de commande.|
|[ICommandSource :: AddCommandRangeUIHandler](#addcommandrangeuihandler)|Ajoute un groupe de gestionnaires de messages de commande d’interface utilisateur à un objet source de commande.|
|[ICommandSource :: AddCommandUIHandler](#addcommandrangeuihandler)|Ajoute un gestionnaire de messages de commande d’interface utilisateur à un objet source de commande.|
|[ICommandSource ::P ostCommand](#postcommand)|Publie un message sans attendre qu’il soit traité.|
|[ICommandSource :: RemoveCommandHandler](#removecommandhandler)|Supprime un gestionnaire de commandes d’un objet source de commande.|
|[ICommandSource :: RemoveCommandRangeHandler](#removecommandrangehandler)|Supprime un groupe de gestionnaires de commandes d’un objet source de commande.|
|[ICommandSource :: RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Supprime un groupe de gestionnaires de messages de commande d’interface utilisateur d’un objet source de commande.|
|[ICommandSource :: RemoveCommandUIHandler](#removecommandrangeuihandler)|Supprime un gestionnaire de messages de commande de l’interface utilisateur d’un objet source de commande.|
|[ICommandSource :: SendCommand](#sendcommand)|Envoie un message et attend qu’il soit traité avant de retourner.|

### <a name="remarks"></a>Notes

Quand vous hébergez un contrôle utilisateur dans une vue MFC, la [classe CWinFormsView](../../mfc/reference/cwinformsview-class.md) achemine les commandes et met à jour les messages de l’interface utilisateur de commande au contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu Frame et les boutons de barre d’outils). En implémentant l' [interface ICommandTarget](../../mfc/reference/icommandtarget-interface.md), vous donnez à l’utilisateur le contrôle d’une référence à l’objet `ICommandSource`.

Consultez [Comment : ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple d’utilisation de `ICommandTarget`.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>ICommandSource :: AddCommandHandler

Ajoute un gestionnaire de commandes à un objet source de commande.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
*cmdHandler*<br/>
Handle de la méthode du gestionnaire de commandes.

### <a name="remarks"></a>Notes

Cette méthode ajoute le gestionnaire de commandes cmdHandler à l’objet source de la commande et mappe le gestionnaire à cmdID.
Consultez [Comment : ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple d’utilisation de AddCommandHandler.

## <a name="addcommandrangehandler"></a>ICommandSource :: AddCommandRangeHandler

Ajoute un groupe de gestionnaires de commandes à un objet source de commande.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.
*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.
*cmdHandler*<br/>
Handle de la méthode de gestionnaire de messages à laquelle les commandes sont mappées.
### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commandes à un seul gestionnaire de messages et l’ajoute à l’objet source de la commande. Cela permet de gérer un groupe de boutons associés avec une méthode.

## <a name="addcommandrangeuihandler"></a>ICommandSource :: AddCommandRangeUIHandler

Ajoute un groupe de gestionnaires de messages de commande d’interface utilisateur à un objet source de commande.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.
*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.
*cmdHandler*<br/>
Handle de la méthode de gestionnaire de messages à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commandes à un gestionnaire de messages de commande d’interface utilisateur unique et l’ajoute à l’objet source de la commande. Cela permet de gérer un groupe de boutons associés avec une méthode.

## <a name="addcommanduihandler"></a>ICommandSource :: AddCommandUIHandler

Ajoute un gestionnaire de messages de commande d’interface utilisateur à un objet source de commande.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
*cmdUIHandler*<br/>
Handle de la méthode du gestionnaire de messages de commande de l’interface utilisateur.

### <a name="remarks"></a>Notes

Cette méthode ajoute le gestionnaire de messages de commande de l’interface utilisateur cmdHandler à l’objet source de la commande et mappe le gestionnaire à cmdID.

## <a name="postcommand"></a>ICommandSource ::P ostCommand

Publie un message sans attendre qu’il soit traité.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*command*<br/>
ID de commande du message à publier.
### <a name="remarks"></a>Notes

Cette méthode publie de manière asynchrone le message mappé à l’ID spécifié par la commande. Il appelle CWnd ::P ostMessage pour placer le message dans la file d’attente de messages de la fenêtre, puis retourne sans attendre que la fenêtre correspondante traite le message.

## <a name="removecommandhandler"></a>ICommandSource :: RemoveCommandHandler

Supprime un gestionnaire de commandes d’un objet source de commande.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
### <a name="remarks"></a>Notes

Cette méthode supprime le gestionnaire de commandes mappé à cmdID de l’objet source de la commande.

## <a name="removecommandrangehandler"></a>ICommandSource :: RemoveCommandRangeHandler

Supprime un groupe de gestionnaires de commandes d’un objet source de commande.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.
*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.
### <a name="remarks"></a>Notes

Cette méthode supprime un groupe de gestionnaires de messages, mappé aux ID de commande spécifiés par cmdIDMin et cmdIDMax, à partir de l’objet source de la commande.

## <a name="removecommandrangeuihandler"></a>ICommandSource :: RemoveCommandRangeUIHandler

Supprime un groupe de gestionnaires de messages de commande d’interface utilisateur d’un objet source de commande.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.
*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.
### <a name="remarks"></a>Notes

Cette méthode supprime un groupe de gestionnaires de messages de commande d’interface utilisateur, mappés aux ID de commande spécifiés par cmdIDMin et cmdIDMax, à partir de l’objet source de la commande.

## <a name="removecommanduihandler"></a>ICommandSource :: RemoveCommandUIHandler

Supprime un gestionnaire de messages de commande de l’interface utilisateur d’un objet source de commande.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
### <a name="remarks"></a>Notes

Cette méthode supprime le gestionnaire de messages de commande de l’interface utilisateur mappé à cmdID à partir de l’objet source de la commande.

## <a name="sendcommand"></a>ICommandSource :: SendCommand

Envoie un message et attend qu’il soit traité avant de retourner.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*command*<br/>
ID de commande du message à envoyer.
### <a name="remarks"></a>Notes

Cette méthode envoie de façon synchrone le message mappé à l’ID spécifié par la commande. Il appelle CWnd :: SendMessage pour placer le message dans la file d’attente de messages de la fenêtre et attend que cette procédure de fenêtre ait traité le message avant de retourner.
## <a name="see-also"></a>Voir aussi

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget, interface](../../mfc/reference/icommandtarget-interface.md)
