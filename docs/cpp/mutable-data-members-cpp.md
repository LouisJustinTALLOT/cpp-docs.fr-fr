---
title: Données membres mutables (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de0a208341e6a687d1319c4d8d60cc8671555dd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106991"
---
# <a name="mutable-data-members-c"></a>Membres de données mutables (C++)

Ce mot clé peut être appliqué uniquement aux données membres non statiques et non constantes d'une classe. Si un membre de données est déclaré **mutable**, puis il est permis d’assigner une valeur à ce membre de données à partir d’un **const** fonction membre.

## <a name="syntax"></a>Syntaxe

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Notes

Par exemple, le code suivant sera compilé sans erreur, car `m_accessCount` a été déclarée comme étant **mutable**et peut donc être modifié par `GetFlag` même si `GetFlag` est une fonction membre const.

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