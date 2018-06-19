---
title: 1.2 définition des termes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8563bb757ad8d30f1639f017769bfd6c4084efa0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688594"
---
# <a name="12-definition-of-terms"></a>1.2 Définition des termes
Les termes suivants sont utilisés dans ce document :  
  
 barrier  
 Un point de synchronisation doit être accessible par tous les threads dans une équipe.  Chaque thread attend jusqu'à ce que tous les threads de l’équipe arrivent à ce stade. Il existe des barrières explicites identifiées par les directives et barrières implicites créées par l’implémentation.  
  
 construct  
 Une construction est une instruction. Il se compose d’une directive et le bloc structuré. Notez que certaines directives ne font pas partie d’une construction. (Consultez *la directive openmp* dans [annexe C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).  
  
 directive  
 Un C ou du C++ **#pragma** suivi par le **omp** identificateur, tout autre texte et une nouvelle ligne. La directive spécifie le comportement du programme.  
  
 étendue dynamique  
 Toutes les instructions dans le *étendue lexicale*, ainsi que n’importe quelle instruction à l’intérieur d’une fonction qui est exécutée à la suite de l’exécution des instructions au sein de l’étendue lexicale. Une étendue dynamique est également appelée un *région*.  
  
 étendue lexicale  
 Instructions lexicalement contenues dans un *bloc structuré*.  
  
 thread principal  
 Le thread qui crée une équipe lorsqu’un *région parallèle* est entré.  
  
 région parallèle  
 Instructions qui peuvent être exécutées par plusieurs threads et les lier à une construction parallèle OpenMP.  
  
 private  
 Une variable privée désigne un bloc de stockage qui est unique pour le thread qui effectue la référence. Notez qu’il existe plusieurs façons de spécifier qu’une variable est privée : une définition dans une région parallèle, un **threadprivate** directive, un **privé**, **firstprivate**, **lastprivate**, ou **réduction** clause, ou l’utilisation de la variable comme un **pour**variable de contrôle de boucle dans un **pour** boucle immédiatement après un **pour** ou **parallèles pour** la directive.  
  
 region  
 Une étendue dynamique.  
  
 région de série  
 Instructions exécutées uniquement par le *maître thread* en dehors de l’étendue dynamique de n’importe quel *région parallèle*.  
  
 Sérialiser  
 Pour exécuter une construction parallèle avec une équipe de threads consistant en un seul thread (qui est le thread principal pour cette construction parallèle), avec la série ordre d’exécution pour les instructions dans le bloc structuré (le même ordre que si le bloc n’ont pas été partie d’une construction parallèle) et sans aucune incidence sur la valeur retournée par **omp_in_parallel()** (outre les effets de n’importe quel imbriquées parallèles).  
  
 partagés  
 Une variable partagée désigne un bloc unique de stockage. Tous les threads qui accèdent à cette variable dans une équipe accèderont à ce bloc unique de stockage.  
  
 bloc structuré  
 Un bloc structuré est une instruction (unique ou composée) qui a une seule entrée et une sortie unique. Aucune instruction n’est un bloc structuré s’il existe un saut dans ou en dehors de cette instruction (y compris un appel à **longjmp**(3C) ou l’utilisation de **lever**, mais un appel à **quitter** est autorisé). Une instruction composée est un bloc structuré si son exécution toujours commence à l’ouverture **{** et se termine toujours à la fermeture **}**. Une instruction d’expression, une instruction de sélection, une instruction d’itération, ou **essayez** bloc est un bloc structuré si l’instruction composée correspondante est obtenu en le plaçant dans **{** et **}** serait un bloc structuré. Une instruction de saut, une instruction étiquetée ou une instruction de déclaration n’est pas un bloc structuré.  
  
 Équipe  
 Un ou plusieurs threads coopérer dans l’exécution d’une construction.  
  
 thread  
 Une entité d’exécution ayant un flux de contrôle de série, un ensemble de variables privées et l’accès aux variables partagées.  
  
 variable  
 Un identificateur, éventuellement qualifié par le nom de l’espace de noms, qui désigne un objet.