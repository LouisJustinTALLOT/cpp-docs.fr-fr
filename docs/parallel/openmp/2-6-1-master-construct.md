---
title: 2.6.1 maître construction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d82ae673e428c635172f35f9b0f682aa65dc2b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445631"
---
# <a name="261-master-construct"></a>2.6.1 Construction master

Le **master** directive identifie une construction qui spécifie un bloc structuré qui est exécuté par le thread principal de l’équipe. La syntaxe de la **master** directive se présente comme suit :

```
#pragma omp master new-linestructured-block
```

Autres threads dans l’équipe n’exécutent pas le bloc structuré associé. Il n’existe plus aucune barrière implicite sur entrée ou sortie à partir de la construction master.