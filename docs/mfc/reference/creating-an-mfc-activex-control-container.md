---
title: Création d’un conteneur de contrôle ActiveX MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.container
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 322e7feba87b83802299a99ad36b16e35704f2ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372480"
---
# <a name="creating-an-mfc-activex-control-container"></a>Création d'un conteneur de contrôles ActiveX MFC
Un conteneur de contrôles ActiveX est un programme parent qui fournit l’environnement pour un contrôle ActiveX (anciennement appelés OLE) à exécuter. Vous pouvez créer une application capable de contenir des contrôles ActiveX avec ou sans MFC, mais il est beaucoup plus facile de faire avec MFC.  
  
 Création d’un programme MFC conteneur à l’aide du [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md) permet d’accéder aux principales fonctionnalités des contrôles ActiveX et Automation qui sont implémentées par les classes MFC et ActiveX. Ces fonctionnalités incluent la modification visuelle, l’Automation, la création de fichiers composés et prend en charge pour les contrôles. Les options d’édition visuelle Assistant Application MFC qui prennent en charge votre programme parent incluent la création d’un conteneur, un mini-serveur, un serveur complet et un programme qui est un conteneur et un serveur.  
  
-   **Nouvelle Application MFC**. Pour créer un nouveau programme MFC contenant Automation, la modification sur place, fichiers composés ou contrôle prennent en charge, utilisez l’Assistant Application MFC et choisissez les options Automation appropriées.  
  
-   **Application MFC existante**. Si vous ajoutez la relation contenant-contenu de contrôle à une application MFC existante, consultez [conteneurs de contrôles OLE : activation manuelle de la contenance de contrôles OLE](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).  
  
### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Pour créer un conteneur ActiveX pour un des types suivants d’applications  
  
1.  [Conteneurs](../../mfc/containers.md)  
  
2.  [Édition visuelle](../../mfc/ole-mfc.md)  
  
3.  [Contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Types de projets Visual C++](../../ide/visual-cpp-project-types.md)

