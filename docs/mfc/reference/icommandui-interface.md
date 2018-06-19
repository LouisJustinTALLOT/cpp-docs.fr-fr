---
title: Interface de ICommandUI | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
dev_langs:
- C++
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70e6f1eb8848c5ee93063877ae036f66584b69c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371808"
---
# <a name="icommandui-interface"></a>Interface de ICommandUI
Gère les commandes de l’interface utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class ICommandUI  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[icommandui__Check](#check)|Définit l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée.|  
|[ICommandUI::ContinueRouting](#continuerouting)|Indique au mécanisme de routage des commandes pour continuer le routage du message en cours dans la chaîne de gestionnaires.|  
|[ICommandUI::Enabled](#enabled)|Active ou désactive l’élément d’interface utilisateur pour cette commande.|  
|[ICommandUI::ID](#id)|Obtient l’ID de l’objet d’interface utilisateur représenté par le `ICommandUI` objet.|  
|[ICommandUI::Index](#index)|Obtient l’index de l’objet d’interface utilisateur représenté par le `ICommandUI` objet.|  
|[ICommandUI::Radio](#radio)|Définit l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée.|  
|[ICommandUI::Text](#text)|Définit le texte de l’élément d’interface utilisateur pour cette commande.|  
  
## <a name="remarks"></a>Notes  
 Cette interface fournit les méthodes et propriétés qui gèrent les commandes de l’interface utilisateur. `ICommandUI` est semblable à [CCmdUI (classe)](../../mfc/reference/ccmdui-class.md), sauf que `ICommandUI` est utilisé pour les applications MFC qui interagissent avec des composants .NET.  
  
 `ICommandUI` est utilisé dans une `ON_UPDATE_COMMAND_UI` gestionnaire dans un [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-classe dérivée. Lorsqu’un utilisateur d’une application active (sélectionne ou clics) un menu, chaque élément de menu s’affiche comme activé ou désactivé. La cible de chaque commande de menu fournit ces informations en implémentant un `ON_UPDATE_COMMAND_UI` gestionnaire. Pour chacun des objets d’interface utilisateur commande dans votre application, utilisez la fenêtre Propriétés pour créer une entrée de table des messages et le prototype de fonction pour chaque gestionnaire.  
  
 Pour plus d’informations sur la façon dont le `ICommandUI` interface est utilisée dans le routage des commandes, consultez [Comment : ajouter routage des commandes pour le contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Pour plus d’informations sur la gestion des commandes de l’interface utilisateur dans MFC, consultez [CCmdUI (classe)](../../mfc/reference/ccmdui-class.md).  
  
## <a name="check"></a> ICommandUI::Check  
Définit l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée.
```
property UICheckState Check;
```
## <a name="remarks"></a>Notes  
Cette propriété définit l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée. Vérification de l’ensemble les valeurs suivantes :  
- Désactivez 0  
- 1 vérification  
- 2 défini indéterminé  

## <a name="continuerouting"></a> ICommandUI::ContinueRouting   
Indique au mécanisme de routage de commande pour continuer le routage du message en cours dans la chaîne de gestionnaires.
```
void ContinueRouting();
```
## <a name="remarks"></a>Notes
Il s’agit d’une fonction membre avancée qui doit être utilisée conjointement avec un gestionnaire ON_COMMAND_EX qui renvoie la valeur FALSE. Pour plus d’informations, consultez Technical Note TN006 : tables des messages.

## <a name="enabled"></a> ICommandUI::Enabled 
Active ou désactive l’élément d’interface utilisateur pour cette commande.
```
property bool Enabled;
```
## <a name="remarks"></a>Notes
Cette propriété Active ou désactive l’élément d’interface utilisateur pour cette commande. Définir Enabled à True pour activer l’élément de la valeur FALSE pour la désactiver.

## <a name="id"></a> ICommandUI::ID  
Obtient l’ID de l’objet d’interface utilisateur représenté par l’objet ICommandUI.
```
property unsigned int ID;
```
## <a name="remarks"></a>Notes
Cette propriété obtient l’ID de l’élément de menu, le bouton de barre d’outils ou un autre objet d’interface utilisateur représenté par l’objet ICommandUI (un handle).

## <a name="index"></a> ICommandUI::Index   
Obtient l’index de l’objet d’interface utilisateur représenté par l’objet ICommandUI.
```
property unsigned int Index;
```
## <a name="remarks"></a>Notes
Cette propriété obtient l’index de l’élément de menu, le bouton de barre d’outils ou un autre objet d’interface utilisateur représenté par l’objet ICommandUI (un handle).

## <a name="radio"></a> ICommandUI::Radio 
Définit l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée.
```
property bool Radio;
```
## <a name="remarks"></a>Notes
Cette propriété définit l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée. Définir des cases d’option à True pour activer l’élément ; Sinon, FALSE.

## <a name="text"></a> ICommandUI::Text 
Définit le texte de l’élément d’interface utilisateur pour cette commande.
```
property String^ Text;
```
## <a name="remarks"></a>Notes
Cette propriété définit le texte de l’élément d’interface utilisateur pour cette commande. Définir le texte à un descripteur de chaîne de texte.

## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdUI, classe](../../mfc/reference/ccmdui-class.md)
