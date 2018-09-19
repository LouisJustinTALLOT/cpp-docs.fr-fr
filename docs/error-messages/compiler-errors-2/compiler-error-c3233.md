---
title: Erreur du compilateur C3233 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3233
dev_langs:
- C++
helpviewer_keywords:
- C3233
ms.assetid: a9210830-1136-4f02-ba41-030c85f93547
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87a5494e4894077d6f9dc61d920ed42db9872988
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035446"
---
# <a name="compiler-error-c3233"></a>Erreur du compilateur C3233

'type' : paramètre de type générique déjà limité

Il n’est pas possible de contraindre un paramètre générique dans plusieurs clauses `where` .

L’exemple suivant génère l’erreur C3233 :

```
// C3233.cpp
// compile with: /clr /LD

interface struct C {};
interface struct D {};

generic <class T>
where T : C
where T : D
ref class E {};   // C3233
```