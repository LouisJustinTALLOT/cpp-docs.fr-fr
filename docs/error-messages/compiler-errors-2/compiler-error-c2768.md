---
title: Erreur du compilateur C2768 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c76173f99dbc2fb415b60212109242845501694
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109104"
---
# <a name="compiler-error-c2768"></a>Erreur du compilateur C2768

'fonction' : utilisation non conforme d’arguments template explicites

Le compilateur n’a pas pu déterminer si une définition de fonction était supposé pour être une spécialisation explicite d’un modèle de fonction ou si la définition de fonction était supposé pour être pour une nouvelle fonction.

Cette erreur a été introduite dans Visual Studio .NET 2003, dans le cadre des améliorations de la conformité du compilateur.

L’exemple suivant génère l’erreur C2768 :

```
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```