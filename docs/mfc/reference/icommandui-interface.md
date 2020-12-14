---
description: 'En savoir plus sur : interface ICommandUI'
title: Interface ICommandUI
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
ms.openlocfilehash: 26ddd4366994c9e0cecba2b4902a36e1038896c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219536"
---
# <a name="icommandui-interface"></a>Interface ICommandUI

Gère les commandes de l’interface utilisateur.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandUI
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[icommandui__Check](#check)|Affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande.|
|[ICommandUI::ContinueRouting](#continuerouting)|Indique au mécanisme de routage de commande de continuer à acheminer le message actuel vers le dessous de la chaîne de gestionnaires.|
|[ICommandUI :: Enabled](#enabled)|Active ou désactive l’élément d’interface utilisateur pour cette commande.|
|[ICommandUI :: ID](#id)|Obtient l’ID de l’objet d’interface utilisateur représenté par l' `ICommandUI` objet.|
|[ICommandUI :: index](#index)|Obtient l’index de l’objet d’interface utilisateur représenté par l' `ICommandUI` objet.|
|[ICommandUI :: radio](#radio)|Affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande.|
|[ICommandUI :: Text](#text)|Définit le texte de l’élément d’interface utilisateur pour cette commande.|

### <a name="remarks"></a>Notes

Cette interface fournit des méthodes et des propriétés qui gèrent les commandes de l’interface utilisateur. `ICommandUI` est similaire à la [classe CCmdUI](../../mfc/reference/ccmdui-class.md), sauf que `ICommandUI` est utilisé pour les applications MFC qui interagissent avec les composants .net.

`ICommandUI` est utilisé dans un gestionnaire de ON_UPDATE_COMMAND_UI dans une classe dérivée de [ICommandTarget](../../mfc/reference/icommandtarget-interface.md). Lorsqu’un utilisateur d’une application active (sélectionne ou clique) un menu, chaque élément de menu est affiché comme activé ou désactivé. La cible de chaque commande de menu fournit ces informations en implémentant un gestionnaire de ON_UPDATE_COMMAND_UI. Pour chacun des objets de l’interface utilisateur de commande de votre application, utilisez l' [Assistant classe](mfc-class-wizard.md) pour créer une entrée de table des messages et un prototype de fonction pour chaque gestionnaire.

Pour plus d’informations sur l' `ICommandUI` utilisation de l’interface dans le routage des commandes, consultez [Comment : ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Pour plus d’informations sur la façon dont les commandes de l’interface utilisateur sont gérées dans MFC, consultez la [classe CCmdUI](../../mfc/reference/ccmdui-class.md).

## <a name="icommanduicheck"></a><a name="check"></a> ICommandUI :: Check

Affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande.

```
property UICheckState Check;
```

### <a name="remarks"></a>Notes

Cette propriété affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande. Définissez le contrôle sur les valeurs suivantes :

- 0 décocher
- 1 vérification
- 2 définir comme indéterminé

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a> ICommandUI::ContinueRouting

Indique au mécanisme de routage des commandes de continuer à acheminer le message actuel vers le dessous de la chaîne de gestionnaires.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>Notes

Il s’agit d’une fonction membre avancée qui doit être utilisée conjointement avec un gestionnaire de ON_COMMAND_EX qui retourne FALSe. Pour plus d’informations, consultez Technical note TN006 : messages Maps.

## <a name="icommanduienabled"></a><a name="enabled"></a> ICommandUI :: Enabled

Active ou désactive l’élément d’interface utilisateur pour cette commande.

```
property bool Enabled;
```

### <a name="remarks"></a>Notes

Cette propriété active ou désactive l’élément d’interface utilisateur pour cette commande. Affectez la valeur TRUE à Enabled pour activer l’élément, FALSe pour le désactiver.

## <a name="icommanduiid"></a><a name="id"></a> ICommandUI :: ID

Obtient l’ID de l’objet d’interface utilisateur représenté par l’objet ICommandUI.

```
property unsigned int ID;
```

### <a name="remarks"></a>Notes

Cette propriété obtient l’ID (un handle) de l’élément de menu, du bouton de barre d’outils ou d’un autre objet d’interface utilisateur représenté par l’objet ICommandUI.

## <a name="icommanduiindex"></a><a name="index"></a> ICommandUI :: index

Obtient l’index de l’objet d’interface utilisateur représenté par l’objet ICommandUI.

```
property unsigned int Index;
```

### <a name="remarks"></a>Notes

Cette propriété obtient l’index (un handle) de l’élément de menu, du bouton de barre d’outils ou d’un autre objet d’interface utilisateur représenté par l’objet ICommandUI.

## <a name="icommanduiradio"></a><a name="radio"></a> ICommandUI :: radio

Affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande.

```
property bool Radio;
```

### <a name="remarks"></a>Notes

Cette propriété affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande. Affectez la valeur TRUE à radio pour activer l’élément. Sinon, FALSe.

## <a name="icommanduitext"></a><a name="text"></a> ICommandUI :: Text

Définit le texte de l’élément d’interface utilisateur pour cette commande.

```
property String^ Text;
```

### <a name="remarks"></a>Notes

Cette propriété définit le texte de l’élément d’interface utilisateur pour cette commande. Définissez le texte sur un handle de chaîne de texte.

## <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Voir aussi

[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)
