---
title: Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 8925b86a5920df6a53a2625b782cf41e1a7fe32c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964965"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC

MFC héberge un contrôle de Windows Forms comme un type spécial de contrôle ActiveX et communique avec le contrôle à l’aide d’interfaces ActiveX, ainsi que des propriétés et des méthodes de la classe <xref:System.Windows.Forms.Control>. Nous vous recommandons d’utiliser des propriétés et des méthodes .NET Framework pour fonctionner sur le contrôle.

Pour obtenir un exemple d’application qui montre Windows Forms utilisé avec MFC, consultez [MFC and Windows Forms Integration](https://www.microsoft.com/download/details.aspx?id=2113).

> [!NOTE]
>  Dans la version actuelle, un objet `CDialogBar` ne peut pas héberger des contrôles Windows Forms.

## <a name="in-this-section"></a>Dans cette section

[Guide pratique pour créer le contrôle utilisateur et l’héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Comment : effectuer une liaison de données DDX/DDV avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Guide pratique pour recevoir des événements Windows Forms de classes C++ natives](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Reference

&#124; Classe [CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) [CDialog](../mfc/reference/cdialog-class.md) &#124; Class [CWnd](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Voir aussi

[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Différences de programmation entre Windows Forms et MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
