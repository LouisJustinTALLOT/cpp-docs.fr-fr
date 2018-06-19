---
title: LNK4086 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7b3ad3a8ceebf97ccdcf7a1d8079886f54a3984
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301159"
---
# <a name="linker-tools-warning-lnk4086"></a>Avertissement des outils Éditeur de liens LNK4086
point d’entrée 'fonction' n’est pas __stdcall avec des octets de 'nombre' arguments ; image ne peut pas s’exécuter  
  
 Le point d’entrée pour une DLL doit être `__stdcall`. Vous pouvez soit recompiler la fonction avec le [GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md) soit spécifier `__stdcall` ou WINAPI lors de la définition de la fonction.