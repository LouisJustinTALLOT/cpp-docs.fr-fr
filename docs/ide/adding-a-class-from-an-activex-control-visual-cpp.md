---
title: Ajout d’une classe à partir d’un contrôle ActiveX (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b676e35dcf98ef7ae1f41e4a91922d689bd40409
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202137"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Ajout d'une classe à partir d'un contrôle ActiveX (Visual C++)
Utilisez cet Assistant pour créer une classe MFC à partir d’une interface dans un contrôle ActiveX disponible. Vous pouvez ajouter une classe MFC à une [application MFC](../mfc/reference/creating-an-mfc-application.md), une [DLL MFC](../mfc/reference/creating-an-mfc-dll-project.md) ou un [contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Il n’est pas nécessaire de créer un projet MFC avec l’option Automation activée pour ajouter une classe à partir d’un contrôle ActiveX.  
  
 Un contrôle ActiveX est un composant logiciel réutilisable qui repose sur le modèle COM (Component Object Model), prend en charge une large gamme de fonctionnalités OLE et peut être personnalisé pour répondre à de nombreux besoins logiciels. Les contrôles ActiveX sont conçus pour être utilisés à la fois dans des conteneurs de contrôles ActiveX ordinaires et sur Internet, dans des pages web.  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Pour ajouter une classe MFC à partir d’un contrôle ActiveX  
  
1.  Dans **l’Explorateur de solutions** ou dans [l’affichage de classes](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter la classe du contrôle ActiveX.  
  
2.  Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.  
  
3.  Dans le volet Modèles de la boîte de dialogue [Ajouter une classe](../ide/add-class-dialog-box.md), cliquez sur **Classe MFC à partir du contrôle ActiveX**, puis sur **Ouvrir** pour afficher [l’Assistant Ajout d’une classe à partir d’un contrôle ActiveX](../ide/add-class-from-activex-control-wizard.md).  
  
 Dans l’Assistant, vous pouvez ajouter plusieurs interfaces dans un contrôle ActiveX. De même, vous pouvez créer des classes à partir de plusieurs contrôles ActiveX dans une session d’Assistant unique.  
  
 Vous pouvez ajouter des classes à partir des contrôles ActiveX inscrits dans votre système ou situés dans des fichiers bibliothèques de types (.tlb, .olb, .dll, .ocx ou .exe) sans avoir à les inscrire au préalable dans votre système. Pour plus d’informations sur l’inscription des contrôles ActiveX, consultez [Inscription des contrôles OLE](../mfc/reference/registering-ole-controls.md).  
  
 L’Assistant crée une classe MFC, dérivée de [CWnd](../mfc/reference/cwnd-class.md) ou de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), pour chaque interface que vous ajoutez à partir du contrôle ActiveX sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Introduction à COM et ATL](../atl/introduction-to-com-and-atl.md)