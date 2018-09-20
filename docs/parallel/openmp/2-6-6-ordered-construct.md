---
title: 2.6.6 construction ordered | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b83c3dfc13b231a1314343a1dff496acf7a99b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412195"
---
# <a name="266-ordered-construct"></a>2.6.6 Construction ordered

Ce qui suit le bloc structuré une **classés** directive est exécutée dans l’ordre dans lequel les itérations seraient exécutées dans une boucle séquentielle. La syntaxe de la **classés** directive se présente comme suit :

```
#pragma omp ordered new-linestructured-block
```

Un **classés** directive doit se trouver dans l’étendue dynamique d’un **pour** ou **parallèles pour** construire. Le **pour** ou **parallèles pour** directive auquel le **classés** lie de construction doit avoir un **classés** clause spécifié comme décrit dans [Section 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) à la page 11. Dans l’exécution d’un **pour** ou **parallèles pour** construire avec un **classés** clause, **classés** constructions sont exécutées strictement dans la ordre dans lequel ils sont exécutés dans une exécution séquentielle de la boucle.

Restrictions pour le **classés** directive sont les suivantes :

- Une itération d’une boucle avec une **pour** construction ne doit pas exécuter plusieurs fois la même directive ordonnée et qu’il ne doit pas exécuter plusieurs **classés** directive.