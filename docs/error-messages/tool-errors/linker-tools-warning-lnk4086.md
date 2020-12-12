---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4086'
title: Avertissement des outils Éditeur de liens LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: f19138d895706579cff13bd1d43b9a64ccaa5044
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210112"
---
# <a name="linker-tools-warning-lnk4086"></a>Avertissement des outils Éditeur de liens LNK4086

le point d’entrée’fonction’n’est pas __stdcall avec’nombre’octets d’arguments ; l’image risque de ne pas s’exécuter

Le point d’entrée d’une DLL doit être **`__stdcall`** . Recompilez la fonction avec l’option [/gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) ou spécifiez **`__stdcall`** ou WINAPI quand vous définissez la fonction.
