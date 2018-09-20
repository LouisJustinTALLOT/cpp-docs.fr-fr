---
title: 2.6.2 construction critical | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e51bd425999081c7a06a7d5692dbea16c887fa0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417850"
---
# <a name="262-critical-construct"></a>2.6.2 Construction critical

Le **critique** directive identifie une construction qui limite l’exécution du bloc structuré associé à un seul thread à la fois. La syntaxe de la **critique** directive se présente comme suit :

```
#pragma omp critical [(name)]  new-linestructured-block
```

Facultatif *nom* peut être utilisé pour identifier la zone critique. Identificateurs utilisés pour identifier une zone critique ont une liaison externe et se trouvent dans un espace de noms qui diffèrent dans les espaces de noms utilisés par les étiquettes, les balises, les membres et les identificateurs ordinaires.

Un thread attend au début d’une zone critique aucun autre thread n’exécute une zone critique (n’importe où dans le programme) portant le même nom. Tous les sans nom **critique** directives mappent le même nom pas spécifié.