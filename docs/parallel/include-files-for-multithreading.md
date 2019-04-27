---
title: Fichiers include pour le multithreading
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
ms.openlocfilehash: 79b5c56eecfaf28743eec4ba6b4cee56156d6e2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212894"
---
# <a name="include-files-for-multithreading"></a>Fichiers include pour le multithreading

Fichiers include standard déclarent les fonctions de bibliothèque du run-time C comme elles sont implémentées dans les bibliothèques. Si vous utilisez le [optimisation complète](../build/reference/ox-full-optimization.md) (/ Ox) ou [appel fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) option, le compilateur suppose que toutes les fonctions doivent être appelées à l’aide de la convention d’appel de Registre. Les fonctions de bibliothèque du run-time ont été compilées à l’aide de la convention d’appel C, et les déclarations dans les fichiers include standard indiquent au compilateur de générer des références externes correctes à ces fonctions.

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)
