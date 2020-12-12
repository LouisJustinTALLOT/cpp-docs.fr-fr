---
description: 'En savoir plus sur : séquence d’opérations pour la création de contrôles ActiveX'
title: Ordre des opérations pour la création de contrôles ActiveX
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
ms.openlocfilehash: 15b81716f5feee4dfd4d0ebf47ee4d0d648c4536
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217626"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Ordre des opérations pour la création de contrôles ActiveX

Le tableau suivant montre votre rôle et le rôle de l’infrastructure dans la création de contrôles ActiveX (anciennement appelés contrôles OLE).

### <a name="creating-activex-controls"></a>Création de contrôles ActiveX

|Tâche|Ce que vous devez faire|Ce que le framework fait|
|----------|------------|------------------------|
|Créer une infrastructure de contrôle ActiveX.|Exécutez l’Assistant contrôle ActiveX MFC pour créer votre contrôle. Spécifiez les options souhaitées dans les pages d'options. Les options incluent le type et le nom du contrôle dans le projet, la gestion des licences, le sous-classement et une méthode à propos de Box.|L’Assistant contrôle ActiveX MFC crée les fichiers pour un contrôle ActiveX avec des fonctionnalités de base, notamment les fichiers sources de votre application, contrôle, page de propriétés et pages de propriétés ; un fichier de ressources ; un fichier projet ; et d’autres, adaptés à vos spécifications.|
|Découvrez ce que propose le contrôle et l’Assistant contrôle ActiveX sans ajouter une ligne de votre propre code.|Générez le contrôle ActiveX et testez-le à l’aide d’Internet Explorer ou de l' [exemple TSTCON](../overview/visual-cpp-samples.md).|Le contrôle en cours d’exécution a la possibilité d’être redimensionné et déplacé. Elle dispose également d’une méthode **à propos de Box** (si elle est choisie) qui peut être appelée.|
|Implémentez les méthodes et les propriétés du contrôle.|Implémentez vos méthodes et propriétés spécifiques au contrôle en ajoutant des fonctions membres pour fournir une interface exposée aux données du contrôle. Ajoutez des variables membres pour contenir des structures de données et utiliser des gestionnaires d’événements pour déclencher des événements lorsque vous déterminez.|L’infrastructure a déjà défini un mappage pour prendre en charge les événements, les propriétés et les méthodes du contrôle, ce qui vous permet de vous concentrer sur la façon dont les propriétés et les méthodes sont implémentées. La page de propriétés par défaut est affichable et une méthode de boîte de message par défaut est fournie.|
|Construisez la ou les pages de propriétés du contrôle.|Utilisez le Visual C++ éditeurs de ressources pour modifier visuellement l’interface de la page de propriétés du contrôle :<br /><br />-Créer des pages de propriétés supplémentaires.<br />-Créez et modifiez des bitmaps, des icônes et des curseurs.<br /><br /> Vous pouvez également tester la ou les pages de propriétés dans l’éditeur de boîtes de dialogue.|Le fichier de ressources par défaut créé par l'Assistant Application MFC fournit plusieurs ressources dont vous avez besoin. Visual C++ vous permet de modifier les ressources existantes et d'ajouter de nouvelles ressources facilement et visuellement.|
|Testez les événements, les méthodes et les propriétés du contrôle.|Régénérez le contrôle et utilisez le conteneur de test pour vérifier que vos gestionnaires fonctionnent correctement.|Vous pouvez appeler les méthodes du contrôle et manipuler ses propriétés via l’interface de la page de propriétés ou via le conteneur de test. En outre, utilisez le conteneur de test pour suivre les événements déclenchés à partir du contrôle et les notifications reçues par le conteneur du contrôle.|

## <a name="see-also"></a>Voir aussi

[Génération sur le Framework](../mfc/building-on-the-framework.md)<br/>
[Séquence d’opérations pour la génération d’applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Séquence d’opérations pour la création d’applications OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Séquence d’opérations pour la création d’applications de base de données](../mfc/sequence-of-operations-for-creating-database-applications.md)
