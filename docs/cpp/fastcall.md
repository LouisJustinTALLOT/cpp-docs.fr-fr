---
title: __fastcall | Documents Microsoft
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
ms.openlocfilehash: 03f286f21f213f5b2a193ccb824ba22b7c7c1f00
ms.sourcegitcommit: 39585672df8874fb5df4e70de97cd7f328fe9880
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2018
ms.locfileid: "34153117"
---
# <a name="fastcall"></a>__fastcall
**Section spécifique à Microsoft**  
  
 La convention d'appel `__fastcall` spécifie que les arguments des fonctions doivent être passés dans les registres, lorsque cela est possible. Cette convention d’appel s’applique uniquement à l’architecture x86. La liste suivante illustre l’implémentation de cette convention d’appel.  
  
|Élément|Implémentation|  
|-------------|--------------------|  
|Ordre de transmission des arguments|Les deux premiers DWORD ou arguments plus petits qui figurent dans la liste d'arguments de gauche à droite sont transmis dans les registres ECX et EDX ; tous les autres arguments sont transmis sur la pile de droite à gauche.|  
|Responsabilité de la maintenance de la pile|La fonction appelée enlève les arguments de la pile.|  
|Convention de décoration de nom|Arobase (\@) est préfixé aux noms ; un arobase suivi du nombre d’octets (au format décimal) dans le paramètre de liste est suffixée aux noms.|  
|Convention de conversion de casse|Aucune conversion de casse n'est effectuée.|  
  
> [!NOTE]
>  Les futures versions du compilateur peuvent utiliser des registres pour stocker les paramètres.  
  
 À l’aide de la [/GR](../build/reference/gd-gr-gv-gz-calling-convention.md) option du compilateur, chaque fonction dans le module pour compiler en `__fastcall` à moins que la fonction est déclarée à l’aide d’un attribut en conflit, ou le nom de la fonction `main`.  
  
 Le mot clé `__fastcall` est accepté et ignoré par les compilateurs qui ciblent les architectures ARM et x64 ; sur un processeur x64, par convention, les quatre premiers arguments sont transmis dans les registres si possible, et les arguments supplémentaires sont transmis sur la pile. Pour plus d’informations, consultez [vue d’ensemble de x64 Conventions d’appel](../build/overview-of-x64-calling-conventions.md). Sur un processeur ARM, jusqu’à quatre arguments entiers et huit arguments à virgule flottante peuvent être transmis dans les registres, et des arguments supplémentaires sont transmis sur la pile.  
  
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
 [Passage des arguments et Conventions d’affectation de noms](../cpp/argument-passing-and-naming-conventions.md)   
 [Mots clés](../cpp/keywords-cpp.md)
