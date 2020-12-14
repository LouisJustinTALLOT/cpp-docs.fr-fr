---
description: 'En savoir plus sur : interface ICommandTarget'
title: Interface ICommandTarget
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: 6deb11ecca94160ea19225fb955826845a4cdefa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219575"
---
# <a name="icommandtarget-interface"></a>Interface ICommandTarget

Fournit un contrôle utilisateur avec une interface pour recevoir des commandes d’un objet source de commande.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandTarget
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ICommandTarget :: Initialize](#initialize)|Initialise l’objet de la cible de la commande.|

## <a name="remarks"></a>Notes

Quand vous hébergez un contrôle utilisateur dans une vue MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) achemine les commandes et met à jour les messages de l’interface utilisateur vers le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu Frame et les boutons de barre d’outils). En implémentant `ICommandTarget` , vous donnez à l’utilisateur le contrôle d’une référence à l’objet [ICommandSource](../../mfc/reference/icommandsource-interface.md) .

Consultez [Comment : ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple d’utilisation de `ICommandTarget` .

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a> ICommandTarget :: Initialize

Initialise l’objet de la cible de la commande.

```cpp
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Paramètres

*cmdSource*<br/>
Handle de l’objet source de la commande.

### <a name="remarks"></a>Notes

Quand vous hébergez un contrôle utilisateur dans une vue MFC, CWinFormsView achemine les commandes et met à jour les messages de l’interface utilisateur vers le contrôle utilisateur pour lui permettre de gérer les commandes MFC.

Cette méthode initialise l’objet de la cible de commande et l’associe à l’objet de source de commande spécifié cmdSource. Elle doit être appelée dans l’implémentation de la classe de contrôle utilisateur. Lors de l’initialisation, vous devez inscrire les gestionnaires de commandes avec l’objet source de la commande en appelant ICommandSource :: AddCommandHandler dans l’implémentation de Initialize. Consultez Comment : ajouter le routage des commandes au contrôle Windows Forms pour obtenir un exemple d’utilisation de Initialize.

## <a name="see-also"></a>Voir aussi

[Comment : ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Interface ICommandSource](../../mfc/reference/icommandsource-interface.md)
