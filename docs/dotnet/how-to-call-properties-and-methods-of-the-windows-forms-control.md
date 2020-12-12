---
description: 'En savoir plus sur : Comment : appeler des propriétés et des méthodes du contrôle Windows Forms'
title: 'Comment : appeler des propriétés et des méthodes du contrôle Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
ms.openlocfilehash: a797084a28eefec27699814a09c8521da7460bc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268403"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Comment : appeler des propriétés et des méthodes du contrôle Windows Forms

Étant donné que [CWinFormsView :: GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) retourne un pointeur vers <xref:System.Windows.Forms.Control?displayProperty=fullName> , et non un pointeur vers `WindowsControlLibrary1::UserControl1` , il est recommandé d’ajouter un membre du type de contrôle utilisateur et de l’initialiser dans [iView :: OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate). Vous pouvez maintenant appeler des méthodes et des propriétés à l’aide de `m_ViewControl` .

Cette rubrique part du principe que vous avez déjà terminé [Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) et [Comment : créer le contrôle utilisateur et héberger l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application hôte MFC

1. Ouvrez l’application MFC que vous avez créée dans [How to : Create the User Control and Host MDI View](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Ajoutez la ligne suivante à la section des substitutions publiques de la `CMFC02View` déclaration de classe dans MFC02View. h.

   `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. Ajoutez un remplacement pour OnInitialupdate.

   Affichez la fenêtre **Propriétés** (F4). Dans **affichage de classes** (Ctrl + Maj + C), sélectionnez classe CMFC02View. Dans la fenêtre **Propriétés** , sélectionnez l’icône pour les remplacements. Scoll la liste jusqu’à OnInitialUpdate. Cliquez sur la liste déroulante et sélectionnez \<Add> . Dans MFC02View. cpp. Assurez-vous que le corps de la fonction OnInitialUpdate est le suivant :

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. Générez et exécutez le projet.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Dans le menu **Déboguer** , cliquez sur **exécuter sans débogage**.

   Notez que la zone de texte est maintenant initialisée.

## <a name="see-also"></a>Voir aussi

[Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
