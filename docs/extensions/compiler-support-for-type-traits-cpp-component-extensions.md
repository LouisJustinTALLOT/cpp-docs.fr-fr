---
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
ms.openlocfilehash: 1bfb4308dc76e3393eceddf8dedd6d11e73adc17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172528"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Prise en charge du compilateur pour les traits de type (C++/CLI et C++/CX)

Le compilateur Microsoft C++ prend en charge les *traits de type* pour C++/CLI et les extensions C++/CX. Ils indiquent diverses caractéristiques d’un type au moment de la compilation.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Notes

Les traits de type s'avèrent particulièrement utiles pour les programmeurs qui écrivent des bibliothèques.

La liste suivante répertorie les traits de type pris en charge par le compilateur. Tous les traits de type retournent **false** si la condition spécifiée par le nom du trait de type n’est pas remplie.

(Dans la liste suivante, les exemples de code sont écrits uniquement en C++/CLI. Mais le trait de type correspondant est également pris en charge dans C++/CX sauf indication contraire. Le terme « type de plateforme » fait référence aux types Windows Runtime ou aux types du Common Language Runtime.)

- *type* de `__has_assign(` `)`

   Retourne la valeur **true** si le type de plateforme ou le type natif possède un opérateur d’assignation de copie.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- *type* de `__has_copy(` `)`

   Retourne la valeur **true** si le type de plateforme ou natif possède un constructeur de copie.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- *type* de `__has_finalizer(` `)`

   (Non pris en C++charge dans/CX.) Retourne la **valeur true** si le type CLR a un finaliseur. Pour plus d’informations, consultez [destructeurs et finaliseurs dans Guide pratique pour définir et consommerC++des classes et des structs (/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) .

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

- *type* de `__has_nothrow_assign(` `)`

   Retourne la valeur **true** si un opérateur d’assignation de copie a une spécification d’exception vide.

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

- *type* de `__has_nothrow_constructor(` `)`

   Retourne la valeur **true** si le constructeur par défaut a une spécification d’exception vide.

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

- *type* de `__has_nothrow_copy(` `)`

   Retourne la valeur **true** si le constructeur de copie a une spécification d’exception vide.

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

- *type* de `__has_trivial_assign(` `)`

   Retourne la valeur **true** si le type a un opérateur d’assignation trivial généré par le compilateur.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *type* de `__has_trivial_constructor(` `)`

   Retourne la valeur **true** si le type a un constructeur trivial généré par le compilateur.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *type* de `__has_trivial_copy(` `)`

   Retourne la valeur **true** si le type a un constructeur de copie trivial généré par le compilateur.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *type* de `__has_trivial_destructor(` `)`

   Retourne la valeur **true** si le type a un destructeur trivial généré par le compilateur.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *type* de `__has_user_destructor(` `)`

   Retourne la valeur **true** si le type de plateforme ou natif a un destructeur déclaré par l’utilisateur.

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

- *type* de `__has_virtual_destructor(` `)`

   Retourne la valeur **true** si le type a un destructeur virtuel.

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

- *type* de `__is_abstract(` `)`

   Retourne la valeur **true** si le type est un type abstract. Pour plus d’informations sur les types abstract natifs, consultez [Classes abstract](../cpp/abstract-classes-cpp.md).

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

   Retourne la valeur **true** si le premier type est une classe de base du second type, ou si ces deux types sont les mêmes.

   `__is_base_of` fonctionne également sur les types de plateforme. Par exemple, la valeur **true** est retournée si le premier type est une [classe d’interface](interface-class-cpp-component-extensions.md) et que le second type implémente l’interface.

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

- *type* de `__is_class(` `)`

   Retourne la valeur **true** si le type est une classe native ou un struct natif.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,``to` `)`

   Retourne la valeur **true** si le premier type peut être converti en second type.

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

- *type* de `__is_delegate(` `)`

   Retourne la valeur **true** si `type` est un délégué. Pour plus d’informations, consultez [délégué (C++/CLI et C++/CX)](delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- *type* de `__is_empty(` `)`

   Retourne la valeur **true** si le type ne possède aucun membre de données d’instance.

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

- *type* de `__is_enum(` `)`

   Retourne la valeur **true** si le type est un enum natif.

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

- *type* de `__is_interface_class(` `)`

   Retourne la valeur **true** si une interface de plateforme est passée. Pour plus d’informations, consultez [classe d’interface](interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- *type* de `__is_pod(` `)`

   Retourne la valeur **true** si le type est une classe ou une union sans aucun constructeur ni aucun membre non static privé ou protégé, ni aucune classe de base ni aucune fonction virtuelle. Consultez la norme C++, sections 8.5.1/1, 9/4 et 3.9/10 pour plus d'informations sur les POD.

   `__is_pod` retourne la valeur false sur les types fondamentaux.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *type* de `__is_polymorphic(` `)`

   Retourne la valeur **true** si un type natif possède des fonctions virtuelles.

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

- *type* de `__is_ref_array(` `)`

   Retourne la valeur **true** si un tableau de plateforme est passé. Pour plus d’informations, consultez [Tableaux](arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- *type* de `__is_ref_class(` `)`

   Retourne la valeur **true** si une classe de référence est passée. Pour plus d’informations sur les types référence définis par l’utilisateur, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- *type* de `__is_sealed(` `)`

   Retourne la valeur **true** si un type de plateforme ou un type natif marqué comme sealed est passé. Pour plus d’informations, consultez [sealed](sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- *type* de `__is_simple_value_class(` `)`

   Retourne la valeur **true** si un type valeur qui ne contient aucune référence au tas récupéré par le garbage collector est passé. Pour plus d’informations sur les types valeur définis par l’utilisateur, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

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

- *type* de `__is_union(` `)`

   Retourne la valeur **true** si un type est une union.

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

- *type* de `__is_value_class(` `)`

   Retourne la valeur **true** si un type valeur est passé. Pour plus d’informations sur les types valeur définis par l’utilisateur, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

Le trait de type `__has_finalizer(`*type*`)` n’est pas pris en charge car cette plateforme ne prend pas en charge les finaliseurs.

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

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
