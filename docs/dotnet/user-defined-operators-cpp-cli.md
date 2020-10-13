---
title: Opérateurs définis par l'utilisateur (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: ee5aa122983a315e55884c643a9b7894f075e260
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008946"
---
# <a name="user-defined-operators-ccli"></a>Opérateurs définis par l'utilisateur (C++/CLI)

Les opérateurs définis par l’utilisateur pour les types managés sont autorisés en tant que membres statiques ou membres d’instance, ou au niveau de la portée globale. Toutefois, seuls les opérateurs statiques sont accessibles par le biais de métadonnées aux clients écrits dans un langage autre que Visual C++.

Dans un type référence, l’un des paramètres d’un opérateur statique défini par l’utilisateur doit être l’un des suivants :

- Handle ( `type` ^) vers une instance du type englobant.

- Indirection de type référence ( `type` ^& ou type ^%) à un handle vers une instance du type englobant.

Dans un type valeur, l’un des paramètres d’un opérateur statique défini par l’utilisateur doit être l’un des suivants :

- Du même type que le type valeur englobante.

- Indirection de type pointeur ( `type` ^) vers le type englobant.

- Indirection de type référence ( `type` % ou `type`&) vers le type englobant.

- Indirection de type référence ( `type` ^% ou `type` ^&) vers le descripteur.

Vous pouvez définir les opérateurs suivants :

|Opérateur|Formulaires unaires/binaires ?|
|--------------|--------------------------|
|!|Unaire|
|!=|Binary|
|%|Binary|
|&|Unaire et binaire|
|&&|Binary|
|*|Unaire et binaire|
|+|Unaire et binaire|
|++|Unaire|
|,|Binary|
|-|Unaire et binaire|
|--|Unaire|
|->|Unaire|
|/|Binary|
|<|Binary|
|<<|Binary|
|\<=|Binary|
|=|Binary|
|==|Binary|
|>|Binary|
|>=|Binary|
|>>|Binary|
|^|Binary|
|false|Unaire|
|true|Unaire|
|&#124;|Binary|
|&#124;&#124;|Binary|
|~|Unaire|

## <a name="example-user-defined-operators"></a>Exemple : opérateurs définis par l’utilisateur

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example-operator-synthesis"></a>Exemple : synthèse d’opérateur

L’exemple suivant illustre la synthèse d’opérateur, qui n’est disponible que lorsque vous utilisez **/CLR** pour compiler. La synthèse d’opérateur crée la forme d’assignation d’un opérateur binaire, si aucune n’est définie, où la partie gauche de l’opérateur d’assignation a un type CLR.

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md)
