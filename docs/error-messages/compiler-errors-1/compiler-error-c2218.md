---
title: Erreur du compilateur C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: db14c37992fc1e2dd409c653d622d3419fcae4f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206646"
---
# <a name="compiler-error-c2218"></a>Erreur du compilateur C2218

'__vectorcall' ne peut pas s'utiliser avec '/arch:IA32'

La convention d’appel `__vectorcall` est prise en charge uniquement dans le code natif sur les processeurs x86 et x64 qui incluent les extensions Streaming SIMD 2 (SSE2) et versions ultérieures. Pour plus d’informations, consultez [__vectorcall](../../cpp/vectorcall.md).

Pour corriger cette erreur, modifiez les options du compilateur pour cibler les jeux d'instructions SSE2, AVX ou AVX2. Pour plus d’informations, consultez l’article [/arch (x86)](../../build/reference/arch-x86.md).
