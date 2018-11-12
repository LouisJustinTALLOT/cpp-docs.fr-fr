---
title: Avertissement du compilateur (niveau 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 87f13f7da12a3f7e40aaad180e2a3bc83e121771
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586912"
---
# <a name="compiler-warning-level-1-c4276"></a>Avertissement du compilateur (niveau 1) C4276

'fonction' : aucun prototype fourni ; supposé sans paramètres

Lorsque vous prenez l’adresse d’une fonction avec la [__stdcall](../../cpp/stdcall.md) convention d’appel, vous devez donner un prototype afin que le compilateur peut créer le nom décoré de la fonction. Dans la mesure où *fonction* a pas de prototype, le compilateur, lors de la création du nom décoré, suppose que la fonction n’a aucun paramètre.