---
title: "&lt;queue&gt;, opérateurs | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 3160c7fb3965bc05ceace5722a9c502e60f89442
ms.lasthandoff: 02/24/2017

---
# <a name="ltqueuegt-operators"></a>&lt;queue&gt;, opérateurs
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_neq"></a>  operator!=  
 Teste si l'objet de file d'attente situé à gauche de l'opérateur n'est pas égal à l'objet de file d'attente situé à droite.  
  
```  
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **queue**.  
  
 `right`  
 Objet de type **queue**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si les objets queue ne sont pas égaux. **false** s’ils sont égaux.  
  
### <a name="remarks"></a>Notes  
 La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. Deux objets queue sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// queue_op_ne.cpp  
// compile with: /EHsc  
#include <queue>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queues with list base containers  
   queue <int, list<int> > q1, q2, q3;  
  
   // The following line would have caused an error because vector   
   // does not support pop_front( ) and so cannot be adapted  
   // by queue as a base container  
   // queue <int, vector<int> > q1, q2, q3;  
  
   q1.push( 1 );  
   q2.push( 1 );  
   q2.push( 2 );  
   q3.push( 1 );  
  
   if ( q1 != q2 )  
      cout << "The queues q1 and q2 are not equal." << endl;  
   else  
      cout << "The queues q1 and q2 are equal." << endl;  
  
   if ( q1 != q3 )  
      cout << "The queues q1 and q3 are not equal." << endl;  
   else  
      cout << "The queues q1 and q3 are equal." << endl;  
}  
```  
  
```Output  
The queues q1 and q2 are not equal.  
The queues q1 and q3 are equal.  
```  
  
##  <a name="operator_lt_"></a>  operator&lt;  
 Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur à l'objet de file d'attente situé à droite.  
  
```  
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **queue**.  
  
 `right`  
 Objet de type **queue**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’objet queue à gauche de l’opérateur est strictement inférieur à l’objet queue à droite de l’opérateur. Sinon, **false**.  
  
### <a name="remarks"></a>Notes  
 La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. La relation d’infériorité entre deux objets queue est basée sur une comparaison de la première paire d’éléments inégaux.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// queue_op_lt.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queues with default deque base container  
   queue <int> q1, q2, q3;  
  
   q1.push( 1 );  
   q1.push( 2 );  
   q2.push( 5 );  
   q2.push( 10 );  
   q3.push( 1 );  
   q3.push( 2 );  
  
   if ( q1 < q2 )  
      cout << "The queue q1 is less than the queue q2." << endl;  
   else  
      cout << "The queue q1 is not less than the queue q2." << endl;  
  
   if ( q1 < q3 )  
      cout << "The queue q1 is less than the queue q3." << endl;  
   else  
      cout << "The queue q1 is not less than the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is less than the queue q2.  
The queue q1 is not less than the queue q3.  
```  
  
##  <a name="operator_lt__eq"></a>  operator&lt;=  
 Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur ou égal à l'objet de file d'attente situé à droite.  
  
```  
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **queue**.  
  
 `right`  
 Objet de type **queue**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’objet queue situé à gauche de l’opérateur est strictement inférieur à l’objet queue situé à droite de l’opérateur. Sinon, **false**.  
  
### <a name="remarks"></a>Notes  
 La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. La relation d’infériorité ou d’égalité entre deux objets queue est basée sur une comparaison de la première paire d’éléments inégaux.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// queue_op_le.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2, q3;  
  
   q1.push( 5 );  
   q1.push( 10 );  
   q2.push( 1 );  
   q2.push( 2 );  
   q3.push( 5 );  
   q3.push( 10 );  
  
   if ( q1 <= q2 )  
      cout << "The queue q1 is less than or equal to "  
           << "the queue q2." << endl;  
   else  
      cout << "The queue q1 is greater than "  
           << "the queue q2." << endl;  
  
   if ( q1 <= q3 )  
      cout << "The queue q1 is less than or equal to "  
           << "the queue q3." << endl;  
   else  
      cout << "The queue q1 is greater than "  
           << "the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is greater than the queue q2.  
The queue q1 is less than or equal to the queue q3.  
```  
  
##  <a name="operator_eq_eq"></a>  operator==  
 Teste si l’objet queue situé à gauche de l’opérateur est égal à l’objet queue situé à droite.  
  
```  
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **queue**.  
  
 `right`  
 Objet de type **queue**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si les objets queue ne sont pas égaux. **false** s’ils sont égaux.  
  
### <a name="remarks"></a>Notes  
 La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. Deux objets queue sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// queue_op_eq.cpp  
// compile with: /EHsc  
#include <queue>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queues with list base containers  
   queue <int, list<int> > q1, q2, q3;  
  
   // The following line would have caused an error because vector   
   // does not support pop_front( ) and so cannot be adapted  
   // by queue as a base container  
   // queue <int, vector<int> > q1, q2, q3;  
  
   q1.push( 1 );  
   q2.push( 2 );  
   q3.push( 1 );  
  
   if ( q1 != q2 )  
      cout << "The queues q1 and q2 are not equal." << endl;  
   else  
      cout << "The queues q1 and q2 are equal." << endl;  
  
   if ( q1 != q3 )  
      cout << "The queues q1 and q3 are not equal." << endl;  
   else  
      cout << "The queues q1 and q3 are equal." << endl;  
}  
```  
  
```Output  
The queues q1 and q2 are not equal.  
The queues q1 and q3 are equal.  
```  
  
##  <a name="operator_gt_"></a>  operator&gt;  
 Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur à l'objet de file d'attente situé à droite.  
  
```  
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **queue**.  
  
 `right`  
 Objet de type **queue**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’objet queue situé à gauche de l’opérateur est strictement inférieur à l’objet queue situé à droite de l’opérateur. Sinon, **false**.  
  
### <a name="remarks"></a>Notes  
 La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. La relation de supériorité entre deux objets queue est basée sur une comparaison de la première paire d’éléments inégaux.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// queue_op_gt.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2, q3;  
  
   q1.push( 1 );  
   q1.push( 2 );  
   q1.push( 3 );  
   q2.push( 5 );  
   q2.push( 10 );  
   q3.push( 1 );  
   q3.push( 2 );  
  
   if ( q1 > q2 )  
      cout << "The queue q1 is greater than "  
           << "the queue q2." << endl;  
   else  
      cout << "The queue q1 is not greater than "  
           << "the queue q2." << endl;  
  
   if ( q1> q3 )  
      cout << "The queue q1 is greater than "  
           << "the queue q3." << endl;  
   else  
      cout << "The queue q1 is not greater than "  
           << "the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is not greater than the queue q2.  
The queue q1 is greater than the queue q3.  
```  
  
##  <a name="operator_gt__eq"></a>  operator&gt;=  
 Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur ou égal à l'objet de file d'attente situé à droite.  
  
```  
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Paramètres  
 `left`  
 Objet de type **queue**.  
  
 `right`  
 Objet de type **queue**.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’objet queue situé à gauche de l’opérateur est strictement inférieur à l’objet queue situé à droite de l’opérateur. Sinon, **false**.  
  
### <a name="remarks"></a>Notes  
 La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. Deux objets queue sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// queue_op_ge.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2, q3;  
  
   q1.push( 1 );  
   q1.push( 2 );  
   q2.push( 5 );  
   q2.push( 10 );  
   q3.push( 1 );  
   q3.push( 2 );  
  
   if ( q1 >= q2 )  
      cout << "The queue q1 is greater than or equal to "  
           << "the queue q2." << endl;  
   else  
      cout << "The queue q1 is less than "  
           << "the queue q2." << endl;  
  
   if ( q1>= q3 )  
      cout << "The queue q1 is greater than or equal to "  
           << "the queue q3." << endl;  
   else  
      cout << "The queue q1 is less than "  
           << "the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is less than the queue q2.  
The queue q1 is greater than or equal to the queue q3.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<queue>](../standard-library/queue.md)


