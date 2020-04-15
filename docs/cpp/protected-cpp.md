---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 79ca081726c1f26a251763e2533ade730f075e2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317262"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Syntaxe

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Notes

Le mot clé **protégé** précise l’accès aux membres de la classe dans la *liste des membres* jusqu’au prochain spécificateur d’accès **(public** ou **privé)** ou à la fin de la définition de classe. Les membres du groupe **déclarés protégés** ne peuvent être utilisés que par les éléments suivants :

- Les fonctions membres de la classe qui a initialement déclaré ces membres.

- Les friends de la classe qui a initialement déclaré ces membres.

- Les classes dérivées ayant un accès public ou protégé à partir de la classe qui a initialement déclaré ces membres.

- Les classes directes dérivées de manière privée qui ont également un accès privé aux membres protégés.

Lorsqu’il précède le nom d’une classe de base, le mot clé **protégé** précise que le public et les membres protégés de la classe de base sont des membres protégés de ses classes dérivées.

Les membres protégés ne sont pas aussi privés que les membres **privés,** qui ne sont accessibles qu’aux membres de la classe dans laquelle ils sont déclarés, mais ils ne sont pas aussi publics que les membres **du public,** qui sont accessibles dans n’importe quelle fonction.

Les membres protégés qui sont également déclarés **statiques** sont accessibles à toute fonction d’ami ou de membre d’une classe dérivée. Les membres protégés qui ne sont pas déclarés **statiques** ne sont accessibles aux amis et aux fonctions des membres dans une classe dérivée que par un pointeur, une référence ou un objet de la classe dérivée.

Pour obtenir des renseignements connexes, consultez [l’ami,](../cpp/friend-cpp.md) [le public,](../cpp/public-cpp.md)le [privé](../cpp/private-cpp.md)et la table d’accès des membres dans [le contrôle de l’accès aux membres de la classe.](member-access-control-cpp.md)

## <a name="clr-specific"></a>Spécifique /clr

Dans les types CLR, les mots-clés de spécificateur d’accès CMD **(publics,** **privés**et **protégés**) peuvent affecter la visibilité des types et des méthodes en ce qui concerne les assemblages. Pour plus d’informations, voir [Contrôle d’accès des membres](member-access-control-cpp.md).

> [!NOTE]
> Les fichiers compilés avec [/LN](../build/reference/ln-create-msil-module.md) ne sont pas affectés par ce comportement. Dans ce cas, toutes les classes managées (public ou privées) seront visibles.

## <a name="end-clr-specific"></a>Spécifique END /clr

## <a name="example"></a>Exemple

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>Voir aussi

[Contrôle de l’accès aux membres de classe](member-access-control-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
