---
description: 'En savoir plus sur : erreur du compilateur C2212'
title: Erreur du compilateur C2212
ms.date: 11/04/2016
f1_keywords:
- C2212
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
ms.openlocfilehash: 614c93cf2c933cbdf043108c35bc06260a123ce1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245601"
---
# <a name="compiler-error-c2212"></a>Erreur du compilateur C2212

'identificateur' : __based pas disponible pour les pointeurs vers des fonctions

Les pointeurs vers des fonctions ne peuvent pas être déclarés **`__based`** . Si vous avez besoin de données basées sur du code, utilisez le **`__declspec`** mot clé ou le `data_seg` pragma.
