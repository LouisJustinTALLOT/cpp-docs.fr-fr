---
title: Erreur du compilateur C2129 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d151c774672b1788ca893a9812deb3e41100dc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171716"
---
# <a name="compiler-error-c2129"></a>Erreur du compilateur C2129
fonction static 'function' déclarée mais non définie  
  
 Une référence vers l’avant est faite à un `static` fonction qui n’est jamais définie.  
  
 A `static` fonction doit être définie dans la portée du fichier. Si la fonction est définie dans un autre fichier, elle doit être déclarée `extern`.