---
title: 'Comment : recevoir des événements Windows Forms de Classes C++ natives | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0fec32bf179424b5ec0164e4511f74eae44f7320
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130423"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Comment : recevoir des événements Windows Forms de classes C++ natives
Vous pouvez activer les classes C++ natives de recevoir des rappels d’événements managés déclenchés à partir de contrôles Windows Forms ou d’autres formulaires avec le format de mappage de macro MFC. Réception des événements dans les vues et les boîtes de dialogue est similaire à l’exécution de la même tâche pour les contrôles.  
  
 Pour ce faire, vous devez :  
  
-   Attacher un `OnClick` Gestionnaire d’événements pour le contrôle à l’aide de [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate).  
  
-   Créer un mappage de délégué à l’aide de [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map), et [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).  
  
 Cet exemple continue les tâches que vous l’avez fait dans [Comment : effectuer une liaison de données DDX/DDV avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
  
 Vous allez maintenant associer votre contrôle MFC (`m_MyControl`) avec un délégué de gestionnaire d’événements managé appelé `OnClick` pour managé <xref:System.Windows.Forms.Control.Click> événement.  
  
### <a name="to-attach-the-onclick-event-handler"></a>Pour attacher le Gestionnaire d’événements OnClick :  
  
1.  Ajoutez le code suivant à l’implémentation de BOOL CMFC01Dlg::OnInitDialog :  
  
    ```  
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );  
    ```  
  
2.  Ajoutez le code suivant à la section public dans la déclaration de classe CMFC01Dlg : CDialog publique.  
  
    ```  
    // delegate map  
    BEGIN_DELEGATE_MAP( CMFC01Dlg )  
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )  
    END_DELEGATE_MAP()  
  
    void OnClick( System::Object^ sender, System::EventArgs^ e );  
    ```  
  
3.  Enfin, ajoutez l’implémentation pour `OnClick` à CMFC01Dlg.cpp :  
  
    ```  
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)  
    {  
        AfxMessageBox(_T("Button clicked"));  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)   
 [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)   
 [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)   
 [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)