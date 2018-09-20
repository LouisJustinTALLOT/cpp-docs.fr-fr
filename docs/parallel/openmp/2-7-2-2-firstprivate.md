---
title: 2.7.2.2 firstprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e6ad966f4cf895da9374798f6c9a4079ccc2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400963"
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

Le **firstprivate** clause offre un sur-ensemble de la fonctionnalité fournie par le **privé** clause. La syntaxe de la **firstprivate** clause se présente comme suit :

```
firstprivate(variable-list)
```

Variables spécifiées dans *variable-list* ont **privé** la sémantique de clause, comme décrit dans [Section 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) page 25. L’initialisation ou une construction qui se passe comme si elle a été effectuée qu’une fois par thread, avant l’exécution du thread de la construction. Pour un **firstprivate** clause sur une construction parallèle, la valeur initiale du nouvel objet privé est la valeur de l’objet d’origine existe immédiatement avant la construction parallèle pour le thread qu’il rencontre. Pour un **firstprivate** clause sur une construction de partage de travail, la valeur initiale du nouvel objet privée pour chaque thread qui exécute la construction de partage de travail est la valeur de l’objet d’origine qui existe avant le point dans le temps qui le même thread rencontre la construction de partage de travail. En outre, pour les objets C++, le nouvel objet privé pour chaque thread est copie construit à partir de l’objet d’origine.

Les restrictions à le **firstprivate** clause sont les suivantes :

- Une variable spécifiée dans un **firstprivate** clause ne doit pas avoir un type incomplet ou un type référence.

- Une variable avec un type de classe qui est spécifié en tant que **firstprivate** doivent avoir un constructeur de copie accessible et non équivoque.

- Variables qui sont privés au sein d’une région parallèle ou qui apparaissent dans le **réduction** clause d’un **parallèles** directive ne peut pas être spécifiée dans un **firstprivate** clause sur une directive de partage de travail qui est liée à la construction parallèle.