---
title: Erreur du compilateur C2873 | Documents Microsoft
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
ms.openlocfilehash: 94a04d650729bdda949754c5070a6c307d390929
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244376"
---
# <a name="compiler-error-c2873"></a>Erreur du compilateur C2873
'symbole' : symbole ne peut pas être utilisé dans une déclaration using  
  
 A `using` la directive il manque un [espace de noms](../../cpp/namespaces-cpp.md) (mot clé). Le compilateur interprète le code comme un [à l’aide de la déclaration](../../cpp/using-declaration.md) plutôt qu’un [à l’aide de la directive](../../cpp/namespaces-cpp.md#using_directives).