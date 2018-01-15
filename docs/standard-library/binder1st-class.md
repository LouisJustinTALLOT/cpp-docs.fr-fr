---
title: binder1st, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::binder1st
dev_langs: C++
helpviewer_keywords: binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed005f1e8d87841eb0d78d5f7283baff2039897a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="binder1st-class"></a>binder1st, classe
Classe de modèle fournissant un constructeur qui convertit un objet de fonction binaire en objet de fonction unaire en liant le premier argument de la fonction binaire à une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& Func,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```  
  
#### <a name="parameters"></a>Paramètres  
 `Func`  
 Objet de fonction binaire à convertir en un objet de fonction unaire.  
  
 `left`  
 Valeur à laquelle le premier argument de l’objet de fonction binaire doit être lié.  
  
 `right`  
 Valeur de l’argument que l’objet binaire adapté compare à la valeur fixe du deuxième argument.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet de fonction unaire qui résulte de la liaison du premier argument de l’objet de fonction binaire avec la valeur `left.`  
  
## <a name="remarks"></a>Notes  
 La classe de modèle stocke une copie d’un objet de fonction binaire `Func` dans **op** et une copie de `left` dans **value**. Elle définit sa fonction membre `operator()` comme retournant **op**( **value**, `right`).  
  
 Si `Func` est un objet de type **Operation** et que `c` est une constante, [bind1st](../standard-library/functional-functions.md#bind1st) ( `Func`, `c` ) est équivalent au constructeur de classe `binder1st` `binder1st`\< **Operation**> ( `Func`, `c` ) et il est plus pratique.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// functional_binder1st.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(),  
        binder1st<less<int> >(less<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    // Compare use of binder2nd fixing 2nd argument:  
    // count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(),  
        binder2nd<less<int> >(less<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
\* Output:   
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 less than 10 is: 2.  
*\  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<functional>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)



