---
title: "Ajout d’objets et des contrôles à un projet ATL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.controls
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 319d130b9d8f17875aaa8bac15f546401457b963
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Ajout d’objets et des contrôles à un projet ATL
Vous pouvez utiliser un des Assistants code ATL pour ajouter un objet ou un contrôle à vos projets basés sur ATL ou MFC. Pour chaque objet COM ou d’un contrôle que vous ajoutez, l’Assistant génère .cpp et .h fichiers, mais aussi un fichier .rgs pour la prise en charge basée sur un script de Registre. Assistants code ATL suivants sont disponibles dans Visual Studio :  
  
||||  
|-|-|-|  
|[Objet Simple ATL](../../atl/reference/atl-simple-object-wizard.md)|[Boîte de dialogue ATL](../../atl/reference/atl-dialog-wizard.md)|[Contrôle ATL](../../atl/reference/atl-control-wizard.md)|  
|[Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md)|[Composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Consommateur OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md)|  
|[Ajouter la prise en charge ATL aux MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Assistant Composant COM+ 1.0 ATL](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Fournisseur OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|  
  
> [!NOTE]
>  Avant d’ajouter un objet ATL à votre projet, vous devez passer en revue les détails et la configuration requise pour l’objet dans les rubriques d’aide connexes.  
  
### <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Pour ajouter un objet ou un contrôle à l’aide de l’Assistant contrôle ATL  
  
1.  Dans l’Explorateur de solutions, cliquez sur le nœud du projet, puis cliquez sur **ajouter** dans le menu contextuel. Cliquez sur **ajouter une classe**.  
  
     Le [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue s’affiche.  
  
2.  Le dossier ATL sélectionné dans le volet des catégories, sélectionnez un objet à insérer dans le volet Modèles. Cliquez sur **ouvrir**. L’Assistant de code de l’objet sélectionné s’affiche.  
  
    > [!NOTE]
    >  Si vous souhaitez ajouter un objet ATL à un projet MFC, vous devez ajouter la prise en charge ATL au projet existant. Vous faire cela en suivant les instructions de [ajoutant la prise en charge ATL à votre projet MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
     Ou bien, si vous essayez d’ajouter un objet ATL à votre projet MFC sans ajouter de précédemment prise en charge ATL, Visual Studio vous invite à spécifier si vous souhaitez que la prise en charge ATL ajoutée à votre projet. Cliquez sur **Oui** pour ajouter la prise en charge ATL au projet et ouvrir l’Assistant ATL sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)   
 [Types de projet Visual C++](../../ide/visual-cpp-project-types.md)   
 [Création de projets du Bureau à l’aide des Assistants Application](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Notions de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programmation avec ATL et le Code d’exécution C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)

