---
title: ICommandTarget, Interface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee8a4bb3f80d9776aec4fd7a6af0d1523c60064d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066082"
---
# <a name="icommandtarget-interface"></a>ICommandTarget, Interface

Fournit un contrôle utilisateur avec une interface pour recevoir des commandes à partir d’un objet de source de commande.

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

Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) commandes d’itinéraires et mise à jour de commande des messages de l’interface utilisateur pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu de frame et boutons de barre d’outils). En implémentant `ICommandTarget`, vous donner le contrôle utilisateur, une référence à la [ICommandSource](../../mfc/reference/icommandsource-interface.md) objet.

Consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `ICommandTarget`.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

##  <a name="initialize"></a> ICommandTarget::Initialize

Initialise l’objet cible de commande.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Paramètres

*cmdSource*<br/>
Handle vers l’objet de source de commande.

### <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, CWinFormsView achemine les commandes et les messages de l’interface utilisateur de commande de mise à jour vers le contrôle utilisateur pour lui permettre de gérer les commandes MFC.

Cette méthode initialise l’objet cible de commande et l’associe à la cmdSource d’objet de source de commande spécifiée. Il doit être appelée dans l’implémentation de classe de contrôle utilisateur. Lors de l’initialisation, vous devez inscrire des gestionnaires de commandes avec l’objet de source de commande en appelant ICommandSource::AddCommandHandler dans l’implémentation de l’initialisation. Consultez Comment : ajouter le routage des commandes au contrôle Windows Forms pour obtenir un exemple d’utilisation d’initialisation pour ce faire.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource, interface](../../mfc/reference/icommandsource-interface.md)

