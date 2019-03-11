---
title: Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 56cf00da71fe6c47e39de2a8fc06df572a301a61
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748565"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC

MFC héberge un contrôle Windows Forms sous la forme d’un type spécial de contrôle ActiveX et communique avec le contrôle à l’aide des interfaces ActiveX et les propriétés et méthodes de la <xref:System.Windows.Forms.Control> classe. Nous vous recommandons d’utiliser les propriétés de .NET Framework et les méthodes pour agir sur le contrôle.

Pour un exemple d’application qui illustre Windows Forms avec MFC, consultez [MFC et l’intégration de formulaires Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

> [!NOTE]
>  Dans la version actuelle, un `CDialogBar` objet ne peut pas héberger de contrôles Windows Forms.

## <a name="in-this-section"></a>Dans cette section

[Guide pratique pour créer le contrôle utilisateur et l’héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Guide pratique pour Faire de DDX/DDV liaison de données avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Guide pratique pour recevoir des événements Windows Forms de classes C++ natives](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Référence

[CWinFormsControl, classe](../mfc/reference/cwinformscontrol-class.md) &#124; [classe CDialog](../mfc/reference/cdialog-class.md) &#124; [classe CWnd](../mfc/reference/cwnd-class.md)&#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Voir aussi

[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Différences de programmation entre Windows Forms et MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
