---
title: 'Multithreading : Création de threads d’interface utilisateur MFC'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: 1cd28a848f9be223f43412c3e0f3961cef9db6c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512088"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>Multithreading : Création de threads d’interface utilisateur MFC

Un thread d’interface utilisateur est couramment utilisé pour gérer les entrées d’utilisateur et répondre aux événements utilisateur indépendamment des threads qui exécutent d’autres parties de l’application. Le thread d’application principal (fourni dans `CWinApp`votre classe dérivée de) est déjà créé et démarré pour vous. Cette rubrique décrit les étapes nécessaires à la création de threads d’interface utilisateur supplémentaires.

La première chose à faire lorsque vous créez un thread d’interface utilisateur est de dériver une classe de [CWinThread](../mfc/reference/cwinthread-class.md). Vous devez déclarer et implémenter cette classe à l’aide des macros [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) et [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) . Cette classe doit substituer certaines fonctions et peut substituer d’autres. Ces fonctions et ce qu’elles doivent faire sont présentés dans le tableau suivant.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Fonctions à substituer lors de la création d’un thread d’interface utilisateur

|Fonction|Objectif|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|Effectue un nettoyage lorsque le thread se termine. Généralement substitué.|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|Effectuer l’initialisation de l’instance de thread. Doit être substitué.|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|Effectue un traitement du temps d’inactivité spécifique au thread. Ce n’est généralement pas le cas.|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|Filtrer les messages avant leur distribution vers `TranslateMessage` et. `DispatchMessage` Ce n’est généralement pas le cas.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|Interceptez les exceptions non gérées levées par les gestionnaires de commandes et de messages du thread. Ce n’est généralement pas le cas.|
|[Exécuter](../mfc/reference/cwinthread-class.md#run)|Contrôle de la fonction pour le thread. Contient la pompe de messages. Rarement substitué.|

MFC fournit deux versions de `AfxBeginThread` via la surcharge des paramètres: une qui peut uniquement créer des threads de travail et une qui peut créer des threads d’interface utilisateur ou des threads de travail. Pour démarrer votre thread d’interface utilisateur, appelez la deuxième surcharge de [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), en fournissant les informations suivantes:

- [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) de la classe à partir `CWinThread`de laquelle vous avez dérivé.

- Facultatif Niveau de priorité souhaité. La valeur par défaut est la priorité normale. Pour plus d’informations sur les niveaux de priorité disponibles, consultez [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

- Facultatif Taille de pile souhaitée pour le thread. La valeur par défaut est la même pile de taille que le thread de création.

- Facultatif CREATE_SUSPENDED si vous souhaitez que le thread soit créé dans un état suspendu. La valeur par défaut est 0 ou démarre le thread normalement.

- Facultatif Attributs de sécurité souhaités. La valeur par défaut est le même accès que le thread parent. Pour plus d’informations sur le format de ces informations de sécurité, consultez [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

`AfxBeginThread`effectue la majeure partie du travail pour vous. Il crée un nouvel objet de votre classe, l’initialise avec les informations que vous fournissez et appelle [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread) pour démarrer l’exécution du thread. Les vérifications sont effectuées tout au long de la procédure pour s’assurer que tous les objets sont désalloués correctement en cas d’échec d’une partie de la création.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Multithreading : Arrêt de threads](multithreading-terminating-threads.md)

- [Multithreading : Création de threads de travail](multithreading-creating-worker-threads.md)

- [Processus et threads](/windows/win32/ProcThread/processes-and-threads)

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)
