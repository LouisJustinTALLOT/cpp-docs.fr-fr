---
title: 'Procédure : Appeler des propriétés et méthodes des formulaires Windows de contrôle'
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
ms.openlocfilehash: 61b565839b3f3c24670819fdcf2dde558e3461ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152811"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Procédure : Appeler des propriétés et méthodes des formulaires Windows de contrôle

Étant donné que [CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) retourne un pointeur vers <xref:System.Windows.Forms.Control?displayProperty=fullName>et non un pointeur vers `WindowsControlLibrary1::UserControl1`, il est recommandé d’ajouter un membre du type de contrôle utilisateur et l’initialiser dans [IView::OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Vous pouvez maintenant appeler à l’aide des propriétés et méthodes `m_ViewControl`.

Cette rubrique suppose que vous avez déjà effectué [Comment : Créer le contrôle utilisateur et l’héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) et [Comment : Créer le contrôle utilisateur et héberger l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application MFC hôte

1. Ouvrez l’application MFC que vous avez créé dans [Comment : Créer le contrôle utilisateur et héberger l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Ajoutez la ligne suivante à la section publique de remplacements de la `CMFC02View` déclaration dans MFC02View.h de classe.

   `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. Ajoutez une substitution pour OnInitialupdate.

   Afficher le **propriétés** fenêtre (F4). Dans **affichage de classes** (CTRL + MAJ + C), sélectionnez CMFC02View classe. Dans le **propriétés** fenêtre, sélectionnez l’icône pour les remplacements. Scoll vers le bas la liste pour OnInitialUpdate. Cliquez sur la liste déroulante et sélectionnez \<Ajouter >. Dans MFC02View.cpp. Assurez-vous que le corps de la fonction OnInitialUpdate est comme suit :

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. Générez et exécutez le projet.

   Dans le menu **Générer** , cliquez sur **Générer la solution**.

   Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.

   Notez que la zone de texte est maintenant initialisée.

## <a name="see-also"></a>Voir aussi

[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
