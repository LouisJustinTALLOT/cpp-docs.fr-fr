---
title: Ordre des opérations pour la création d’Applications OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 412fa5c104d6e85bcaa6ba3703cc8c7ba535f25f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381207"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Ordre des opérations pour la création d'applications OLE
Le tableau suivant indique votre rôle et l’infrastructure lors de la création de la liaison OLE et l’incorporation des applications. Ils représentent des options disponibles au lieu d’une séquence d’étapes à effectuer.  
  
### <a name="creating-ole-applications"></a>Création d’Applications OLE  
  
|Tâche|Ce que vous devez faire|Ce que le framework fait|  
|----------|------------|------------------------|  
|Créer un composant COM.|Exécutez l’Assistant Application MFC. Choisissez **serveur complet** ou **mini-serveur** dans les **prise en charge des documents composés** onglet.|L’infrastructure génère une application squelette avec fonction de composant COM. Tous les de la fonctionnalité COM peuvent être transférées à votre application existante avec une seule petite modification.|  
|Créer une application conteneur à partir de zéro.|Exécutez l’Assistant Application MFC. Choisissez **conteneur** dans les **prise en charge des documents composés** onglet. L’affichage de classes, accédez à l’éditeur de code source. Renseignez le code pour vos fonctions de gestionnaire COM.|L’infrastructure génère une application squelette qui peut insérer des objets COM créés par les applications COM composant (serveur).|  
|Créer une application qui prend en charge d’Automation à partir de zéro.|Exécutez l’Assistant Application MFC. Choisissez **Automation** à partir de la **fonctionnalités avancées** onglet. Affichage de classes permet d’exposer les méthodes et propriétés dans votre application pour l’automatisation.|L’infrastructure génère une application squelette qui peut être activée et automatisée par d’autres applications.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération à partir de l’infrastructure](../mfc/building-on-the-framework.md)   
 [Ordre des opérations pour la génération d’Applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Ordre des opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Ordre des opérations pour la création d’applications de base de données](../mfc/sequence-of-operations-for-creating-database-applications.md)

