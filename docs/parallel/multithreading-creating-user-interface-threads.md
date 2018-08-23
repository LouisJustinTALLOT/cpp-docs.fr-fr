---
title: 'Multithreading : Création de Threads d’Interface utilisateur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0223e342bf2312919247d42564445a9e116ca59b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607393"
---
# <a name="multithreading-creating-user-interface-threads"></a>Multithreading : création de threads d'interface utilisateur
Un thread d’interface utilisateur est couramment utilisé pour gérer l’entrée d’utilisateur et répondre aux événements utilisateur indépendamment des threads exécutant d’autres parties de l’application. Le thread principal de l’application (fourni dans votre `CWinApp`-classe dérivée) est déjà créée et démarrée pour vous. Cette rubrique décrit les étapes nécessaires à la création de threads d’interface utilisateur supplémentaires.  
  
La première chose que vous devez effectuer lors de la création d’un thread d’interface utilisateur est de dériver une classe de [CWinThread](../mfc/reference/cwinthread-class.md). Vous devez déclarer et implémenter cette classe, à l’aide de la [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) et [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) macros. Cette classe doit substituer certaines fonctions et peut substituer d’autres. Ces fonctions et leur finalité sont présentées dans le tableau suivant.  
  
### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Fonctions à remplacer lors de la création d’un Thread d’Interface utilisateur  
  
|Fonction|Objectif|  
|--------------|-------------|  

|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)| Effectuer un nettoyage lorsque le thread s’arrête. Généralement remplacées. |  
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)| Effectuer une initialisation d’instance de thread. Doit être substitué. |  
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)| Exécuter le traitement des temps d’inactivité spécifique au thread. Substitution ne sont généralement pas. |  
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)| Filtrer les messages avant qu’ils soient distribués aux `TranslateMessage` et `DispatchMessage`. Substitution ne sont généralement pas. |  
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)| Intercepter des exceptions non gérées levées par les gestionnaires de commandes et de messages du thread. Substitution ne sont généralement pas. |  
|[Exécutez](../mfc/reference/cwinthread-class.md#run)| Fonction de contrôle pour le thread. Contient la pompe de messages. Substitution rarement. |  

  
MFC fournit deux versions de `AfxBeginThread` via la surcharge de paramètres : une qui peut seulement créer des threads de travail et une autre qui peut créer des threads d’interface utilisateur ou des threads de travail. Pour démarrer votre thread d’interface utilisateur, appelez la deuxième surcharge de [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), fournissant les informations suivantes :  
  
- Le [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) de la classe dérivée à partir de `CWinThread`.  
  
- (Facultatif) Le niveau de priorité souhaité. La valeur par défaut est une priorité normale. Pour plus d’informations sur les niveaux de priorité disponibles, consultez [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) dans le SDK Windows.  
  
- (Facultatif) La taille de pile pour le thread. La valeur par défaut est la même taille de pile du thread parent.  
  
- (Facultatif) CREATE_SUSPENDED si vous souhaitez que le thread peut être créé dans un état suspendu. La valeur par défaut est 0, ou démarrez le thread normalement.  
  
- (Facultatif) Les attributs de sécurité souhaité. La valeur par défaut est le même accès que le thread parent. Pour plus d’informations sur le format de ces informations de sécurité, consultez [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) dans le SDK Windows.  
  
`AfxBeginThread` effectue l’essentiel du travail pour vous. Elle crée un nouvel objet de votre classe, l’initialise avec les informations que vous fournissez et appelle [CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread) pour démarrer l’exécution du thread. S’assurer que tous les objets sont libérés correctement doit échouer de n’importe quelle partie de la création, les vérifications sont effectuées tout au long de la procédure.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
- [Multithreading : arrêt d’exécution des threads](../parallel/multithreading-terminating-threads.md)  
  
- [Multithreading : création de threads de travail](../parallel/multithreading-creating-worker-threads.md)  
  
- [Processus et Threads](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## <a name="see-also"></a>Voir aussi  
 
[Multithreading à l’aide de C++ et de MFC](../parallel/multithreading-with-cpp-and-mfc.md)