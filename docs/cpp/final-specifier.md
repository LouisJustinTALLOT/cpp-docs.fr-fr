---
description: 'En savoir plus sur : spécificateur final'
title: Spécificateur final
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: 5fd6ee3c23a455c4316593cc089c26c34477709d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242610"
---
# <a name="final-specifier"></a>Spécificateur final

Vous pouvez utiliser le mot clé **final** pour désigner des fonctions virtuelles qui ne peuvent pas être substituées dans une classe dérivée. Vous pouvez également l'utiliser pour désigner les classes qui ne peuvent pas être héritées.

## <a name="syntax"></a>Syntaxe

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Notes

**final** est contextuel et a une signification spéciale uniquement lorsqu’il est utilisé après une déclaration de fonction ou un nom de classe ; dans le cas contraire, il ne s’agit pas d’un mot clé réservé.

Lorsque **final** est utilisé dans les déclarations de classe, `base-classes` est une partie facultative de la déclaration.

## <a name="example"></a>Exemple

L’exemple suivant utilise le mot clé **final** pour spécifier qu’une fonction virtuelle ne peut pas être substituée.

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

Pour plus d’informations sur la façon de spécifier que les fonctions membres peuvent être substituées, consultez [spécificateur de substitution](../cpp/override-specifier.md).

L’exemple suivant utilise le mot clé **final** pour spécifier qu’une classe ne peut pas être héritée.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Spécificateur de substitution](../cpp/override-specifier.md)
