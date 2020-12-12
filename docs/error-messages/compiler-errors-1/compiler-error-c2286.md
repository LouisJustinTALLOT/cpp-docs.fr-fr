---
description: 'En savoir plus sur : erreur du compilateur C2286'
title: Erreur du compilateur C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 89c8b69c42188d448fad0cd08287773d7a713d08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298459"
---
# <a name="compiler-error-c2286"></a>Erreur du compilateur C2286

les pointeurs vers les membres de la représentation’identifier’ont déjà la valeur’Inheritance'-déclaration ignorée

Il existe deux représentations de pointeur vers membre différentes pour la classe.

Pour plus d’informations, consultez [Mots clés d’héritage](../../cpp/inheritance-keywords.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2286 :

```cpp
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```
