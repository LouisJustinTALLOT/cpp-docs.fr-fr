---
title: 'Procédure : Récepteur d’événements de Windows Forms de Classes C++ natives'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: d02bcea4efce03c8fb11650d344468236737cfbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387264"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Procédure : Récepteur d’événements de Windows Forms de Classes C++ natives

Vous pouvez activer les classes C++ natives recevoir des rappels d’événements managés déclenchés à partir de contrôles Windows Forms ou d’autres formes avec le format de mappage de macro MFC. Réception des événements dans les vues et les boîtes de dialogue est similaire à l’exécution de la même tâche pour les contrôles.

Pour ce faire, vous devez :

- Attacher un `OnClick` Gestionnaire d’événements pour le contrôle à l’aide [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate).

- Créer un mappage de délégué à l’aide [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map), et [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).

Cet exemple continue le travail que vous l’avez fait dans [Comment : Liaison des données DDX/DDV avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

Vous allez maintenant associer votre contrôle MFC (`m_MyControl`) avec un délégué de gestionnaire d’événements managé appelé `OnClick` pour managé <xref:System.Windows.Forms.Control.Click> événement.

### <a name="to-attach-the-onclick-event-handler"></a>Pour attacher le Gestionnaire d’événements SurClic :

1. Ajoutez le code suivant à l’implémentation de BOOL CMFC01Dlg::OnInitDialog :

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. Ajoutez le code suivant à la section publique de la déclaration de classe CMFC01Dlg : CDialog publique.

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. Enfin, ajoutez l’implémentation pour `OnClick` à CMFC01Dlg.cpp :

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>Voir aussi

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)
