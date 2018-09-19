---
title: Avertissement LNK4086 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a2ee7660f0ad78d04f7edb191929296c8d47a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079230"
---
# <a name="linker-tools-warning-lnk4086"></a>Avertissement des outils Éditeur de liens LNK4086

point d’entrée 'function' n’est pas __stdcall avec des octets de 'nombre' arguments ; image ne peut pas s’exécuter

Le point d’entrée pour une DLL doit être `__stdcall`. Soit recompiler la fonction avec le [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) soit spécifier `__stdcall` ou WINAPI lorsque vous définissez la fonction.