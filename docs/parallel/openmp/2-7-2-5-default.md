---
title: 2.7.2.5 par défaut | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 047110fe80d15d0ff3d979eeec8abf3e42dc35f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401561"
---
# <a name="2725-default"></a>2.7.2.5 default

Le **par défaut** clause permet à l’utilisateur d’affecter les attributs de partage de données de variables. La syntaxe de la **par défaut** clause se présente comme suit :

```
default(shared | none)
```

Spécification **default(shared)** équivaut à répertorier explicitement chaque variable actuellement visible dans un **partagé** clause, sauf s’il est **threadprivate** ou **inconvénients**`t`-qualifié. En l’absence d’un texte explicite **par défaut** clause, le comportement par défaut est le même qu’if **default(shared)** ont été spécifiés.

Spécification **default (None)** requiert qu’au moins un des éléments suivants doit être remplie pour chaque référence à une variable dans l’étendue lexicale de la construction parallèle :

- La variable est explicitement répertoriée dans une clause d’attribut de partage de données d’une construction qui contient la référence.

- La variable est déclarée au sein de la construction parallèle.

- La variable est **threadprivate**.

- La variable a un **const**-type qualifié.

- La variable est la variable de contrôle de boucle pour un **pour** boucle qui le suit immédiatement un **pour** ou **parallèles pour** directive et la référence variable apparaît à l’intérieur de la boucle .

Spécification d’une variable sur une **firstprivate**, **lastprivate**, ou **réduction** clause d’une directive délimitée provoque une référence implicite à la variable dans la forme contexte. De telles références implicites sont également soumis aux spécifications ci-dessus.

Un seul **par défaut** clause peut être spécifiée sur un **parallèles** directive.

Attributs de partage de données peut être substituée à l’aide de la valeur par défaut d’une variable le **privé**, **firstprivate**, **lastprivate**, **réduction**, et **partagé** clauses, comme illustré dans l’exemple suivant :

```
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```