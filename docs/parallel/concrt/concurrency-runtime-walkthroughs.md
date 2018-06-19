---
title: Procédures pas à pas de concurrence Runtime | Documents Microsoft
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
ms.openlocfilehash: 05e50530bf1c7aa401a7422a0119f004e30234a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686631"
---
# <a name="concurrency-runtime-walkthroughs"></a>Procédures pas à pas relatives au runtime d'accès concurrentiel
Les rubriques basée sur un scénario de cette section montrent comment utiliser la plupart des fonctionnalités du Runtime d’accès concurrentiel.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Montre comment utiliser le [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) et [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfaces avec des tâches pour envoyer des demandes HTTP GET et POST à un service web dans une application de plateforme Windows universelle (UWP).  
  
 [Procédure pas à pas : création d’une application basée sur un agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 Décrit comment créer une application basée sur l’agent de base.  
  
 [Procédure pas à pas : création des agents de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 Montre comment créer des applications basées sur l’agent qui reposent sur le flux de données, au lieu de flux de contrôle.  
  
 [Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 Montre comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement d’image.  
  
 [Procédure pas à pas : implémentation d’objets future](../../parallel/concrt/walkthrough-implementing-futures.md)  
 Montre comment calculer des valeurs pour une utilisation ultérieure de façon asynchrone.  
  
 [Procédure pas à pas : utilisation de la classe join pour empêcher l’interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 Utilise le problème du dîner des philosophes pour illustrer comment utiliser la [concurrency::join](../../parallel/concrt/reference/join-class.md) classe pour empêcher tout interblocage dans votre application.  
  
 [Procédure pas à pas : suppression de travail d’un thread d’interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 Montre comment améliorer les performances d’une application MFC qui dessine une fractale de Mandelbrot.  
  
 [Procédure pas à pas : utilisation du runtime d’accès concurrentiel routage dans une application COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 Montre comment utiliser le Runtime d’accès concurrentiel dans une application qui utilise le modèle COM (Component Object).  
  
 [Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 Montre comment adapter du code existant qui utilise l’API Windows pour créer et exécuter un thread pour utiliser une tâche légère.  
  
 [Procédure pas à pas : création d’un bloc de message personnalisé](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 Décrit comment créer un type de bloc de message personnalisé qui classe les messages entrants par priorité.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)  
 Présente l’infrastructure de programmation simultanée pour Visual C++.

