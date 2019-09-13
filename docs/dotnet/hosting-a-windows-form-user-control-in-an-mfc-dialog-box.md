---
title: Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 22f2c5c6c162e459470f9babab66c61c096540ec
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "70311869"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC

MFC héberge un contrôle de Windows Forms comme un type spécial de contrôle ActiveX et communique avec le contrôle à l’aide d’interfaces ActiveX, ainsi que des <xref:System.Windows.Forms.Control> propriétés et des méthodes de la classe. Nous vous recommandons d’utiliser des propriétés et des méthodes .NET Framework pour fonctionner sur le contrôle.

Pour obtenir un exemple d’application qui montre Windows Forms utilisé avec MFC, consultez [MFC and Windows Forms Integration](https://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

> [!NOTE]
>  Dans la version actuelle, un `CDialogBar` objet ne peut pas héberger des contrôles Windows Forms.

## <a name="in-this-section"></a>Dans cette section

[Guide pratique : créer le contrôle utilisateur et l’héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Guide pratique pour Liaison de données DDX/DDV avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Guide pratique pour recevoir des événements Windows Forms de classes C++ natives](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Référence

[CWinFormsControl, classe](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog, classe](../mfc/reference/cdialog-class.md) &#124; [CWnd, classe](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Voir aussi

[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Différences de programmation entre Windows Forms et MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
