---
title: Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 2704e04df3792edfee6c39f597fcbe71b6ce51b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374488"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC

MFC héberge un contrôle Windows Forms comme un type spécial de contrôle ActiveX et communique avec <xref:System.Windows.Forms.Control> le contrôle en utilisant des interfaces ActiveX, et les propriétés et les méthodes de la classe. Nous vous recommandons d’utiliser des propriétés et des méthodes de cadre .NET pour opérer le contrôle.

Pour une application d’échantillon qui affiche les formulaires Windows utilisés avec MFC, voir [MFC et Windows Forms Integration](https://www.microsoft.com/download/details.aspx?id=2113).

> [!NOTE]
> Dans la version `CDialogBar` actuelle, un objet ne peut pas héberger les commandes de formulaires Windows.

## <a name="in-this-section"></a>Dans cette section

[Comment : créer le contrôle utilisateur et l'héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Comment : établir la liaison des données DDX/DDV avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Comment : recevoir des événements Windows Forms de classes C++ natives](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Informations de référence

[Classe CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; [classe CDialog](../mfc/reference/cdialog-class.md) &#124; [classe CWnd](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Voir aussi

[Utilisation d'un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Formulaires Windows/Différences de programmation MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hébergement d’un contrôle de l’utilisateur formulaire Windows comme une boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
