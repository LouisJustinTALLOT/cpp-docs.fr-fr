---
description: 'En savoir plus sur : propriété (C++)'
title: property (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: ed996ecadd16837af1e28b71bbedd9b4e3c1abaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299161"
---
# <a name="property-c"></a>property (C++)

**Spécifique à Microsoft**

Cet attribut peut être appliqué à des « données membres virtuelles » non statiques dans une définition de classe ou de structure. Le compilateur traite ces « données membres virtuelles » comme des données membres en changeant leurs références en appels de fonction.

## <a name="syntax"></a>Syntaxe

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>Notes

Lorsque le compilateur voit un membre de données déclaré avec cet attribut à droite d’un opérateur de sélection de membres («**.**» ou « **->** »), il convertit l’opération en une `get` `put` fonction ou, selon qu’une telle expression est une l-value ou une r-value. Dans les contextes plus complexes, tels que « `+=` », une réécriture est effectuée en effectuant les opérations `get` et `put` .

Cet attribut peut également être utilisé dans la déclaration d'un tableau vide dans une définition de classe ou de structure. Par exemple :

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

L'instruction ci-dessus indique que `x[]` peut être utilisé avec un ou plusieurs index de tableau. Dans ce cas, `i=p->x[a][b]` est converti en `i=p->GetX(a, b)` et `p->x[a][b] = i` est converti en `p->PutX(a, b, i);`

**FIN spécifique à Microsoft**

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
