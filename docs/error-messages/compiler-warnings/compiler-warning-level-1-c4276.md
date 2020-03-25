---
title: Avertissement du compilateur (niveau 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: c1de07cd65bbc9f02a979ceebe31be4143af70ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175816"
---
# <a name="compiler-warning-level-1-c4276"></a>Avertissement du compilateur (niveau 1) C4276

'fonction' : aucun prototype fourni ; aucun paramètre pris par défaut

Lorsque vous prenez l’adresse d’une fonction avec la Convention d’appel [__stdcall](../../cpp/stdcall.md) , vous devez attribuer un prototype afin que le compilateur puisse créer le nom décoré de la fonction. Étant donné que la *fonction* n’a pas de prototype, le compilateur, lors de la création du nom décoré, suppose que la fonction n’a aucun paramètre.
