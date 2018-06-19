---
title: 'Multithreading : Arrêt d’exécution Threads | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
dev_langs:
- C++
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdf9376e9f8c9e9d74d88d0bef40dc71fd43d51f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689582"
---
# <a name="multithreading-terminating-threads"></a>Multithreading : arrêt d'exécution des threads
Deux situations normales provoquent un arrêt du thread : la fonction de contrôle s’arrête ou que le thread n’est pas autorisé à s’exécuter jusqu'à la fin. Si un traitement de texte utilise un thread pour l’impression en arrière-plan, la fonction de contrôle s’arrêtera normalement si l’impression terminée. Si l’utilisateur souhaite annuler l’impression, toutefois, le thread d’impression en arrière-plan doit s’est arrêté prématurément. Cette rubrique explique comment implémenter chaque situation et comment obtenir le code de sortie d’un thread qui se termine.  
  
-   [Arrêt du Thread normal](#_core_normal_thread_termination)  
  
-   [Arrêt du Thread prématurée](#_core_premature_thread_termination)  
  
-   [La récupération du Code de sortie d’un Thread](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> Arrêt du Thread normal  
 Pour un thread de travail, l’arrêt d’exécution normal est simple : quitter la fonction de contrôle et de retourner une valeur qui indique la raison de l’arrêt. Vous pouvez utiliser la [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) fonction ou un `return` instruction. En règle générale, 0 signifie l’achèvement réussi, mais que vous revient.  
  
 Pour un thread d’interface utilisateur, le processus est tout aussi simple : dans le thread d’interface utilisateur, appelez [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Le seul paramètre qui **PostQuitMessage** prend est le code de sortie du thread. Comme pour les threads de travail, 0 signifie généralement réussite.  
  
##  <a name="_core_premature_thread_termination"></a> Arrêt du Thread prématurée  
 Fin prématurée d’un thread est presque aussi simple : appelez [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) à partir du thread. Passez le code de sortie souhaité comme seul paramètre. Cela arrête l’exécution du thread, libère la pile du thread, déconnecte toutes les DLL attachés au thread et supprime l’objet thread à partir de la mémoire.  
  
 `AfxEndThread` Doit être appelée depuis le thread peut être interrompue. Si vous souhaitez terminer un thread à partir d’un autre thread, vous devez configurer une méthode de communication entre les deux threads.  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> La récupération du Code de sortie d’un Thread  
 Pour obtenir le code de sortie de l’utilisateur ou le thread d’interface utilisateur, appelez le [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) (fonction). Pour plus d’informations sur cette fonction, consultez le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Cette fonction prend le handle du thread (stocké dans le `m_hThread` membre de données de `CWinThread` objets) et l’adresse d’un `DWORD`.  
  
 Si le thread est toujours actif, **GetExitCodeThread** place **STILL_ACTIVE** fourni `DWORD` adresse ; sinon, le code de sortie est placé dans cette adresse.  
  
 Le code de sortie de la récupération des [CWinThread](../mfc/reference/cwinthread-class.md) objets prend une étape supplémentaire. Par défaut, lorsqu’un `CWinThread` thread se termine, l’objet thread est supprimé. Cela signifie que vous ne pouvez pas accéder à la `m_hThread` membre de données, car le `CWinThread` objet n’existe plus. Pour éviter cette situation, effectuez l’une des opérations suivantes :  
  
-   Définir le `m_bAutoDelete` membre de données **FALSE**. Cela permet la `CWinThread` objet survivre à une fois que le thread a été arrêté. Vous pouvez accéder à la `m_hThread` membre de données une fois que le thread a été arrêté. Si vous utilisez cette technique, toutefois, vous êtes responsable de la destruction de le `CWinThread` de l’objet, car le framework ne le supprimera pas automatiquement pour vous. Il s’agit de la méthode recommandée.  
  
-   Stocker le handle du thread séparément. Une fois que le thread est créé, copiez son `m_hThread` membre de données (à l’aide de **:: DuplicateHandle**) à une autre variable et d’y accéder via cette variable. L’objet est ainsi supprimé automatiquement lors de l’arrêt se produit et vous pouvez toujours savoir pourquoi le thread s’est arrêté. Veillez à ce que le thread s’arrête avant que vous pouvez dupliquer le handle. La méthode la plus sûre consiste à passer **CREATE_SUSPENDED** à [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), stocker le handle, puis de reprendre le thread en appelant [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).  
  
 Soit la méthode vous permet de déterminer la raison pour laquelle un `CWinThread` objet terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C++ et MFC](../parallel/multithreading-with-cpp-and-mfc.md)   
 [_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
 [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)