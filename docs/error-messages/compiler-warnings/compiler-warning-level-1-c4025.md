---
title: Compilateur avertissement (niveau 1) C4025 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4025
dev_langs:
- C++
helpviewer_keywords:
- C4025
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e84ba11c7bed7420a9a1c699361612ef2002d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273947"
---
# <a name="compiler-warning-level-1-c4025"></a>Avertissement du compilateur (niveau 1) C4025
'number' : pointeur based passé à une fonction avec des arguments de variables : paramètre number  
  
 Passer un pointeur based à une fonction avec des arguments de variables entraîne la normalisation du pointeur, avec des résultats imprévisibles. Ne passez pas de pointeurs based à des fonctions avec des arguments de variables.