---
title: Opérateurs de décalage vers la gauche et droit (&gt; &gt; et &lt; &lt;) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- <<
- '>>'
dev_langs:
- C++
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6f38b5ec30626f73ab3681f674fb39c5492eb49
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939727"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Opérateurs de décalage vers la gauche et droit (&gt; &gt; et &lt; &lt;)
Les opérateurs de décalage de bits sont l’opérateur de décalage vers la droite (>>), qui déplace les bits de *shift-expression* vers la droite et l’opérateur de décalage vers la gauche (<<), qui déplace les bits de *shift-expression* vers la gauche. <sup>1</sup>  
  
## <a name="syntax"></a>Syntaxe  
  
> *expression-décalage* `<<` *additive-expression*  
> *expression-décalage* `>>` *additive-expression*  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
> Les descriptions et les exemples suivants ne sont pas valides sur les architectures Windows pour x86 et x64. L'implémentation des opérateurs de décalage vers la droite et vers la gauche est très différente sur les appareils Windows RT pour ARM. Pour plus d’informations, consultez la section « Shift Operators » de la [Hello ARM](http://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) billet de blog.  
  
## <a name="left-shifts"></a>Décalages vers la gauche  
 L’opérateur de décalage vers la gauche provoque les bits de *shift-expression* être décalés à gauche par le nombre de positions spécifié par *additive-expression*. Les positions de bits qui ont été libérées par l'opération de décalage sont remplies de zéros. Un décalage vers la gauche est un décalage logique (les bits qui sont déplacés après la fin sont ignorés, y compris le bit de signe). Pour plus d’informations sur les types de décalages de bits, consultez [décalages de bits](http://en.wikipedia.org/wiki/Bitwise_shift).  
  
 L'exemple suivant illustre les opérations de décalage vers la gauche à l'aide de nombres non signés. L'exemple montre ce qui arrive aux bits en représentant la valeur en tant que bitset. Pour plus d’informations, consultez [bitset, classe](../standard-library/bitset-class.md).  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short1 = 4;      
    bitset<16> bitset1{short1};   // the bitset representation of 4  
    cout << bitset1 << endl;  // 0000000000000100  
  
    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;  // 0000000000001000  
  
    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16  
    bitset<16> bitset3{short3};  
    cout << bitset3 << endl;  // 0000000000010000  
}  
  
```  
  
 Si vous décalez vers la gauche un nombre signé de manière à affecter le bit de signe, le résultat n'est pas défini. L'exemple suivant montre ce qui se produit dans Visual C++ lorsqu'un bit 1 est décalé vers la gauche dans la position du bit de signe.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 16384;      
    bitset<16> bitset1{short2};  
    cout << bitset1 << endl;  // 0100000000000000   
  
    short short3 = short1 << 1;  
    bitset<16> bitset3{short3};  // 16384 left-shifted by 1 = -32768  
    cout << bitset3 << endl;  // 100000000000000  
  
    short short4 = short1 << 14;  
    bitset<16> bitset4{short4};  // 4 left-shifted by 14 = 0  
    cout << bitset4 << endl;  // 000000000000000    
}  
```  
  
## <a name="right-shifts"></a>Décalages vers la droite  
 L’opérateur de décalage vers la droite provoque le modèle binaire de *shift-expression* être décalés vers la droite par le nombre de positions spécifié par *additive-expression*. Pour les nombres non signés, les positions de bit qui ont été libérées par l'opération de décalage sont remplies de zéros. Pour les nombres signés, le bit de signe est utilisé pour remplir les positions de bit libérées. En d'autres termes, si le nombre est positif, 0 est utilisé, et si le nombre est négatif, 1 est utilisé.  
  
> [!IMPORTANT]
> Le résultat d'un décalage vers la droite d'une nombre négatif signé dépend de l'implémentation. Bien que Visual C++ utilise le bit de signe pour remplir les positions du bit libérées, il n'y a aucune garantie que d'autres implémentations puissent également le faire.  
  
 Cet exemple illustre les opérations de décalage vers la droite à l'aide de nombres non signés :  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short11 = 1024;  
    bitset<16> bitset11{short11};  
    cout << bitset11 << endl;     // 0000010000000000  
  
    unsigned short short12 = short11 >> 1;  // 512  
    bitset<16> bitset12{short12};  
    cout << bitset12 << endl;     // 0000001000000000  
  
    unsigned short short13 = short11 >> 10;  // 1  
    bitset<16> bitset13{short13};  
    cout << bitset13 << endl;     // 0000000000000001  
  
    unsigned short short14 = short11 >> 11;  // 0  
    bitset<16> bitset14{short14};  
    cout << bitset14 << endl;     // 0000000000000000}  
}  
```  
  
 L'exemple suivant illustre les opérations de décalage vers la droite avec des nombres positifs signés.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 1024;  
    bitset<16> bitset1{short1};  
    cout << bitset1 << endl;     // 0000010000000000  
  
    short short2 = short1 >> 1;  // 512  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;     // 0000001000000000  
  
    short short3 = short1 >> 11;  // 0  
    bitset<16> bitset3{short3};     
    cout << bitset3 << endl;     // 0000000000000000  
}  
```  
  
 L'exemple suivant illustre les opérations de décalage vers la droite avec des entiers négatifs signés.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short neg1 = -16;  
    bitset<16> bn1{neg1};  
    cout << bn1 << endl;  // 1111111111110000  
  
    short neg2 = neg1 >> 1; // -8  
    bitset<16> bn2{neg2};  
    cout << bn2 << endl;  // 1111111111111000  
  
    short neg3 = neg1 >> 2; // -4  
    bitset<16> bn3{neg3};  
    cout << bn3 << endl;  // 1111111111111100  
  
    short neg4 = neg1 >> 4; // -1  
    bitset<16> bn4{neg4};      
    cout << bn4 << endl;  // 1111111111111111  
  
    short neg5 = neg1 >> 5; // -1   
    bitset<16> bn5{neg5};      
    cout << bn5 << endl;  // 1111111111111111  
}  
```  
  
## <a name="shifts-and-promotions"></a>Décalages et promotions  
 Les expressions des deux côtés de l'opérateur de décalage doivent être de type intégral. Promotions intégrales sont exécutées selon les règles décrites dans [Conversions Standard](standard-conversions.md). Le type du résultat est le même que le type de promu *shift-expression*.  
  
 Dans l’exemple suivant, une variable de type **char** est promu à un **int**.  
  
```cpp  
#include <iostream>  
#include <typeinfo>  
  
using namespace std;  
  
int main() {  
    char char1 = 'a';  
  
    auto promoted1 = char1 << 1;   // 194  
    cout << typeid(promoted1).name() << endl;  // int  
  
    auto promoted2 = char1 << 10;  // 99328  
    cout << typeid(promoted2).name() << endl;  // int  
}  
```  
  
## <a name="additional-details"></a>Détails supplémentaires  
 Le résultat d’une opération de décalage est indéfini si *additive-expression* est négatif ou si *additive-expression* est supérieur ou égal au nombre de bits dans (promues)  *expression-décalage*. Aucune opération de décalage n’est effectuée si *additive-expression* est 0.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned int int1 = 4;  
    bitset<32> b1{int1};  
    cout << b1 << endl;    // 00000000000000000000000000000100  
  
    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior  
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior  
  
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int6 = int1 << 0;  
    bitset<32> b6{int6};  
    cout << b6 << endl;    // 00000000000000000000000000000100 (no change)}  
}  
```  
  
## <a name="footnotes"></a>Notes de bas de page  
 1 Voici la description des opérateurs de décalage dans la spécification C ++ 11 ISO (INCITS/ISO/IEC 14882-2011[2012]), sections 5.8.2 et 5.8.3.  
  
 La valeur de `E1 << E2` est `E1` décalée vers la gauche de positions de bit `E2` ; les bits libérés sont remplis de zéros. Si `E1` a un type non signé, la valeur du résultat est **E1 × 2**<sup>**E2**</sup>, réduit au modulo plus que la valeur maximale représentable dans le type de résultat. Sinon, si `E1` a un type signé et une valeur non négative, et **E1 × 2**<sup>**E2** </sup> est représentable dans le type non signé correspondant du type du résultat, puis Cette valeur convertie en type de résultat, est la valeur résultante. Sinon, le comportement est indéfini.  
  
 La valeur de `E1 >> E2` est `E1` décalée vers la droite de positions de bit `E2`. Si `E1` a un type non signé ou si `E1` a un type signé et une valeur non négative, la valeur du résultat fait partie intégrante du quotient de **E1/2**<sup>**E2** </sup>. Si `E1` a un type signé et une valeur négative, la valeur résultante est définie par l'implémentation.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)   
 [Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)