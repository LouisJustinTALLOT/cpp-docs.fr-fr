---
title: Erreur du compilateur C3550 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91003af2069ba32083caefa8f5a79cbe0e7cd9c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252892"
---
# <a name="compiler-error-c3550"></a>Erreur du compilateur C3550
'decltype(auto)' simple est le seul autorisé dans ce contexte  
  
 Si `decltype(auto)` est utilisé comme espace réservé pour le type de retour d'une fonction, il doit être utilisé par lui-même. Il ne peut pas être utilisé dans le cadre d'une déclaration de pointeur (`decltype(auto*)`), d'une déclaration de référence (`decltype(auto&)`) ni de toute autre qualification de ce genre.  
  
## <a name="see-also"></a>Voir aussi  
 [auto](../../cpp/auto-cpp.md)