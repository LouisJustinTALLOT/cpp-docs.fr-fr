---
title: Erreur du compilateur C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 97f3290ef8bcb6a91442effdbf84261c03545ce2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209524"
---
# <a name="compiler-error-c2218"></a>Erreur du compilateur C2218

> '__vectorcall' ne peut pas s'utiliser avec '/arch:IA32'

La **`__vectorcall`** Convention d’appel est uniquement prise en charge dans le code natif sur les processeurs x86 et x64 qui incluent les extensions streaming SIMD 2 (SSE2) et versions ultérieures. Pour plus d’informations, consultez [`__vectorcall`](../../cpp/vectorcall.md).

Pour corriger cette erreur, modifiez les options du compilateur pour cibler les jeux d'instructions SSE2, AVX ou AVX2. Pour plus d’informations, consultez [ `/arch` (x86)](../../build/reference/arch-x86.md).
