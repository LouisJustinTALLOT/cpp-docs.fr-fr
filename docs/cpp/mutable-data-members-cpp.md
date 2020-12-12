---
description: 'En savoir plus sur : données membres mutables (C++)'
title: Membres de données mutables (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: a288b382b456fa313c49832bd2d13aaceb269be9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313812"
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
