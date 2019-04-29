---
title: Avertissement du compilateur (niveau 1) C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: 9e61d919f08bbbf4f3e74da7ba4f2388516d3152
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374519"
---
# <a name="compiler-warning-level-1-c4678"></a>Avertissement du compilateur (niveau 1) C4678

la classe de base 'base_type' est moins accessible que 'derived_type'

Un type public dérive d’un type privé. Si le type public est instancié dans un assembly référencé, les membres du type de base privé ne sont pas accessibles.

C4678 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**. Il s’agit d’une erreur lors de l’utilisation **/CLR**, d’avoir une classe de base qui est moins accessible que sa classe dérivée.
