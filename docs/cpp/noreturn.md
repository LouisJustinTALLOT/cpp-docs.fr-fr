---
description: 'En savoir plus sur : noreturn'
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: 829f8cc2d81ae1b9f55024442f1a38b495d54896
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195357"
---
# <a name="noreturn"></a>noreturn

**Spécifique à Microsoft**

Cet **`__declspec`** attribut indique au compilateur qu’une fonction ne retourne pas. Par conséquent, le compilateur sait que le code qui suit un appel à une **`__declspec(noreturn)`** fonction est inaccessible.

Si le compilateur recherche une fonction avec un chemin d’accès au contrôle qui ne retourne pas de valeur, il génère un avertissement (C4715) ou le message d’erreur (C2202). Si le chemin d’accès au contrôle ne peut pas être atteint en raison d’une fonction qui ne retourne jamais, vous pouvez utiliser **`__declspec(noreturn)`** pour éviter cet avertissement ou cette erreur.

> [!NOTE]
> **`__declspec(noreturn)`** L’ajout à une fonction supposée être retournée peut entraîner un comportement indéfini.

## <a name="example"></a>Exemple

Dans l’exemple suivant, la **`else`** clause ne contient pas d’instruction return.  La Déclaration `fatal` de comme **`__declspec(noreturn)`** évite un message d’erreur ou d’avertissement.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
