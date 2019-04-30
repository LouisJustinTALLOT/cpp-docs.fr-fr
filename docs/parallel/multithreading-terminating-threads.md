---
title: 'Multithreading : Arrêt des Threads dans MFC'
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
ms.openlocfilehash: dd11f5db646e172d7ea2c2cc646841249d95ef31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407729"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Multithreading : Arrêt des Threads dans MFC

Deux situations normales provoquent un arrêt du thread : la fonction de contrôle se ferme ou le thread n’est pas autorisé à s’exécuter jusqu'à la fin. Si un traitement de texte utilise un thread pour l’impression en arrière-plan, la fonction de contrôle s’arrêtera normalement si l’impression se termine avec succès. Si l’utilisateur souhaite annuler l’impression, toutefois, le thread d’impression en arrière-plan doit être arrêté avant terme. Cette rubrique explique comment implémenter chaque situation et comment obtenir le code de sortie d’un thread qui se termine.

- [Arrêt du Thread normal](#_core_normal_thread_termination)

- [Arrêt d’exécution prématuré d’un Thread](#_core_premature_thread_termination)

- [La récupération du Code de sortie d’un Thread](#_core_retrieving_the_exit_code_of_a_thread)

##  <a name="_core_normal_thread_termination"></a> Arrêt du Thread normal

Un thread de travail, l’arrêt du thread normal est simple : Quittez la fonction de contrôle et retournent une valeur qui indique la raison de l’arrêt. Vous pouvez utiliser la [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) fonction ou un **retourner** instruction. En règle générale, 0 signifie l’achèvement réussi, mais vous revient.

Pour un thread d’interface utilisateur, le processus est tout aussi simple : dans le thread d’interface utilisateur, appelez [PostQuitMessage](/windows/desktop/api/winuser/nf-winuser-postquitmessage) dans le SDK Windows. Le seul paramètre qui `PostQuitMessage` accepte est le code de sortie du thread. Comme pour les threads de travail, 0 signifie généralement un achèvement réussi.

##  <a name="_core_premature_thread_termination"></a> Arrêt d’exécution prématuré d’un Thread

Fin prématurée d’un thread est presque aussi simple : Appelez [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) à partir du thread. Passez le code de sortie voulu comme seul paramètre. Cela arrête l’exécution du thread, libère la pile du thread, déconnecte toutes les DLL attachés au thread et supprime l’objet thread à partir de la mémoire.

`AfxEndThread` Doit être appelée depuis le thread à arrêter. Si vous souhaitez terminer un thread à partir d’un autre thread, vous devez configurer une méthode de communication entre les deux threads.

##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> La récupération du Code de sortie d’un Thread

Pour obtenir le code de sortie de travail ou le thread d’interface utilisateur, appelez le [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) (fonction). Pour plus d’informations sur cette fonction, consultez le Kit de développement Windows. Cette fonction prend le handle du thread (stocké dans le `m_hThread` membre de données de `CWinThread` objets) et l’adresse d’un DWORD.

Si le thread est toujours actif, `GetExitCodeThread` place STILL_ACTIVE dans l’adresse DWORD fournie ; sinon, le code de sortie est placé dans cette adresse.

La récupération du code de sortie de [CWinThread](../mfc/reference/cwinthread-class.md) objets prend une étape supplémentaire. Par défaut, quand un `CWinThread` thread se termine, l’objet thread est supprimé. Cela signifie que vous ne pouvez pas accéder à la `m_hThread` membre de données, car le `CWinThread` objet n’existe plus. Pour éviter cette situation, effectuez l’une des opérations suivantes :

- Définir le `m_bAutoDelete` données membres à FALSE. Cela permet la `CWinThread` objet pour survivre pendant une fois que le thread a été arrêté. Vous pouvez ensuite accéder à la `m_hThread` membre de données une fois que le thread a été arrêté. Si vous utilisez cette technique, toutefois, vous êtes responsable de la destruction de le `CWinThread` de l’objet, car le framework ne le supprimera pas automatiquement pour vous. Il s’agit de la méthode préférée.

- Store le handle du thread séparément. Une fois que le thread est créé, copiez son `m_hThread` membre de données (à l’aide de `::DuplicateHandle`) à une autre variable et accédez-y en utilisant cette variable. L’objet est ainsi supprimé automatiquement dès son achèvement et vous pouvez toujours savoir pourquoi le thread s’est arrêté. Veillez à ce que le thread ne se termine pas avant que vous pouvez dupliquer le handle. La méthode la plus sûre consiste à passer CREATE_SUSPENDED à [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), stocker le handle, puis de reprendre le thread en appelant [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).

Soit la méthode vous permet de savoir pourquoi un `CWinThread` objet s’est arrêté.

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread)
