---
description: 'En savoir plus sur : extension SIMD'
title: Extension SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 58a3f29002c4e517a2019454dfe741dfb5352a3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342424"
---
# <a name="simd-extension"></a>Extension SIMD

Visual C++ prend actuellement en charge la norme OpenMP 2,0, mais Visual Studio 2019 offre désormais également une fonctionnalité SIMD.

> [!NOTE]
> Pour utiliser SIMD, compilez avec le `-openmp:experimental` commutateur qui active les fonctionnalités OpenMP supplémentaires qui ne sont pas disponibles lors de l’utilisation du `-openmp` commutateur.
>
> Le `-openmp:experimental` commutateur subsumes `-openmp` , ce qui signifie que toutes les fonctionnalités OpenMP 2,0 sont incluses dans son utilisation.

Pour plus d’informations, consultez [extension SIMD pour l’OpenMP C++ dans Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP SIMD dans Visual C++

OpenMP SIMD, introduit dans la norme OpenMP 4,0, cible la création de boucles vectorielles. En utilisant la `simd` directive avant une boucle, le compilateur peut ignorer les dépendances vectorielles, rendre la boucle aussi conviviale que possible et respecter l’intention des utilisateurs d’avoir plusieurs itérations de boucle exécutées simultanément.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ fournit des pragmas de boucle non OpenMP similaires comme `#pragma vector` et `#pragma ivdep` , mais avec OpenMP SIMD, le compilateur peut faire plus, comme :

- Toujours autorisé à ignorer les dépendances de vecteur actuelles.
- `/fp:fast` est activé dans la boucle.
- Les boucles externes et les boucles avec les appels de fonction sont compatibles avec les vecteurs.
- Les boucles imbriquées peuvent être fusionnées en une seule boucle et devenir conviviales.
- Accélération hybride avec `#pragma omp for simd` pour activer le multithreading et les vecteurs affinés à granularité grossière.  

Pour les boucles tactiles vectorielles, le compilateur reste en mode silencieux, sauf si vous utilisez un commutateur de journal de support vectoriel :

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Pour les boucles non vectorielles, le compilateur émet chaque message :

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Clauses

La directive d’OpenMP SIMD peut également prendre les clauses suivantes pour améliorer la prise en charge de vector :

|Directive|Description|
|---|---|
|`simdlen(length)`|Spécifiez le nombre de couloirs vectoriels.|
|`safelen(length)`|Spécifiez la distance de dépendance vectorielle.|
|`linear(list[ : linear-step]`)|Mappage linéaire de la variable d’induction de boucle à l’abonnement de tableau.|
|`aligned(list[ : alignment])`|Alignement des données.|
|`private(list)`|Spécifiez la privatisation des données.|
|`lastprivate(list)`|Spécifiez la privatisation des données avec la valeur finale de la dernière itération.|
|`reduction(reduction-identifier:list)`|Spécifiez des opérations de réduction personnalisées.|
|`collapse(n)`|Imbrication de la boucle de fusion.|

> [!NOTE]
> Les clauses SIMD non efficaces sont analysées et ignorées par le compilateur avec un avertissement.
>
> Par exemple, l’utilisation du code suivant émet un avertissement :
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>Exemple
  
La directive d’OpenMP SIMD fournit aux utilisateurs un moyen de dicter les boucles de création de boucles avec des vecteurs. En annotant une boucle avec la directive d’OpenMP SIMD, les utilisateurs envisagent d’exécuter simultanément plusieurs itérations de boucle.

Par exemple, la boucle suivante est annotée avec la directive d’OpenMP SIMD. Il n’existe pas de parallélisme parfait parmi les itérations de boucle puisqu’il y a une dépendance descendante entre un [i] et un [i-1], mais en raison de la directive SIMD, le compilateur est toujours autorisé à compresser des itérations consécutives de la première instruction dans une instruction vectorielle et à les exécuter en parallèle.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Par conséquent, la forme vectorielle transformée suivante de la boucle est **conforme** car le compilateur conserve le comportement séquentiel de chaque itération de boucle d’origine. En d’autres termes, `a[i]` est exécuté après `a[-1]` , `b[i]` est après `a[i]` et l’appel à `bar` se produit en dernier.

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

Il **n’est pas légal** de déplacer la référence `*c` de mémoire en dehors de la boucle si elle peut être un alias avec `a[i]` ou `b[i]` . Il n’est pas non plus légal de réorganiser les instructions à l’intérieur d’une itération d’origine si elle interrompt la dépendance séquentielle. Par exemple, la boucle transformée suivante n’est pas légale :

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>Voir aussi

[/OpenMP (activer la prise en charge d’OpenMP 2,0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
