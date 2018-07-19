---
title: Modèles (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- template_cpp
dev_langs:
- C++
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 673eadf3651d15f480ee2cff9ef3f7319dee4d84
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942905"
---
# <a name="templates-c"></a>Modèles (C++)
Les modèles constituent la base pour la programmation générique dans C++. Comme un langage fortement typé, C++ exige que toutes les variables pour avoir un type spécifique, soit explicitement déclarée par le programmeur soit déduit par le compilateur. Toutefois, plusieurs algorithmes et structures de données identiques, quel que soit le type qu’ils fonctionnent sur. Ces derniers permettent de définir les opérations d’une classe ou une fonction, et permettent à l’utilisateur de spécifier quels concret types ces opérations doit fonctionner sur.  
  
## <a name="defining-and-using-templates"></a>Définition et utilisation de modèles  
 Un modèle est une construction qui génère un type ordinaire ou une fonction au moment de la compilation en fonction des arguments de l’utilisateur fournit des paramètres du modèle. Par exemple, vous pouvez définir un modèle de fonction comme suit :  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Le code ci-dessus décrit un modèle pour une fonction générique avec un seul paramètre de type `T`, dont la valeur de retour et appeler des paramètres (lhs et rhs) sont tous de ce type. Vous pouvez nommer un paramètre de type que vous comme, mais par convention unique majuscules sont couramment utilisés. `T` est un paramètre de modèle ; le **typename** mot clé indique que ce paramètre est un espace réservé pour un type. Lorsque la fonction est appelée, le compilateur remplace toutes les instances de `T` avec l’argument de type concret qui est spécifié par l’utilisateur ou déduit par le compilateur. Le processus dans lequel le compilateur génère une classe ou fonction à partir d’un modèle est appelée *instanciation de modèle*;   `minimum<int>` est une instanciation du modèle `minimum<T>`.  
  
 Par ailleurs, un utilisateur peut déclarer une instance du modèle qui est spécialisé pour int. Supposons que get_a() et get_b() sont des fonctions qui retournent une valeur int :  
  
```cpp 
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 Toutefois, car il s’agit d’un modèle de fonction et le compilateur peuvent déduire le type de `T` à partir des arguments `a` et `b`, vous pouvez l’appeler comme une fonction ordinaire :  
  
```cpp  
int i = minimum(a, b);  
```  
  
 Lorsque le compilateur rencontre cette dernière instruction, il génère une nouvelle fonction dans chaque occurrence de *T* dans le modèle est remplacé par **int**:  
  
```cpp 
  
      int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Les règles de la façon dont le compilateur effectue la déduction de type dans les modèles de fonction sont basées sur les règles pour les fonctions ordinaires. Pour plus d’informations, consultez [surcharger la résolution de modèle appels de fonction](../cpp/overload-resolution-of-function-template-calls.md).  
  
## <a id="type_parameters"></a> Paramètres de type  
 Dans le `minimum` modèle ci-dessus, notez que le paramètre de type `T` n’est pas qualifié en aucune façon jusqu'à ce qu’il est utilisé dans les paramètres d’appel de fonction, où la const et qualificateurs de référence sont ajoutés.  
  
 Il n’existe aucune limite pratique au nombre de paramètres de type. Séparez plusieurs paramètres par des virgules :  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
  
```  
  
 Le mot clé **classe** équivaut à **typename** dans ce contexte. Vous pouvez exprimer l’exemple précédent en tant que :  
  
```cpp 
template <class T, class U, class V> class Foo{};   
```  
  
 Vous pouvez utiliser l’opérateur de points de suspension (...) pour définir un modèle qui accepte un nombre arbitraire de zéro ou plusieurs paramètres de type :  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 N’importe quel type intégré ou défini par l’utilisateur peut être utilisé comme argument de type. Par exemple, vous pouvez utiliser std::vector dans la bibliothèque Standard pour stocker des entiers, des doubles, des chaînes, MyClass, MyClass const *, MyClass &. La principale restriction lors de l’utilisation de modèles est qu’un argument de type doit prendre en charge toutes les opérations qui sont appliquées aux paramètres de type. Par exemple, si nous appelons minimale à l’aide de MyClass comme dans cet exemple :  
  
```cpp  
class MyClass  
{  
public:  
    int num;  
    std::wstring description;  
};  
  
int main()  
{      
    MyClass mc1 {1, L"hello"};  
    MyClass mc2 {2, L"goodbye"};  
    auto result = minimum(mc1, mc2); // Error! C2678  
}  
  
```  
  
 Une erreur du compilateur est générée car MyClass ne fournit pas une surcharge pour le < opérateur.  
  
 Bien que vous pouvez définir un modèle qui impose une restriction de ce type n’est pas obligatoire inhérente que les arguments de type pour n’importe quel modèle particulier à tous les appartiennent à la même hiérarchie d’objets. Vous pouvez combiner des techniques orientées objet avec des modèles ; par exemple, vous pouvez stocker un dérivé * dans un vecteur\<Base\*>.    Notez que les arguments doivent être des pointeurs  
  
```cpp 
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 Les exigences de base vecteur et autres conteneurs de bibliothèque standard imposent sur les éléments de `T` qui est `T` être copie-assignable et constructible de copie.  
  
## <a name="non-type-parameters"></a>Paramètres sans type  
 Contrairement aux types génériques dans d’autres langages tels que c# et Java, les modèles C++ prend en charge les paramètres sans type, également appelées paramètres de valeur. Par exemple, vous pouvez fournir une valeur constante intégrale pour spécifier la longueur d’un tableau, comme dans cet exemple est similaire à la classe std::array dans la bibliothèque Standard :  
  
```cpp 
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
  
```  
  
 Notez la syntaxe dans la déclaration de modèle. La valeur size_t est transmise comme argument de modèle au moment de la compilation et doit être une constante ou une expression constexpr. Vous l’utilisez comme suit :  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 Autres types de valeurs, y compris des pointeurs et références peuvent être passés en tant que paramètres de type non. Par exemple, vous pouvez passer un pointeur à une fonction ou un objet de fonction à personnaliser une opération dans le code du modèle.  
  
## <a id="template_parameters"></a> Modèles en tant que paramètres de modèle  
 Un modèle peut être un paramètre de modèle. Dans cet exemple, MyClass2 a deux paramètres de modèle : un paramètre typename `T` et un paramètre de modèle `Arr`:  
  
```cpp  
template<typename T, template<typename U, int I> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
    U u; //Error. U not in scope  
};  
```  
  
 Étant donné que le `Arr` paramètre lui-même n’a aucun corps, ses noms de paramètre ne sont pas nécessaires. En fait, il est une erreur pour faire référence à `Arr`de typename ou classe noms de paramètres à partir du corps de `MyClass2`. Pour cette raison, `Arr`de noms de paramètre de type peuvent être omis, comme illustré dans cet exemple :  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>Arguments template par défaut  
 Les modèles de classe et de fonction peuvent avoir des arguments par défaut. Quand un modèle a un argument par défaut que vous pouvez laisser il n’est pas spécifié lorsque vous l’utilisez. Par exemple, le modèle de std::vector a un argument par défaut pour l’allocateur :  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 Dans la plupart des cas, la classe de std::allocator par défaut est acceptable, vous donc utiliser un vecteur comme suit :  
  
```cpp  
vector<int> myInts;  
```  
  
 Mais si nécessaire vous pouvez spécifier un allocateur personnalisé comme ceci :  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 Pour plusieurs arguments template, tous les arguments après le premier argument par défaut doivent avoir des arguments par défaut.  
  
 Lorsque vous utilisez un modèle dont les paramètres sont tous définis par défaut, utilisez des crochets pointus :  
  
```cpp  
template<typename A = int, typename B = double>  
class Bar  
{  
    //...  
};  
...  
int main()  
{  
    Bar<> bar; // use all default type arguments  
}  
  
```  
  
## <a name="template-specialization"></a>Spécialisation de modèle  
 Dans certains cas, il n’est pas possible ou souhaitable pour un modèle définir exactement le même code pour n’importe quel type. Par exemple, vous pouvez être amené définir un chemin d’accès du code doit être exécuté uniquement si l’argument de type est un pointeur ou un littéral std::wstring, ou un type dérivé d’une classe de base.  Dans ce cas, vous pouvez définir un *spécialisation* du modèle pour ce type particulier. Lorsqu’un utilisateur instancie le modèle avec ce type, le compilateur utilise la spécialisation pour générer la classe, et pour tous les autres types, le compilateur choisit le modèle plus général. Sont des spécialisations dans lequel tous les paramètres sont spécialisées *terminer spécialisations*. Si seuls certains paramètres sont spécialisées, elle est appelée un *spécialisation partielle*.  
  
```cpp  
template <typename K, typename V>  
class MyMap{/*...*/};  
  
// partial specialization for string keys  
template<typename V>  
class MyMap<string, V> {/*...*/};  
...  
MyMap<int, MyClass> classes; // uses original template  
MyMap<string, MyClass> classes2; // uses the partial specialization  
  
```  
  
 Un modèle peut avoir un nombre quelconque de spécialisations tant que chaque paramètre de type spécialisé est unique.   Seuls les modèles de classe peuvent être partiellement spécialisés. Toutes les spécialisations complètes et partielles d’un modèle doivent être déclarées dans le même espace de noms en tant que le modèle d’origine.  
  
 Pour plus d’informations, consultez [spécialisation de modèle](../cpp/template-specialization-cpp.md).