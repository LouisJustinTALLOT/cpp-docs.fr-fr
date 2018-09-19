---
title: Erreur du compilateur C2854 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2854
dev_langs:
- C++
helpviewer_keywords:
- C2854
ms.assetid: 917fec9c-790a-4149-8dfc-00d17a09199c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd49c9fbfa88667cdb2e8bd57466632c0a051e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074810"
---
# <a name="compiler-error-c2854"></a>Erreur du compilateur C2854

Erreur de syntaxe dans #pragma hdrstop

Le `#pragma hdrstop` donne un nom de fichier non valide. Le pragma peut être suivi d’un nom de fichier facultatif entre parenthèses et guillemets :

L’exemple suivant génère C2854 :

```
// C2854.cpp
// compile with: /c
#pragma hdrstop( "\\source\\pchfiles\\myheader.pch" ]   // C2854
// try the following line instead
// #pragma hdrstop( "\\source\\pchfiles\\myheader.pch" )
```