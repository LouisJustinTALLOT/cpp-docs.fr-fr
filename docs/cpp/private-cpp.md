---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 002a8ad2887bd711bc3654d8e8910e2bede889d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177558"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Syntaxe

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Notes

Lorsqu’il précède une liste de membres de classe, le mot clé **Private** spécifie que ces membres sont accessibles uniquement à partir des fonctions membres et des Friends de la classe. Cela s'applique à tous les membres déclarés jusqu'au spécificateur d'accès suivant de la classe.

Quand il précède le nom d’une classe de base, le mot clé **Private** spécifie que les membres publics et protégés de la classe de base sont des membres privés de la classe dérivée.

L'accès par défaut des membres d'une classe est privé. L'accès par défaut des membres d'une structure ou d'une union est public.

L'accès par défaut d'une classe de base est privé pour les classes et public pour les structures. Les unions ne peuvent pas avoir de classes de base.

Pour obtenir des informations connexes, consultez [Friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [protected](../cpp/protected-cpp.md)et la table d’accès aux membres dans [contrôle de l’accès aux membres de classe](member-access-control-cpp.md).

## <a name="clr-specific"></a>Spécifique /clr

Dans les types CLR, C++ les mots clés de spécificateur d’accès (**public**, **privé**et **protégé**) peuvent affecter la visibilité des types et des méthodes en ce qui concerne les assemblys. Pour plus d’informations, consultez [Member Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Les fichiers compilés avec [/LN](../build/reference/ln-create-msil-module.md) ne sont pas affectés par ce comportement. Dans ce cas, toutes les classes managées (public ou privées) seront visibles.

## <a name="end-clr-specific"></a>Spécifique END /clr

## <a name="example"></a>Exemple

```cpp
// keyword_private.cpp
class BaseClass {
public:
   // privMem accessible from member function
   int pubFunc() { return privMem; }
private:
   void privMem;
};

class DerivedClass : public BaseClass {
public:
   void usePrivate( int i )
      { privMem = i; }   // C2248: privMem not accessible
                         // from derived class
};

class DerivedClass2 : private BaseClass {
public:
   // pubFunc() accessible from derived class
   int usePublic() { return pubFunc(); }
};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   DerivedClass2 aDerived2;
   aBase.privMem = 1;     // C2248: privMem not accessible
   aDerived.privMem = 1;  // C2248: privMem not accessible
                          //    in derived class
   aDerived2.pubFunc();   // C2247: pubFunc() is private in
                          //    derived class
}
```

## <a name="see-also"></a>Voir aussi

[Contrôle de l’accès aux membres de classe](member-access-control-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
