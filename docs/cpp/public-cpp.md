---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: dd45430543ead7258096be8f3d8cef0141f27b4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179190"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Syntaxe

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Notes

Lorsqu’il précède une liste de membres de classe, le mot clé **public** spécifie que ces membres sont accessibles à partir de n’importe quelle fonction. Cela s'applique à tous les membres déclarés jusqu'au spécificateur d'accès suivant de la classe.

Quand il précède le nom d’une classe de base, le mot clé **public** spécifie que les membres publics et protégés de la classe de base sont des membres publics et protégés, respectivement, de la classe dérivée.

L'accès par défaut des membres d'une classe est privé. L'accès par défaut des membres d'une structure ou d'une union est public.

L'accès par défaut d'une classe de base est privé pour les classes et public pour les structures. Les unions ne peuvent pas avoir de classes de base.

Pour plus d’informations, consultez [Private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md), [Friend](../cpp/friend-cpp.md)et la table d’accès aux membres dans [contrôle de l’accès aux membres de classe](member-access-control-cpp.md).

## <a name="clr-specific"></a>Spécifique /clr

Dans les types CLR, C++ les mots clés de spécificateur d’accès (**public**, **privé**et **protégé**) peuvent affecter la visibilité des types et des méthodes en ce qui concerne les assemblys. Pour plus d’informations, consultez [Member Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Les fichiers compilés avec [/LN](../build/reference/ln-create-msil-module.md) ne sont pas affectés par ce comportement. Dans ce cas, toutes les classes managées (public ou privées) seront visibles.

## <a name="end-clr-specific"></a>Spécifique END /clr

## <a name="example"></a>Exemple

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>Voir aussi

[Contrôle de l’accès aux membres de classe](member-access-control-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
