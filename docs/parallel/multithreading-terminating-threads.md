---
title: 'Multithreading : Arrêter des threads dans MFC'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
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
ms.openlocfilehash: 97a99eb2382c4864f1bd8cc881fab5e32a1e2070
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511711"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Multithreading : Arrêter des threads dans MFC

Deux situations normales entraînent l’arrêt d’un thread: la fonction de contrôle se termine ou le thread n’est pas autorisé à s’exécuter jusqu’à la fin. Si un traitement de texte a utilisé un thread pour l’impression en arrière-plan, la fonction de contrôle s’arrête normalement si l’impression s’est terminée avec succès. Toutefois, si l’utilisateur souhaite annuler l’impression, le thread d’impression en arrière-plan doit se terminer prématurément. Cette rubrique explique à la fois comment implémenter chaque situation et comment obtenir le code de sortie d’un thread après son arrêt.

- [Arrêt normal du thread](#_core_normal_thread_termination)

- [Fin prématurée du thread](#_core_premature_thread_termination)

- [Récupération du code de sortie d’un thread](#_core_retrieving_the_exit_code_of_a_thread)

##  <a name="_core_normal_thread_termination"></a>Arrêt normal du thread

Pour un thread de travail, l’arrêt de thread normal est simple: Quittez la fonction de contrôle et retournez une valeur qui indique la raison de l’arrêt. Vous pouvez utiliser la fonction [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) ou une instruction **Return** . En règle générale, 0 signifie que l’opération a réussi, mais c’est à vous de vous.

Pour un thread d’interface utilisateur, le processus est tout aussi simple: depuis le thread d’interface utilisateur, appelez [PostQuitMessage](/windows/win32/api/winuser/nf-winuser-postquitmessage) dans le SDK Windows. Le seul paramètre qui `PostQuitMessage` accepte est le code de sortie du thread. Comme pour les threads de travail, la valeur 0 signifie généralement que l’opération est terminée correctement.

##  <a name="_core_premature_thread_termination"></a>Fin prématurée du thread

L’arrêt d’un thread prématurément est presque aussi simple: Appelez [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) à partir du thread. Transmettez le code de sortie souhaité comme seul paramètre. Cela arrête l’exécution du thread, libère la pile du thread, détache toutes les dll attachées au thread, puis supprime l’objet thread de la mémoire.

`AfxEndThread`doit être appelé à partir du thread à arrêter. Si vous souhaitez terminer un thread d’un autre thread, vous devez configurer une méthode de communication entre les deux threads.

##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a>Récupération du code de sortie d’un thread

Pour récupérer le code de sortie du thread de travail ou de l’interface utilisateur, appelez la fonction [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) . Pour plus d’informations sur cette fonction, consultez la SDK Windows. Cette fonction prend le handle du thread (stocké dans le `m_hThread` membre de données `CWinThread` des objets) et l’adresse d’une valeur DWORD.

Si le thread est toujours actif, `GetExitCodeThread` place STILL_ACTIVE dans l’adresse DWORD fournie; sinon, le code de sortie est placé dans cette adresse.

La récupération du code de sortie des objets [CWinThread](../mfc/reference/cwinthread-class.md) prend une étape supplémentaire. Par défaut, lorsqu’un `CWinThread` thread se termine, l’objet thread est supprimé. Cela signifie que vous ne pouvez `m_hThread` pas accéder au membre `CWinThread` de données, car l’objet n’existe plus. Pour éviter cette situation, effectuez l’une des opérations suivantes:

- Affectez `m_bAutoDelete` la valeur false au membre de données. Cela permet à `CWinThread` l’objet de survivre après l’arrêt du thread. Vous pouvez ensuite accéder au `m_hThread` membre de données une fois que le thread a été arrêté. Toutefois, si vous utilisez cette technique, vous êtes responsable de la destruction `CWinThread` de l’objet, car l’infrastructure ne le supprimera pas automatiquement pour vous. Il s’agit de la méthode recommandée.

- Stocke le handle du thread séparément. Une fois le thread créé, copiez `m_hThread` son membre de données `::DuplicateHandle`(à l’aide de) vers une autre variable et accédez-y par le biais de cette variable. De cette façon, l’objet est automatiquement supprimé lorsque l’arrêt se produit et vous pouvez toujours déterminer la raison pour laquelle le thread s’est arrêté. Veillez à ce que le thread ne se termine pas avant de pouvoir dupliquer le descripteur. La méthode la plus sûre consiste à passer CREATE_SUSPENDED à [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), à stocker le handle, puis à reprendre le thread en appelant [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).

L’une ou l’autre méthode vous permet `CWinThread` de déterminer la raison de l’arrêt d’un objet.

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
