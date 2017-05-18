---
title: lognormal_distribution, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- lognormal_distribution
- random/std::lognormal_distribution
- random/std::lognormal_distribution::reset
- random/std::lognormal_distribution::m
- random/std::lognormal_distribution::s
- random/std::lognormal_distribution::param
- random/std::lognormal_distribution::min
- random/std::lognormal_distribution::max
- random/std::lognormal_distribution::operator()
- random/std::lognormal_distribution::param_type
- random/std::lognormal_distribution::param_type::m
- random/std::lognormal_distribution::param_type::s
- random/std::lognormal_distribution::param_type::operator==
- random/std::lognormal_distribution::param_type::operator!=
- random/std::lognormal_distribution::param_type
dev_langs:
- C++
helpviewer_keywords:
- lognormal_distribution class
ms.assetid: f2d6a431-6c3a-4370-b12e-4adb4ddf6cc4
caps.latest.revision: 15
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
ms.openlocfilehash: 3c5d969e7250987471f88579d30e36d7838a9ed1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="lognormaldistribution-class"></a>lognormal_distribution, classe
Génère une distribution suivant une loi log-normale.  
  
## <a name="syntax"></a>Syntaxe  
```  
template <class RealType = double>  
class lognormal_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   // constructor and reset functions  
   explicit lognormal_distribution(result_type m = 0.0, result_type s = 1.0);
   explicit lognormal_distribution(const param_type& parm);
   void reset();
   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   // property functions  
   result_type m() const;
   result_type s() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
### <a name="parameters"></a>Paramètres  
*RealType*  
Le type des résultats à virgule flottante est `double` par défaut. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Remarques  
La classe de modèle décrit une distribution qui produit des valeurs d'un type intégral spécifié par l'utilisateur, ou du type `double` si aucun n'est fourni, distribuées selon une loi log-normale. Le tableau suivant contient des liens vers des articles sur différents membres.  
  
||||  
|-|-|-|  
|[lognormal_distribution](#lognormal_distribution)|`lognormal_distribution::m`|`lognormal_distribution::param`|  
|`lognormal_distribution::operator()`|`lognormal_distribution::s`|[param_type](#param_type)|  
  
Les fonctions de propriété `m()` et `s()` retournent les valeurs des paramètres de distribution stockés *m* et *s*, respectivement.  
  
Le membre de propriété `param()` définit ou retourne le package de paramètres de distribution stocké `param_type`.  

Les fonctions membres `min()` et `max()` retournent respectivement le plus petit et le plus grand résultat possible.  
  
La fonction membre `reset()` ignore toutes les valeurs mises en cache. Ainsi, le résultat de l’appel suivant à `operator()` ne dépend d’aucune valeur obtenue à partir du moteur avant l’appel.  
  
Les fonctions membres `operator()` retournent la valeur générée suivante d’après le moteur URNG, à partir du package de paramètres actuel ou spécifié.
  
Pour plus d’informations sur les classes de distribution et leurs membres, consultez [\<random>](../standard-library/random.md).  
  
Pour plus d’informations sur la distribution suivant une loi log-normale, consultez l’article de Wolfram MathWorld [LogNormal Distribution](http://go.microsoft.com/fwlink/LinkId=400917).  
  
## <a name="example"></a>Exemple  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const double m, const double s, const int samples) {  
  
    // uncomment to use a non-deterministic seed  
    //    random_device gen;  
    //    mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    lognormal_distribution<> distr(m, s);  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.m() << endl;  
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.s() << endl;  
  
    // generate the distribution as a histogram  
    map<double, int> histogram;  
    for (int i = 0; i < samples; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << samples << " samples:" << endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        cout << fixed << setw(11) << ++counter << ": "  
            << setw(14) << setprecision(10) << elem.first << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    double m_dist = 1;  
    double s_dist = 1;  
    int samples = 10;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter a floating point value for the 'm' distribution parameter: ";  
    cin >> m_dist;  
    cout << "Enter a floating point value for the 's' distribution parameter (must be greater than zero): ";  
    cin >> s_dist;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(m_dist, s_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'm' distribution parameter: 0  
Enter a floating point value for the 's' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
m() == 0.0000000000  
s() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.3862809339  
    2: 0.4128865601  
    3: 0.4490576787  
    4: 0.4862035428  
    5: 0.5930607126  
    6: 0.8190778771  
    7: 0.8902379317  
    8: 2.8332911667  
    9: 5.1359445565  
    10: 5.4406507912  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<random>  
  
 **Espace de noms :** std  
  
##  <a name="lognormal_distribution"></a>  lognormal_distribution::lognormal_distribution  
 Construit la distribution.  
  
```  
explicit lognormal_distribution(RealType m = 0.0, RealType s = 1.0);
explicit lognormal_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Paramètres  
*m*  
Paramètre de distribution `m`.  
  
*s*  
Paramètre de distribution `s`.  
  
*parm*  
Structure `param_type` utilisée pour construire la distribution.  
  
### <a name="remarks"></a>Notes  
**Condition préalable :** `0.0 < s`  
  
Le premier constructeur construit un objet dont la valeur `m` stockée contient la valeur *m* et dont la valeur `s` stockée contient la valeur *s*.  
  
Le second constructeur construit un objet dont les paramètres stockés sont initialisés à partir de *parm*. Vous pouvez obtenir et définir les paramètres actuels d'une distribution existante en appelant la fonction membre `param()`.  
  
##  <a name="param_type"></a>  lognormal_distribution::param_type  
Stocke les paramètres de la distribution.  
  
```  
struct param_type {  
   typedef lognormal_distribution<result_type> distribution_type;  
   param_type(result_type m = 0.0, result_type s = 1.0);
   result_type m() const;
   result_type s() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
};  
```    
### <a name="parameters"></a>Paramètres  
*m*  
Paramètre de distribution `m`.  
  
*s*  
Paramètre de distribution `s`.  
  
*right*  
Structure `param_type` utilisée pour comparer.  
  
### <a name="remarks"></a>Remarques  
**Condition préalable :** `0.0 < s`  
  
Cette structure peut être passée au constructeur de classe de la distribution au moment de l'instanciation, à la fonction membre `param()` pour définir les paramètres stockés d'une distribution existante et à `operator()` pour une utilisation à la place des paramètres stockés.  
  
## <a name="see-also"></a>Voir aussi  
[\<random>](../standard-library/random.md)


