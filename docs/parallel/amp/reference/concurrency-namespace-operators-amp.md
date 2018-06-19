---
title: Opérateurs d’espace de noms d’accès concurrentiel (AMP) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d3bb77599fc81fa29f2c8155a6fd491ed2d639c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686706"
---
# <a name="concurrency-namespace-operators-amp"></a>Opérateurs d’espace de noms d’accès concurrentiel (AMP)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|  
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a>  operator==   
 Détermine si les arguments spécifiés sont égaux.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang des arguments de tuple.  
  
 `_Lhs`  
 Une des tuples à comparer.  
  
 `_Rhs`  
 Une des tuples à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si les tuples sont égales ; dans le cas contraire, `false`.  
  
##  <a name="operator_neq"></a>  operator!=   
 Détermine si les arguments spécifiés ne sont pas égaux.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang des arguments de tuple.  
  
 `_Lhs`  
 Une des tuples à comparer.  
  
 `_Rhs`  
 Une des tuples à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si les tuples ne sont pas égales ; dans le cas contraire, `false`.  
  
##  <a name="operator_add"></a>  operator+   

 Calcule la somme component-wise des arguments spécifiés.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang des arguments de tuple.  
  
 `_Lhs`  
 Un des arguments à ajouter.  
  
 `_Rhs`  
 Un des arguments à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 La somme component-wise des arguments spécifiés.  
  
##  <a name="operator-"></a>  operator-   

 Calcule la différence component-wise entre les arguments spécifiés.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang des arguments de tuple.  
  
 `_Lhs`  
 L’argument à soustraire.  
  
 `_Rhs`  
 L’argument à soustraire.  
  
### <a name="return-value"></a>Valeur de retour  
 La différence component-wise entre les arguments spécifiés.  
  
##  <a name="operator_star"></a>  operator*   

 Calcule le produit component-wise des arguments spécifiés.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang des arguments de tuple.  
  
 `_Lhs`  
 Une des tuples à multiplier.  
  
 `_Rhs`  
 Une des tuples à multiplier.  
  
### <a name="return-value"></a>Valeur de retour  
 Le produit component-wise des arguments spécifiés.  
  

##  <a name="operator_div"></a>  operator/   
 Calcule le quotient component-wise des arguments spécifiés.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang des arguments de tuple.  
  
 `_Lhs`  
 Le tuple à diviser.  
  
 `_Rhs`  
 Le tuple par laquelle diviser.  
  
### <a name="return-value"></a>Valeur de retour  
 Quotient component-wise des arguments spécifiés.  
  
##  <a name="operator_mod"></a>  operator%   

 Calcule le modulo du premier argument spécifié par le deuxième argument spécifié.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang des arguments de tuple.  
  
 `_Lhs`  
 Le tuple à partir de laquelle le modulo est calculée.  
  
 `_Rhs`  
 Le tuple à modulo par.  
  
### <a name="return-value"></a>Valeur de retour  
 Le résultat du modulo premier argument spécifié le deuxième argument spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace ](concurrency-namespace-cpp-amp.md)
