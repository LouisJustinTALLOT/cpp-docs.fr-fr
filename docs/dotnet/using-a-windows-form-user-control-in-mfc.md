---
description: 'En savoir plus sur : utilisation d’un contrôle utilisateur Windows Form dans MFC'
title: Utilisation d'un contrôle utilisateur Windows Form dans MFC
ms.date: 01/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: 61022d241faba1650d1a044ef6d3667febe34cde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319025"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Utilisation d'un contrôle utilisateur Windows Form dans MFC

À l’aide des classes de prise en charge MFC Windows Forms, vous pouvez héberger des contrôles Windows Forms dans vos applications MFC en tant que contrôle ActiveX dans des boîtes de dialogue ou des vues MFC. En outre, les formulaires Windows Forms peuvent être hébergés en tant que boîtes de dialogue MFC.

Les sections suivantes décrivent comment :

- Héberger un contrôle de Windows Forms dans une boîte de dialogue MFC.

- Hébergez un contrôle utilisateur Windows Forms en tant que vue MFC.

- Hébergez un formulaire de Windows Forms en tant que boîte de dialogue MFC.

> [!NOTE]
> L’intégration des Windows Forms MFC fonctionne uniquement dans les projets qui sont liés de manière dynamique aux MFC (projets dans lesquels `_AFXDLL` est défini).

> [!NOTE]
> Quand vous générez votre application à l’aide d’une copie privée (modifiée) de la DLL des interfaces MFC Windows Forms (mfcmifc80.dll), elle ne peut pas être installée dans le GAC, sauf si vous remplacez la clé Microsoft par votre propre clé de fournisseur. Pour plus d’informations sur la signature d’assembly, consultez [programmation à l’aide d’assemblys](/dotnet/framework/app-domains/programming-with-assemblies) et d' [assemblys de nom fort (signature d’assembly) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Si votre application MFC utilise Windows Forms, vous devez redistribuer mfcmifc80.dll avec votre application. Pour plus d’informations, consultez [redistribution de la bibliothèque MFC](../windows/redistributing-the-mfc-library.md).

## <a name="in-this-section"></a>Dans cette section

[Hébergement d’un contrôle utilisateur Windows Form dans une boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>Informations de référence

[CWinFormsControl, classe](../mfc/reference/cwinformscontrol-class.md)

[CWinFormsDialog, classe](../mfc/reference/cwinformsdialog-class.md)

[CWinFormsView (classe)](../mfc/reference/cwinformsview-class.md)

[Interface ICommandSource](../mfc/reference/icommandsource-interface.md)

[Interface ICommandTarget](../mfc/reference/icommandtarget-interface.md)

[Interface ICommandUI](../mfc/reference/icommandui-interface.md)

[Interface IView](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Sections connexes

[Windows Forms](/dotnet/framework/winforms/index)

[Contrôles Windows Forms](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](../mfc/user-interface-elements-mfc.md)<br/>
[Mode Formulaire](../mfc/form-views-mfc.md)
