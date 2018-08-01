---
title: __fastcall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fastcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e32bb8ac2fa453159b501ddc848348952b8d4468
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401728"
---
# <a name="fastcall"></a>__fastcall
**Section spécifique à Microsoft**  
  
 Le **__fastcall** convention d’appel spécifie que les arguments des fonctions doivent être passés dans les registres, lorsque cela est possible. Cette convention d’appel s’applique uniquement à l’architecture x86. La liste suivante illustre l’implémentation de cette convention d’appel.  
  
|Élément|Implémentation|  
|-------------|--------------------|  
|Ordre de transmission des arguments|Les deux premiers DWORD ou arguments plus petits qui figurent dans la liste d'arguments de gauche à droite sont transmis dans les registres ECX et EDX ; tous les autres arguments sont transmis sur la pile de droite à gauche.|  
|Responsabilité de la maintenance de la pile|La fonction appelée enlève les arguments de la pile.|  
|Convention de décoration de nom|Arobase (\@) est préfixé aux noms ; un arobase suivi du nombre d’octets (au format décimal) dans le paramètre de liste est suffixée aux noms.|  
|Convention de conversion de casse|Aucune conversion de casse n'est effectuée.|  
  
> [!NOTE]
>  Les futures versions du compilateur peuvent utiliser des registres pour stocker les paramètres.  
  
 À l’aide de la [/GR](../build/reference/gd-gr-gv-gz-calling-convention.md) option du compilateur provoque de chaque fonction dans le module pour compiler en **__fastcall** à moins que la fonction est déclarée à l’aide d’un attribut en conflit, ou le nom de la fonction `main` .  
  
 Le **__fastcall** mot clé est accepté et ignoré par les compilateurs qui ciblent ARM et x64 architectures ; sur un x64 de processeur, par convention, les quatre premiers arguments sont passés dans les registres quand cela est possible, et les arguments supplémentaires sont passés sur la pile. Pour plus d’informations, consultez [vue d’ensemble de x64 Conventions d’appel](../build/overview-of-x64-calling-conventions.md). Sur un processeur ARM, jusqu’à quatre arguments entiers et huit arguments à virgule flottante peuvent être transmis dans les registres, et des arguments supplémentaires sont transmis sur la pile.  
  
 Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition. Compte tenu de la définition de classe suivante :  
  
```cpp  
struct CMyClass {  
   void __fastcall mymethod();  
};  
```  
  
 le code suivant :  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 équivaut au code :  
  
```cpp  
void __fastcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, la fonction `DeleteAggrWrapper` correspond aux arguments transmis dans les registres :  
  
```cpp  
// Example of the __fastcall keyword  
#define FASTCALL    __fastcall  
  
void FASTCALL DeleteAggrWrapper(void* pWrapper);  
// Example of the __ fastcall keyword on function pointer  
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Passage des arguments et Conventions de nommage](../cpp/argument-passing-and-naming-conventions.md)   
 [Mots clés](../cpp/keywords-cpp.md)