---
title: ICommandSource, Interface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5071f2c6f00b3cc4aaf09974a01c4601d0078e42
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377955"
---
# <a name="icommandsource-interface"></a>ICommandSource, Interface

Gère les commandes envoyées à partir d’un objet de source de commande à un contrôle utilisateur.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandSource
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Ajoute un gestionnaire de commandes à un objet de source de commande.|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Ajoute un groupe de gestionnaires de commandes à un objet de source de commande.|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Ajoute un groupe de gestionnaires de messages de commande interface utilisateur à un objet de source de commande.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Ajoute un gestionnaire de messages de commande interface utilisateur à un objet de source de commande.|
|[ICommandSource::PostCommand](#postcommand)|Publie un message sans attendre qu’il soit traité.|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Supprime un gestionnaire de commandes à partir d’un objet de source de commande.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Supprime un groupe de gestionnaires de commandes à partir d’un objet de source de commande.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Supprime un groupe de gestionnaires de messages de commande interface utilisateur à partir d’un objet de source de commande.|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Supprime un gestionnaire de messages de commande interface utilisateur à partir d’un objet de source de commande.|
|[ICommandSource::SendCommand](#sendcommand)|Envoie un message et attend qu’il soit traité avant de retourner.|

### <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, [CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md) commandes d’itinéraires et mise à jour de commande des messages de l’interface utilisateur pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu de frame et boutons de barre d’outils). En implémentant [ICommandTarget, Interface](../../mfc/reference/icommandtarget-interface.md), vous donner le contrôle utilisateur, une référence à la `ICommandSource` objet.

Consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `ICommandTarget`.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Ajoute un gestionnaire de commandes à un objet de source de commande.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
*cmdHandler*<br/>
Handle vers la méthode de gestionnaire de commande.

### <a name="remarks"></a>Notes

Cette méthode ajoute la cmdHandler de gestionnaire de commande à l’objet de source de commande et mappe le gestionnaire à cmdID.
Consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser AddCommandHandler.

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

Ajoute un groupe de gestionnaires de commandes à un objet de source de commande.
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
Handle vers la méthode de gestionnaire de message à laquelle les commandes sont mappées.
### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commande à un seul gestionnaire de messages et l’ajoute à l’objet de source de commande. Cela est utilisé pour gérer un groupe de boutons associés avec une méthode.

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler

Ajoute un groupe de gestionnaires de messages de commande interface utilisateur à un objet de source de commande.
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
Handle vers la méthode de gestionnaire de message à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commande à un gestionnaire de messages de commande interface utilisateur unique et l’ajoute à l’objet de source de commande. Cela est utilisé pour gérer un groupe de boutons associés avec une méthode.

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler

Ajoute un gestionnaire de messages de commande interface utilisateur à un objet de source de commande.
```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
*cmdUIHandler*<br/>
Handle vers la méthode de gestionnaire de message de commande utilisateur interface.

### <a name="remarks"></a>Notes

Cette méthode ajoute la cmdHandler Gestionnaire message de commande d’interface utilisateur à l’objet de source de commande et mappe le gestionnaire à cmdID.

## <a name="postcommand"></a> ICommandSource::PostCommand

Publie un message sans attendre qu’il soit traité.
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>Paramètres

*command*<br/>
L’ID de commande du message à publier.
### <a name="remarks"></a>Notes

Cette méthode publie façon asynchrone le message mappé à l’ID spécifié par la commande. Il appelle CWnd::PostMessage pour placer le message dans la file d’attente de messages de la fenêtre et puis retourne sans attendre que la fenêtre correspondante traiter le message.


## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler

Supprime un gestionnaire de commandes à partir d’un objet de source de commande.
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
### <a name="remarks"></a>Notes

Cette méthode supprime le Gestionnaire de commandes mappé à cmdID à partir de l’objet de source de commande.


## <a name="removecommandrangecommandhandler"></a> ICommandSource::RemoveCommandRangeHandler

Supprime un groupe de gestionnaires de commandes à partir d’un objet de source de commande.
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

Cette méthode supprime un groupe de gestionnaires de messages, mappé la spécifiée d’ID de commande par cmdIDMin et cmdIDMax, à partir de l’objet de source de commande.

## <a name="removecommandrangeuihandler"></a> ICommandSource::RemoveCommandRangeUIHandler

Supprime un groupe de gestionnaires de messages de commande interface utilisateur à partir d’un objet de source de commande.
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

Cette méthode supprime un groupe de gestionnaires de messages de commande interface utilisateur, mappé la spécifiée d’ID de commande par cmdIDMin et cmdIDMax, à partir de l’objet de source de commande.

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler

Supprime un gestionnaire de messages de commande interface utilisateur à partir d’un objet de source de commande.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
### <a name="remarks"></a>Notes

Cette méthode supprime le Gestionnaire de messages de commande d’interface utilisateur mappé à cmdID à partir de l’objet de source de commande.

## <a name="sendcommand"></a> ICommandSource::SendCommand

Envoie un message et attend qu’il soit traité avant de retourner.
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>Paramètres

*command*<br/>
L’ID de commande du message à envoyer.
### <a name="remarks"></a>Notes

Cette méthode envoie de façon synchrone le message mappé à l’ID spécifié par la commande. Il appelle CWnd::SendMessage pour placer le message dans la file d’attente de messages de la fenêtre et attend jusqu'à ce que cette procédure de fenêtre ait traité le message avant de retourner.
## <a name="see-also"></a>Voir aussi

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget, interface](../../mfc/reference/icommandtarget-interface.md)
