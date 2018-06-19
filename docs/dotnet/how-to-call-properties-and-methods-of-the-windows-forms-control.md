---
title: 'Comment : appeler des propriétés et méthodes des Windows Forms contrôlent | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 206c7bc89ce2bbc48beb1d95f3929ea4694fce20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131353"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Comment : appeler des propriétés et des méthodes du contrôle Windows Forms
Étant donné que [CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) retourne un pointeur vers <xref:System.Windows.Forms.Control?displayProperty=fullName>et non un pointeur vers `WindowsControlLibrary1::UserControl1`, il est recommandé d’ajouter un membre du type de contrôle utilisateur et l’initialiser dans [IView::OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Vous pouvez maintenant appeler à l’aide des propriétés et méthodes `m_ViewControl`.  
  
 Cette rubrique suppose que vous avez déjà terminées [Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) et [Comment : créer le contrôle utilisateur et l’affichage des ordinateurs hôtes MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application MFC hôte  
  
1.  Ouvrez l’application MFC que vous avez créé dans [Comment : créer le contrôle utilisateur et l’affichage des ordinateurs hôtes MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
2.  Ajoutez la ligne suivante à la section des substitutions publique de la `CMFC02View` déclaration dans MFC02View.h de classe.  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  Ajoutez une substitution pour OnInitialupdate.  
  
     Afficher le **propriétés** fenêtre (F4). Dans **affichage de classes** (CTRL + MAJ + C), sélectionnez CMFC02View classe. Dans le **propriétés** fenêtre, sélectionnez l’icône pour les remplacements. Scoll vers le bas de la liste pour OnInitialUpdate. Cliquez sur la liste déroulante et sélectionnez \<Ajouter >. Dans MFC02View.cpp. Assurez-vous que le corps de la fonction OnInitialUpdate comme suit :  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  Générez et exécutez le projet.  
  
     Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.  
  
     Notez que la zone de texte est maintenant initialisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)