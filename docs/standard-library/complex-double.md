---
title: complex&lt;double&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.complex<double>
- complex<double>
- std::complex<double>
dev_langs:
- C++
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 3b5e57b3bda68995f24a21ffedb9d533e7c65a0f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/04/2017

---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;
Décrit un objet qui stocke une paire ordonnée d’objets tous deux de type **double***,* le premier représentant la partie réelle d’un nombre complexe et le deuxième représentant la partie imaginaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as template class complex
};
```  
  
#### <a name="parameters"></a>Paramètres  
 `RealVal`  
 Valeur de type **double** pour la partie réelle du nombre complexe en cours de construction.  
  
 `ImagVal`  
 Valeur de type **double** pour la partie imaginaire du nombre complexe en cours de construction.  
  
 `complexNum`  
 Nombre complexe de type **float** ou `long double` dont les parties réelle et imaginaire sont utilisées pour initialiser un nombre complexe de type **double** en cours de construction.  
  
## <a name="return-value"></a>Valeur de retour  
 Nombre complexe de type **double**.  
  
## <a name="remarks"></a>Notes  
 La spécialisation explicite de la classe de modèle complex en classe complex de type **double** diffère de la classe de modèle seulement par les constructeurs qu’elle définit. La conversion de **float** en **double** peut être implicite, mais la conversion de `long double` en **double** doit être de type **explicit**. L’utilisation d’**explicit** exclut l’initialisation avec la conversion de type à l’aide de la syntaxe d’assignation.  
  
 Pour plus d’informations sur la classe de modèle `complex`, consultez [complex, classe](../standard-library/complex-class.md). Pour obtenir la liste des membres de la classe de modèle `complex`, consultez .  
  
## <a name="example"></a>Exemple  
  
```cpp  
// complex_comp_dbl.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <double> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type double gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type float  
   complex <float> c2float ( 4.0 , 5.0 );  
   complex <double> c2double ( c2float );  
   cout << "Implicit conversion from type float to type double,"  
        << "\n gives c2double = " << c2double << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 4.0 , 5.0 );  
   complex <double> c3double ( c3longdouble );  
   cout << "Explicit conversion from type float to type double,"  
        << "\n gives c3longdouble = " << c3longdouble << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3longdouble );  
   double argc3 = arg ( c3longdouble );  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
\* Output:   
Specifying initial real & imaginary parts,  
 as type double gives c1 = (4,5)  
Implicit conversion from type float to type double,  
 gives c2double = (4,5)  
Explicit conversion from type float to type double,  
 gives c3longdouble = (4,5)  
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312  
Argument of c3 is recovered from c3 using:  
 arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.  
*\  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête** : \<complex>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [complex, classe](../standard-library/complex-class.md)   
 [Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)




