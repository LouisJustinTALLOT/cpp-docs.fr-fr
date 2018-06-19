---
title: 'Multithreading : Création de Threads d’Interface utilisateur | Documents Microsoft'
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
ms.openlocfilehash: 480839316cc8d47b2af4be1cd81c0d02f09fad25
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688867"
---
# <a name="multithreading-creating-user-interface-threads"></a>Multithreading : création de threads d'interface utilisateur
Un thread d’interface utilisateur est généralement utilisé pour gérer l’entrée d’utilisateur et répondre aux événements utilisateur indépendamment des threads exécutant d’autres parties de l’application. Le thread d’application principal (fourni dans votre `CWinApp`-classe dérivée) est déjà créé et lancé pour vous. Cette rubrique décrit les étapes nécessaires à la création de threads d’interface utilisateur supplémentaires.  
  
 La première chose que vous devez effectuer lors de la création d’un thread d’interface utilisateur est de dériver une classe de [CWinThread](../mfc/reference/cwinthread-class.md). Vous devez déclarer et implémenter cette classe, à l’aide de la [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) et [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) macros. Cette classe doit substituer certaines fonctions et peut remplacer d’autres. Ces fonctions et leur finalité sont présentées dans le tableau suivant.  
  
### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Fonctions à substituer lors de la création d’un Thread d’Interface utilisateur  
  
|Fonction|Objectif|  
|--------------|-------------|  

|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)| Effectuer un nettoyage lorsque le thread s’arrête. Est généralement substituée. |  
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)| Effectuer une initialisation d’instance de thread. Doit être substitué. |  
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)| Effectuer le traitement des temps d’inactivité spécifique au thread. Est généralement pas substituée. |  
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)| Filtre les messages avant qu’ils sont distribués à **TranslateMessage** et **DispatchMessage**. Est généralement pas substituée. |  
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)| Intercepter des exceptions non gérées levées par les gestionnaires de commandes et de messages du thread. Est généralement pas substituée. |  
|[Exécutez](../mfc/reference/cwinthread-class.md#run)| Fonction de contrôle pour le thread. Contient la pompe de messages. Substitution rarement. |  

  
 MFC fournit deux versions de `AfxBeginThread` via la surcharge de paramètres : un qui peut uniquement créer des threads de travail et l’autre qui peut créer des threads d’interface utilisateur ou des threads de travail. Pour démarrer votre thread d’interface utilisateur, appelez la deuxième surcharge de [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), fournissant les informations suivantes :  
  
-   Le [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) de la classe dérivée à partir de `CWinThread`.  
  
-   (Facultatif) Niveau de priorité souhaité. La valeur par défaut est une priorité normale. Pour plus d’informations sur les niveaux de priorité disponibles, consultez [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
-   (Facultatif) La taille de pile du thread. La valeur par défaut est la même taille de pile en tant que le thread de création.  
  
-   (Facultatif) **CREATE_SUSPENDED** si vous souhaitez que le thread peut être créé dans un état suspendu. La valeur par défaut est 0, ou démarrez le thread normalement.  
  
-   (Facultatif) Les attributs de sécurité souhaité. La valeur par défaut est le même accès que le thread parent. Pour plus d’informations sur le format de ces informations de sécurité, consultez [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread` effectue la plupart du travail pour vous. Elle crée un nouvel objet de votre classe, l’initialise avec les informations que vous fournissez et appelle [CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread) pour démarrer l’exécution du thread. Vérifications sont effectuées dans l’ensemble de la procédure pour vous assurer que tous les objets sont libérés correctement n’importe quelle partie de la création échoue.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Multithreading : arrêt d’exécution des threads](../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading : création de threads de travail](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Processus et Threads](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C++ et de MFC](../parallel/multithreading-with-cpp-and-mfc.md)