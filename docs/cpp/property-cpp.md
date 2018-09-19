---
title: propriété (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- property_cpp
dev_langs:
- C++
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7388fd180da4bd82b343d193f62c30ff1069342
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064909"
---
# <a name="property-c"></a>property (C++)

**Section spécifique à Microsoft**

Cet attribut peut être appliqué à des « données membres virtuelles » non statiques dans une définition de classe ou de structure. Le compilateur traite ces « données membres virtuelles » comme des données membres en changeant leurs références en appels de fonction.

## <a name="syntax"></a>Syntaxe

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>Notes

Lorsque le compilateur détecte une donnée membre déclarée avec cet attribut sur la droite d’un opérateur de sélection de membres («**.**« ou »**->**»), il convertit l’opération à un `get` ou `put` (fonction), selon que cette expression est une l-value ou une r-value. En savoir plus compliqué contextes, tels que «`+=`», une réécriture est effectuée par ces deux approches `get` et `put`.

Cet attribut peut également être utilisé dans la déclaration d'un tableau vide dans une définition de classe ou de structure. Exemple :

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

L'instruction ci-dessus indique que `x[]` peut être utilisé avec un ou plusieurs index de tableau. Dans ce cas, `i=p->x[a][b]` est converti en `i=p->GetX(a, b)` et `p->x[a][b] = i` est converti en `p->PutX(a, b, i);`

**FIN de la section spécifique à Microsoft**

## <a name="example"></a>Exemple

```cpp
// declspec_property.cpp
struct S {
   int i;
   void putprop(int j) {
      i = j;
   }

   int getprop() {
      return i;
   }

   __declspec(property(get = getprop, put = putprop)) int the_prop;
};

int main() {
   S s;
   s.the_prop = 5;
   return s.the_prop;
}
```

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)