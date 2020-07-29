---
title: Erreur du compilateur C3166
ms.date: 11/04/2016
f1_keywords:
- C3166
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
ms.openlocfilehash: 1915d58f73ce8d16135951b359c3f0fd48aea3ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230868"
---
# <a name="compiler-error-c3166"></a>Erreur du compilateur C3166

> 'pointeur' : impossible de déclarer un pointeur vers un pointeur __gc intérieur en tant que membre de’type'

Le compilateur a détecté une déclaration de pointeur non valide (un **`__nogc`** pointeur vers un **`__gc`** pointeur.).

C3166 est accessible uniquement à l’aide de l’option de compilateur obsolète **`/clr:oldSyntax`** .
