---
title: Windows Runtime et modèles gérés (C++/CLI and C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: 5765370e611e5822b3b2d156d2eee5d21e5b453d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376307"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows Runtime et modèles gérés (C++/CLI and C++/CX)

Les modèles permettent de définir le prototype d’un type Windows Runtime ou common language runtime, puis instancient les variantes de ce type à l’aide des différents paramètres de type de modèle.

## <a name="all-runtimes"></a>Tous les runtimes

Vous pouvez créer des modèles à partir des types valeur ou référence.  Pour plus d’informations sur les types référence ou valeur, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

Pour plus d’informations sur les modèles de classe C++ standard, consultez [Modèles de classe](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Windows Runtime

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

La création de modèles de classe à partir de types managés comporte des limitations, présentées dans les exemples de code suivants.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

Il est possible d’instancier un type générique avec un paramètre de modèle de type managé, mais vous ne pouvez pas instancier un modèle managé avec un paramètre de modèle de type générique. C’est parce que les types génériques sont résolus au moment du runtime. Pour plus d’informations, consultez [Génériques et modèles (C++/CLI)](generics-and-templates-visual-cpp.md).

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

Un type ou une fonction générique ne peut pas être imbriqué dans un modèle managé.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Vous ne pouvez pas accéder aux modèles définis dans un assembly référencé avec une syntaxe de langage C++/CLI, mais vous pouvez utiliser la réflexion. Si un modèle n’est pas instantané, il n’est pas émis dans les métadonnées. Si un modèle est instancié, seules les fonctions membres référencées s’affichent dans les métadonnées.

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

Vous pouvez modifier le modificateur managé d’une classe dans une spécialisation partielle ou une spécialisation explicite d’un modèle de classe.

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
