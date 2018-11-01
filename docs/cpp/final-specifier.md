---
title: Spécificateur final
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: c6400c8060664713fdd004a5aa9536e0617bc0c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588082"
---
# <a name="final-specifier"></a>Spécificateur final

Vous pouvez utiliser la **finale** mot clé pour désigner les fonctions virtuelles qui ne peut pas être substituées dans une classe dérivée. Vous pouvez également l'utiliser pour désigner les classes qui ne peuvent pas être héritées.

## <a name="syntax"></a>Syntaxe

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Notes

**finale** est contextuel et a une signification spéciale uniquement lorsqu’il est utilisé après une déclaration de fonction ou le nom de classe ; sinon, il n’est pas un mot clé réservé.

Lorsque **finale** est utilisé dans les déclarations de classe, `base-classes` est une partie facultative de la déclaration.

## <a name="example"></a>Exemple

L’exemple suivant utilise le **finale** mot clé pour spécifier qu’une fonction virtuelle ne peut pas être substituée.

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

Pour plus d’informations sur la façon de spécifier que les fonctions membres peuvent être remplacées, consultez [spécificateur de substitution](../cpp/override-specifier.md).

L’exemple suivant utilise le **finale** mot clé pour spécifier qu’une classe ne peut pas être héritée.

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
[override, spécificateur](../cpp/override-specifier.md)