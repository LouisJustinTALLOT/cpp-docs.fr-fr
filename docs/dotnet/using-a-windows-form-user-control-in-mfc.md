---
title: À l’aide d’une fenêtre de former le contrôle utilisateur dans MFC | Documents Microsoft
ms.custom: ''
ms.date: 1/08/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8ceb424d6c5061ac5ccafc62d8748be4de3ab3d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33174311"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Utilisation d'un contrôle utilisateur Windows Form dans MFC

À l’aide des classes de prise en charge de MFC Windows Forms, vous pouvez héberger des contrôles Windows Forms dans vos applications MFC comme contrôle ActiveX dans des vues ou des boîtes de dialogue MFC. En outre, les formulaires Windows Forms peuvent être hébergés en tant que les boîtes de dialogue MFC.

Les sections suivantes décrivent comment :

- Héberger un contrôle Windows Forms dans une boîte de dialogue MFC.

- Héberger un contrôle utilisateur Windows Forms en tant que vue MFC.

- Héberger un formulaire Windows Forms en tant que boîte de dialogue MFC.

> [!NOTE]
> Intégration de MFC Windows Forms fonctionne uniquement dans les projets qui lient dynamiquement à MFC (projets dans lesquels `_AFXDLL` est défini).

> [!NOTE]
> Lorsque vous générez votre application à l’aide d’une copie privée (modifiée) des interfaces MFC Windows Forms DLL (mfcmifc80.dll), il échouera à installer dans le GAC, sauf si vous remplacez la clé Microsoft par votre propre clé de fournisseur. Pour plus d’informations sur la signature d’assembly, consultez [programmation avec des assemblys](/dotnet/framework/app-domains/programming-with-assemblies) et [les assemblys de nom fort (signature d’Assembly) (C + c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Pour plus d’exemples d’applications à l’aide de Windows Forms, consultez [BirthdayPicker, exemple : illustre les ressources du .NET Framework avec Windows Forms](http://msdn.microsoft.com/ac932aed-5502-4667-be29-709bca435317), [exemple Calculator : calculatrice de poche Windows Forms](http://msdn.microsoft.com/2283b516-3b7e-45f2-80c4-fdcfb366ce25)et [ Scribble, exemple : Application de dessin MDI](http://msdn.microsoft.com/f025da3e-659b-4222-b991-554a1b8b2358).

Pour un exemple d’application qui affiche des Windows Forms avec les MFC, consultez [intégration de Windows Forms et MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

Si votre application MFC utilise des Windows Forms, vous devez redistribuer mfcmifc80.dll avec votre application. Pour plus d’informations, consultez [redistribution de la bibliothèque MFC](../ide/redistributing-the-mfc-library.md).

## <a name="in-this-section"></a>Dans cette section

[Hébergement d’un contrôle utilisateur Windows Form dans une boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>Référence

[CWinFormsControl, classe](../mfc/reference/cwinformscontrol-class.md)

[CWinFormsDialog, classe](../mfc/reference/cwinformsdialog-class.md)

[CWinFormsView, classe](../mfc/reference/cwinformsview-class.md)

[ICommandSource, interface](../mfc/reference/icommandsource-interface.md)

[ICommandTarget, interface](../mfc/reference/icommandtarget-interface.md)

[ICommandUI, interface](../mfc/reference/icommandui-interface.md)

[IView, interface](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Rubriques connexes

[Windows Forms](/dotnet/framework/winforms/index)

[Contrôles Windows Forms](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Voir aussi

[Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)  
[Mode formulaire](../mfc/form-views-mfc.md)  
