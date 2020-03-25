---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 29f57eac7201ac0647275c70c539f9b2f28eb81b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179248"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Syntaxe

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Notes

Le mot clé **protected** spécifie l’accès aux membres de classe dans la *liste de membres* jusqu’au spécificateur d’accès suivant (**public** ou **privé**) ou la fin de la définition de classe. Les membres de classe déclarés comme **protégés** peuvent être utilisés uniquement par les éléments suivants :

- Les fonctions membres de la classe qui a initialement déclaré ces membres.

- Les friends de la classe qui a initialement déclaré ces membres.

- Les classes dérivées ayant un accès public ou protégé à partir de la classe qui a initialement déclaré ces membres.

- Les classes directes dérivées de manière privée qui ont également un accès privé aux membres protégés.

Quand il précède le nom d’une classe de base, le mot clé **protected** spécifie que les membres publics et protégés de la classe de base sont des membres protégés de ses classes dérivées.

Les membres protégés ne sont pas aussi privés que les membres **privés** , qui sont accessibles uniquement aux membres de la classe dans laquelle ils sont déclarés, mais ils ne sont pas aussi publics que les membres **publics** , qui sont accessibles dans toutes les fonctions.

Les membres protégés qui sont également déclarés comme **statiques** sont accessibles à tout ami ou fonction membre d’une classe dérivée. Les membres protégés qui ne sont pas déclarés comme **statiques** sont accessibles aux amis et aux fonctions membres dans une classe dérivée uniquement par le biais d’un pointeur vers, d’une référence ou d’un objet de la classe dérivée.

Pour obtenir des informations connexes, consultez [Friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md)et la table d’accès aux membres dans [contrôle de l’accès aux membres de classe](member-access-control-cpp.md).

## <a name="clr-specific"></a>Spécifique /clr

Dans les types CLR, C++ les mots clés de spécificateur d’accès (**public**, **privé**et **protégé**) peuvent affecter la visibilité des types et des méthodes en ce qui concerne les assemblys. Pour plus d’informations, consultez [Member Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Les fichiers compilés avec [/LN](../build/reference/ln-create-msil-module.md) ne sont pas affectés par ce comportement. Dans ce cas, toutes les classes managées (public ou privées) seront visibles.

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
