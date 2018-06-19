---
title: Compilateur avertissement (niveau 1) C4799 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f888d6a941ad487ce122e46c43582e1c96525c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282936"
---
# <a name="compiler-warning-level-1-c4799"></a>Avertissement du compilateur (niveau 1) C4799  
  
> Aucune instruction EMMS à la fin de la fonction '*fonction*'  
  
La fonction a au moins une instruction MMX, mais n’a pas un `EMMS` instruction. Lorsqu’une instruction multimédia est utilisée, un `EMMS` instruction ou `_mm_empty` intrinsèque doit également être utilisée pour effacer le mot de la balise multimédia à la fin du code MMX.  
  
C4799 peut apparaître lorsque vous utilisez ivec.h, indiquant que le code n’utilise pas correctement exécuter l’instruction EMMS avant de retourner. Il s’agit d’un avertissement erroné pour ces en-têtes. Vous pouvez désactiver ceux-ci en définissant _SILENCE_IVEC_C4799 dans ivec.h. Toutefois, sachez que cela empêchera le compilateur de fournir des avertissements corrects de ce type.  
  
Pour plus d’informations, consultez [du jeu d’instructions MMX d’Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).