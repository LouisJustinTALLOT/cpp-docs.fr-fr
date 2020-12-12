---
description: 'En savoir plus sur : erreur du compilateur C2854'
title: Erreur du compilateur C2854
ms.date: 11/04/2016
f1_keywords:
- C2854
helpviewer_keywords:
- C2854
ms.assetid: 917fec9c-790a-4149-8dfc-00d17a09199c
ms.openlocfilehash: beb4947e365d1a64d5b0c8ad5ffcdf647b0939d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260135"
---
# <a name="compiler-error-c2854"></a>Erreur du compilateur C2854

erreur de syntaxe dans #pragma hdrstop

`#pragma hdrstop`Donne un nom de fichier non valide. Le pragma peut être suivi d’un nom de fichier facultatif entre parenthèses et guillemets :

L’exemple suivant génère l’C2854 :

```cpp
// C2854.cpp
// compile with: /c
#pragma hdrstop( "\\source\\pchfiles\\myheader.pch" ]   // C2854
// try the following line instead
// #pragma hdrstop( "\\source\\pchfiles\\myheader.pch" )
```
