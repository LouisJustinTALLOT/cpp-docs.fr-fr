---
title: Ordre des opérations pour la création d'applications OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: b281cbeb4670af0efd232152010fdc90795af103
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437347"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Ordre des opérations pour la création d'applications OLE

Le tableau suivant indique votre rôle et l’infrastructure lors de la création de la liaison OLE et l’incorporation d’applications. Ils représentent les options disponibles au lieu d’une séquence d’étapes à effectuer.

### <a name="creating-ole-applications"></a>Création d’Applications OLE

|Tâche|Ce que vous devez faire|Ce que le framework fait|
|----------|------------|------------------------|
|Créer un composant COM.|Exécutez l’Assistant Application MFC. Choisissez **serveur complet** ou **mini-serveur** dans le **prise en charge des documents composés** onglet.|L’infrastructure génère une application squelette avec la fonctionnalité de composant COM est activée. Tous de la fonctionnalité de COM peuvent être transférée à votre application existante avec de légères modifications uniquement.|
|Créer une application de conteneur à partir de zéro.|Exécutez l’Assistant Application MFC. Choisissez **conteneur** dans le **prise en charge des documents composés** onglet. Affichage de classes, accédez à l’éditeur de code source. Renseignez le code pour vos fonctions de gestionnaire COM.|L’infrastructure génère une application squelette qui peut insérer des objets COM créés par les applications COM composant (serveur).|
|Créer une application qui prend en charge d’Automation à partir de zéro.|Exécutez l’Assistant Application MFC. Choisissez **Automation** à partir de la **fonctionnalités avancées** onglet. Affichage de classes permet d’exposer les méthodes et propriétés dans votre application pour l’automatisation.|L’infrastructure génère une application squelette qui peut être activée et automatisée par d’autres applications.|

## <a name="see-also"></a>Voir aussi

[Génération à partir du Framework](../mfc/building-on-the-framework.md)<br/>
[Ordre des opérations pour la génération d’applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Ordre des opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[Ordre des opérations pour la création d’applications de base de données](../mfc/sequence-of-operations-for-creating-database-applications.md)

