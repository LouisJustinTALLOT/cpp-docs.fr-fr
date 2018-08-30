---
title: Ajout d’une classe MFC à partir d’une bibliothèque de types | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 656d5c357874a7b470eb2fd630c91ad0aefa5a0d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205371"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Ajout d'une classe MFC à partir d'une bibliothèque de types
Utilisez cet Assistant pour créer une classe MFC à partir d’une interface dans une bibliothèque de types disponibles. Vous pouvez ajouter une classe MFC à une [application MFC](../../mfc/reference/creating-an-mfc-application.md), une [DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md) ou un [contrôle ActiveX MFC](../../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Vous n’avez pas besoin de créer votre projet MFC avec Automation activée pour ajouter une classe à partir d’une bibliothèque de types.  
  
 Une bibliothèque de types contient une description binaire des interfaces exposées par un composant, en définissant les méthodes, ainsi que leurs paramètres et les types de retour. Votre bibliothèque de types doit être inscrite pour qu’il apparaisse dans le **bibliothèques de types disponibles** liste dans Ajouter une classe à partir d’une Typelib, Assistant. Consultez « À l’intérieur de Distributed COM : Type de bibliothèques et langue intégration » dans la bibliothèque MSDN pour plus d’informations.  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>Pour ajouter une classe MFC à partir d’une bibliothèque de types  
  
1.  Dans le **l’Explorateur de solutions** ou [affichage de classes](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), cliquez sur le nom du projet auquel vous souhaitez ajouter la classe.  
  
2.  Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.  
  
3.  Dans le [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue, dans le volet Modèles, cliquez sur **classe MFC à partir d’une Typelib**, puis cliquez sur **Open** pour afficher le [ajouter une classe à partir d’une Typelib, Assistant ](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 Dans l’Assistant, vous pouvez ajouter plusieurs classes dans une bibliothèque de types. De même, vous pouvez ajouter des classes à partir de plus d’une bibliothèque de types dans une session d’Assistant unique.  
  
 L’Assistant crée une classe MFC, dérivée de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), pour chaque interface que vous ajoutez à partir de la bibliothèque de types sélectionnée. `COleDispatchDriver` implémente le côté client d’OLE automation.  
  
## <a name="see-also"></a>Voir aussi  
 [Clients Automation](../../mfc/automation-clients.md)   
 [Clients Automation : utilisation des bibliothèques de types](../../mfc/automation-clients-using-type-libraries.md)

