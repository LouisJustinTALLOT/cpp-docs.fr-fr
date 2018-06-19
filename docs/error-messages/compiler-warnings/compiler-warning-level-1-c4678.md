---
title: Compilateur avertissement (niveau 1) C4678 | Documents Microsoft
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
ms.openlocfilehash: 73871d69198752e12a629d441982c2da47146517
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284236"
---
# <a name="compiler-warning-level-1-c4678"></a>Avertissement du compilateur (niveau 1) C4678
la classe de base 'base_type' est moins accessible que 'derived_type'  
  
Un type public dérive d’un type privé. Si le type public est instancié dans un assembly référencé, les membres du type de base privé ne sont pas accessibles.  
  
C4678 est uniquement accessible à l’aide de l’option du compilateur obsolète **oldSyntax ;**. C’est une erreur lors de l’utilisation **/CLR**, d’avoir une classe de base qui est moins accessible que sa classe dérivée.  
