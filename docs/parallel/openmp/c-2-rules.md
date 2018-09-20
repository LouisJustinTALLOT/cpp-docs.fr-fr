---
title: C.2 règles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c5845a9125bb32254fc0c03b03e9b6076a086d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404772"
---
# <a name="c2-rules"></a>C.2 Règles

La notation est décrite dans la section 6.1 de la norme C. Cette annexe grammaire montre les extensions à la grammaire du langage de base pour les directives OpenMP C et C++.

**/\* en C++ (ISO/IEC 14882:1998) \*/**

*instruction-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive OpenMP*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction de déclaration-seq*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*-modifier-seq instruction de la directive openmp*

**/\* dans C90 (9899 : 1990 de la norme ISO/IEC) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive OpenMP*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction de la liste d’instructions*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste d’instructions de la directive openmp*

**/\* dans C99 (ISO/IEC 9899 : 1999) \*/**

*élément de bloc*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Déclaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive OpenMP*

**/\* instructions standard \*/**

*instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction d’OpenMP*

*construction d’OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction parallèle*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction for*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction de sections*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction d’unique*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallèle de construction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction de sections parallèles*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction de master*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction Critical*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction atomic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construction commandée*

*la directive OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive Barrier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive Flush*

*bloc structuré*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instruction*

*construction parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive parallèle*

*la directive parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp parallel** *parallèle-clause*<sub>optseq</sub> *nouvelle ligne*

*clause parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause unique parallèle*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause de données*

*clause unique parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Si (** *expression* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**num_threads (** *expression* **)**

*construction for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’itération pour (directive)*

*pour directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp pour** *clause for*<sub>optseq</sub> *nouvelle ligne*

*clause for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique pour la clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause de données*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*unique pour la clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Commandée**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**planification (** *genre de planification* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**planification (** *genre de planification* **,** *expression* **)**

*genre de planification*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Dynamique**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**guidée**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Runtime**

*construction de sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive de sections section-étendue*

*directive de sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sections de # pragma omp** *sections-clause*<sub>optseq</sub> *nouvelle ligne*

*clause de sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause de données*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*étendue de la section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{séquence-section}*

*séquence de la section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive de section*<sub>opt</sub> *bloc structuré*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive de section section-séquence structuré par bloc.*

*directive de section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp section** *nouvelle ligne*

*unique-construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive unique*

*la directive unique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp unique** *à clause unique*<sub>optseq</sub> *nouvelle ligne*

*clause unique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause de données*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*parallèle pour construction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’itération parallèle de directive*

*parallèle pour directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp parallel pour** *parallèle-clause for*<sub>optseq</sub> *nouvelle ligne*

*parallèle-clause for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause unique parallèle*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique pour la clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause de données*

*construction de sections parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive parallèle-sections section-étendue*

*directive parallèle-sections*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sections de # pragma omp parallel** *parallèle-sections-clause*<sub>optseq</sub> *nouvelle ligne*

*clause de sections de parallèle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause unique parallèle*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*clause de données*

*construction de master*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive principale*

*la directive principale*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**maître de # pragma omp** *nouvelle ligne*

*construction Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de la directive Critical*

*la directive Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp critiques** *une expression de la région*<sub>opt</sub> *nouvelle ligne*

*une expression de la région*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identificateur)*

*la directive Barrier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**cloisonnement de # pragma omp** *nouvelle ligne*

*construction atomic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’expression directive atomic*

*directive atomic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp atomic** *nouvelle ligne*

*la directive Flush*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp vidage** *var de vidage*<sub>opt</sub> *nouvelle ligne*

*var de vidage*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(liste de variable)*

*construction classés*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloc structuré de directive commandée*

*la directive classés*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp classés** *nouvelle ligne*

**/\* déclarations standards \*/**

*declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*directive threadprivate*

*la directive threadprivate*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp threadprivate (** *variable-list***)** *nouvelle ligne* 

*clause de données*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**privé (** *variable-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyprivate (***variable-list***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**firstprivate (***variable-list***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**lastprivate (** *variable-list***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**partagé (** *variable-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**par défaut (partagé)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**par défaut (aucun)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**réduction (***opérateur de réduction***:***variable-list***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyin (***variable-list***)** 

*opérateur de réduction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Une des :  **+  \* -& ^ &#124; & &&#124;&#124;**

**/\* en C \*/**

*liste de la variable*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste de la variable* **,** *identificateur*

**/\* en C++ \*/**

*liste de la variable*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ID-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste de la variable* **,** *id-expression*