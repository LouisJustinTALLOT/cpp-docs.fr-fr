---
title: 2.7.2.5 la valeur par défaut | Documents Microsoft
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
ms.openlocfilehash: c054c7f0ac7d1d73768d84613524afc979fecaa5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695874"
---
# <a name="2725-default"></a>2.7.2.5 default
Le **par défaut** clause permet à l’utilisateur affecter les attributs de partage de données de variables. La syntaxe de la **par défaut** clause est comme suit :  
  
```  
default(shared | none)  
```  
  
 Spécification de **default(shared)** équivaut à répertoriant explicitement chaque variable actuellement visible dans un **partagé** clause, sauf s’il est **threadprivate** ou **inconvénients**`t`-qualifié. En l’absence d’explicite **par défaut** clause, le comportement par défaut est le même qu’if **default(shared)** ont été spécifiés.  
  
 Spécification de **default (None)** requiert qu’au moins une des valeurs suivantes doit être remplie pour chaque référence à une variable dans l’étendue lexicale de la construction parallèle :  
  
-   La variable est explicitement répertoriée dans une clause partage des données d’attribut d’une construction qui contient la référence.  
  
-   La variable est déclarée au sein de la construction parallèle.  
  
-   La variable est **threadprivate**.  
  
-   La variable a une **const**-type qualifié.  
  
-   La variable est la variable de contrôle de boucle pour un **pour** boucle qui suit immédiatement un **pour** ou **parallèles pour** la directive et la référence variable apparaît à l’intérieur de la boucle .  
  
 Spécification d’une variable sur une **firstprivate**, **lastprivate**, ou **réduction** clause d’une directive entre provoque une référence implicite à la variable dans la forme contexte. De telles références implicites sont également soumises à la configuration requise ci-dessus.  
  
 Un seul **par défaut** clause peut être spécifiée sur un **parallèles** directive.  
  
 Attributs de partage de données peut être remplacée à l’aide de la valeur par défaut d’une variable le **privé**, **firstprivate**, **lastprivate**, **réduction**, et **partagé** clauses, comme illustré dans l’exemple suivant :  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```