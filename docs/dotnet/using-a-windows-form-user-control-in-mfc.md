---
title: Utilisation d'un contrôle utilisateur Windows Form dans MFC
ms.date: 1/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: 38c5c37712b430b137934d441056e60f2c130f78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384489"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Utilisation d'un contrôle utilisateur Windows Form dans MFC

En utilisant les classes de prise en charge de MFC Windows Forms, vous pouvez héberger des contrôles Windows Forms dans vos applications MFC comme un contrôle ActiveX dans des vues ou des boîtes de dialogue MFC. En outre, les formulaires Windows Forms peuvent être hébergés en tant que boîtes de dialogue MFC.

Les sections suivantes décrivent comment :

- Héberger un contrôle Windows Forms dans une boîte de dialogue MFC.

- Héberger un contrôle utilisateur Windows Forms en tant que vue MFC.

- Héberger un formulaire Windows Forms en tant que boîte de dialogue MFC.

> [!NOTE]
> Intégration de MFC Windows Forms fonctionne uniquement dans les projets qui se lient dynamiquement avec MFC (projets dans lesquels `_AFXDLL` est défini).

> [!NOTE]
> Lorsque vous générez votre application à l’aide d’une copie privée (modifiée) des interfaces MFC Windows Forms DLL (mfcmifc80.dll), il échouera à installer dans le GAC, sauf si vous remplacez la clé Microsoft par votre propre clé de fournisseur. Pour plus d’informations sur la signature d’assembly, consultez [programmation avec des assemblys](/dotnet/framework/app-domains/programming-with-assemblies) et [les assemblys de nom fort (signature d’Assembly) (C++ / c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Si votre application MFC utilise Windows Forms, vous devez redistribuer mfcmifc80.dll avec votre application. Pour plus d’informations, consultez [redistribution de la bibliothèque MFC](../windows/redistributing-the-mfc-library.md).

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

[Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)<br/>
[Mode formulaire](../mfc/form-views-mfc.md)
