---
title: Erreur du compilateur C2873 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2873
dev_langs:
- C++
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf0cc5663d81d6c1e7ad6a9f1a5f7ca167f12909
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049902"
---
# <a name="compiler-error-c2873"></a>Erreur du compilateur C2873

'symbole' : symbole ne peut pas être utilisé dans une déclaration using

Un `using` la directive il manque un [espace de noms](../../cpp/namespaces-cpp.md) mot clé. Ainsi, le compilateur interprète le code comme un [à l’aide de la déclaration](../../cpp/using-declaration.md) au lieu d’un [à l’aide de la directive](../../cpp/namespaces-cpp.md#using_directives).