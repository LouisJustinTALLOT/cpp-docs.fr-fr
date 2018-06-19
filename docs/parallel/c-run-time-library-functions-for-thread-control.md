---
title: Fonctions de bibliothèque C Run-Time pour le contrôle du Thread | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _beginthread function
- _endthread function
- threading [C++], controlling threads
- multithreading [C++], controlling threads
- _beginthreadex function
- _endthreadex function
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a505bae156edba6798812b807d7ab5c6ea9e396
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685760"
---
# <a name="c-run-time-library-functions-for-thread-control"></a>Fonctions des bibliothèques Runtime C pour le contrôle des threads
Tous les programmes Win32 ont au moins un thread. N’importe quel thread peut créer des threads supplémentaires. Un thread peut effectuer son travail rapidement, puis se ferme, ou elle peut rester actif pendant la durée de vie du programme.  
  
 Les bibliothèques Runtime C LIBCMT et MSVCRT fournissent les fonctions suivantes pour la création de threads et de l’arrêt : [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) et [_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).  
  
 Le `_beginthread` et `_beginthreadex` fonctions créer un nouveau thread et renvoyer un identificateur de thread si l’opération a réussi. Le thread s’arrête automatiquement si la fin de l’exécution, ou il peut se terminer par un appel à `_endthread` ou `_endthreadex`.  
  
> [!NOTE]
>  Si vous vous apprêtez à appeler des routines d’exécution C à partir d’un programme créé à l’aide de Libcmt.lib, vous devez démarrer vos threads avec le `_beginthread` ou `_beginthreadex` (fonction). N’utilisez pas les fonctions Win32 `ExitThread` et `CreateThread`. À l’aide de `SuspendThread` peut provoquer un blocage lorsque plus d’un thread est bloqué en attente pour le thread suspendu effectuer son accès à une structure de données d’exécution C.  
  
##  <a name="_core_the__beginthread_function"></a> Les fonctions _beginthread et _beginthreadex  
 Le `_beginthread` et `_beginthreadex` fonctions créer un nouveau thread. Un thread partage les segments de code et les données d’un processus avec les autres threads dans le processus, mais possède ses propres valeurs de registres uniques, espace de pile et adresse d’instruction en cours. Le système attribue le temps processeur pour chaque thread, afin que tous les threads dans un processus peuvent s’exécuter simultanément.  
  
 `_beginthread` et `_beginthreadex` sont similaires à la [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) fonction dans l’API Win32, mais elles présente les différences :  
  
-   Ils initialisent certaines variables de la bibliothèque Runtime C. Il est important que si vous utilisez la bibliothèque Runtime C dans vos threads.  
  
-   `CreateThread` aide à fournit un contrôle sur les attributs de sécurité. Vous pouvez utiliser cette fonction pour démarrer un thread dans un état suspendu.  
  
 `_beginthread` et `_beginthreadex` retourner un handle au nouveau thread en cas de réussite ou un code d’erreur si une erreur s’est produite.  
  
##  <a name="_core_the__endthread_function"></a> Les fonctions _endthread et _endthreadex  
 Le [_endthread](../c-runtime-library/reference/endthread-endthreadex.md) fonction met fin à un thread créé par `_beginthread` (de la même manière, `_endthreadex` met fin à un thread créé par `_beginthreadex`). Les threads s’arrêtent automatiquement lorsqu’ils ont terminé. `_endthread` et `_endthreadex` sont utiles pour un arrêt conditionnel dans un thread. Un thread dédié au traitement des communications, par exemple, peut quitter s’il est impossible d’obtenir le contrôle du port de communication.  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C et de Win32](../parallel/multithreading-with-c-and-win32.md)