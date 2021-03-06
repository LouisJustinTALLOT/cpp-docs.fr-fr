---
description: 'En savoir plus sur : prise en charge du compilateur pour les traits de type (C++/CLI et C++/CX)'
title: Prise en charge du compilateur pour les traits de type (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
ms.openlocfilehash: ec9efe1305a844779b4848cbae155d2946488d11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176923"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Prise en charge du compilateur pour les traits de type (C++/CLI et C++/CX)

Le compilateur Microsoft C++ prend en charge les *traits de type* pour C++/CLI et les extensions C++/CX. Ils indiquent diverses caractéristiques d’un type au moment de la compilation.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Notes

Les traits de type s'avèrent particulièrement utiles pour les programmeurs qui écrivent des bibliothèques.

La liste suivante répertorie les traits de type pris en charge par le compilateur. Toutes les caractéristiques de type retournent **`false`** si la condition spécifiée par le nom du trait de type n’est pas remplie.

(Dans la liste suivante, les exemples de code sont écrits uniquement en C++/CLI. Mais le trait de type correspondant est également pris en charge dans C++/CX sauf indication contraire. Le terme « type de plateforme » fait référence aux types Windows Runtime ou aux types du Common Language Runtime.)

- `__has_assign(`*type*`)`

   Retourne **`true`** si la plateforme ou le type natif possède un opérateur d’assignation de copie.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(`*type*`)`

   Retourne **`true`** si la plateforme ou le type natif a un constructeur de copie.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(`*type*`)`

   (Non pris en charge en C++/CX.) Retourne **`true`** si le type CLR a un finaliseur. Pour plus d’informations, consultez [destructeurs et finaliseurs dans Guide pratique pour définir et consommer des classes et des structs (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) .

    ```cpp
    using namespace System;
    ref struct R {
    ~R() {}
    protected:
    !R() {}
    };

    int main() {
    Console::WriteLine(__has_finalizer(R));
    }
    ```

- `__has_nothrow_assign(`*type*`)`

   Retourne **`true`** si un opérateur d’assignation de copie a une spécification d’exception vide.

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(`*type*`)`

   Retourne **`true`** si le constructeur par défaut a une spécification d’exception vide.

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(`*type*`)`

   Retourne **`true`** si le constructeur de copie a une spécification d’exception vide.

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(`*type*`)`

   Retourne **`true`** si le type a un opérateur d’assignation trivial généré par le compilateur.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(`*type*`)`

   Retourne **`true`** si le type a un constructeur trivial généré par le compilateur.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(`*type*`)`

   Retourne **`true`** si le type a un constructeur de copie trivial généré par le compilateur.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(`*type*`)`

   Retourne **`true`** la valeur si le type a un destructeur trivial généré par le compilateur.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(`*type*`)`

   Retourne **`true`** si la plateforme ou le type natif possède un destructeur déclaré par l’utilisateur.

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(`*type*`)`

   Retourne **`true`** si le type a un destructeur virtuel.

   `__has_virtual_destructor` fonctionne également sur les types de plateforme et tout destructeur défini par l'utilisateur dans un type de plateforme est un destructeur virtuel.

    ```cpp
    // has_virtual_destructor.cpp
    #include <stdio.h>
    struct S {
    virtual ~S() {}
    };

    int main() {
    __has_virtual_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_abstract(`*type*`)`

   Retourne **`true`** si le type est un type abstrait. Pour plus d’informations sur les types abstract natifs, consultez [Classes abstract](../cpp/abstract-classes-cpp.md).

   `__is_abstract` fonctionne également pour les types de plateforme. Une interface avec au moins un membre est un type abstrait, à l'instar d'un type référence avec au moins un membre abstrait. Pour plus d’informations sur les types de plateforme abstraits, consultez [abstract](abstract-cpp-component-extensions.md).

    ```cpp
    // is_abstract.cpp
    #include <stdio.h>
    struct S {
    virtual void Test() = 0;
    };

    int main() {
    __is_abstract(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_base_of(` `base` `,` `derived` `)`

   Retourne **`true`** si le premier type est une classe de base du deuxième type, de si les deux types sont identiques.

   `__is_base_of` fonctionne également sur les types de plateforme. Par exemple, il retourne **`true`** si le premier type est une [classe d’interface](interface-class-cpp-component-extensions.md) et le second implémente l’interface.

    ```cpp
    // is_base_of.cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    __is_base_of(S, T) == true ?
    printf("true\n") : printf("false\n");

    __is_base_of(S, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_class(`*type*`)`

   Retourne **`true`** si le type est une classe ou un struct natif.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   Retourne **`true`** si le premier type peut être converti vers le second type.

    ```cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    S * s = new S;
    T * t = new T;
    s = t;
    __is_convertible_to(T, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_delegate(`*type*`)`

   Retourne **`true`** si `type` est un délégué. Pour plus d’informations, consultez [délégué (C++/CLI et C++/CX)](delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(`*type*`)`

   Retourne **`true`** si le type n’a pas de données membres d’instance.

    ```cpp
    #include <stdio.h>
    struct S {
    int Test() {}
    static int i;
    };
    int main() {
    __is_empty(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_enum(`*type*`)`

   Retourne **`true`** si le type est une énumération native.

    ```cpp
    // is_enum.cpp
    #include <stdio.h>
    enum E { a, b };

    struct S {
    enum E2 { c, d };
    };

    int main() {
    __is_enum(E) == true ?
    printf("true\n") : printf("false\n");

    __is_enum(S::E2) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_interface_class(`*type*`)`

   Retourne **`true`** si une interface de plateforme est passée. Pour plus d’informations, consultez [classe d’interface](interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(`*type*`)`

   Retourne **`true`** si le type est une classe ou une Union sans constructeur ni membre non statique privé ou protégé, aucune classe de base et aucune fonction virtuelle. Consultez la norme C++, sections 8.5.1/1, 9/4 et 3.9/10 pour plus d'informations sur les POD.

   `__is_pod` retourne la valeur false sur les types fondamentaux.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(`*type*`)`

   Retourne **`true`** si un type natif a des fonctions virtuelles.

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(`*type*`)`

   Retourne **`true`** si un tableau de plateforme est passé. Pour plus d’informations, consultez [Tableaux](arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(`*type*`)`

   Retourne **`true`** si une classe de référence a été passée. Pour plus d’informations sur les types référence définis par l’utilisateur, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(`*type*`)`

   Retourne **`true`** si une plateforme ou un type natif ont été marqués comme étant sealed. Pour plus d’informations, consultez [sealed](sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(`*type*`)`

   Retourne **`true`** si un type valeur qui ne contient aucune référence au tas récupéré par le garbage collector est passé. Pour plus d’informations sur les types valeur définis par l’utilisateur, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    value struct V {};
    value struct V2 {
    R ^ r;   // not a simnple value type
    };

    int main() {
    Console::WriteLine(__is_simple_value_class(V));
    Console::WriteLine(__is_simple_value_class(V2));
    }
    ```

- `__is_union(`*type*`)`

   Retourne **`true`** si un type est une Union.

    ```cpp
    #include <stdio.h>
    union A {
    int i;
    float f;
    };

    int main() {
    __is_union(A) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_value_class(`*type*`)`

   Retourne **`true`** si un type valeur est passé. Pour plus d’informations sur les types valeur définis par l’utilisateur, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

Le `__has_finalizer(`  `)` trait de type type n’est pas pris en charge, car cette plateforme ne prend pas en charge les finaliseurs.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

(Il n’existe aucune note spécifique à la plateforme pour cette fonctionnalité.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

**Exemple**

L'exemple de code suivant montre comment utiliser un modèle de classe pour exposer un trait de type de compilateur pour une compilation `/clr`. Pour plus d’informations, consultez [Windows Runtime et modèles managés](windows-runtime-and-managed-templates-cpp-component-extensions.md).

```cpp
// compiler_type_traits.cpp
// compile with: /clr
using namespace System;

template <class T>
ref struct is_class {
   literal bool value = __is_ref_class(T);
};

ref class R {};

int main () {
   if (is_class<R>::value)
      Console::WriteLine("R is a ref class");
   else
      Console::WriteLine("R is not a ref class");
}
```

```Output
R is a ref class
```

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
