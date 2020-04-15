---
title: ICommandSource Interface
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
ms.openlocfilehash: 6a03c46c972f7746f39a3c5c65ca9b5509983d59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356977"
---
# <a name="icommandsource-interface"></a>ICommandSource Interface

Gère les commandes envoyées à partir d’un objet source de commande à un contrôle de l’utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
interface class ICommandSource
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Ajoute un gestionnaire de commande à un objet source de commande.|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Ajoute un groupe de gestionnaires de commande à un objet source de commande.|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Ajoute un groupe de gestionnaires de messages de commande d’interface utilisateur à un objet source de commande.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Ajoute un gestionnaire de message de commande d’interface utilisateur à un objet source de commande.|
|[ICommandSource::PostCommand](#postcommand)|Affiche un message sans attendre qu’il soit traité.|
|[ICommandSource::SupprimerCommandHandler](#removecommandhandler)|Retire un gestionnaire de commande d’un objet source de commande.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Retire un groupe de gestionnaires de commande d’un objet source de commande.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Supprime un groupe de gestionnaires de messages de commande d’interface utilisateur à partir d’un objet source de commande.|
|[ICommandSource::SupprimerCommandUIHandler](#removecommandrangeuihandler)|Supprime un gestionnaire de message de commande d’interface utilisateur d’un objet source de commande.|
|[ICommandSource::SendCommand](#sendcommand)|Envoie un message et attend qu’il soit traité avant de revenir.|

### <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue MFC, les commandes [de la classe CWinFormsView](../../mfc/reference/cwinformsview-class.md) et mettez à jour les messages d’interface utilisateur de commande au contrôle de l’utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu d’encadrement et les boutons de barre d’outils). En implémentant [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md), vous `ICommandSource` donnez au contrôle de l’utilisateur une référence à l’objet.

Voir [comment : Ajouter le routage de commande au contrôle des formulaires Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) par exemple de la façon d’utiliser `ICommandTarget`.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h (défini dans l’assemblage atlmfc-lib-mfcmifc80.dll)

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a>ICommandSource::AddCommandHandler

Ajoute un gestionnaire de commande à un objet source de commande.

```cpp
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
*cmdHandler*<br/>
Une poignée à la méthode du gestionnaire de commande.

### <a name="remarks"></a>Notes

Cette méthode ajoute le gestionnaire de commande cmdHandler à l’objet source de commande et cartographie le gestionnaire à cmdID.
Voir [comment : Ajouter le routage de commande au contrôle des formulaires Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) par exemple de la façon d’utiliser AddCommandHandler.

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

Ajoute un groupe de gestionnaires de commande à un objet source de commande.

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
L’index de départ de la plage d’identification de commande.
*cmdIDMax (en)*<br/>
L’index de fin de la plage d’identification de commande.
*cmdHandler*<br/>
Une poignée à la méthode de gestionnaire de message à laquelle les commandes sont cartographiées.

### <a name="remarks"></a>Notes

Cette méthode cartographie une gamme contigue d’IDs de commande à un seul gestionnaire de message et l’ajoute à l’objet source de commande. Ceci est utilisé pour la manipulation d’un groupe de boutons connexes avec une méthode.

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler

Ajoute un groupe de gestionnaires de messages de commande d’interface utilisateur à un objet source de commande.

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
L’index de départ de la plage d’identification de commande.
*cmdIDMax (en)*<br/>
L’index de fin de la plage d’identification de commande.
*cmdHandler*<br/>
Une poignée à la méthode de gestionnaire de message à laquelle les commandes sont cartographiées.

### <a name="remarks"></a>Notes

Cette méthode cartographie une gamme contigue d’identifiants de commande à un seul gestionnaire de message de commande d’interface utilisateur et l’ajoute à l’objet source de commande. Ceci est utilisé pour la manipulation d’un groupe de boutons connexes avec une méthode.

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler

Ajoute un gestionnaire de message de commande d’interface utilisateur à un objet source de commande.

```cpp
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.
*cmdUIHandler*<br/>
Une poignée à la méthode de gestionnaire de message de commande d’interface utilisateur.

### <a name="remarks"></a>Notes

Cette méthode ajoute le gestionnaire de message de commande d’interface utilisateur cmdHandler à l’objet source de commande et cartographie le gestionnaire à cmdID.

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a>ICommandSource::PostCommand

Affiche un message sans attendre qu’il soit traité.

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*Commande*<br/>
L’id de commande du message à poster.

### <a name="remarks"></a>Notes

Cette méthode affiche asynchronement le message cartographié à l’ID spécifié par commande. Il appelle CWnd::PostMessage pour placer le message dans la file d’attente du message de la fenêtre, puis revient sans attendre la fenêtre correspondante pour traiter le message.

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a>ICommandSource::SupprimerCommandHandler

Retire un gestionnaire de commande d’un objet source de commande.

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Cette méthode élimine le gestionnaire de commande cartographié à cmdID de l’objet source de commande.

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a>ICommandSource::RemoveCommandRangeHandler

Retire un groupe de gestionnaires de commande d’un objet source de commande.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
L’index de départ de la plage d’identification de commande.
*cmdIDMax (en)*<br/>
L’index de fin de la plage d’identification de commande.

### <a name="remarks"></a>Notes

Cette méthode supprime un groupe de gestionnaires de messages, cartographiés sur les IDE de commande spécifiées par cmdIDMin et cmdIDMax, à partir de l’objet source de commande.

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler

Supprime un groupe de gestionnaires de messages de commande d’interface utilisateur à partir d’un objet source de commande.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
L’index de départ de la plage d’identification de commande.
*cmdIDMax (en)*<br/>
L’index de fin de la plage d’identification de commande.

### <a name="remarks"></a>Notes

Cette méthode supprime un groupe de gestionnaires de messages de commande d’interface utilisateur, cartographiés sur les identifiants de commande spécifiés par cmdIDMin et cmdIDMax, à partir de l’objet source de commande.

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a>ICommandSource::SupprimerCommandUIHandler

Supprime un gestionnaire de message de commande d’interface utilisateur d’un objet source de commande.

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Cette méthode supprime le gestionnaire de message de commande d’interface utilisateur cartographié à cmdID à partir de l’objet source de commande.

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a>ICommandSource::SendCommand

Envoie un message et attend qu’il soit traité avant de revenir.

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*Commande*<br/>
L’id de commande du message à envoyer.

### <a name="remarks"></a>Notes

Cette méthode envoie synchroniséement le message cartographié à l’ID spécifié par commande. Il appelle CWnd::SendMessage pour placer le message dans la file d’attente du message de la fenêtre et attend que cette procédure de fenêtre a traité le message avant de revenir.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md)
