---
title: LNK1223 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e50d29af6ac563fadd3a52e5b1d3d15201289083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298650"
---
# <a name="linker-tools-error-lnk1223"></a>Erreur des outils Éditeur de liens LNK1223
fichier non valide ou endommagé : le fichier contient des contributions .pdata non valides  
  
 Pour les plateformes RISC qui utilisent des pdata, cette erreur survient si le compilateur a émis une section .pdata avec des entrées non triées.  
  
 Pour résoudre ce problème, essayez de compiler sans [/GL (optimisation de l’ensemble du programme)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) activé. Les corps de fonction vides peuvent aussi provoquer cette erreur dans certains cas.