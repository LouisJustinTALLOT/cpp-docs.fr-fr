---
title: Extension SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 52402aa553c6d68d3073aba26ecac7b784522ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363269"
---
# <a name="simd-extension"></a>Extension SIMD

Visual C++ prend actuellement en charge la norme OpenMP 2.0, mais Visual Studio 2019 offre désormais des fonctionnalités SIMD.

> [!NOTE]
> Pour utiliser SIMD, compilez avec le `-openmp:experimental` commutateur qui permet des fonctionnalités OpenMP supplémentaires non disponibles lorsque vous utilisez le `-openmp` basculer.
>
> Le `-openmp:experimental` commutateur absorbe `-openmp`, ce qui signifie que toutes les fonctionnalités d’OpenMP 2.0 sont incluses dans son utilisation.

Pour plus d’informations, consultez [Extension SIMD C++ OpenMP dans Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>SIMD OpenMP dans Visual c#C++

SIMD OpenMP, introduit dans 4.0 OpenMP standard, effectuer des boucles de vecteurs de cibles. À l’aide de la `simd` directive avant une boucle, le compilateur peut ignorer les dépendances vectorielles, vérifiez la boucle comme vecteur conviviale que possible et respecter l’intention des utilisateurs d’avoir plusieurs itérations de boucle exécutées simultanément.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ fournit des pragmas de boucle non OpenMP similaires telles que `#pragma vector` et `#pragma ivdep`, mais avec OpenMP SIMD, le compilateur peut effectuer plus d’informations, telles que :

- Toujours autorisé à ignorer les dépendances vectorielles présents.
- `/fp:fast` est activée dans la boucle.
- Boucles externes et les boucles avec les appels de fonction sont compatibles avec le vecteur.
- Boucles imbriquées peuvent être fusionnés dans une boucle et effectués des vecteurs.
- Accélération hybride avec `#pragma omp for simd` pour activer des vecteurs de multi-threads et affinées à granularité grossière.  

Pour les boucles de vecteurs, le compilateur reste en mode silencieux, sauf si vous utilisez un commutateur de journal vecteur-prise en charge :

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Pour les boucles non compatibles avec les vecteurs, le compilateur chacun émet un message :

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Clauses

La directive OpenMP SIMD accepte également les clauses suivantes pour améliorer la prise en charge de vecteur :

|Directive|Description|
|---|---|
|`simdlen(length)`|Spécifiez le nombre de couloirs de vecteur.|
|`safelen(length)`|Spécifiez la distance de dépendance de vecteur.|
|`linear(list[ : linear-step]`)|Le mappage linéaire à partir de la variable d’induction de boucle à l’abonnement de tableau.|
|`aligned(list[ : alignment])`|L’alignement des données.|
|`private(list)`|Spécifiez la privatisation de données.|
|`lastprivate(list)`|Spécifiez la privatisation de données avec la valeur finale à partir de la dernière itération.|
|`reduction(reduction-identifier:list)`|Spécifier les opérations de réduction personnalisé.|
|`collapse(n)`|Imbrication de boucle fusion.|

> [!NOTE]
> Clauses SIMD inefficace sont analysées et ignorés par le compilateur avec un avertissement.
>
> Par exemple, utiliser des problèmes de code suivants un avertissement :
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
  
La directive OpenMP SIMD fournit aux utilisateurs un moyen de dicter le compilateur marque boucles vecteur conviviale. En annotant une boucle avec la directive OpenMP SIMD, les utilisateurs envisagez d’exécuter plusieurs itérations de boucle exécutées simultanément.

Par exemple, la boucle suivante est annotée avec la directive OpenMP SIMD. Il est sans parallélisme parfait entre les itérations de boucle dans la mesure où il existe une dépendance vers l’arrière à partir d’un [i] [i-1], mais en raison de la directive SIMD que le compilateur est toujours autorisé à empaqueter des itérations consécutives de la première instruction dans une instruction de vecteur et exécuter les en parallèle.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Par conséquent, la forme de vecteur transformé suivante de la boucle est **juridique** , car le compilateur conserve le comportement séquentiel de chaque itération de boucle d’origine. En d’autres termes, `a[i]` est exécutée après `a[-1]`, `b[i]` est après `a[i]` et l’appel à `bar` se produit en dernier.

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

Il a **légales** pour déplacer la référence de la mémoire `*c` en dehors de la boucle si elle peut alias avec `a[i]` ou `b[i]`. Également, il n’est pas conforme à réorganiser les instructions à l’intérieur d’une itération d’origine si elle rompt la dépendance séquentielle. Par exemple, la boucle transformée suivante n’est pas légale :

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

[/openmp (Activer la prise en charge OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
