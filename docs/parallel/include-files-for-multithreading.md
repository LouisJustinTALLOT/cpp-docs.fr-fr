---
title: Fichiers Include pour le Multithreading | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64ba6ec639151ca659e3bd075f691176ef4edbdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422322"
---
# <a name="include-files-for-multithreading"></a>Fichiers include pour le multithreading

Fichiers include standard déclarent les fonctions de bibliothèque du run-time C comme elles sont implémentées dans les bibliothèques. Si vous utilisez le [optimisation complète](../build/reference/ox-full-optimization.md) (/ Ox) ou [appel fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) option, le compilateur suppose que toutes les fonctions doivent être appelées à l’aide de la convention d’appel de Registre. Les fonctions de bibliothèque du run-time ont été compilées à l’aide de la convention d’appel C, et les déclarations dans les fichiers include standard indiquent au compilateur de générer des références externes correctes à ces fonctions.

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)