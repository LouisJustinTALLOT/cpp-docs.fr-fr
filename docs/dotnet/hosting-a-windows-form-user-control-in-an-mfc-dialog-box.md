---
description: 'En savoir plus sur : Hébergement d’un contrôle utilisateur Windows Form dans une boîte de dialogue MFC'
title: Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 3ccfbb32132f5732c244473c652bb6b2df175efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335444"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hébergement d'un contrôle utilisateur Windows Form dans une boîte de dialogue MFC

MFC héberge un contrôle de Windows Forms comme un type spécial de contrôle ActiveX et communique avec le contrôle à l’aide d’interfaces ActiveX, ainsi que des propriétés et des méthodes de la <xref:System.Windows.Forms.Control> classe. Nous vous recommandons d’utiliser des propriétés et des méthodes .NET Framework pour fonctionner sur le contrôle.

Pour obtenir un exemple d’application qui montre Windows Forms utilisé avec MFC, consultez [MFC and Windows Forms Integration](https://www.microsoft.com/download/details.aspx?id=2113).

> [!NOTE]
> Dans la version actuelle, un `CDialogBar` objet ne peut pas héberger des contrôles Windows Forms.

## <a name="in-this-section"></a>Dans cette section

[Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Comment : effectuer une liaison de données DDX/DDV avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Comment : recevoir des événements Windows Forms à partir de classes C++ natives](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Informations de référence

Classe [CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; classe [CDialog](../mfc/reference/cdialog-class.md) &#124; [classe CWnd](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Voir aussi

[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Différences de programmation de Windows Forms/MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
