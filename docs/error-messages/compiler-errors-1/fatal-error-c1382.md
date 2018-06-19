---
title: Erreur irrécupérable C1382 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07c6af1209faface96585224cbd08b4e35101478
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229253"
---
# <a name="fatal-error-c1382"></a>Erreur irrécupérable C1382
fichier PCH 'fichier' recompilé depuis la génération de 'obj'. Régénérez cet objet  
  
 Lorsque vous utilisez [LTCG](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un fichier .pch qui est plus récent qu’un fichier CIL .obj qui pointe vers elle. Les informations contenues dans le fichier CIL .obj sont obsolètes. Reconstruire l’objet.  
  
 C1382 peut également se produire si vous compilez avec **/Yc**, mais également passer plusieurs source des fichiers de code pour le compilateur.  Pour résoudre, n’utilisez pas **/Yc** lors du passage des fichiers de code source multiples au compilateur.  Pour plus d’informations, consultez [/Yc (créer un en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md).