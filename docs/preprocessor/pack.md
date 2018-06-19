---
title: Pack | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pack_CPP
- vc-pragma.pack
dev_langs:
- C++
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c29c31cae2b7de59d4db5ed6546ad4eda6baecf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843624"
---
# <a name="pack"></a>pack
Spécifie l'alignement de compression pour des membres de structure, d'union et de classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## <a name="remarks"></a>Notes  
 La compression d'une classe consiste à placer ses membres directement les uns après les autres dans la mémoire, ce qui peut signifier que certains ou l'ensemble des membres peuvent être alignés sur une limite inférieure à l'alignement par défaut de l'architecture cible. `pack` donne le contrôle au niveau de la déclaration des données. Cela diffère de l’option du compilateur [/Zp](../build/reference/zp-struct-member-alignment.md), qui fournit uniquement un contrôle au niveau du module. `pack` entre en vigueur dès la première déclaration `struct`, `union` ou `class` après détection du pragma. `pack` n'a aucun effet sur les définitions. Appel de `pack` sans arguments affecte `n` à la valeur définie dans l’option du compilateur **/Zp**. Si l'option du compilateur n'est pas définie, la valeur par défaut est 8.  
  
 Si vous modifiez l'alignement d'une structure, il est possible qu'elle n'utilise pas autant d'espace en mémoire, mais vous risquez de constater une baisse des performances ou même d'obtenir une exception générée par le matériel relative au non-alignement de l'accès.  Vous pouvez modifier ce comportement d’exception à l’aide de [SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621).  
  
 **afficher** (facultatif)  
 Affiche la valeur d'octet actuelle pour l'alignement de compression. La valeur est affichée par un message d'avertissement.  
  
 **Push** (facultatif)  
 La valeur actuelle de l'alignement de compression fait l'objet d'un push sur la pile interne du compilateur et `n` est affecté comme valeur actuelle de l'alignement de compression. Si `n` n'est pas spécifié, la valeur actuelle de l'alignement de compression fait l'objet d'un push.  
  
 **POP** (facultatif)  
 Supprime l'enregistrement du haut de la pile interne du compilateur. Si `n` n’est pas spécifié avec **pop**, la valeur de compression associée à l’enregistrement obtenu en haut de la pile est la nouvelle valeur d’alignement de compression. Si `n` est spécifié, par exemple `#pragma pack(pop, 16)`, `n` devient la nouvelle valeur d'alignement de compression. Si vous effectuez un pop avec `identifier`, par exemple `#pragma pack(pop, r1)`, tous les enregistrements de la pile sont dépilés jusqu'à ce que l'enregistrement ayant `identifier` soit détecté. Cet enregistrement est dépilé et la valeur de compression associée à l'enregistrement obtenu en haut de la pile est la nouvelle valeur d'alignement de compression. Si vous effectuez un pop avec un `identifier` qui est introuvable dans tous les enregistrements sur la pile, puis le **pop** est ignoré.  
  
 `identifier`(facultatif)  
 Lorsqu’il est utilisé avec **push**, attribue un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu'à ce que `identifier` est supprimé ; si `identifier` est introuvable sur la pile interne, rien n’est dépilé.  
  
 `n`(facultatif)  
 Spécifie la valeur, en octets, à utiliser pour la compression. Si l’option du compilateur [/Zp](../build/reference/zp-struct-member-alignment.md) n’est pas définie pour le module, la valeur par défaut `n` est 8. Les valeurs valides sont 1, 2, 4, 8 et 16. L'alignement d'un membre sera sur une limite qui est soit un multiple de `n`, soit un multiple de la taille du membre (selon celui qui est le plus petit).  
  
 `#pragma pack(pop, identifier, n)` n’est pas défini.  
  
 Pour plus d'informations sur la façon de modifier l'alignement, consultez les rubriques suivantes :  
  
-   [__alignof](../cpp/alignof-operator.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [Exemples d’alignement de Structure](../build/examples-of-structure-alignment.md) (x64 spécifique)  
  
    > [!WARNING]
    >  Notez que, dans Visual Studio 2015 et versions ultérieures, vous pouvez utiliser les opérateurs alignas et alignof standard qui sont portables entre les compilateurs, contrairement à `__alignof` et `declspec( align )`. La norme C++ ne traitant pas la compression, vous devez toujours utiliser `pack` (ou l'extension correspondante sur d'autres compilateurs) pour spécifier les alignements inférieurs à la taille du mot de l'architecture cible.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser le pragma `pack` pour modifier l'alignement d'une structure.  
  
```  
// pragma_directives_pack.cpp  
#include <stddef.h>  
#include <stdio.h>  
  
struct S {  
   int i;   // size 4  
   short j;   // size 2  
   double k;   // size 8  
};  
  
#pragma pack(2)  
struct T {  
   int i;  
   short j;  
   double k;  
};  
  
int main() {  
   printf("%zu ", offsetof(S, i));  
   printf("%zu ", offsetof(S, j));  
   printf("%zu\n", offsetof(S, k));  
  
   printf("%zu ", offsetof(T, i));  
   printf("%zu ", offsetof(T, j));  
   printf("%zu\n", offsetof(T, k));  
}  
```  
  
```  
0 4 8  
0 4 6  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le **push**, **pop**, et **afficher** syntaxe.  
  
```  
// pragma_directives_pack_2.cpp  
// compile with: /W1 /c  
#pragma pack()   // n defaults to 8; equivalent to /Zp8  
#pragma pack(show)   // C4810  
#pragma pack(4)   // n = 4  
#pragma pack(show)   // C4810  
#pragma pack(push, r1, 16)   // n = 16, pushed to stack  
#pragma pack(show)   // C4810  
#pragma pack(pop, r1, 2)   // n = 2 , stack popped  
#pragma pack(show)   // C4810  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)