---
title: C.2 règles | Documents Microsoft
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
ms.openlocfilehash: a3bdf26435fdfeea2196b9ef281d656805f51bf2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694990"
---
# <a name="c2-rules"></a>C.2 Règles
La notation est décrite dans la section 6.1 de la norme C. Cette annexe grammaire montre les extensions à la grammaire du langage de base pour les directives OpenMP C et C++.  
  
 **/\* en C++ (ISO/IEC 14882:1998) \*/**  
  
 *instruction-seq*:  
  
 *statement*  
  
 *directive OpenMP*  
  
 *instruction-seq instruction*  
  
 *instruction-seq directive openmp*  
  
 **/\* dans C90 (9899 : 1990 de la norme ISO/IEC) \*/**  
  
 *statement-list*:  
  
 *statement*  
  
 *directive OpenMP*  
  
 *statement-list statement*  
  
 *liste d’instructions de la directive openmp*  
  
 **/\* dans C99 (ISO/IEC la 9899 : 1999) \*/**  
  
 *élément de bloc*:  
  
 *déclaration*  
  
 *statement*  
  
 *directive OpenMP*  
  
 *instruction* :  
  
 **/\* instructions standards \*/**  
  
 *construction d’OpenMP*  
  
 *construction d’OpenMP*:  
  
 *construction parallèle*  
  
 *construction for*  
  
 *construction de sections*  
  
 *construction d’unique*  
  
 *construction parallèle-for*  
  
 *construction de sections parallèles*  
  
 *construc de master*  
  
 *construction Critical*  
  
 *construction atomic*  
  
 *construction ordonnée*  
  
 *la directive OpenMP*:  
  
 *directive du cloisonnement*  
  
 *directive du vidage*  
  
 *bloc structuré*:  
  
 *statement*  
  
 *construction parallèle*:  
  
 *bloc structuré de directive parallèle*  
  
 *directive parallèle*:  
  
 **# pragma pragma omp parallel***parallèle-clause*optseq *nouvelle ligne*   
  
 *clause parallèle*:  
  
 *clause unique parallèle*  
  
 *clause de données*  
  
 *clause unique parallèle*:  
  
 **Si (** *expression* **)**  
  
 **num_threads (** *expression* **)**  
  
 *construction for*:  
  
 *instruction d’itération pour (directive)*  
  
 *pour la directive*:  
  
 **# pragma omp de pragma pour** *clause for*optseq *nouvelle ligne*  
  
 *clause for*:  
  
 *unique pour la clause*  
  
 *clause de données*  
  
 **nowait**  
  
 *unique pour la clause*:  
  
 **commandée**  
  
 **planification (** *genre de planification* **)**  
  
 **planification (** *genre de planification* **,** *expression* **)**  
  
 *type de planification*:  
  
 **static**  
  
 **dynamic**  
  
 **Interactive**  
  
 **Runtime**  
  
 *construction de sections*:  
  
 *directive de sections section-étendue*  
  
 *directive de sections*:  
  
 **sections de # pragma omp** *sections-clause*optseq *nouvelle ligne*  
  
 *clause de sections*:  
  
 *clause de données*  
  
 **nowait**  
  
 *étendue de la section*:  
  
 *{séquence-section}*  
  
 *séquence de la section*:  
  
 *directive de section*opt *bloc structuré*  
  
 *directive de section section séquence structuré par bloc.*  
  
 *directive de section*:  
  
 **# pragma omp section** *nouvelle ligne*  
  
 *construction d’unique*:  
  
 *bloc structuré de directive unique*  
  
 *la directive du seul*:  
  
 **# pragma pragma omp unique** *unique clause*optseq *nouvelle ligne*  
  
 *une clause unique*:  
  
 *clause de données*  
  
 **nowait**  
  
 *construction parallèle-for*:  
  
 *instruction d’itération parallèle pour (directive)*  
  
 *-parallèle pour la directive*:  
  
 **# pragma pragma omp parallel pour** *parallèle de clause for*optseq *nouvelle ligne*  
  
 *parallèle de clause for*:  
  
 *clause unique parallèle*  
  
 *unique pour la clause*  
  
 *clause de données*  
  
 *construction de sections parallèles*:  
  
 *directive parallèle-sections section-étendue*  
  
 *directive parallèle-sections*:  
  
 **sections de # pragma omp parallel** *parallèle-sections-clause*optseq *nouvelle ligne*  
  
 *clause de sections de parallèle*:  
  
 *clause unique parallèle*  
  
 *clause de données*  
  
 *construction de master*:  
  
 *bloc structuré de directive de master*  
  
 *directive de master*:  
  
 **masque de # pragma omp** *nouvelle ligne*  
  
 *construction Critical*:  
  
 *bloc structuré critiques (directive)*  
  
 *directive Critical*:  
  
 **# pragma pragma omp critique** *une expression de la région*opt *nouvelle ligne*  
  
 *une expression de la région*:  
  
 *(identificateur)*  
  
 *la directive du cloisonnement*:  
  
 **barrière de # pragma omp** *nouvelle ligne*  
  
 *construction atomic*:  
  
 *instruction d’expression atomic (directive)*  
  
 *directive atomic*:  
  
 **# pragma pragma omp atomic** *nouvelle ligne*  
  
 *la directive du vidage*:  
  
 **# pragma pragma omp vidage** *var de vidage*opt *nouvelle ligne*  
  
 *Flush-var*:  
  
 *(liste de variable)*  
  
 *construction ordonnée*:  
  
 *bloc structuré de directive commandée*  
  
 *la directive classés*:  
  
 **# pragma omp classés** *nouvelle ligne*  
  
 *déclaration*:  
  
 **/\* déclarations standards \*/**  
  
 *directive threadprivate*  
  
 *la directive threadprivate*:  
  
 **# pragma omp threadprivate (** *variable-list***)** *nouvelle ligne*   
  
 *clause de données*:  
  
 **privé (** *variable-list* **)**  
  
 **copyprivate (***variable-list***)**   
  
 **firstprivate (***variable-list***)**   
  
 **lastprivate (** *variable-list***)**   
  
 **partagé (** *variable-list* **)**  
  
 **par défaut (partagé)**  
  
 **par défaut (aucun)**  
  
 **la réduction (***opérateur de réduction***:***variable-list***)**   
  
 **copyin (***variable-list***)**   
  
 *opérateur de réduction*:  
  
 *Un des*:  **+  \* -& ^ &#124; & &&#124;&#124;**  
  
 **/\* en C \*/**  
  
 *liste de la variable*:  
  
 *identifier*  
  
 *liste de la variable* **,** *identificateur*  
  
 **/\* en C++ \*/**  
  
 *liste de la variable*:  
  
 *ID-expression*  
  
 *liste de la variable* **,** *id-expression*