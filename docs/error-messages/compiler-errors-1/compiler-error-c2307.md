---
title: Erreur du compilateur C2307 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2307
dev_langs:
- C++
helpviewer_keywords:
- C2307
ms.assetid: ce6c8033-a673-4679-9883-bedec36ae385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7136b5b49371c9181780bfa4a7bc7a17416a7ad2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169944"
---
# <a name="compiler-error-c2307"></a>Erreur du compilateur C2307
pragma 'pragma' doit être une fonction externe si la compilation incrémentielle est activée  
  
 Vous devez placer le `data_seg` pragma entre les fonctions si vous utilisez la compilation incrémentielle.