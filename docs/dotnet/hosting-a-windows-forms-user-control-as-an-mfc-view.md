---
title: Hébergement Windows Forms contrôle utilisateur en tant que vue MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf9e54b3e2808a232bc13052c885a341cb51297f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137625"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC
MFC utilise la classe CWinFormsView pour héberger un contrôle utilisateur de Windows Forms dans une vue MFC. Vues de MFC Windows Forms sont des contrôles ActiveX. Le contrôle utilisateur est hébergé en tant qu’enfant de la vue native et occupe la zone cliente de la vue native.  
  
 Le résultat final ressemble au modèle utilisé par le [CFormView, classe](../mfc/reference/cformview-class.md). Cela vous permet de tirer parti du Concepteur Windows Forms et du runtime pour créer des vues basées sur le formulaire riches.  
  
 Étant donné que les vues MFC Windows Forms sont des contrôles ActiveX, elles n’ont pas le même `hwnd` que les vues MFC. Également qu’ils ne peuvent pas être passés comme un pointeur vers un [CView](../mfc/reference/cview-class.md) vue. En règle générale, utilisez les méthodes .NET Framework pour travailler avec des vues Windows Forms et dépendre moins de Win32.  
  
 Pour un exemple d’application qui affiche des Windows Forms avec les MFC, consultez [intégration de Windows Forms et MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer le contrôle utilisateur et héberger l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [Guide pratique pour appeler des propriétés et des méthodes du contrôle Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Guide pratique pour créer des contrôles composites](/dotnet/framework/winforms/controls/how-to-author-composite-controls)