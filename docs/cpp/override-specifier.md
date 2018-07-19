---
title: Spécificateur de substitution | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50ffc096cc710f4028c7effc2dda8822f077f29
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940652"
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
 [Spécificateur final](../cpp/final-specifier.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 