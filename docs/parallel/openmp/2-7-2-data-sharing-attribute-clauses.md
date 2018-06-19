---
title: 2.7.2 attribut de partage de données Clauses | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecc6efac6e3d7356e51dc0ec57009ca9e5a71890
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691901"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Clauses d'attributs de partage de données
Plusieurs directives acceptent les clauses qui lui permet de contrôler les attributs de partage des variables pendant la durée de la région. Les clauses d’attributs de partage s’appliquent uniquement aux variables dans l’étendue lexicale de la directive de sur lequel la clause apparaît. Toutes les clauses suivantes sont autorisées sur toutes les directives. La liste des clauses qui sont valides sur une directive particulière sont décrites dans la directive.  
  
 Si une variable est visible lorsqu’un parallèle ou de construction de partage de travail se produite et de la variable n’est pas spécifiée dans une clause d’attribut partage ou **threadprivate** directive, puis la variable est partagée. Variables statiques déclarées dans l’étendue dynamique d’une région parallèle sont partagés. Segment de mémoire allouée (par exemple, à l’aide de **malloc()** en C ou C++ ou **nouveau** opérateur en C++) est partagé. (Le pointeur à cette mémoire, toutefois, permettre être privés ou partagés.) Les variables avec une durée de stockage automatique déclarée dans l’étendue dynamique d’une région parallèle sont privés.  
  
 La plupart des clauses accepte un *variable-list* argument, qui est une liste séparée par des virgules de variables qui sont visibles. Si une variable est référencée dans une clause partage des données d’attribut a un type dérivé d’un modèle et il en existe aucune autre référence à cette variable dans le programme, le comportement est indéfini.  
  
 Toutes les variables qui apparaissent dans les clauses de directive doivent être visibles. Clauses peuvent être répétées en fonction des besoins, mais aucune variable ne peut-être être spécifié dans plusieurs clauses, sauf qu’une variable peut être spécifiée à la fois dans un **firstprivate** et un **lastprivate** clause.  
  
 Les sections suivantes décrivent les clauses d’attributs de partage de données :  
  
-   **privé**, [Section 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) page 25.  
  
-   **firstprivate**, [Section 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) sur la page 26.  
  
-   **lastprivate**, [Section 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) page 27.  
  
-   **partagé**, [Section 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) page 27.  
  
-   **par défaut**, [Section 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) à la page 28.  
  
-   **réduction**, [Section 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) à la page 28.  
  
-   **copyin**, [Section 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) sur la page 31.  
  
-   **copyprivate**, [Section 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) à la page 32.