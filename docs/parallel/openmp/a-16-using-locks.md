---
title: A.16 utilisation des verrous | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb901ab311221f1375bb5f3bfe7f996981e97a6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432748"
---
# <a name="a16---using-locks"></a>A.16   Utilisation des verrous

Dans l’exemple suivant, (pour [Section 3.2](../../parallel/openmp/3-2-lock-functions.md) page 41) Notez que l’argument pour les fonctions de verrouillage doit avoir type `omp_lock_t`, et qu’il n’est pas nécessaire de le videz.  Les fonctions de verrouillage entraînent les threads pour être inactif en attendant d’entrée à la première section critique, mais pour effectuer d’autres tâches en attendant d’entrée à la seconde.  Le `omp_set_lock` blocs de fonction, mais la `omp_test_lock` fonction est pas le cas, ce qui permet le travail dans skip() à faire.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```