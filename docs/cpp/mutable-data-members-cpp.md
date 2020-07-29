---
title: Membres de données mutables (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 9370952f503850fbc296c3df912d4a0fafe163f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227346"
---
# <a name="mutable-data-members-c"></a>Membres de données mutables (C++)

Ce mot clé peut être appliqué uniquement aux données membres non statiques et non constantes d'une classe. Si un membre de données est déclaré **`mutable`** , il est légal d’assigner une valeur à ce membre de données à partir d’une **`const`** fonction membre.

## <a name="syntax"></a>Syntaxe

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Notes

Par exemple, le code suivant est compilé sans erreur, car `m_accessCount` a été déclaré comme étant **`mutable`** et peut donc être modifié par `GetFlag` même si `GetFlag` est une fonction membre const.

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
