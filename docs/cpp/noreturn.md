---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f37ce13e27f9b141eab928b88102813a5b6d65f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177883"
---
# <a name="noreturn"></a>noreturn

**Section spécifique de Microsoft**

Cet attribut **__declspec** indique au compilateur qu’une fonction ne retourne pas. Par conséquent, le compilateur sait que le code qui suit un appel à une fonction **__declspec (noreturn)** est inaccessible.

Si le compilateur recherche une fonction avec un chemin d’accès au contrôle qui ne retourne pas de valeur, il génère un avertissement (C4715) ou le message d’erreur (C2202). Si le chemin d’accès au contrôle ne peut pas être atteint en raison d’une fonction qui ne retourne jamais, vous pouvez utiliser **__declspec (noreturn)** pour éviter cet avertissement ou cette erreur.

> [!NOTE]
>  L’ajout d' **__declspec (noreturn)** à une fonction supposée être retournée peut entraîner un comportement indéfini.

## <a name="example"></a>Exemple

Dans l’exemple suivant, la clause **else** ne contient pas d’instruction return.  La déclaration d' `fatal` en tant que **__declspec (noreturn)** évite un message d’erreur ou d’avertissement.

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

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
