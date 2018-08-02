---
title: 'Opérateur de résolution de portée : :: | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '::'
dev_langs:
- C++
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baf3678d204042bdea5e892a6e89d041b5091f38
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467077"
---
# <a name="scope-resolution-operator-"></a>Opérateur de résolution de portée : ::
L’opérateur de résolution de portée **::** sert à identifier et lever l’ambiguïté des identificateurs utilisés dans différentes portées. Pour plus d’informations sur l’étendue, consultez [étendue](../cpp/scope-visual-cpp.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
:: identifier  
class-name :: identifier  
namespace :: identifier  
enum class :: identifier  
enum struct :: identifier  
```  
  
## <a name="remarks"></a>Notes  
 `identifier` peut être une variable, une fonction ou une valeur d'énumération.  
  
## <a name="with-classes-and-namespaces"></a>Avec les classes et les espaces de noms  
 L'exemple suivant montre comment l'opérateur de résolution de portée est utilisé avec les espaces de noms et les classes :  
  
```cpp  
namespace NamespaceA{  
    int x;  
    class ClassA {  
    public:  
        int x;  
    };  
}  
  
int main() {  
  
    // A namespace name used to disambiguate  
    NamespaceA::x = 1;  
  
    // A class name used to disambiguate  
    NamespaceA::ClassA a1;  
    a1.x = 2;  
}  
```  
  
 Un opérateur de résolution de portée sans qualificateur de portée fait référence à l'espace de noms global.  
  
```cpp  
namespace NamespaceA{  
    int x;  
}  
  
int x;   
  
int main() {  
    int x;  
  
    // the x in main()  
    x = 0;   
    // The x in the global namespace  
    ::x = 1;   
  
    // The x in the A namespace  
    NamespaceA::x = 2;   
}  
```  
  
 Vous pouvez utiliser l'opérateur de résolution de portée pour identifier un membre d'un espace de noms ou un espace de noms désignant l'espace de noms du membre dans une directive using. Dans l'exemple ci-dessous, vous pouvez utiliser `NamespaceC` pour qualifier `ClassB`, même si `ClassB` a été déclaré dans l'espace de noms `NamespaceB`, car `NamespaceB` a été désigné dans `NamespaceC` à l'aide d'une directive.  
  
```cpp  
namespace NamespaceB {  
    class ClassB {  
    public:  
        int x;  
    };  
}  
  
namespace NamespaceC{  
    using namespace B;  
}  
int main() {  
    NamespaceB::ClassB c_b;  
    NamespaceC::ClassB c_c;  
  
    c_b.x = 3;  
    c_c.x = 4;  
}  
```  
  
 Vous pouvez utiliser des chaînes d'opérateurs de résolution de portée. Dans l'exemple suivant, `NamespaceD::NamespaceD1` identifie l'espace de noms imbriqué `NamespaceD1` et `NamespaceE::ClassE::ClassE1` identifie la classe imbriquée `ClassE1`.  
  
```cpp  
namespace NamespaceD{  
    namespace NamespaceD1{  
        int x;  
    }  
}  
  
namespace NamespaceE{  
    class ClassE{  
    public:  
        class ClassE1{  
        public:  
            int x;  
        };  
    };  
}  
  
int main() {  
    NamespaceD:: NamespaceD1::x = 6;  
    NamespaceE::ClassE::ClassE1 e1;  
    e1.x = 7  ;  
}  
```  
  
## <a name="with-static-members"></a>Avec des membres statiques  
 Vous devez utiliser l'opérateur de résolution de portée pour appeler des membres statiques de classes.  
  
```cpp  
class ClassG {  
public:  
    static int get_x() { return x;}  
    static int x;  
};  
  
int ClassG::x = 6;  
  
int main() {  
  
    int gx1 = ClassG::x;  
    int gx2 = ClassG::get_x();   
}  
```  
  
## <a name="with-scoped-enumerations"></a>Avec des énumérations délimitées  
 L’opérateur de résolution de portée est également utilisé avec les valeurs d’une énumération délimitée [déclarations d’énumération](../cpp/enumerations-cpp.md), comme dans l’exemple suivant :  
  
```cpp  
enum class EnumA{  
    First,  
    Second,  
    Third  
};  
  
int main() {  
    EnumA enum_value = EnumA::First;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs C++ intégrés, priorité et associativité](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Espaces de noms](../cpp/namespaces-cpp.md)   