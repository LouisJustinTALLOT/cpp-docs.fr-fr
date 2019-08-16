---
title: Procédures pas à pas relatives au runtime d'accès concurrentiel
ms.date: 11/04/2016
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
ms.openlocfilehash: 7c5973f8010d7c428406a8a3f69574eab20edf82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512824"
---
# <a name="concurrency-runtime-walkthroughs"></a>Procédures pas à pas relatives au runtime d'accès concurrentiel

Les rubriques basées sur des scénarios de cette section montrent comment utiliser la plupart des fonctionnalités du runtime d’accès concurrentiel.

## <a name="in-this-section"></a>Dans cette section

[Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Montre comment utiliser les interfaces [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) et [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) avec des tâches pour envoyer des requêtes http et de publication à un service web dans une application plateforme Windows universelle (UWP).

[Procédure pas à pas : création d'une application basée sur des agents](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
Décrit comment créer une application de base basée sur un agent.

[Procédure pas à pas : création d’un agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
Montre comment créer des applications basées sur un agent basées sur le flux de données, plutôt que sur le flux de contrôle.

[Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
Montre comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement d’image.

[Procédure pas à pas : implémentation de tâches futures](../../parallel/concrt/walkthrough-implementing-futures.md)<br/>
Montre comment calculer des valeurs de façon asynchrone en vue d’une utilisation ultérieure.

[Procédure pas à pas : Utilisation de jointures pour prévenir les interblocages](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)<br/>
Utilise le problème du dîner de philosophes pour illustrer comment utiliser la classe [Concurrency:: Join](../../parallel/concrt/reference/join-class.md) pour empêcher tout interblocage dans votre application.

[Procédure pas à pas : suppression de travail d’un thread d’interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
Montre comment améliorer les performances d’une application MFC qui dessine la fractale de Mandelbrot.

[Procédure pas à pas : utilisation du runtime d'accès concurrentiel dans une application COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)<br/>
Montre comment utiliser le runtime d’accès concurrentiel dans une application qui utilise le modèle COM (Component Object Model).

[Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)<br/>
Montre comment adapter le code existant qui utilise l’API Windows pour créer et exécuter un thread afin d’utiliser une tâche légère.

[Procédure pas à pas : création d’un bloc de message personnalisé](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)<br/>
Décrit comment créer un type de bloc de message personnalisé qui classe les messages entrants par priorité.

## <a name="related-sections"></a>Rubriques connexes

[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)<br/>
Présente l’infrastructure de programmation simultanée C++pour Visual.
