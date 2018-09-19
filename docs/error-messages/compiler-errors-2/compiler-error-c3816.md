---
title: Erreur du compilateur C3816 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3816
dev_langs:
- C++
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfc0cf864caeefd5b19e3d40383724909575d4df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115890"
---
# <a name="compiler-error-c3816"></a>Erreur du compilateur C3816

'déclaration' a été précédemment déclarée ou définie avec un autre gérés ou WinRTmodifier

Une déclaration anticipée et une déclaration réelle nécessitent qu'il n'y ait aucun conflit ni incohérence dans la déclaration des attributs.

L'exemple suivant génère l'erreur C3816 et montre comment la corriger :

```
// C3816a.cpp
// compile with: /clr /c
class C1;
// try the following line instead
// ref class C1;

ref class C1{  // C3816, forward declaration does not use ref
};
```