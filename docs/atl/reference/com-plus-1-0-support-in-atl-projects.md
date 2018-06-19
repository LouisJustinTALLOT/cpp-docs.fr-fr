---
title: Prise en charge COM + 1.0 dans les projets ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3440d3ed2e3244b35588d5c07fd181f1ad2f082
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359355"
---
# <a name="com-10-support-in-atl-projects"></a>Prise en charge COM + 1.0 dans les projets ATL
Vous pouvez utiliser la [Assistant Projet ATL](../../atl/reference/creating-an-atl-project.md) pour créer un projet avec prise en charge de base des composants COM + 1.0.  
  
 COM + 1.0 est conçu pour le développement d’applications distribuées dans un composant. Il fournit également une infrastructure runtime pour le déploiement et la gestion de ces applications.  
  
 Si vous sélectionnez le **prise en charge COM + 1.0** case à cocher, l’Assistant modifie le script de compilation dans l’étape de liaison. Plus précisément, les COM + 1.0 projet liens vers les bibliothèques suivantes :  
  
-   Comsvcs.lib  
  
-   Mtxguid.lib  
  
 Si vous sélectionnez le **prise en charge COM + 1.0** case à cocher, vous pouvez également sélectionner **inscription de composants de prise en charge**. L’inscription de composants permet à votre objet COM + 1.0 obtenir la liste des composants, d’inscrire des composants ou d’annuler l’inscription de composants (individuellement ou tous en même temps).  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programmation avec ATL et le Code d’exécution C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)

