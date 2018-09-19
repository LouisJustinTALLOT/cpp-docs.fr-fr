---
title: Erreur du compilateur C3166 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3166
dev_langs:
- C++
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c568f1732a4be5d890a5a654b09638828385383
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035511"
---
# <a name="compiler-error-c3166"></a>Erreur du compilateur C3166

'pointeur' : Impossible de déclarer un pointeur vers un pointeur intérieur __gc en tant que membre de 'type'

Le compilateur a détecté une déclaration de pointeur non valide (un `__nogc` pointeur vers un `__gc` pointeur.).

C3166 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**.
