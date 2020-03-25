---
title: Avertissement des outils Éditeur de liens LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: 6e012ceb5e20855353c69bbcde85fb78afad2011
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183421"
---
# <a name="linker-tools-warning-lnk4086"></a>Avertissement des outils Éditeur de liens LNK4086

le point d’entrée’fonction’n’est pas __stdcall avec’nombre’octets d’arguments ; l’image risque de ne pas s’exécuter

Le point d’entrée d’une DLL doit être `__stdcall`. Recompilez la fonction avec l’option [/gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) ou spécifiez `__stdcall` ou WINAPI quand vous définissez la fonction.
