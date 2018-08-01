---
title: Pointeurs const et volatile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e32312e8c6f3dc149f6e5e1f8dc37b1395732d02
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408188"
---
# <a name="const-and-volatile-pointers"></a>Pointeurs const et volatile
Le [const](../cpp/const-cpp.md) et [volatile](../cpp/volatile-cpp.md) mots clés modifier la façon dont les pointeurs sont traités. Le **const** mot clé spécifie que le pointeur ne peut pas être modifié après l’initialisation ; le pointeur est protégé contre toute modification ultérieure.  
  
 Le **volatile** mot clé spécifie que la valeur associée au nom qui suit peut être modifiée par les actions autres que celles de l’application de l’utilisateur. Par conséquent, le **volatile** mot clé est utile pour déclarer des objets dans la mémoire partagée qui est accessible par plusieurs processus ou zones de données globales utilisées pour la communication avec les routines ISR.  
  
 Lorsqu’un nom est déclaré en tant que **volatile**, le compilateur recharge la valeur de la mémoire chaque fois qu’il est accessible par le programme. Cela réduit considérablement les optimisations possibles. Toutefois, lorsque l'état d'un objet peut changer de manière inattendue, c'est la seule façon de garantir des performances prévisibles du programme.  
  
 Pour déclarer l’objet vers lequel pointé le pointeur en tant que **const** ou **volatile**, utilisez une déclaration de la forme :  
  
```cpp 
const char *cpch;  
volatile char *vpch;  
```  
  
 Pour déclarer la valeur du pointeur, autrement dit, l’adresse réelle stockée dans le pointeur — en tant que **const** ou **volatile**, utiliser une déclaration de la forme :  
  
```cpp 
char * const pchc;  
char * volatile pchv;  
```  
  
 Le langage C++ empêche les assignations qui permettraient la modification d’un objet ou pointeur déclaré en tant que **const**. De telles assignations supprimeraient les informations avec lesquelles l'objet ou le pointeur a été déclaré, ce qui entraînerait la violation de l'objectif de la déclaration d'origine. Prenons les déclarations suivantes :  
  
```cpp 
const char cch = 'A';  
char ch = 'B';  
```  
  
 Compte tenu des déclarations de deux objets précédentes (`cch`, de type **const char**, et `ch`, de type **char)**, les déclarations/initialisations suivantes sont valides :  
  
```cpp 
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 Les déclarations/initialisations suivantes sont erronées.  
  
```cpp 
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 La déclaration de `pch2` déclare un pointeur par l'intermédiaire duquel un objet constant peut être modifié et par conséquent désactivé. La déclaration de `pch3` Spécifie que le pointeur est constant, pas l’objet ; la déclaration n’est pas autorisée pour la même raison le `pch2` déclaration n’est pas autorisée.  
  
 Les huit assignations suivantes indiquent l'assignation par l'intermédiaire du pointeur et la modification de la valeur du pointeur pour les déclarations précédentes ; pour le moment, supposons que l'initialisation est correcte de `pch1` à `pch8`.  
  
```cpp 
*pch1 = 'A';  // Error: object declared const  
pch1 = &ch;   // OK: pointer not declared const  
*pch2 = 'A';  // OK: normal pointer  
pch2 = &ch;   // OK: normal pointer  
*pch3 = 'A';  // OK: object not declared const  
pch3 = &ch;   // Error: pointer declared const  
*pch4 = 'A';  // Error: object declared const  
pch4 = &ch;   // Error: pointer declared const  
```  
  
 Les pointeurs déclarés comme **volatile**, ou comme un mélange de **const** et **volatile**, obéissent aux mêmes règles.  
  
 Pointeurs vers **const** objets sont souvent utilisés dans les déclarations de fonction comme suit :  
  
```cpp 
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 L’instruction précédente déclare une fonction, [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), où deux des trois arguments sont de type pointeur vers **char**. Étant donné que les arguments sont passés par référence et non par valeur, la fonction serait libre de modifier `strDestination` et `strSource` si `strSource` n’était pas déclaré comme **const**. La déclaration de `strSource` comme **const** garantit à l’appelant qui `strSource` ne peut pas être modifié par la fonction appelée.  
  
> [!NOTE]
>  Car il existe une conversion standard de *typename* **\*** à **const** *typename* **\***, il est permis de passer un argument de type `char *` à [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Toutefois, l’inverse n’est pas vrai ; Il n’existe aucune conversion implicite pour supprimer le **const** attribut à partir d’un objet ou pointeur.  
  
 Un **const** pointeur d’un type donné peut être assigné à un pointeur du même type. Toutefois, un pointeur qui n’est pas **const** ne peut pas être assigné à un **const** pointeur. L'exemple de code suivant montre des assignations correctes et incorrectes :  
  
```cpp 
// const_pointer.cpp  
int *const cpObject = 0;  
int *pObject;  
  
int main() {  
pObject = cpObject;  
cpObject = pObject;   // C3892  
}  
```  
  
 L'exemple suivant montre comment déclarer un objet comme const si vous avez un pointeur désignant un pointeur vers un objet.  
  
```cpp 
// const_pointer2.cpp  
struct X {  
   X(int i) : m_i(i) { }  
   int m_i;  
};  
  
int main() {  
   // correct  
   const X cx(10);  
   const X * pcx = &cx;  
   const X ** ppcx = &pcx;  
  
   // also correct  
   X const cx2(20);  
   X const * pcx2 = &cx2;  
   X const ** ppcx2 = &pcx2;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Pointeurs](../cpp/pointers-cpp.md)