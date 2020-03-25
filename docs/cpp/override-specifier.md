---
title: Spécificateur de substitution
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 82837ae34ab786e607df54038493b14350574a15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188478"
---
# <a name="override-specifier"></a>Spécificateur de substitution

Vous pouvez utiliser le mot clé **override** pour désigner des fonctions membres qui remplacent une fonction virtuelle dans une classe de base.

## <a name="syntax"></a>Syntaxe

```
function-declaration override;
```

## <a name="remarks"></a>Notes

**override** est sensible au contexte et a une signification spéciale uniquement lorsqu’il est utilisé après une déclaration de fonction membre ; dans le cas contraire, il ne s’agit pas d’un mot clé réservé.

## <a name="example"></a>Exemple

Utilisez **override** pour empêcher un comportement d’héritage inopportun dans votre code. L’exemple suivant indique où, sans utiliser **override**, le comportement de la fonction membre de la classe dérivée n’a peut-être pas été prévu. Le compilateur n'émet pas d'erreurs pour ce code.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

Quand vous utilisez **override**, le compilateur génère des erreurs au lieu de créer silencieusement de nouvelles fonctions membres.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

Pour spécifier que les fonctions ne peuvent pas être substituées et que les classes ne peuvent pas être héritées, utilisez le mot clé [final](../cpp/final-specifier.md) .

## <a name="see-also"></a>Voir aussi

[final, spécificateur](../cpp/final-specifier.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
