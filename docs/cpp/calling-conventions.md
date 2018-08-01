---
title: Conventions d’appel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4a8b77985a06a3898c525500b8a23eab9b54f87
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407343"
---
# <a name="calling-conventions"></a>Conventions d’appel
Le compilateur Visual C/C++ fournit diverses conventions pour appeler des fonctions internes et externes. La compréhension de ces différentes approches peut vous aider à déboguer votre programme et à lier votre code avec des routines en langage assembleur.  
  
 Les rubriques se rapportant à ce sujet expliquent les différences entre les conventions d'appel, la façon dont les arguments sont passés et la manière dont les valeurs sont retournées par les fonctions. Elles présentent également les appels de fonction naked, une fonctionnalité avancée qui vous permet d’écrire votre propre code de prologue et d’épilogue.  
  
 Pour plus d’informations sur les conventions d’appel de x64 processeurs, consultez [Convention d’appel](../build/calling-convention.md).  
  
## <a name="topics-in-this-section"></a>Rubriques de cette section  
  
-   [Passage d’arguments et Conventions d’affectation de noms](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`, etc.)  
  
-   [Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [À l’aide d’appels de fonction naked pour écrire du code de prologue/épilogue personnalisées](../cpp/naked-function-calls.md)  
  
-   [Coprocesseur à virgule flottante et conventions d’appel](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [Conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modificateurs propres à Microsoft](../cpp/microsoft-specific-modifiers.md)