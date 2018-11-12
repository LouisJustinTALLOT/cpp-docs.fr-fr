---
title: Avertissement des outils Éditeur de liens LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: c6a5a0714e070e6cf3aee8efcdfbdfa07fa9ee69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427857"
---
# <a name="linker-tools-warning-lnk4086"></a>Avertissement des outils Éditeur de liens LNK4086

point d’entrée 'function' n’est pas __stdcall avec des octets de 'nombre' arguments ; image ne peut pas s’exécuter

Le point d’entrée pour une DLL doit être `__stdcall`. Soit recompiler la fonction avec le [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) soit spécifier `__stdcall` ou WINAPI lorsque vous définissez la fonction.