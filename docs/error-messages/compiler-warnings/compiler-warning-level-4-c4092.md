---
title: Compilateur avertissement (niveau 4) C4092 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca145addc16306d613817643e363ecd9c95069a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292186"
---
# <a name="compiler-warning-level-4-c4092"></a>Compilateur avertissement (niveau 4) C4092
sizeof retourne 'unsigned long'  
  
 L’opérande de le `sizeof` opérateur a été très volumineux, de sorte que `sizeof` retourné non **long**. Cet avertissement se produit sous les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)). Sous compatibilité ANSI (/Za), le résultat est tronqué à la place.