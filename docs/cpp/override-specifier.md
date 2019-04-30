---
title: Spécificateur de substitution
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 71505f8b9b4dc2800e80a78a64f0ca6984af1349
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345869"
---
# <a name="override-specifier"></a>Spécificateur de substitution

Vous pouvez utiliser la **remplacer** mot clé pour désigner les fonctions qui remplacent une fonction virtuelle dans une classe de base de membre.

## <a name="syntax"></a>Syntaxe

```
function-declaration override;
```

## <a name="remarks"></a>Notes

**substituer** est contextuel et a spéciales, ce qui signifie que lorsqu’il est utilisé après une déclaration de fonction membre ; sinon, il n’est pas un mot clé réservé.

## <a name="example"></a>Exemple

Utilisez **remplacer** permettant d’empêcher le comportement d’héritage inopportun dans votre code. L’exemple suivant indique où, sans utiliser **remplacer**, le comportement de la fonction membre de la classe dérivée ne peut-être pas avoir été conçu. Le compilateur n'émet pas d'erreurs pour ce code.

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

Lorsque vous utilisez **remplacer**, le compilateur génère des erreurs au lieu de créer en mode silencieux à nouveau membre de fonctions.

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

Pour spécifier que les fonctions ne peut pas être substituées et que les classes ne peut pas être héritées, utilisez le [finale](../cpp/final-specifier.md) mot clé.

## <a name="see-also"></a>Voir aussi

[final, spécificateur](../cpp/final-specifier.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)