---
title: __stdcall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __stdcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8b845fd147f51e3546f7a11afa0bae6deb5d527
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461463"
---
# <a name="stdcall"></a>__stdcall
**Section spécifique à Microsoft**  
  
 Le **__stdcall** convention d’appel est utilisée pour appeler des fonctions API Win32. L’appelé nettoie la pile, donc le compilateur est `vararg` fonctions **__cdecl**. Les fonctions qui utilisent cette convention d’appel requièrent un prototype de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
return-type __stdcall function-name[(argument-list)]  
```  
  
## <a name="remarks"></a>Notes  
 La liste suivante illustre l’implémentation de cette convention d’appel.  
  
|Élément|Implémentation|  
|-------------|--------------------|  
|Ordre de transmission des arguments|De droite à gauche|  
|Convention de passage d'argument|Par valeur, à moins qu'un type pointeur ou référence soit passé.|  
|Responsabilité de la maintenance de la pile|La fonction appelée enlève ses propres arguments de la pile.|  
|Convention de décoration de nom|Un trait de soulignement (_) est ajouté en préfixe au nom. Le nom est suivi de l'arobase (@), suivi du nombre d'octets (au format décimal) dans la liste d'arguments. Par conséquent, la fonction déclarée comme `int func( int a, double b )` est décorée comme suit : `_func@12`|  
|Convention de conversion de casse|Aucun.|  
  
 Le [/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) option du compilateur spécifie **__stdcall** pour toutes les fonctions ne sont pas explicitement déclarées avec une autre convention d’appel.  
  
 Les fonctions déclarées à l’aide de la **__stdcall** la même façon que les fonctions déclarées à l’aide des valeurs de retour de modificateur [__cdecl](../cpp/cdecl.md).  
  
 Sur ARM et x64 processeurs, **__stdcall** est accepté et ignoré par le compilateur ; sur ARM et x64 architectures, par convention, les arguments sont passés dans les registres quand cela est possible, et les arguments suivants sont passés sur la pile.  
  
 Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition. Étant donné cette définition de classe,  
  
```cpp  
struct CMyClass {  
   void __stdcall mymethod();  
};  
```  
  
 this  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 équivaut à ceci  
  
```cpp  
void __stdcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, l’utilisation de **__stdcall** entraîne tous `WINAPI` types de fonction comme un appel standard :  
  
```cpp  
// Example of the __stdcall keyword  
#define WINAPI __stdcall  
// Example of the __stdcall keyword on function pointer  
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Passage des arguments et Conventions de nommage](../cpp/argument-passing-and-naming-conventions.md)   
 [Mots clés](../cpp/keywords-cpp.md)