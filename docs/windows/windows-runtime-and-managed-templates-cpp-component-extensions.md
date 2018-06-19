---
title: Windows Runtime et modèles gérés (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e9053b101428ac26e96446d9c6756ec5de35e06c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891361"
---
# <a name="windows-runtime-and-managed-templates-c-component-extensions"></a>Windows Runtime et modèles gérés (extensions du composant C++)
Les modèles vous permettent de définir un prototype d’un type common language runtime ou le Windows Runtime et ensuite instancier des variantes de ce type à l’aide des paramètres de type de modèle différent.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 Vous pouvez créer des modèles à partir des types valeur ou référence.  Pour plus d’informations sur la création de types valeur ou référence, consultez [les Classes et Structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Pour plus d’informations sur les modèles de classe C++ standards, consultez [les modèles de classe](../cpp/class-templates.md).  
  
## <a name="windows-runtime"></a>Windows Runtime  
 (Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 Il existe certaines limitations à la création de modèles de classe à partir de types managés, qui sont illustrées dans les exemples de code suivant.  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 Il est possible d’instancier un type générique avec un paramètre de modèle de type managé, mais vous ne pouvez pas instancier un modèle géré avec un paramètre de modèle de type générique.  Il s’agit, car les types génériques sont résolues au moment de l’exécution.  Pour plus d’informations, consultez [génériques et les modèles (Visual C++)](../windows/generics-and-templates-visual-cpp.md).  
  
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
  
 **Exemple**  
  
 Un type générique ou une fonction ne peut pas être imbriquée dans un modèle géré.  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **Exemple**  
  
 Impossible d’accéder aux modèles définis dans un assembly référencé avec C + c++ / syntaxe du langage CLI, mais vous pouvez utiliser la réflexion.  Si un modèle n’est pas instancié, il n’est pas émis dans les métadonnées.  Si un modèle est instancié, seules les fonctions de membre référencé seront affiche dans les métadonnées.  
  
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
  
 **Exemple**  
  
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
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)