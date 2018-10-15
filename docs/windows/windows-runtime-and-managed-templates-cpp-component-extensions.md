---
title: Windows Runtime et modèles gérés (C++ / c++ / CLI et c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b83aa54b9f9697fddbefc6da29e7cf99d497cc12
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328296"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows Runtime et modèles gérés (C++ / c++ / CLI et c++ / CX)

Les modèles vous permettent de définir un prototype d’un Runtime de Windows ou d’un type common language runtime et instancie ensuite les variantes de ce type à l’aide des paramètres de type de modèle différent.

## <a name="all-runtimes"></a>Tous les runtimes

Vous pouvez créer des modèles à partir des types valeur ou référence.  Pour plus d’informations sur la création des types valeur ou référence, consultez [les Classes et Structs](../windows/classes-and-structs-cpp-component-extensions.md).

Pour plus d’informations sur les modèles de classe C++ standards, consultez [modèles de classe](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Windows Runtime

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Il existe certaines limitations à la création de modèles de classe à partir de types managés, qui sont illustrées dans les exemples de code suivants.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

Il est possible d’instancier un type générique avec un paramètre de modèle de type managé, mais vous ne pouvez pas instancier un modèle géré avec un paramètre de modèle de type générique. Il s’agit, car les types génériques sont résolues lors de l’exécution. Pour plus d’informations, consultez [génériques et modèles (C++ / c++ / CLI)](../windows/generics-and-templates-visual-cpp.md).

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

Un type générique ou une fonction ne peut pas être imbriquée dans un modèle géré.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Vous ne pouvez pas accéder aux modèles définis dans un assembly référencé avec C++ / c++ / syntaxe du langage CLI, mais vous pouvez utiliser la réflexion. Si un modèle n’est pas instancié, il n’est pas émis dans les métadonnées. Si un modèle est instancié, seules les fonctions de membre référencé seront affiche dans les métadonnées.

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

Vous pouvez modifier le modificateur managé d’une classe dans une spécialisation partielle ou d’une spécialisation explicite d’un modèle de classe.

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

[Extensions de composant pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)