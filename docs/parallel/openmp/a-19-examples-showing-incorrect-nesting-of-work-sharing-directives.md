---
title: A.19 exemples illustrant l’imbrication incorrecte de Directives de partage de travail | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cf9502fd17fced7a4bc2a208634b825443f196a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411519"
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19   Exemples illustrant l'imbrication incorrecte de directives de partage de travail

Les exemples de cette section illustrent les règles d’imbrication de directive. Pour plus d’informations sur l’imbrication de directives, consultez [Section 2.9](../../parallel/openmp/2-9-directive-nesting.md) sur page 33.

L’exemple suivant n’est pas conforme, car les intérieurs et extérieurs `for` directives sont imbriqués et les lier au même `parallel` directive :

```
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

La version dynamiquement imbriquée suivante de l’exemple précédent est également non conforme :

```
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

L’exemple suivant n’est pas conforme, car le `for` et `single` directives sont imbriqués, et ils sont liés à la même région parallèle :

```
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

L’exemple suivant n’est pas conforme, car un `barrier` directive à l’intérieur d’un `for` peut entraîner un blocage :

```
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

L’exemple suivant n’est pas conforme, car le `barrier` entraîne un blocage dû au fait que qu’un seul thread à la fois peut entrer dans la section critique :

```
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

L’exemple suivant n’est pas conforme, car le `barrier` entraîne un blocage dû au fait que seul un thread exécute le `single` section :

```
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```