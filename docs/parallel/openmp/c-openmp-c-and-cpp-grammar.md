---
title: C. Grammaire OpenMP C et C++
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 85e18161079b49e83cc9fedb3184ee220c889e75
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397353"
---
# <a name="c-openmp-c-and-c-grammar"></a>C. Grammaire OpenMP C et C++

[C.1 Notation](#c1-notation)<br/>
[C.2 Règles](#c2-rules)

## <a name="c1-notation"></a>C.1 Notation

Les règles de grammaire se composent du nom pour un non terminaux, suivie du signe deux-points, suivi d’alternatives de remplacement sur des lignes distinctes.

Le terme d’expression syntaxique<sub>opt</sub> indique que le terme est facultatif dans le remplacement.

L’expression syntaxique *terme*<sub>optseq</sub> équivaut à *terme-seq*<sub>opt</sub> avec les règles supplémentaires suivantes :

*term-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*term*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq* *term*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq*   `,` *term*

## <a name="c2-rules"></a>C.2 Règles

La notation est décrite dans la section 6.1 de la norme C. Cette annexe grammaire montre les extensions à la grammaire du langage de base pour les directives OpenMP C et C++.

**/\* en C++ (ISO/IEC 14882:1998) \*/**

*instruction-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-seq statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*-modifier-seq instruction de la directive openmp*

**/\* dans C90 (9899 : 1990 de la norme ISO/IEC) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction de la liste d’instructions*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste d’instructions de la directive openmp*

**/\* dans C99 (ISO/IEC 9899 : 1999) \*/**

*block-item*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*

**/\* instructions standard \*/**

*instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-construct*

*construction d’OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*single-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ordered-construct*

*la directive OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrier-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*flush-directive*

*bloc structuré*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*

*construction parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive parallèle*

*la directive parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel` *parallel-clause*<sub>optseq</sub> *new-line*

*clause parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*clause unique parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (` *expression*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (` *expression*   `)`

*construction for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’itération pour (directive)*

*pour directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for` *for-clause*<sub>optseq</sub> *new-line*

*clause for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*unique pour la clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *schedule-kind*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *schedule-kind*   `,` *expression*   `)`

*genre de planification*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*construction de sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive de sections section-étendue*

*directive de sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections` *sections-clause*<sub>optseq</sub> *new-line*

*clause de sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*étendue de la section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{séquence-section}*

*séquence de la section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-directive*<sub>opt</sub> *structured-block*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive de section section-séquence structuré par bloc.*

*directive de section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section` *new-line*

*unique-construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive unique*

*la directive unique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single` *single-clause*<sub>optseq</sub> *new-line*

*clause unique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*parallèle pour construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’itération parallèle de directive*

*parallèle pour directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for` *parallel-for-clause*<sub>optseq</sub> *new-line*

*parallèle-clause for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*construction de sections parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive parallèle-sections section-étendue*

*directive parallèle-sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections` *parallel-sections-clause*<sub>optseq</sub> *new-line*

*clause de sections de parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*construction de master*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive principale*

*la directive principale*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master` *new-line*

*construction Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive Critical*

*la directive Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical` *region-phrase*<sub>opt</sub> *new-line*

*une expression de la région*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identifier)*

*la directive Barrier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier` *new-line*

*construction atomic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’expression directive atomic*

*directive atomic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic` *new-line*

*la directive Flush*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush` *flush-vars*<sub>opt</sub> *new-line*

*var de vidage*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(variable-list)*

*construction classés*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de directive commandée*

*la directive classés*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered` *new-line*

**/\* déclarations standards \*/**

*declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate-directive*

*la directive threadprivate*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (` *variable-list*    `)` *new-line*

*clause de données*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (` *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *reduction-operator*    `:`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *variable-list*    `)`

*opérateur de réduction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;L’une des :   `+ \* - & ^ | && ||`

**/\* en C \*/**

*liste de la variable*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *identifier*

**/\* en C++ \*/**

*liste de la variable*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*id-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *id-expression*
