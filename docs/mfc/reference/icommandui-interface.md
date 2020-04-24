---
title: ICommandUI Interface
ms.date: 09/07/2019
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
ms.openlocfilehash: b75509beb7287fad5e51dc9d15fc3e47cacf6854
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751310"
---
# <a name="icommandui-interface"></a>ICommandUI Interface

Gère les commandes d’interface utilisateur.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandUI
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[icommandui__Check](#check)|Définit l’élément d’interface utilisateur de cette commande à l’état de contrôle approprié.|
|[ICommandUI::ContinuerRouting](#continuerouting)|Indique au mécanisme de routage de commande de continuer à acheminer le message actuel dans la chaîne des gestionnaires.|
|[ICommandUI::Activé](#enabled)|Permet ou désactive l’élément d’interface utilisateur pour cette commande.|
|[ICommandUI::ID](#id)|Obtient l’ID de l’objet `ICommandUI` d’interface utilisateur représenté par l’objet.|
|[ICommandUI::Index](#index)|Obtient l’index de l’objet `ICommandUI` d’interface utilisateur représenté par l’objet.|
|[ICommandUI::Radio](#radio)|Définit l’élément d’interface utilisateur de cette commande à l’état de contrôle approprié.|
|[ICommandUI::Texte](#text)|Définit le texte de l’élément d’interface utilisateur pour cette commande.|

## <a name="remarks"></a>Notes

Cette interface fournit des méthodes et des propriétés qui gèrent les commandes d’interface utilisateur. `ICommandUI`est similaire à [la classe CCmdUI](../../mfc/reference/ccmdui-class.md), sauf que c’est `ICommandUI` utilisé pour les applications MFC qui interopément avec des composants .NET.

`ICommandUI`est utilisé dans un gestionnaire de ON_UPDATE_COMMAND_UI dans une classe [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)dérivé. Lorsqu’un utilisateur d’une application active (sélectionne ou clique) un menu, chaque élément de menu s’affiche comme activé ou désactivé. La cible de chaque commande de menu fournit cette information en mettant en œuvre un gestionnaire de ON_UPDATE_COMMAND_UI. Pour chacun des objets d’interface utilisateur de commande de votre application, utilisez le [Maître de classe](mfc-class-wizard.md) pour créer une entrée et un prototype de fonction de carte de message pour chaque gestionnaire.

Pour plus d’informations sur la façon dont l’interface est utilisée dans le `ICommandUI` routage de commande, voir Comment : Ajouter le [routage de commande au contrôle des formulaires Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Pour plus d’informations sur la façon dont les commandes d’interface utilisateur sont gérées dans MFC, voir [CCmdUI Class](../../mfc/reference/ccmdui-class.md).

## <a name="icommanduicheck"></a><a name="check"></a>ICommandUI::Vérifier

Définit l’élément d’interface utilisateur de cette commande à l’état de contrôle approprié.

```
property UICheckState Check;
```

## <a name="remarks"></a>Notes

Cette propriété définit l’élément d’interface utilisateur de cette commande à l’état de contrôle approprié. Réglez la vérification des valeurs suivantes :

- 0 Uncheck
- 1 Vérifier
- 2 Ensemble pour une durée indéterminée

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a>ICommandUI::ContinuerRouting

Indique au mécanisme de routage de commande de continuer à acheminer le message actuel dans la chaîne des gestionnaires.

```cpp
void ContinueRouting();
```

## <a name="remarks"></a>Notes

Il s’agit d’une fonction de membre avancée qui doit être utilisée en conjonction avec un gestionnaire de ON_COMMAND_EX qui retourne FALSE. Pour plus d’informations, voir Note technique TN006: Cartes de message.

## <a name="icommanduienabled"></a><a name="enabled"></a>ICommandUI::Activé

Permet ou désactive l’élément d’interface utilisateur pour cette commande.

```
property bool Enabled;
```

## <a name="remarks"></a>Notes

Cette propriété permet ou désactive l’élément d’interface utilisateur pour cette commande. Définir Enabled to TRUE pour activer l’élément, FALSE pour le désactiver.

## <a name="icommanduiid"></a><a name="id"></a>ICommandUI::ID

Obtient l’ID de l’objet d’interface utilisateur représenté par l’objet ICommandUI.

```
property unsigned int ID;
```

## <a name="remarks"></a>Notes

Cette propriété obtient l’ID (une poignée) de l’élément de menu, bouton barre d’outils, ou tout autre objet d’interface utilisateur représenté par l’objet ICommandUI.

## <a name="icommanduiindex"></a><a name="index"></a>ICommandUI::Index

Obtient l’index de l’objet d’interface utilisateur représenté par l’objet ICommandUI.

```
property unsigned int Index;
```

## <a name="remarks"></a>Notes

Cette propriété obtient l’index (une poignée) de l’élément de menu, bouton barre d’outils, ou tout autre objet d’interface utilisateur représenté par l’objet ICommandUI.

## <a name="icommanduiradio"></a><a name="radio"></a>ICommandUI::Radio

Définit l’élément d’interface utilisateur de cette commande à l’état de contrôle approprié.

```
property bool Radio;
```

## <a name="remarks"></a>Notes

Cette propriété définit l’élément d’interface utilisateur de cette commande à l’état de contrôle approprié. Définissez la radio à TRUE pour activer l’article; autrement FALSE.

## <a name="icommanduitext"></a><a name="text"></a>ICommandUI::Texte

Définit le texte de l’élément d’interface utilisateur pour cette commande.

```
property String^ Text;
```

## <a name="remarks"></a>Notes

Cette propriété définit le texte de l’élément d’interface utilisateur pour cette commande. Réglez le texte à une poignée de chaîne de texte.

## <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h (défini dans l’assemblage atlmfc-lib-mfcmifc80.dll)

## <a name="see-also"></a>Voir aussi

[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)
