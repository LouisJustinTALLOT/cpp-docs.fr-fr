---
title: uniform_int_distribution, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- uniform_int_distribution
- random/std::uniform_int_distribution
- random/std::uniform_int_distribution::reset
- random/std::uniform_int_distribution::a
- random/std::uniform_int_distribution::b
- random/std::uniform_int_distribution::param
- random/std::uniform_int_distribution::min
- random/std::uniform_int_distribution::max
- random/std::uniform_int_distribution::operator()
- random/std::uniform_int_distribution::param_type
- random/std::uniform_int_distribution::param_type::a
- random/std::uniform_int_distribution::param_type::b
- random/std::uniform_int_distribution::param_type::operator==
- random/std::uniform_int_distribution::param_type::operator!=
- random/std::uniform_int_distribution::param_type
dev_langs:
- C++
helpviewer_keywords:
- uniform_int_distribution class
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 0555c6562ee987eab9eebc2e9e178a31cdf684e9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="uniformintdistribution-class"></a>uniform_int_distribution, classe
Génère une distribution d'entiers uniforme (toutes les valeurs ont le même degré de probabilité) dans une plage de sortie qui est inclusive-inclusive.  
  
## <a name="syntax"></a>Syntaxe  
```  
template<class IntType = int>
   class uniform_int_distribution {
public:    
   // types 
   typedef IntType result_type;    
   struct param_type;    
   
   // constructors and reset functions 
   explicit uniform_int_distribution(
      result_type a = 0, result_type b = numeric_limits<result_type>::max());
   explicit uniform_int_distribution(const param_type& parm);
   void reset();

   // generating functions 
   template <class URNG>  
      result_type operator()(URNG& gen);
   template <class URNG>  
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions 
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
};  
```  
### <a name="parameters"></a>Paramètres  
*IntType*  
Le type des résultats entiers est `int` par défaut. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Notes  
La classe de modèle décrit une distribution inclusive-inclusive qui produit des valeurs d'un type intégral spécifié par l'utilisateur avec une distribution pour que toutes les valeurs aient le même degré de probabilité. Le tableau suivant contient des liens vers des articles sur différents membres.  
  
||||  
|-|-|-|  
|[uniform_int_distribution](#uniform_int_distribution)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|  
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[param_type](#param_type)|  
  
Le membre de propriété `a()` retourne la limite minimale de la distribution stockée actuellement, tandis que `b()` retourne la limite maximale stockée actuellement. Pour cette classe de distribution, ces valeurs minimales et maximales sont les mêmes que celles retournées par les fonctions de propriété courantes `min()` et `max()`.  
  
Le membre de propriété `param()` définit ou retourne le package de paramètres de distribution stockés `param_type`.  

Les fonctions membres `min()` et `max()` retournent respectivement le plus petit et le plus grand résultat possible.  
  
La fonction membre `reset()` ignore toutes les valeurs mises en cache. Ainsi, le résultat de l’appel suivant à `operator()` ne dépend d’aucune valeur obtenue à partir du moteur avant l’appel.  
  
Les fonctions membres `operator()` retournent la valeur générée suivante d’après le moteur URNG, à partir du package de paramètres actuel ou spécifié.
  
Pour plus d’informations sur les classes de distribution et leurs membres, consultez [\<random>](../standard-library/random.md).  
  
## <a name="example"></a>Exemple  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const int a, const int b, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::uniform_int_distribution<> distr(a, b);  
  
    std::cout << "lower bound == " << distr.a() << std::endl;  
    std::cout << "upper bound == " << distr.b() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    int a_dist = 1;  
    int b_dist = 10;  
  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter an integer value for the lower bound of the distribution: ";  
    std::cin >> a_dist;  
    std::cout << "Enter an integer value for the upper bound of the distribution: ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the lower bound of the distribution: 0
Enter an integer value for the upper bound of the distribution: 12
Enter an integer value for the sample count: 200
lower bound == 0
upper bound == 12
Distribution for 200 samples:
    0 :::::::::::::::
    1 :::::::::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::
    4 :::::::
    5 :::::::::::::::::::::
    6 :::::::::::::
    7 ::::::::::
    8 :::::::::::::::
    9 :::::::::::::
   10 ::::::::::::::::::::::
   11 :::::::::::::
   12 :::::::::::::::::
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<random>  
  
 **Espace de noms :** std  
  
##  <a name="uniform_int_distribution"></a>  uniform_int_distribution::uniform_int_distribution  
Construit la distribution.  
  
```  
explicit uniform_int_distribution(
   result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
explicit uniform_int_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Paramètres  
*a*  
Limite inférieure pour les valeurs aléatoires, valeur comprise.  
  
*b*  
Limite supérieure pour les valeurs aléatoires, valeur comprise.  
  
*parm*  
Structure `param_type` utilisée pour construire la distribution.  
  
### <a name="remarks"></a>Notes  
**Condition préalable :** `a ≤ b`  
  
Le premier constructeur construit un objet dont la valeur `a` stockée contient la valeur *a* et dont la valeur `b` stockée contient la valeur *b*.  
  
Le deuxième constructeur construit un objet dont les paramètres stockés sont initialisés à partir de *parm*. Vous pouvez obtenir et définir les paramètres actuels d'une distribution existante en appelant la fonction membre `param()`.  
  
##  <a name="param_type"></a>  uniform_int_distribution::param_type  
 Stocke les paramètres de la distribution.  
```cpp  
struct param_type {  
   typedef uniform_int_distribution<result_type> distribution_type;  
   param_type(
      result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>Paramètres  
*a*  
Limite inférieure pour les valeurs aléatoires, valeur comprise.  
  
*b*  
Limite supérieure pour les valeurs aléatoires, valeur comprise.  
  
*right*  
Objet `param_type` à comparer à this.  
  
### <a name="remarks"></a>Notes  
**Condition préalable :** `a ≤ b`  
  
Cette structure peut être passée au constructeur de classe de la distribution au moment de l'instanciation, à la fonction membre `param()` pour définir les paramètres stockés d'une distribution existante et à `operator()` pour une utilisation à la place des paramètres stockés.  
  
## <a name="see-also"></a>Voir aussi  
 [\<random>](../standard-library/random.md)




