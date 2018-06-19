---
title: Erreur du compilateur C2218 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1efda7258616862efc464b493b51ada2c6bd7674
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172209"
---
# <a name="compiler-error-c2218"></a>Erreur du compilateur C2218
'__vectorcall' ne peut pas s'utiliser avec '/arch:IA32'  
  
 La convention d'appel `__vectorcall` est prise en charge uniquement dans le code natif sur les processeurs x86 et x64 qui incluent les extensions Streaming SIMD 2 (SSE2) et versions ultérieures. Pour plus d’informations, consultez [__vectorcall](../../cpp/vectorcall.md).  
  
 Pour corriger cette erreur, modifiez les options du compilateur pour cibler les jeux d'instructions SSE2, AVX ou AVX2. Pour plus d’informations, consultez l’article [/arch (x86)](../../build/reference/arch-x86.md).