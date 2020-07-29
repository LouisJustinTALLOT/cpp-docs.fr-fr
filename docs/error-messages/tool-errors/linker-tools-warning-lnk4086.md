---
title: Avertissement des outils Éditeur de liens LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: f692f848825cd3d8e5e1fc042cb94d7cce8ea6bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195809"
---
# <a name="linker-tools-warning-lnk4086"></a>Avertissement des outils Éditeur de liens LNK4086

le point d’entrée’fonction’n’est pas __stdcall avec’nombre’octets d’arguments ; l’image risque de ne pas s’exécuter

Le point d’entrée d’une DLL doit être **`__stdcall`** . Recompilez la fonction avec l’option [/gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) ou spécifiez **`__stdcall`** ou WINAPI quand vous définissez la fonction.
