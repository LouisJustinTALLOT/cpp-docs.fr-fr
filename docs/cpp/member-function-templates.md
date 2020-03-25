---
title: Modèles de fonctions membres
ms.date: 11/04/2016
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
ms.openlocfilehash: ee36d4f33f3e4216e2ad9c434ac1da4ca3aa83e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177979"
---
# <a name="member-function-templates"></a>Modèles de fonctions membres

Le terme « modèle membre » fait référence aux modèles de fonction membre et aux modèles de classes imbriqués. Les modèles de fonction membre sont des fonctions de modèle qui sont membres d'une classe ou d'un modèle de classe.

Les fonctions membres peuvent être des modèles de fonction dans plusieurs contextes. Toutes les fonctionnalités des modèles de classe sont génériques, mais ne sont pas appelés modèles membres ou modèles de fonction membre. Si ces fonctions membres prennent leurs propres arguments template, elles sont considérées comme des modèles de fonction membre.

## <a name="example"></a>Exemple

Les modèles de fonction membre de classes de modèles ou de classes non basées sur un modèle sont déclarés comme modèles de fonction avec leurs paramètres de modèle.

```cpp
// member_function_templates.cpp
struct X
{
   template <class T> void mf(T* t) {}
};

int main()
{
   int i;
   X* x = new X();
   x->mf(&i);
}
```

## <a name="example"></a>Exemple

L'exemple suivant montre un modèle de fonction membre d'une classe de modèle.

```cpp
// member_function_templates2.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u)
   {
   }
};

int main()
{
}
```

## <a name="example"></a>Exemple

```cpp
// defining_member_templates_outside_class.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u);
};

template<typename T> template <typename U>
void X<T>::mf(const U &u)
{
}

int main()
{
}
```

## <a name="example"></a>Exemple

Les classes locales ne doivent pas avoir de modèles membres.

Les fonctions des modèles membres ne peuvent pas être des fonctions virtuelles et ne peuvent pas remplacer des fonctions virtuelles d'une classe de base lorsqu'elles sont déclarées avec le même nom qu'une fonction virtuelle d'une classe de base.

L’exemple suivant montre une conversion définie par l’utilisateur basée sur un modèle :

```cpp
// templated_user_defined_conversions.cpp
template <class T>
struct S
{
   template <class U> operator S<U>()
   {
      return S<U>();
   }
};

int main()
{
   S<int> s1;
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.
}
```

## <a name="see-also"></a>Voir aussi

[Modèles de fonctions](../cpp/function-templates.md)
