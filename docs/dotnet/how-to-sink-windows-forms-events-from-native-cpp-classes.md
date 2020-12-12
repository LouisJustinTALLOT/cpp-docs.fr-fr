---
description: 'En savoir plus sur : Comment : recevoir des événements de Windows Forms à partir de classes C++ natives'
title: 'Comment : recevoir des événements Windows Forms de classes C++ natives'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: 223590849f114bfe02b030a0639f160b8fc1c321
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286356"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Comment : recevoir des événements Windows Forms de classes C++ natives

Vous pouvez activer les classes C++ natives pour recevoir des rappels d’événements managés déclenchés à partir de Windows Forms contrôles ou d’autres formulaires avec le format de mappage de macro MFC. La réception d’événements dans les vues et les boîtes de dialogue est similaire à la réalisation de la même tâche pour les contrôles.

Pour cela, vous devez procéder comme suit :

- Attachez un `OnClick` Gestionnaire d’événements au contrôle à l’aide de [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate).

- Créez une carte déléguée à l’aide de [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)et [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).

Cet exemple poursuit le travail que vous avez effectué dans [Comment : effectuer une liaison de données DDX/DDV avec Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

À présent, vous allez associer votre contrôle MFC ( `m_MyControl` ) à un délégué de gestionnaire d’événements managé appelé `OnClick` pour l' <xref:System.Windows.Forms.Control.Click> événement managé.

### <a name="to-attach-the-onclick-event-handler"></a>Pour attacher le gestionnaire d’événements OnClick :

1. Ajoutez le code suivant à l’implémentation de BOOL CMFC01Dlg :: OnInitDialog :

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. Ajoutez le code suivant à la section public dans la déclaration de la classe CMFC01Dlg : public CDialog.

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. Enfin, ajoutez l’implémentation de `OnClick` à CMFC01Dlg. cpp :

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
