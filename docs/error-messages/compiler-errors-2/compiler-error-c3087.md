---
title: Erreur du compilateur C3087
ms.date: 11/04/2016
f1_keywords:
- C3087
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
ms.openlocfilehash: 6b9ae71ebfbcfcd5936a2fc3ca666aa51e59bfb5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751415"
---
# <a name="compiler-error-c3087"></a>Erreur du compilateur C3087

'argument_nommé' : l’appel de 'attribut' initialise déjà ce membre

Un argument nommé a été spécifié dans le même bloc d’attributs comme argument sans nom pour la même valeur. Spécifiez uniquement un argument nommé ou sans nom.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3087 :

```cpp
// C3087.cpp
// compile with: /c
[idl_quote("quote1", text="quote2")];   // C3087
[idl_quote(text="quote3")];   // OK
[idl_quote("quote4")];   // OK
```
