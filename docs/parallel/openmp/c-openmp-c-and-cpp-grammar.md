---
description: 'En savoir plus sur : C. OpenMP C et grammaire C++'
title: C. Grammaire OpenMP C et C++
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 9543d721afbff1069b5497ba8dc7092089a1b706
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342502"
---
# <a name="c-openmp-c-and-c-grammar"></a>C. Grammaire OpenMP C et C++

[C.1 Notation](#c1-notation)<br/>
[C.2 Règles](#c2-rules)

## <a name="c1-notation"></a>C.1 Notation

Les règles de grammaire se composent du nom d’un non-terminal, suivi d’un signe deux-points, puis d’alternatives de remplacement sur des lignes distinctes.

Le terme «<sub>OPT</sub> » de l’expression syntaxique indique que le terme est facultatif dans le remplacement.

L’expression syntaxique *terme*<sub>optseq</sub> est équivalente à *term-SEQ*<sub>OPT</sub> avec les règles supplémentaires suivantes :

*terme-SEQ*:  
&nbsp;&nbsp;&nbsp;&nbsp;*terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;terme *-Seq* *terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*terme-SEQ* `,` *terme*   

## <a name="c2-rules"></a>C.2 Règles

La notation est décrite dans la section 6,1 de la norme C. Cette annexe de la grammaire montre les extensions de la grammaire du langage de base pour les directives C et C++ OpenMP.

**/\* en C++ (ISO/IEC 14882:1998) \*/**

*instruction-SEQ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*gestion*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction-Seq (instruction)*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction-SEQ OpenMP-directive*

**/\* dans C90 (ISO/IEC 9899:1990) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*gestion*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction-List, instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction-List OpenMP-directive*

**/\* dans C99 (ISO/IEC 9899:1999) \*/**

*bloc-élément*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaré*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*gestion*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP-directive*

**/\* instructions standard \*/**

*instruction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP-construction*

*OpenMP-construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction parallèle*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for-Construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sections-construction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction unique*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parallel-for-construction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction de sections parallèles*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction maître*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critique-construction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Atomic-construction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ordered-Construct*

*OpenMP-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrière-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Flush-directive*

*bloc structuré*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*gestion*

*construction parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de directives parallèles*

*Parallel-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel`*nouvelle ligne* de la *clause parallèle*<sub>optseq</sub>

*clause parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-clause Parallel*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Data-clause*

*unique-clause parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (`*expression*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (`*expression*   `)`

*pour-construire*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction for-directive Iteration*

*pour-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for`*New-Line* <sub>optseq</sub> *de clause for*

*clause for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*unique-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (`*type de planification*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (`*type* `,` de planification *expression*      `)`

*type de planification*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*sections-construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sections-section de directive-portée*

*sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections`*sections-clause*<sub>optseq</sub> *New-Line*

*sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*portée de la section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{section-Sequence}*

*section-séquence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-directive*<sub>OPT</sub> *Structured-Block*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-section Sequence-directive Structured-Block*

*section-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section`*nouvelle ligne*

*construction unique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré à directive unique*

*directive unique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single`*New-Line* <sub>optseq</sub> à *une seule clause*

*une seule clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*parallèle-pour-construire*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parallel-for-directive Iteration-instruction*

*Parallel-for-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for`*Parallel-for-clause*<sub>optseq</sub> *New-Line*

*Parallel-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-clause Parallel*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Data-clause*

*construction de sections parallèles*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section Parallel-sections-directive-portée*

*Parallel-sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections`*Parallel-sections-clause*<sub>optseq</sub> *New-Line*

*clauses Parallel-sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-clause Parallel*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Data-clause*

*construction principale*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*maître-bloc structuré par directive*

*Master-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master`*nouvelle ligne*

*critique-construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Critical-directive, bloc structuré*

*critique-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical`*Region-expression-*<sub></sub> *nouvelle ligne* opt

*Region-phrase*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*

*barrière-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier`*nouvelle ligne*

*construction atomique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Atomic-directive, expression-instruction*

*Atomic-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic`*nouvelle ligne*

*flush-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush`*flush-var-*<sub></sub> option *de nouvelle ligne*

*variables de vidage*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(liste de variables)*

*ordonné-construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ordered-directive, bloc structuré*

*ordered-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered`*nouvelle ligne*

**/\* déclarations standard \*/**

*déclaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate-directive*

*threadprivate-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (`*liste* `)` de variables *nouvelle ligne*    

*clause de données*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (`*liste de variables*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *liste de variables*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *liste de variables*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (`*liste de variables*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (`*liste de variables*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *Reduction-, opérateur* `:` *liste de variables*          `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *liste de variables*    `)`

*opérateur de réduction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;L’un des éléments suivants :   `+ \* - & ^ | && ||`

**/\* en C \*/**

*liste de variables*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste* `,` de variables *identificateur*   

**/\* en C++ \*/**

*liste de variables*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ID-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste* `,` de variables *ID-expression*   
