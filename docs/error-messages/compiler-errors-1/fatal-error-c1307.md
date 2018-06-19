---
title: Erreur irrécupérable C1307 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d06ce51ada7cd9159b8e02ff627bf12ebb7293d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227133"
---
# <a name="fatal-error-c1307"></a>Erreur irrécupérable C1307
le programme a été modifié depuis que les données du profil ont été recueillies  
  
 Lorsque vous utilisez [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), l’éditeur de liens a détecté un module d’entrée qui a été recompilé après/LTCG : PGINSTRUMENT et que le module a été modifié au point où les données de profil existante ne soient plus pertinentes. Par exemple, si le graphique des appels a changé dans le module recompilé, le compilateur générera C1307.  
  
 Pour résoudre cette erreur, exécutez/LTCG : PGINSTRUMENT, restauration par progression de toutes les séries de tests et exécutez/LTCG : PGOPTIMIZE. Si vous ne pouvez pas exécuter/LTCG : PGINSTRUMENT et restauration par progression de que tous les tests s’exécute, utilisez/LTCG : PGUPDATE au lieu de/LTCG : PGOPTIMIZE pour créer l’image optimisée.