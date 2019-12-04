---
title: Erreur irrécupérable C1190
ms.date: 11/04/2016
f1_keywords:
- C1190
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
ms.openlocfilehash: 261d25d031d3a11f1d9e25ca3fb2c926cd521f97
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747343"
---
# <a name="fatal-error-c1190"></a>Erreur irrécupérable C1190

le code ciblé managé requiert une option '/clr'

Vous utilisez des constructions CLR, mais vous n’avez pas spécifié **/clr**.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant génère l’erreur C1190 :

```cpp
// C1190.cpp
// compile with: /c
__gc class A {};   // C1190
ref class A {};
```
