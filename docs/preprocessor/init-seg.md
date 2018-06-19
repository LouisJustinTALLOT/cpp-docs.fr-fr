---
title: init_seg | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3be66fc2639253d1bbcfec21f544d5537e084e8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840522"
---
# <a name="initseg"></a>init_seg
**Spécifique à C++**  
  
 Spécifie un mot clé ou une section de code qui affecte l'ordre dans lequel le code de démarrage est exécuté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )  
```  
  
## <a name="remarks"></a>Notes  
 La signification des termes du contrat *segment* et *section* sont interchangeables dans cette rubrique.  
  
 Étant donné que l'initialisation d'objets statiques globaux peut impliquer l'exécution de code, vous devez spécifier un mot clé qui définit le moment où les objets doivent être construits. Il est particulièrement important d’utiliser le **init_seg** pragma dans les bibliothèques de liens dynamiques (DLL) ou les bibliothèques nécessitant l’initialisation.  
  
 Les options pour le **init_seg** pragma :  
  
 **compiler**  
 Réservé pour l'initialisation de la bibliothèque Runtime C Microsoft. Les objets de ce groupe sont construits en premier.  
  
 **lib**  
 Disponible pour les initialisations des fournisseurs de bibliothèques de classes tierces. Objets de ce groupe sont construits après ceux marqués **compilateur** mais avant les autres.  
  
 **Utilisateur**  
 Disponible pour tout utilisateur. Les objets de ce groupe sont construits en dernier.  
  
 *nom de la section*  
 Autorise la spécification explicite de la section d'initialisation. Objets dans spécifié par l’utilisateur *-nom de la section* ne sont pas implicitement construits ; Toutefois, leurs adresses sont placées dans la section nommée par *-nom de la section*.  
  
 Le nom de section que vous donnez contiendra les pointeurs vers des fonctions d'assistance qui construiront les objets globaux déclarés dans ce module après le pragma.  
  
 Pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section, consultez [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 *nom de la fonction*  
 Spécifie une fonction à appeler au lieu de `atexit` lorsque le programme se ferme. Cette fonction d’assistance appelle également [atexit](../c-runtime-library/reference/atexit.md) avec un pointeur vers le destructeur de l’objet global. Si vous spécifiez un identificateur de fonction dans le pragma du formulaire,  
  
```  
int __cdecl myexit (void (__cdecl *pf)(void))  
```  
  
 votre fonctionnalité est appelée à la place de l'`atexit`de la bibliothèque Runtime C. Cela vous permet de générer une liste des destructeurs qui devront être appelés lorsque vous êtes prêt à détruire les objets.  
  
 Si vous devez différer l'initialisation (par exemple, dans une DLL) vous pouvez choisir de spécifier le nom de section explicitement. Vous devez ensuite appeler les constructeurs pour chaque objet statique.  
  
 Il ne reste aucun guillemet autour de l'identificateur du remplacement d'`atexit`.  
  
 Vos objets seront toujours placés dans les sections définies par les autres pragmas XXX_seg.  
  
 Les objets déclarés dans le module ne seront pas automatiquement initialisés par le runtime C. Vous devez effectuer cela vous-même.  
  
 Par défaut, les sections `init_seg` sont en lecture seule. Si le nom de section est .CRT, le compilateur passe silencieusement l'attribut en mode de lecture seule même s'il est marqué comme étant en lecture et en écriture.  
  
 Vous ne pouvez pas spécifier **init_seg** plusieurs fois dans une unité de traduction.  
  
 Même si votre objet n'a pas de constructeur défini par l'utilisateur, un constructeur non défini explicitement dans le code, le compilateur peut en générer un (par exemple pour lier des pointeurs v- table).  Par conséquent, votre code doit appeler le constructeur généré par le compilateur.  
  
## <a name="example"></a>Exemple  
  
```  
// pragma_directive_init_seg.cpp  
#include <stdio.h>  
#pragma warning(disable : 4075)  
  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors we need to call  
PF pfx[200];    // pointers to destructors.  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() { puts("A()"); }  
   ~A() { puts("~A()"); }  
};  
  
// ctor & dtor called by CRT startup code   
// because this is before the pragma init_seg  
A aaaa;   
  
// The order here is important.  
// Section names must be 8 characters or less.  
// The sections with the same name before the $  
// are merged into one section. The order that  
// they are merged is determined by sorting  
// the characters after the $.  
// InitSegStart and InitSegEnd are used to set  
// boundaries so we can find the real functions  
// that we need to call for initialization.  
  
#pragma section(".mine$a", read)  
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;  
  
#pragma section(".mine$z",read)  
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;  
  
// The comparison for 0 is important.  
// For now, each section is 256 bytes. When they  
// are merged, they are padded with zeros. You  
// can't depend on the section being 256 bytes, but  
// you can depend on it being padded with zeros.  
  
void InitializeObjects () {  
   const PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if (*x) (*x)();  
}  
  
void DestroyObjects () {  
   while (cxpf>0) {  
      --cxpf;  
      (pfx[cxpf])();  
   }  
}  
  
// by default, goes into a read only section  
#pragma init_seg(".mine$m", myexit)  
  
A bbbb;   
A cccc;  
  
int main () {  
   InitializeObjects();  
   DestroyObjects();  
}  
```  
  
```Output  
A()  
A()  
A()  
~A()  
~A()  
~A()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)