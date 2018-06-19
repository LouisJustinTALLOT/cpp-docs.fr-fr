---
title: Ordre des opérations pour la création de contrôles ActiveX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: caf4c74f2263505ad5d7112021003f92c85a4b84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380368"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Ordre des opérations pour la création de contrôles ActiveX
Le tableau suivant indique votre rôle et l’infrastructure lors de la création de contrôles ActiveX (anciennement appelés contrôles OLE).  
  
### <a name="creating-activex-controls"></a>Création de contrôles ActiveX  
  
|Tâche|Ce que vous devez faire|Ce que le framework fait|  
|----------|------------|------------------------|  
|Créer une infrastructure de contrôle ActiveX.|Exécutez l’Assistant de contrôle ActiveX MFC pour créer votre contrôle. Spécifiez les options souhaitées dans les pages d'options. Options incluent le type et le nom du contrôle dans le projet, les licences, le sous-classement et une méthode sur la zone.|Assistant contrôle ActiveX MFC crée les fichiers pour un contrôle ActiveX avec les fonctionnalités de base, y compris les fichiers source pour votre application, le contrôle et la page de propriétés ou la pages ; un fichier de ressources ; un fichier projet ; et d’autres utilisateurs, tout en respectant vos spécifications.|  
|Voir ce que le contrôle et l’Assistant contrôle ActiveX offrent sans ajouter une ligne de votre propre code.|Générer le contrôle ActiveX et testez-le avec Internet Explorer ou [exemple TSTCON](../visual-cpp-samples.md).|Le contrôle en cours d’exécution a la possibilité d’être redimensionné et déplacé. Il comporte également un **sur la zone** (méthode) (le cas échéant) qui peut être appelée.|  
|Implémentez les méthodes et les propriétés du contrôle.|Implémenter votre propre au contrôle méthodes et des propriétés en ajoutant des fonctions membres pour fournir une interface exposée aux données du contrôle. Ajoutez des variables membres pour les structures de données et utiliser des gestionnaires d’événements pour déclencher des événements lorsque vous déterminez.|L’infrastructure a déjà défini un mappage pour prendre en charge les événements du contrôle, les propriétés et les méthodes, en vous laissant vous concentrer sur la façon dont les propriétés et méthodes sont implémentées. La page de propriétés par défaut est visible et une méthode AboutBox est fournie.|  
|Construire la page de propriétés ou des pages du contrôle.|Utilisez les éditeurs de ressources Visual C++ pour modifier visuellement l’interface du contrôle propriété page :<br /><br /> -Créer des pages de propriétés supplémentaires.<br />-Permet de créer et modifier des bitmaps, icônes et curseurs.<br /><br /> Vous pouvez également tester les pages de propriétés dans l’éditeur de boîte de dialogue.|Le fichier de ressources par défaut créé par l'Assistant Application MFC fournit plusieurs ressources dont vous avez besoin. Visual C++ vous permet de modifier les ressources existantes et d'ajouter de nouvelles ressources facilement et visuellement.|  
|Tester les événements, les méthodes et les propriétés du contrôle.|Régénérez le contrôle et utilisez le conteneur de Test pour vérifier que vos gestionnaires fonctionnent correctement.|Vous pouvez appeler les méthodes du contrôle et manipuler ses propriétés via l’interface de page de propriété ou via le conteneur de Test. En outre, utilisez le conteneur de Test pour suivre les événements déclenchés à partir du contrôle et les notifications reçues par le conteneur du contrôle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération à partir de l’infrastructure](../mfc/building-on-the-framework.md)   
 [Ordre des opérations pour la génération d’Applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Ordre des opérations pour la création d’Applications OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Ordre des opérations pour la création d’applications de base de données](../mfc/sequence-of-operations-for-creating-database-applications.md)

