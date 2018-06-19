---
title: Erreur du compilateur C2818 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10d7f419d528fcd2445b82e29d92442002624909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236051"
---
# <a name="compiler-error-c2818"></a>Erreur du compilateur C2818
application de surchargé 'operator ->' est récurrente à travers le type 'type'  
  
 Une redéfinition de l’opérateur de l’accès de membre de classe contient une récursive `return` instruction. Pour redéfinir la `->` opérateur avec la récurrence, vous devez déplacer la routine récurrente vers une fonction appelée à partir de l’opérateur de substituer la fonction.