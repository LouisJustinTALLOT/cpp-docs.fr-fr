---
title: 2.6.2 construction critical | Documents Microsoft
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
ms.openlocfilehash: ae7070fcc590307e71b0c34259bcbe1c12200550
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689595"
---
# <a name="262-critical-construct"></a>2.6.2 Construction critical
Le **critique** directive identifie une construction qui restreint l’exécution du bloc structuré associé à un seul thread à la fois. La syntaxe de la **critique** la directive est la suivante :  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 Facultatif *nom* peut être utilisé pour identifier la zone critique. Les identificateurs utilisés pour identifier une région critique ont une liaison externe et sont dans un espace de noms qui diffèrent dans les espaces de noms utilisés par les étiquettes, les balises, les membres et les identificateurs ordinaires.  
  
 Un thread attend au début d’une zone critique jusqu'à ce qu’aucun autre thread n’exécute une région critique (n’importe où dans le programme) portant le même nom. Tous les sans nom **critique** directives de mappent le même nom non spécifié.