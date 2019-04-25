---
title: Erreur du compilateur C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 5a9d897686fc915c9892fa2bcd51fa3ca3c8b05e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165669"
---
# <a name="compiler-error-c2218"></a>Erreur du compilateur C2218

'__vectorcall' ne peut pas s'utiliser avec '/arch:IA32'

La convention d’appel `__vectorcall` est prise en charge uniquement dans le code natif sur les processeurs x86 et x64 qui incluent les extensions Streaming SIMD 2 (SSE2) et versions ultérieures. Pour plus d’informations, consultez [__vectorcall](../../cpp/vectorcall.md).

Pour corriger cette erreur, modifiez les options du compilateur pour cibler les jeux d'instructions SSE2, AVX ou AVX2. Pour plus d’informations, consultez l’article [/arch (x86)](../../build/reference/arch-x86.md).