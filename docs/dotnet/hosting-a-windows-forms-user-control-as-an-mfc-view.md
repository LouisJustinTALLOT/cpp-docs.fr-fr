---
title: Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: 9eb157ecbc738e1d7a1c3022d5f156fb590e8f04
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704119"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC

MFC utilise la classe CWinFormsView pour héberger un contrôle utilisateur Windows Forms dans une vue MFC. Les vues MFC Windows Forms sont des contrôles ActiveX. Le contrôle utilisateur est hébergé en tant qu’enfant de la vue native et occupe la totalité de la zone cliente de la vue native.

Le résultat final ressemble au modèle utilisé par la [classe CFormView](../mfc/reference/cformview-class.md). Cela vous permet de tirer parti de Windows Forms Designer et du runtime pour créer des vues riches basées sur des formulaires.

Étant donné que les vues MFC Windows Forms sont des contrôles ActiveX, elles n’ont pas le même `hwnd` que les vues MFC. Ils ne peuvent pas non plus être passés comme pointeur vers une vue [CView](../mfc/reference/cview-class.md) . En général, utilisez .NET Framework méthodes pour travailler avec des vues Windows Forms et compter moins sur Win32.

Pour obtenir un exemple d’application qui montre Windows Forms utilisé avec MFC, consultez [MFC and Windows Forms Integration](https://www.microsoft.com/en-us/download/details.aspx?id=2113).

## <a name="in-this-section"></a>Dans cette section

[Guide pratique pour créer le contrôle utilisateur et héberger l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[Guide pratique pour appeler des propriétés et des méthodes du contrôle Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>Voir aussi

[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Guide pratique pour créer des contrôles composites](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
