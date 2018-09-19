---
title: Compilateur avertissement (niveau 1) C4678 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81eb7df618f97300c2654cc0f4f7a58d18215b26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076097"
---
# <a name="compiler-warning-level-1-c4678"></a>Avertissement du compilateur (niveau 1) C4678

la classe de base 'base_type' est moins accessible que 'derived_type'

Un type public dérive d’un type privé. Si le type public est instancié dans un assembly référencé, les membres du type de base privé ne sont pas accessibles.

C4678 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**. Il s’agit d’une erreur lors de l’utilisation **/CLR**, d’avoir une classe de base qui est moins accessible que sa classe dérivée.
