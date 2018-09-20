---
title: 2.7.2.4 partagé | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d1a545f1c505f9f578cad682399c8d69a882824
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400144"
---
# <a name="2724-shared"></a>2.7.2.4 shared

Cette clause partage les variables qui apparaissent dans le *variable-list* parmi tous les threads dans une équipe. La même zone de stockage pour accèdent à tous les threads au sein d’une équipe **partagé** variables.

La syntaxe de la **partagé** clause se présente comme suit :

```
shared(variable-list)
```