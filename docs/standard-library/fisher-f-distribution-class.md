---
title: fisher_f_distribution, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fisher_f_distribution
- std::fisher_f_distribution
- random/std::fisher_f_distribution
- std::fisher_f_distribution::reset
- random/std::fisher_f_distribution::reset
- std::fisher_f_distribution::m
- random/std::fisher_f_distribution::m
- std::fisher_f_distribution::n
- random/std::fisher_f_distribution::n
- std::fisher_f_distribution::param
- random/std::fisher_f_distribution::param
- std::fisher_f_distribution::min
- random/std::fisher_f_distribution::min
- std::fisher_f_distribution::max
- random/std::fisher_f_distribution::max
- std::fisher_f_distribution::operator()
- random/std::fisher_f_distribution::operator()
- std::fisher_f_distribution::param_type
- random/std::fisher_f_distribution::param_type
- std::fisher_f_distribution::param_type::m
- random/std::fisher_f_distribution::param_type::m
- std::fisher_f_distribution::param_type::n
- random/std::fisher_f_distribution::param_type::n
- std::fisher_f_distribution::param_type::operator==
- random/std::fisher_f_distribution::param_type::operator==
- std::fisher_f_distribution::param_type::operator!=
- random/std::fisher_f_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- fisher_f_distribution class
ms.assetid: 9513b6ce-3309-4be1-829b-f504bca35bbf
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: f293f074f2b8e2334dc70fbebba8e6f4c17efecc
ms.openlocfilehash: 3a0fc233334909249f75978ba095cb3f31af90dc
ms.lasthandoff: 02/24/2017

---
# <a name="fisherfdistribution-class"></a>fisher_f_distribution, classe
Génère une distribution selon la loi de Fisher.  
  
## <a name="syntax"></a>Syntaxe  
```  
template<class RealType = double>
class fisher_f_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  // constructor and reset functions  
   explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
   explicit fisher_f_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions  
   result_type m() const;
   result_type n() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
#### <a name="parameters"></a>Paramètres  
*RealType*  
Le type des résultats à virgule flottante est `double` par défaut. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).  
  
*URNG* Le moteur de génération de nombres aléatoires uniformes. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Notes  
 La classe de modèle décrit une distribution qui produit des valeurs d’un type à virgule flottante spécifié par l’utilisateur, ou du type `double` si aucun type n’est fourni, distribuées selon la loi de Fisher. Le tableau suivant contient des liens vers des articles sur différents membres.  
  
||||  
|-|-|-|  
|[fisher_f_distribution::fisher_f_distribution](#fisher_f_distribution__fisher_f_distribution)|`fisher_f_distribution::m`|`fisher_f_distribution::param`|  
|`fisher_f_distribution::operator()`|`fisher_f_distribution::n`|[fisher_f_distribution::param_type](#fisher_f_distribution__param_type)|  
  
 Les fonctions de propriété `m()` et `n()` retournent les valeurs des paramètres de distribution stockés `m` et `n`, respectivement.  
  
Le membre de propriété `param()` définit ou retourne le package de paramètres de distribution stocké `param_type`.  

Les fonctions membres `min()` et `max()` retournent respectivement le plus petit et le plus grand résultat possible.  
  
La fonction membre `reset()` ignore toutes les valeurs mises en cache. Ainsi, le résultat de l’appel suivant à `operator()` ne dépend d’aucune valeur obtenue à partir du moteur avant l’appel.  
  
Les fonctions membres `operator()` retournent la valeur générée suivante d’après le moteur URNG, à partir du package de paramètres actuel ou spécifié.
  
 Pour plus d’informations sur les classes de distribution et leurs membres, consultez [\<random>](../standard-library/random.md).  
  
 Pour plus d’informations sur la loi de Fisher, consultez l’article de Wolfram MathWorld [-Distribution](http://go.microsoft.com/fwlink/LinkId=400899).  
  
## <a name="example"></a>Exemple  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double m, const double n, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1701);  
  
    std::fisher_f_distribution<> distr(m, n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "m() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.m() << std::endl;  
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<double, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        std::cout << std::fixed << std::setw(11) << ++counter << ": "  
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double m_dist = 1;  
    double n_dist = 1;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'m\' distribution parameter (must be greater than zero): ";  
    std::cin >> m_dist;  
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(m_dist, n_dist, samples);  
}  
  
```  
  
## <a name="output"></a>Sortie  
 Première exécution :  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0204569549  
    2: 0.0221376644  
    3: 0.0297234962  
    4: 0.1600937252  
    5: 0.2775342196  
    6: 0.3950701700  
    7: 0.8363200295  
    8: 0.9512500702  
    9: 2.7844815974  
    10: 3.4320929653  
```  
  
 Deuxième exécution :  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 0.1000000000  
Distribution for 10 samples:  
    1: 0.0977725649  
    2: 0.5304122767  
    3: 4.9468518084  
    4: 25.1012074939  
    5: 48.8082121613  
    6: 401.8075539377  
    7: 8199.5947873699  
    8: 226492.6855335717  
    9: 2782062.6639740225  
    10: 20829747131.7185860000  
```  
  
 Troisième exécution :  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): .1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 0.1000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0000000000  
    2: 0.0000000000  
    3: 0.0000000000  
    4: 0.0000000000  
    5: 0.0000000033  
    6: 0.0000073975  
    7: 0.0000703800  
    8: 0.0280427735  
    9: 0.2660239949  
    10: 3.4363333954  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<random>  
  
 **Espace de noms :** std  
  
##  <a name="a-namefisherfdistributionfisherfdistributiona--fisherfdistributionfisherfdistribution"></a><a name="fisher_f_distribution__fisher_f_distribution"></a>  fisher_f_distribution::fisher_f_distribution  
 Construit la distribution.  
  
```  
explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
explicit fisher_f_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Paramètres  
*m*  
 Paramètre de distribution `m`.  
  
*n*  
 Paramètre de distribution `n`.  
  
*parm*  
 Structure `param_type` utilisée pour construire la distribution.  
  
### <a name="remarks"></a>Notes  
 **Condition préalable :** `0.0 < m` et `0.0 < n`  
  
 Le premier constructeur construit un objet dont la valeur `m` stockée contient la valeur *m* et dont la valeur `n` stockée contient la valeur *n*.  
  
 Le deuxième constructeur construit un objet dont les paramètres stockés sont initialisés à partir de *parm*. Vous pouvez obtenir et définir les paramètres actuels d'une distribution existante en appelant la fonction membre `param()`.  
  
##  <a name="a-namefisherfdistributionparamtypea--fisherfdistributionparamtype"></a><a name="fisher_f_distribution__param_type"></a>  fisher_f_distribution::param_type  
 Stocke les paramètres de la distribution.  
  
```cpp  
struct param_type {  
   typedef fisher_f_distribution<result_type> distribution_type;  
   param_type(result_type m = 1.0, result_type n = 1.0);
   result_type m() const;
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
### <a name="parameters"></a>Paramètres  
*m*  
 Paramètre de distribution `m`.  
  
*n*  
 Paramètre de distribution `n`.  
  
*right*  
Objet `param_type` à comparer à this.  
  
### <a name="remarks"></a>Notes  
 **Condition préalable :** `0.0 < m` et `0.0 < n`  
  
 Cette structure peut être passée au constructeur de classe de la distribution au moment de l'instanciation, à la fonction membre `param()` pour définir les paramètres stockés d'une distribution existante et à `operator()` pour une utilisation à la place des paramètres stockés.  
  
## <a name="see-also"></a>Voir aussi  
 [\<random>](../standard-library/random.md)




