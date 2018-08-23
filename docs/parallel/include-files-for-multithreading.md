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
ms.openlocfilehash: 73444c72878073d881abec08c474eb1f1ce64f02
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42538409"
---
# <a name="include-files-for-multithreading"></a>Fichiers include pour le multithreading
Fichiers include standard déclarent les fonctions de bibliothèque du run-time C comme elles sont implémentées dans les bibliothèques. Si vous utilisez le [optimisation complète](../build/reference/ox-full-optimization.md) (/ Ox) ou [appel fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) option, le compilateur suppose que toutes les fonctions doivent être appelées à l’aide de la convention d’appel de Registre. Les fonctions de bibliothèque du run-time ont été compilées à l’aide de la convention d’appel C, et les déclarations dans les fichiers include standard indiquent au compilateur de générer des références externes correctes à ces fonctions.  
  
## <a name="see-also"></a>Voir aussi  

[Multithreading à l’aide de C et de Win32](../parallel/multithreading-with-c-and-win32.md)