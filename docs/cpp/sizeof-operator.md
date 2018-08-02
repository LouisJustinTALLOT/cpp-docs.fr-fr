---
title: sizeof, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- sizeof_cpp
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3eeda8fd3babed4e5f9cd658ba324dfa057f66ce
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466274"
---
# <a name="sizeof-operator"></a>sizeof, opérateur
Donne la taille de son opérande en ce qui concerne la taille du type **char**.  
  
> [!NOTE]
>  Pour plus d’informations sur la `sizeof ...` opérateur, voir [Ellipses et modèles Variadiques](../cpp/ellipses-and-variadic-templates.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sizeof unary-expression  
sizeof  ( type-name )  
```  
  
## <a name="remarks"></a>Notes  
 Le résultat de la **sizeof** opérateur est de type `size_t`, un type intégral défini dans le fichier include \<stddef.h >. Cet opérateur vous permet d'éviter de spécifier les tailles de données dépendantes de l'ordinateur dans vos programmes.  
  
 L’opérande à **sizeof** peut prendre l’une des opérations suivantes :  
  
-   Un nom de type. Pour utiliser **sizeof** avec un nom de type, le nom doit être entre parenthèses.  
  
-   d'une expression. Lorsqu’il est utilisé avec une expression, **sizeof** peut être spécifié avec ou sans parenthèses. L'expression n'est pas évaluée.  
  
 Lorsque le **sizeof** opérateur est appliqué à un objet de type **char**, il donne 1. Lorsque le **sizeof** opérateur est appliqué à un tableau, il donne le nombre total d’octets dans ce tableau, pas la taille du pointeur représenté par l’identificateur du tableau. Pour obtenir la taille du pointeur représenté par l’identificateur du tableau, passez-le en tant que paramètre à une fonction qui utilise **sizeof**. Exemple :  
  
## <a name="example"></a>Exemple  
  
```cpp 
#include <iostream>  
using namespace std;  
  
size_t getPtrSize( char *ptr )  
{  
   return sizeof( ptr );  
}  
  
int main()  
{  
   char szHello[] = "Hello, world!";  
  
   cout  << "The size of a char is: "  
         << sizeof( char )  
         << "\nThe length of " << szHello << " is: "  
         << sizeof szHello  
         << "\nThe size of the pointer is "  
         << getPtrSize( szHello ) << endl;  
}  
```  
  
## <a name="sample-output"></a>Résultat de l'exemple  
  
```Output  
The size of a char is: 1  
The length of Hello, world! is: 14  
The size of the pointer is 4  
```  
  
 Lorsque le **sizeof** opérateur est appliqué à un **classe**, **struct**, ou **union** type, le résultat est le nombre d’octets dans un objet de ce type, ainsi que tout remplissage ajouté pour aligner les membres sur des limites de mots. Le résultat ne correspond pas forcément à la taille calculée en additionnant les exigences en matière de stockage des membres individuels. Le [/Zp](../build/reference/zp-struct-member-alignment.md) option du compilateur et le [pack](../preprocessor/pack.md) pragma affectent les limites d’alignement pour les membres.  
  
 Le **sizeof** opérateur donne jamais 0, même pour une classe vide.  
  
 Le **sizeof** opérateur ne peut pas être utilisé avec les opérandes suivants :  
  
-   Fonctions. (Toutefois, **sizeof** peuvent être appliquées à des pointeurs vers des fonctions.)  
  
-   Champ de bits.  
  
-   Classes indéfinies.  
  
-   Le type **void**.  
  
-   Tableaux alloués de manière dynamique.  
  
-   Tableaux externes.  
  
-   Types incomplets.  
  
-   Noms entre parenthèses de types incomplets.  
  
 Lorsque le **sizeof** opérateur est appliqué à une référence, le résultat est le même que si **sizeof** avait été appliqué à l’objet lui-même.  
  
 Si un tableau non dimensionné est le dernier élément d’une structure, la **sizeof** opérateur retourne la taille de la structure sans le tableau.  
  
 Le **sizeof** opérateur est souvent utilisé pour calculer le nombre d’éléments dans un tableau à l’aide d’une expression sous la forme :  
  
```cpp 
sizeof array / sizeof array[0]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)   
 [Mots clés](../cpp/keywords-cpp.md)