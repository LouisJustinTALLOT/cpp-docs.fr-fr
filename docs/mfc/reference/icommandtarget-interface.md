---
title: ICommandTarget Interface
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: 865a8a27d96f84f536e40ec5a7bbbbdd9837dfcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356914"
---
# <a name="icommandtarget-interface"></a>ICommandTarget Interface

Fournit un contrôle utilisateur avec une interface pour recevoir des commandes à partir d’un objet source de commande.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandTarget
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|Initialise l’objet cible de commande.|

## <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) itinéraires et mettre à jour les messages d’interface utilisateur de commande au contrôle de l’utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu d’encadreurs et les boutons de barre d’outils). En implémentant, `ICommandTarget`vous donnez au contrôle de l’utilisateur une référence à l’objet [ICommandSource.](../../mfc/reference/icommandsource-interface.md)

Voir [comment : Ajouter le routage de commande au contrôle des formulaires Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) par exemple de la façon d’utiliser `ICommandTarget`.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h (défini dans l’assemblage atlmfc-lib-mfcmifc80.dll)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a>ICommandTarget::Initialize

Initialise l’objet cible de commande.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Paramètres

*cmdSource*<br/>
Une poignée à l’objet source de commande.

### <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue MFC, CWinFormsView itinéraires et mettre à jour les messages d’interface utilisateur de commande au contrôle de l’utilisateur pour lui permettre de gérer les commandes MFC.

Cette méthode initialise l’objet cible de commande et l’associe à l’objet source de commande spécifié cmdSource. Il doit être appelé dans la mise en œuvre de la classe de contrôle des utilisateurs. Lors de l’initialisation, vous devez enregistrer les gestionnaires de commande avec l’objet source de commande en appelant ICommandSource::AddCommandHandler dans la mise en œuvre Initialize. Voir comment : Ajouter le routage de commande au contrôle des formulaires Windows pour un exemple de la façon d’utiliser Initialize pour ce faire.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource Interface](../../mfc/reference/icommandsource-interface.md)
