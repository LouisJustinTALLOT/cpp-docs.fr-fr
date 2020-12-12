---
description: 'En savoir plus sur : erreur du compilateur C2041'
title: Erreur du compilateur C2041
ms.date: 11/04/2016
f1_keywords:
- C2041
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
ms.openlocfilehash: 5c980b6783b4b14e4878278699e5b4f7618ff0f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175259"
---
# <a name="compiler-error-c2041"></a>Erreur du compilateur C2041

chiffre’caractère’non conforme pour la base’nombre'

Le caractère spécifié n’est pas un chiffre valide pour la base (comme octal ou Hex).

L’exemple suivant génère l’C2041 :

```cpp
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

Solution possible :

```cpp
// C2041b.cpp
// compile with: /c
int j = 071;
```
