---
title: Compilateur avertissement (niveau 1) C4799 | Microsoft Docs
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
ms.openlocfilehash: b3d83917289e5ad76a874587894a66e163fed90a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088226"
---
# <a name="compiler-warning-level-1-c4799"></a>Avertissement du compilateur (niveau 1) C4799

> Aucune instruction EMMS à la fin de la fonction '*fonction*'

La fonction a au moins une instruction MMX, mais n’a pas un `EMMS` instruction. Lorsqu’une instruction multimédia est utilisée, un `EMMS` instruction ou `_mm_empty` intrinsèque doit également être utilisé pour effacer le mot de la balise multimédia à la fin du code MMX.

C4799 peut apparaître lorsque vous utilisez ivec.h, indiquant que le code n’utilise pas correctement exécuter l’instruction EMMS avant de retourner. Il s’agit d’un avertissement false pour ces en-têtes. Vous pouvez désactiver ces en définissant _SILENCE_IVEC_C4799 dans ivec.h. Toutefois, n’oubliez pas que cela empêchera le compilateur de fournir des avertissements corrects de ce type.

Pour plus d’informations, consultez [du jeu d’instructions MMX d’Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).