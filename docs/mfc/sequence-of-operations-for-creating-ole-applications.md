---
description: 'En savoir plus sur : séquence des opérations pour la création d’applications OLE'
title: Ordre des opérations pour la création d'applications OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: 2bce49d569c6d3def536cbe9386cafbe08ccdbfb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217560"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Ordre des opérations pour la création d'applications OLE

Le tableau suivant montre votre rôle et le rôle de l’infrastructure dans la création d’applications de liaison et d’incorporation OLE. Celles-ci représentent des options disponibles plutôt qu’une séquence d’étapes à effectuer.

### <a name="creating-ole-applications"></a>Création d’applications OLE

|Tâche|Ce que vous devez faire|Ce que le framework fait|
|----------|------------|------------------------|
|Créez un composant COM.|Exécutez l'Assistant Application MFC. Choisissez **serveur complet** ou **mini-serveur** dans l’onglet **prise en charge des documents composés** .|L’infrastructure génère une application squelette avec la fonctionnalité de composant COM activée. Toutes les fonctionnalités COM peuvent être transférées à votre application existante avec une légère modification uniquement.|
|Créer une application de conteneur à partir de zéro.|Exécutez l'Assistant Application MFC. Choisissez **conteneur** sous l’onglet **prise en charge des documents composés** . l’utilisation de affichage de classes, accédez à l’éditeur de code source. Renseignez le code pour vos fonctions de gestionnaire COM.|L’infrastructure génère une application squelette qui peut insérer des objets COM créés par des applications de composant COM (serveur).|
|Créer une application qui prend en charge Automation à partir de zéro.|Exécutez l'Assistant Application MFC. Choisissez **Automation** sous l’onglet **fonctionnalités avancées** . Utilisez affichage de classes pour exposer des méthodes et des propriétés dans votre application pour l’automatisation.|L’infrastructure génère une application squelette qui peut être activée et automatisée par d’autres applications.|

## <a name="see-also"></a>Voir aussi

[Génération sur le Framework](../mfc/building-on-the-framework.md)<br/>
[Séquence d’opérations pour la génération d’applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Séquence d’opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[Séquence d’opérations pour la création d’applications de base de données](../mfc/sequence-of-operations-for-creating-database-applications.md)
