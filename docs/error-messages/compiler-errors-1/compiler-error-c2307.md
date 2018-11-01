---
title: Erreur du compilateur C2307
ms.date: 11/04/2016
f1_keywords:
- C2307
helpviewer_keywords:
- C2307
ms.assetid: ce6c8033-a673-4679-9883-bedec36ae385
ms.openlocfilehash: 5be197e61e48e47db70e8f23c7ef5b9ade22b1ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506273"
---
# <a name="compiler-error-c2307"></a>Erreur du compilateur C2307

pragma 'pragma' doit être une fonction externe si la compilation incrémentielle est activée

Vous devez placer le `data_seg` pragma entre les fonctions si vous utilisez la compilation incrémentielle.