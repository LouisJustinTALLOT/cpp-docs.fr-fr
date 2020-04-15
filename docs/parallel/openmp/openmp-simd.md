---
title: Extension SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 0a7f1142a3a432628795341f4885b76a5c144990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366454"
---
# <a name="simd-extension"></a>Extension SIMD

Visual CMD prend actuellement en charge la norme OpenMP 2.0, mais Visual Studio 2019 offre également maintenant des fonctionnalités SIMD.

> [!NOTE]
> Pour utiliser SIMD, compilez avec le `-openmp:experimental` commutateur qui permet `-openmp` des fonctionnalités OpenMP supplémentaires non disponibles lors de l’utilisation de l’interrupteur.
>
> Le `-openmp:experimental` commutateur `-openmp`sous-umes , ce qui signifie que toutes les fonctionnalités OpenMP 2.0 sont inclus dans son utilisation.

Pour plus d’informations, voir [l’extension SIMD à L’OpenMP de CMD dans Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP SIMD dans Visual C

OpenMP SIMD, introduit dans la norme OpenMP 4.0, cible les boucles vectorielles. En utilisant `simd` la directive avant une boucle, le compilateur peut ignorer les dépendances vectorielles, rendre la boucle aussi vectorielle que possible, et respecter l’intention des utilisateurs de faire exécuter simultanément plusieurs itérations en boucle.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual CMD fournit des pragmas en `#pragma vector` boucle `#pragma ivdep`similaires non OpenMP comme et, cependant avec OpenMP SIMD, le compilateur peut faire plus, comme:

- Toujours autorisé à ignorer les dépendances actuelles vectorielles.
- `/fp:fast`est activé dans la boucle.
- Les boucles extérieures et les boucles avec les appels de fonction sont vectorielles.
- Les boucles imbriquées peuvent être fusionnées en une seule boucle et rendues vectorielles.
- Accélération hybride `#pragma omp for simd` avec pour permettre des vecteurs à grains multiples grossiers et à grain fin.  

Pour les boucles vectorielles, le compilateur reste silencieux à moins d’utiliser un interrupteur de journal vectoriel :

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Pour les boucles non-vectorielles, le compilateur émet chacun un message :

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Clauses

La directive SIMD OpenMP peut également prendre les clauses suivantes pour renforcer le soutien vectoriel :

|Directive|Description|
|---|---|
|`simdlen(length)`|Spécifier le nombre de voies vectorielles.|
|`safelen(length)`|Spécifier la distance de dépendance vectorielle.|
|`linear(list[ : linear-step]`)|La cartographie linéaire de la variable d’induction de boucle à l’abonnement de tableau.|
|`aligned(list[ : alignment])`|L’alignement des données.|
|`private(list)`|Spécifier la privatisation des données.|
|`lastprivate(list)`|Spécifier la privatisation des données avec la valeur finale de la dernière itération.|
|`reduction(reduction-identifier:list)`|Spécifier les opérations de réduction personnalisées.|
|`collapse(n)`|Nid de boucle de fusion.|

> [!NOTE]
> Les clauses SIMD non efficaces sont analysées et ignorées par le compilateur avec un avertissement.
>
> Par exemple, l’utilisation du code suivant émet un avertissement :
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
  
La directive SimD OpenMP offre aux utilisateurs un moyen de dicter le compilateur faire des boucles vectorielles. En annotant une boucle avec la directive SIMD OpenMP, les utilisateurs ont l’intention d’avoir plusieurs itérations en boucle exécutées simultanément.

Par exemple, la boucle suivante est annotée avec la directive SIMD OpenMP. Il n’y a pas de parallélisme parfait parmi les itérations en boucle puisqu’il y a une dépendance rétrograde d’un[i] à un[i-1], mais en raison de la directive SIMD, le compilateur est toujours autorisé à emballer les itérations consécutives de la première déclaration dans une instruction vectorielle et à les exécuter en parallèle.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Par conséquent, la forme vectorielle transformée suivante de la boucle est **légale** parce que le compilateur garde le comportement séquentiel de chaque itération de boucle originale. En d’autres `a[i]` termes, `a[-1]` `b[i]` est `a[i]` exécuté après `bar` , est après et l’appel à se produit en dernier.

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

Il n’est **pas légal** `*c` de déplacer la référence de `a[i]` `b[i]`mémoire hors de la boucle si elle peut alias avec ou . Il n’est pas non plus légal de réorganiser les déclarations à l’intérieur d’une itération originale si elle brise la dépendance séquentielle. Par exemple, la boucle transformée suivante n’est pas légale :

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
