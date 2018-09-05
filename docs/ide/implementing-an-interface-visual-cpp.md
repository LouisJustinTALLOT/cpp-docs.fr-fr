---
title: Implémentation d’une interface (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f7d7bed9725e4ec1cc8ad0fc66673ce5c6212e1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211210"
---
# <a name="implementing-an-interface-visual-c"></a>Implémentation d'une interface (Visual C++)
Pour implémenter une interface, vous devez avoir créé un projet, comme une application COM ATL ou une application MFC avec prise en charge ATL. Vous pouvez utiliser [l’Assistant Projet ATL](../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.  
  
 Une fois que vous avez créé un projet, vous devez ajouter un objet ATL pour pouvoir implémenter une interface. Consultez [Ajout d’objets et de contrôles à un projet ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) pour obtenir la liste des Assistants permettant d’ajouter des objets à votre projet ATL.  
  
> [!NOTE]
>  L’Assistant ne prend pas en charge les boîtes de dialogue ATL, les services web XML utilisant ATL, les objets de performance ou les compteurs de performance.  
  
 Si vous [ajoutez un contrôle ATL](../atl/reference/adding-an-atl-control.md), vous pouvez spécifier s’il faut implémenter les interfaces par défaut répertoriées dans la page [Interfaces](../atl/reference/interfaces-atl-control-wizard.md) de cet Assistant et définies dans le fichier atlcom.h.  
  
 Une fois que vous avez ajouté l’objet ou le contrôle, vous pouvez implémenter d’autres interfaces, situées dans n’importe quelle bibliothèque de types disponible, à l’aide de l’Assistant Implémentation d’interface.  
  
 Si vous ajoutez une nouvelle interface, vous devez l’ajouter manuellement au fichier .idl du projet. Pour plus d’informations, consultez [Ajout d’une nouvelle interface à un projet ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).  
  
### <a name="to-implement-an-interface"></a>Pour implémenter une interface  
  
1.  Dans Affichage de classes, cliquez avec le bouton droit sur le nom de la classe de votre objet ATL.  
  
2.  Cliquez sur **Ajouter** dans le menu contextuel, puis sur **Implémenter l’interface** pour afficher [l’Assistant Implémentation d’interface](../ide/implement-interface-wizard.md).  
  
3.  Sélectionnez les interfaces à implémenter dans les bibliothèques de types appropriées et cliquez sur **Terminer**.  
  
4.  Dans Affichage de classes, développez les nœuds Bases et Interfaces pour voir l’interface que vous avez implémentée, puis développez le nœud de l’interface pour voir ses propriétés, méthodes et événements disponibles.  
  
    > [!NOTE]
    >  Vous pouvez également utiliser [l’Explorateur d’objets](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470) pour examiner les membres de l’interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une interface COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Modification d’une interface COM](../ide/editing-a-com-interface.md)