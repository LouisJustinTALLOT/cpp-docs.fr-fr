---
title: 2.7.2 Clauses d'attributs de partage de données
ms.date: 11/04/2016
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
ms.openlocfilehash: 4c9209a4d627c6212087b621b223a3fb81b48ce3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559651"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Clauses d'attributs de partage de données

Plusieurs directives acceptent les clauses qui permettent à un utilisateur contrôler les attributs de partage des variables pendant la durée de la région. Les clauses d’attributs de partage s’appliquent uniquement aux variables dans l’étendue lexicale de la directive sur laquelle la clause apparaît. Pas toutes les clauses suivantes sont autorisées sur toutes les directives. La liste des clauses qui ne sont valides sur une directive particulière sont décrits avec la directive.

Si une variable est visible lorsqu’une action parallèle ou partage de travail de construction est rencontrée, et la variable n’est pas spécifiée dans une clause d’attribut de partage ou **threadprivate** directive, puis la variable est partagée. Variables statiques déclarées dans l’étendue dynamique d’une région parallèle sont partagés. Segment de mémoire alloué de la mémoire (par exemple, à l’aide de **malloc()** en C ou C++ ou le **nouveau** opérateur en C++) est partagé. (Le pointeur à cette mémoire, toutefois, permettre être privés ou partagés.) Variables avec une durée de stockage automatique déclarée dans l’étendue dynamique d’une région parallèle sont privés.

La plupart des clauses accepte un *variable-list* argument, qui est une liste séparée par des virgules de variables qui sont visibles. Si une variable est référencée dans une clause d’attribut de partage de données a un type dérivé d’un modèle et il n’existe aucune autre référence à cette variable dans le programme, le comportement est indéfini.

Toutes les variables qui apparaissent dans les clauses de directive doivent être visibles. Clauses peuvent être répétées en fonction des besoins, mais aucune variable ne peut-être être spécifiée dans plusieurs clauses, sauf qu’une variable peut être spécifiée à la fois dans un **firstprivate** et un **lastprivate** clause.

Les sections suivantes décrivent les clauses d’attributs de partage de données :

- **privé**, [Section 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) page 25.

- **firstprivate**, [Section 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) sur la page 26.

- **lastprivate**, [Section 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) page 27.

- **partagé**, [Section 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) page 27.

- **par défaut**, [Section 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) sur la page 28.

- **réduction**, [Section 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) sur la page 28.

- **copyin**, [Section 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) sur la page 31.

- **copyprivate**, [Section 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) à la page 32.