---
title: Icommandui, Interface
ms.date: 11/04/2016
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
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: 31157ba2445a432af274650011b839fb3df9b3c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322054"
---
# <a name="icommandui-interface"></a>Icommandui, Interface

Gère les commandes de l’interface utilisateur.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandUI
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[icommandui__Check](#check)|Définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée.|
|[ICommandUI::ContinueRouting](#continuerouting)|Indique au mécanisme de routage des commandes pour continuer le message en cours dans la chaîne de gestionnaires de routage.|
|[ICommandUI::Enabled](#enabled)|Active ou désactive l’élément d’interface utilisateur pour cette commande.|
|[ICommandUI::ID](#id)|Obtient l’ID de l’objet d’interface utilisateur représenté par le `ICommandUI` objet.|
|[ICommandUI::Index](#index)|Obtient l’index de l’objet d’interface utilisateur représenté par le `ICommandUI` objet.|
|[ICommandUI::Radio](#radio)|Définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée.|
|[ICommandUI::Text](#text)|Définit le texte de l’élément d’interface utilisateur pour cette commande.|

## <a name="remarks"></a>Notes

Cette interface fournit des méthodes et propriétés qui gèrent des commandes de l’interface utilisateur. `ICommandUI` est similaire à [CCmdUI, classe](../../mfc/reference/ccmdui-class.md), sauf que `ICommandUI` est utilisé pour les applications MFC qui interagissent avec des composants .NET.

`ICommandUI` est utilisé au sein d’un gestionnaire ON_UPDATE_COMMAND_UI dans un [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-classe dérivée. Lorsqu’un utilisateur d’une application active (sélectionne ou clics) un menu, chaque élément de menu est affiché comme activé ou désactivé. La cible de chaque commande de menu fournit ces informations en implémentant un gestionnaire ON_UPDATE_COMMAND_UI. Pour chacun des objets d’interface utilisateur commande dans votre application, utilisez la fenêtre Propriétés pour créer une entrée de table des messages et le prototype de fonction pour chaque gestionnaire.

Pour plus d’informations sur la façon dont le `ICommandUI` interface est utilisée dans le routage des commandes, consultez [Comment : Ajoutez la commande routage pour les Windows Forms contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Pour plus d’informations sur la gestion des commandes de l’interface utilisateur dans MFC, consultez [CCmdUI, classe](../../mfc/reference/ccmdui-class.md).

## <a name="check"></a> ICommandUI::Check

Définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée.
```
property UICheckState Check;
```

## <a name="remarks"></a>Notes

Cette propriété définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée. Vérification de l’ensemble les valeurs suivantes :
- Décochez 0
- 1 vérification
- 2 définir indéterminé

## <a name="continuerouting"></a> ICommandUI::ContinueRouting

Indique au mécanisme de routage de commande pour continuer le message en cours dans la chaîne de gestionnaires de routage.
```
void ContinueRouting();
```

## <a name="remarks"></a>Notes

Il s’agit d’une fonction membre avancé qui doit être utilisée conjointement avec un gestionnaire ON_COMMAND_EX qui retourne la valeur FALSE. Pour plus d’informations, consultez Technical Note TN006 : Tables des messages.

## <a name="enabled"></a> ICommandUI::Enabled

Active ou désactive l’élément d’interface utilisateur pour cette commande.
```
property bool Enabled;
```

## <a name="remarks"></a>Notes

Cette propriété Active ou désactive l’élément d’interface utilisateur pour cette commande. Définissez activé à True pour activer l’élément, FALSE pour le désactiver.

## <a name="id"></a> ICommandUI::ID

Obtient l’ID de l’objet d’interface utilisateur représenté par l’objet ICommandUI.
```
property unsigned int ID;
```

## <a name="remarks"></a>Notes

Cette propriété obtient l’ID (un handle) de l’élément de menu, bouton de barre d’outils ou un autre objet d’interface utilisateur représenté par l’objet ICommandUI.

## <a name="index"></a> ICommandUI::Index

Obtient l’index de l’objet d’interface utilisateur représenté par l’objet ICommandUI.
```
property unsigned int Index;
```

## <a name="remarks"></a>Notes

Cette propriété obtient l’index (un handle) de l’élément de menu, bouton de barre d’outils ou un autre objet d’interface utilisateur représenté par l’objet ICommandUI.

## <a name="radio"></a> ICommandUI::Radio

Définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée.
```
property bool Radio;
```

## <a name="remarks"></a>Notes

Cette propriété définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée. Case d’option de jeu à True pour activer l’élément ; Sinon, FALSE.

## <a name="text"></a> ICommandUI::Text

Définit le texte de l’élément d’interface utilisateur pour cette commande.
```
property String^ Text;
```

## <a name="remarks"></a>Notes

Cette propriété définit le texte de l’élément d’interface utilisateur pour cette commande. La valeur texte est un handle de chaîne de texte.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Voir aussi

[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)
