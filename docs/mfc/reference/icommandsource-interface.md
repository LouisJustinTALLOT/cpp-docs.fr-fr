---
title: Interface de ICommandSource | Documents Microsoft
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
ms.openlocfilehash: 5ff57ec9deea4ff8b39e572d720ad7e0fdaa15dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373913"
---
# <a name="icommandsource-interface"></a>Interface de ICommandSource
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
 Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, [classe CWinFormsView](../../mfc/reference/cwinformsview-class.md) commandes d’itinéraires et mise à jour de commande des messages de l’interface utilisateur pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu de frame et boutons de barre d’outils). En implémentant [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md), vous donnez le contrôle utilisateur, une référence à la `ICommandSource` objet.  
  
 Consultez [Comment : ajouter routage des commandes pour le contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `ICommandTarget`.  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)  
  
## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler
Ajoute un gestionnaire de commandes à un objet de source de commande.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres  
`cmdID`  
ID de la commande.  
`cmdHandler`  
Handle vers la méthode de gestionnaire de commandes.

### <a name="remarks"></a>Notes
Cette méthode ajoute la cmdHandler de gestionnaire de commandes à l’objet de source de commande et mappe le gestionnaire à cmdID.
Consultez [Comment : ajouter routage des commandes pour le contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser AddCommandHandler.

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

Ajoute un groupe de gestionnaires de commandes à un objet de source de commande.
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```
### <a name="parameters"></a>Paramètres  
`cmdIDMin`  
L’index de début de la plage d’ID de commande.
`cmdIDMax`  
Index de fin de la plage d’ID de commande.
`cmdHandler`  
Handle vers la méthode de gestionnaire de message à laquelle les commandes sont mappées.
### <a name="remarks"></a>Notes
Cette méthode mappe une plage contiguë de l’ID de commande à un seul gestionnaire de messages et l’ajoute à l’objet de source de commande. Cela est utilisé pour gérer un groupe de boutons associés avec une méthode.

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler
Ajoute un groupe de gestionnaires de messages de commande interface utilisateur à un objet de source de commande.
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin, 
    unsigned int cmdIDMax, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Paramètres  
`cmdIDMin`  
L’index de début de la plage d’ID de commande.
`cmdIDMax`  
Index de fin de la plage d’ID de commande.
`cmdHandler`  
Handle vers la méthode de gestionnaire de message à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes
Cette méthode mappe une plage contiguë de l’ID de commande à un gestionnaire de messages de commande interface utilisateur unique et l’ajoute à l’objet de source de commande. Cela est utilisé pour gérer un groupe de boutons associés avec une méthode.

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler
Ajoute un gestionnaire de messages de commande interface utilisateur à un objet de source de commande.
```
void AddCommandUIHandler(
    unsigned int cmdID, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Paramètres
`cmdID`  
ID de la commande.  
`cmdUIHandler`  
Handle vers la méthode de gestionnaire de message de commande utilisateur interface.

### <a name="remarks"></a>Notes
Cette méthode ajoute la cmdHandler Gestionnaire message de commande d’interface utilisateur à l’objet de source de commande et mappe le gestionnaire à cmdID.

## <a name="postcommand"></a> ICommandSource::PostCommand
Publie un message sans attendre qu’il soit traité.
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>Paramètres
`command`  
L’ID de commande du message à valider.
### <a name="remarks"></a>Notes
Cette méthode valide en mode asynchrone du message mappé à l’ID spécifié par la commande. Il appelle CWnd::PostMessage pour placer le message dans la file d’attente des messages de la fenêtre et retourne sans attendre la fenêtre correspondante traiter le message.


## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler
Supprime un gestionnaire de commandes à partir d’un objet de source de commande.
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Paramètres
`cmdID`  
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
`cmdIDMin`  
L’index de début de la plage d’ID de commande.
`cmdIDMax`  
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
`cmdIDMin`  
L’index de début de la plage d’ID de commande.
`cmdIDMax`  
Index de fin de la plage d’ID de commande.
### <a name="remarks"></a>Notes
Cette méthode supprime un groupe de gestionnaires de messages de commande interface utilisateur, mappé la spécifiée d’ID de commande par cmdIDMin et cmdIDMax, à partir de l’objet de source de commande.

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler 
Supprime un gestionnaire de messages de commande interface utilisateur à partir d’un objet de source de commande.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Paramètres
`cmdID`  
ID de la commande.
### <a name="remarks"></a>Notes
Cette méthode supprime le Gestionnaire de messages de commande d’interface utilisateur mappé à cmdID à partir de l’objet de source de commande.

## <a name="sendcommand"></a> ICommandSource::SendCommand 
Envoie un message et attend qu’il soit traité avant de retourner.
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>Paramètres
`command`  
L’ID de commande du message à envoyer.
### <a name="remarks"></a>Notes
Cette méthode envoie le message mappé à l’ID spécifié par la commande de façon synchrone. Il appelle CWnd::SendMessage pour placer le message dans la file d’attente des messages de la fenêtre et attend jusqu'à ce que cette procédure de fenêtre a traité le message avant de retourner.
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter des commandes routage pour le Windows Forms contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget, interface](../../mfc/reference/icommandtarget-interface.md)
