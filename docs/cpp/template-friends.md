---
title: Friends de modèle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 077acea5-0d0f-4b33-916d-1211797e5e28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c5217b1860affd05f433c6a3bf944afeb6c13f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422122"
---
# <a name="template-friends"></a>Friends de modèle

Modèles de classe peuvent avoir [amis](friend-cpp.md). Une classe ou un modèle de classe, une fonction ou un modèle de fonction peuvent être des éléments friend d'une classe de modèle. Les éléments friend peuvent également être des spécialisations d'un modèle de classe ou de fonction, mais des spécialisations non partielles.  
  
**C++ 11**: un paramètre de type peut être déclaré en tant que friend à l’aide de la forme `friend T;`.  
  
```cpp
template <typename T>  
class my_class  
{  
    friend T;  
    //...  
};  
```  
  
## <a name="example"></a>Exemple

Dans l'exemple suivant, une fonction friend est définie en tant que modèle de fonction dans le modèle de classe. Ce code génère une version de la fonction friend pour chaque instanciation du modèle. Cette construction est utile si votre fonction friend dépend des mêmes paramètres de modèle que la classe.  
  
```cpp
// template_friend1.cpp  
// compile with: /EHsc  
  
#include <iostream>  
using namespace std;  
  
template <class T> class Array {  
   T* array;  
   int size;  
  
public:  
   Array(int sz): size(sz) {  
      array = new T[size];  
      memset(array, 0, size * sizeof(T));  
   }  
  
   Array(const Array& a) {  
      size = a.size;  
      array = new T[size];  
      memcpy_s(array, a.array, sizeof(T));  
   }  
  
   T& operator[](int i) {  
      return *(array + i);  
   }  
  
   int Length() { return size; }  
  
   void print() {  
      for (int i = 0; i < size; i++)        
         cout << *(array + i) << " ";  
  
      cout << endl;  
   }  
  
   template<class T>  
   friend Array<T>* combine(Array<T>& a1, Array<T>& a2);  
};  
  
template<class T>  
Array<T>* combine(Array<T>& a1, Array<T>& a2) {  
   Array<T>* a = new Array<T>(a1.size + a2.size);  
   for (int i = 0; i < a1.size; i++)  
      (*a)[i] = *(a1.array + i);  
  
   for (int i = 0; i < a2.size; i++)  
      (*a)[i + a1.size] = *(a2.array + i);  
  
   return a;  
}  
  
int main() {  
   Array<char> alpha1(26);  
   for (int i = 0 ; i < alpha1.Length() ; i++)  
      alpha1[i] = 'A' + i;  
  
   alpha1.print();  
  
   Array<char> alpha2(26);  
   for (int i = 0 ; i < alpha2.Length() ; i++)  
      alpha2[i] = 'a' + i;  
  
   alpha2.print();  
   Array<char>*alpha3 = combine(alpha1, alpha2);  
   alpha3->print();  
   delete alpha3;  
}  
```  
  
```Output
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z   
a b c d e f g h i j k l m n o p q r s t u v w x y z   
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z a b c d e f g h i j k l m n o p q r s t u v w x y z   
```  
  
## <a name="example"></a>Exemple  

L'exemple suivant implique un élément friend possédant une spécialisation de modèle. Une spécialisation de modèle de fonction est automatiquement un élément friend si le modèle de fonction d'origine est un élément friend.  
  
Il est également possible de déclarer uniquement la version spécialisée du modèle en tant qu'élément friend, comme l'indique le commentaire avant la déclaration friend dans le code suivant. Dans ce cas, vous devez mettre la définition de la spécialisation du modèle friend en dehors de la classe de modèle.  
  
```cpp
// template_friend2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
class Array;  
  
template <class T>  
void f(Array<T>& a);  
  
template <class T> class Array  
{  
    T* array;  
    int size;  
  
public:  
    Array(int sz): size(sz)  
    {  
        array = new T[size];  
        memset(array, 0, size * sizeof(T));  
    }  
    Array(const Array& a)  
    {  
        size = a.size;  
        array = new T[size];  
        memcpy_s(array, a.array, sizeof(T));  
    }  
    T& operator[](int i)  
    {  
        return *(array + i);  
    }  
    int Length()  
    {   
        return size;  
    }  
    void print()  
    {  
        for (int i = 0; i < size; i++)  
        {  
            cout << *(array + i) << " ";  
        }  
        cout << endl;  
    }  
    // If you replace the friend declaration with the int-specific  
    // version, only the int specialization will be a friend.  
    // The code in the generic f will fail  
    // with C2248: 'Array<T>::size' :  
    // cannot access private member declared in class 'Array<T>'.  
    //friend void f<int>(Array<int>& a);  
  
    friend void f<>(Array<T>& a);  
};  
  
// f function template, friend of Array<T>  
template <class T>  
void f(Array<T>& a)  
{  
    cout << a.size << " generic" << endl;  
}  
  
// Specialization of f for int arrays  
// will be a friend because the template f is a friend.  
template<> void f(Array<int>& a)  
{  
    cout << a.size << " int" << endl;  
}  
  
int main()  
{  
    Array<char> ac(10);  
    f(ac);  
  
    Array<int> a(10);  
    f(a);  
}  
```  

```Output
10 generic  
10 int  
```  
  
## <a name="example"></a>Exemple  
 
L'exemple suivant montre un modèle de classe friend déclaré dans un modèle de classe. Le modèle de classe est utilisé ensuite comme argument template pour la classe friend. Les modèles de classe Friend doivent être définis en dehors du modèle de classe dans lequel ils sont déclarés. Toutes les spécialisations ou spécialisations partielles du modèle friend sont également des éléments friend du modèle de classe d'origine.  
  
```cpp  
// template_friend3.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
class X  
{  
private:  
   T* data;  
   void InitData(int seed) { data = new T(seed); }  
public:  
   void print() { cout << *data << endl; }  
   template <class U> friend class Factory;  
};  
  
template <class U>  
class Factory  
{  
public:  
   U* GetNewObject(int seed)  
   {  
      U* pu = new U;  
      pu->InitData(seed);  
      return pu;  
   }  
};  
  
int main()  
{  
   Factory< X<int> > XintFactory;  
   X<int>* x1 = XintFactory.GetNewObject(65);  
   X<int>* x2 = XintFactory.GetNewObject(97);  
  
   Factory< X<char> > XcharFactory;  
   X<char>* x3 = XcharFactory.GetNewObject(65);  
   X<char>* x4 = XcharFactory.GetNewObject(97);  
   x1->print();  
   x2->print();  
   x3->print();  
   x4->print();  
}  
```  

```Output 
65  
97  
A  
a  
```  
  
## <a name="see-also"></a>Voir aussi  

[Arguments par défaut](../cpp/default-arguments.md)
