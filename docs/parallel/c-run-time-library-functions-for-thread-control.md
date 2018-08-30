---
title: Les fonctions C Run-Time Library pour le contrôle de Thread | Microsoft Docs
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
ms.openlocfilehash: 6a0e57931b7f2af3f6232f140fd38155cfa5b2f8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195233"
---
# <a name="c-run-time-library-functions-for-thread-control"></a>Fonctions des bibliothèques Runtime C pour le contrôle des threads
Tous les programmes Win32 ont au moins un thread. N’importe quel thread peut créer des threads supplémentaires. Un thread peut effectuer son travail rapidement, puis se ferme, ou il peut rester actif pendant la durée de vie du programme.  
  
Les bibliothèques Runtime C LIBCMT et MSVCRT fournissent les fonctions suivantes pour la création de threads et l’arrêt : [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) et [_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).  
  
Le `_beginthread` et `_beginthreadex` fonctions créer un nouveau thread et retourner un identificateur de thread si l’opération a réussi. Le thread s’arrête automatiquement si elle a été exécutée ou qu’il puisse se terminer par un appel à `_endthread` ou `_endthreadex`.  
  
> [!NOTE]
> Si vous vous apprêtez à appeler des routines du runtime C à partir d’un programme créé à l’aide de Libcmt.lib, vous devez démarrer vos threads avec le `_beginthread` ou `_beginthreadex` (fonction). N’utilisez pas les fonctions Win32 `ExitThread` et `CreateThread`. À l’aide de `SuspendThread` peut entraîner un blocage quand plusieurs threads est bloqué en attente pour le thread suspendu terminer son accès à une structure de données d’exécution C.  
  
##  <a name="_core_the__beginthread_function"></a> Les fonctions _beginthread et _beginthreadex  
 
Le `_beginthread` et `_beginthreadex` fonctions créent un nouveau thread. Un thread partage les segments de code et les données d’un processus avec d’autres threads du processus, mais possède ses propres valeurs de registres uniques, espace de pile et adresse d’instruction en cours. Le système donne le temps processeur pour chaque thread, afin que tous les threads dans un processus pouvant s’exécuter simultanément.  
  
`_beginthread` et `_beginthreadex` sont similaires à la [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) fonction dans l’API Win32, mais elles présente les différences :  
  
- Ils initialisent certaines variables de la bibliothèque Runtime C. Ceci est important uniquement si vous utilisez la bibliothèque Runtime C dans vos threads.  
  
- `CreateThread` aide à fournit un contrôle sur les attributs de sécurité. Vous pouvez utiliser cette fonction pour démarrer un thread dans un état suspendu.  
  
 `_beginthread` et `_beginthreadex` retourne un handle pour le nouveau thread en cas de réussite ou un code d’erreur si une erreur s’est produite.  
  
##  <a name="_core_the__endthread_function"></a> Les fonctions _endthread et _endthreadex  
 
Le [_endthread](../c-runtime-library/reference/endthread-endthreadex.md) fonction met fin à un thread créé par `_beginthread` (de la même manière, `_endthreadex` termine un thread créé par `_beginthreadex`). Les threads s’arrêtent automatiquement lorsqu’ils ont terminé. `_endthread` et `_endthreadex` sont utiles pour un arrêt conditionnel dans un thread. Par exemple, un thread dédié au traitement des communications, peut quitter s’il est impossible d’obtenir le contrôle du port de communication.  
  
## <a name="see-also"></a>Voir aussi  
 
[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)