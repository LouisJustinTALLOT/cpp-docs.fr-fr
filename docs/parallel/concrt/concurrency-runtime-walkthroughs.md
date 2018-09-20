---
title: Procédures pas à pas de concurrence Runtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 143e9a0bba5aacfd3004bd7b90615692a1cb66bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433192"
---
# <a name="concurrency-runtime-walkthroughs"></a>Procédures pas à pas relatives au runtime d'accès concurrentiel

Les rubriques basées sur des scénarios de cette section montrent comment utiliser la plupart des fonctionnalités du Runtime d’accès concurrentiel.

## <a name="in-this-section"></a>Dans cette section

[Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Montre comment utiliser le [IXMLHTTPRequest2](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) et [IXMLHTTPRequest2Callback](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfaces avec des tâches pour envoyer des demandes HTTP GET et POST à un service web dans une application de plateforme universelle Windows (UWP).

[Procédure pas à pas : création d’une application basée sur un agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
Décrit comment créer une application basée sur un agent de base.

[Procédure pas à pas : création des agents de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
Montre comment créer des applications basées sur l’agent qui reposent sur le flux de données, au lieu de flux de contrôle.

[Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
Montre comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement d’image.

[Procédure pas à pas : implémentation d’objets future](../../parallel/concrt/walkthrough-implementing-futures.md)<br/>
Montre comment calculer des valeurs pour une utilisation ultérieure de façon asynchrone.

[Procédure pas à pas : utilisation de la classe join pour empêcher l’interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)<br/>
Utilise le problème dîner des philosophes pour illustrer comment utiliser le [concurrency::join](../../parallel/concrt/reference/join-class.md) classe pour empêcher tout interblocage dans votre application.

[Procédure pas à pas : suppression de travail d’un thread d’interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
Montre comment améliorer les performances d’une application MFC qui dessine une fractale de Mandelbrot.

[Procédure pas à pas : utilisation du runtime d’accès concurrentiel routage dans une application COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)<br/>
Montre comment utiliser le Runtime d’accès concurrentiel dans une application qui utilise le composant COM (Object Model).

[Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)<br/>
Montre comment adapter du code existant qui utilise l’API Windows pour créer et exécuter un thread pour utiliser une tâche légère.

[Procédure pas à pas : création d’un bloc de message personnalisé](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)<br/>
Décrit comment créer un type de bloc de message personnalisé qui classe les messages entrants par priorité.

## <a name="related-sections"></a>Rubriques connexes

[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)<br/>
Présente l’infrastructure de programmation simultanée pour Visual C++.

