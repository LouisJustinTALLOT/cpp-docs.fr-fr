---
title: À l’aide de sortie ou de retour | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
- return keyword [C++], using for program termination
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47fb8ff09fc50557283a0f4e8ef0e159bc900e86
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460943"
---
# <a name="using-exit-or-return"></a>Utilisation d'exit ou return
Lorsque vous appelez **quitter** ou exécuter un **retourner** instruction à partir de `main`, les objets statiques sont détruits dans l’ordre inverse de leur initialisation. L'exemple suivant montre comment ce type d'initialisation et de nettoyage fonctionne.  
  
## <a name="example"></a>Exemple  
  
```cpp 
// using_exit_or_return1.cpp  
#include <stdio.h>  
class ShowData {  
public:  
   // Constructor opens a file.  
   ShowData( const char *szDev ) {  
   errno_t err;  
      err = fopen_s(&OutputDev, szDev, "w" );  
   }  
  
   // Destructor closes the file.  
   ~ShowData() { fclose( OutputDev ); }  
  
   // Disp function shows a string on the output device.  
   void Disp( char *szData ) {   
      fputs( szData, OutputDev );  
   }  
private:  
   FILE *OutputDev;  
};  
  
//  Define a static object of type ShowData. The output device  
//   selected is "CON" -- the standard output device.  
ShowData sd1 = "CON";  
  
//  Define another static object of type ShowData. The output  
//   is directed to a file called "HELLO.DAT"  
ShowData sd2 = "hello.dat";  
  
int main() {  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
 Dans l'exemple précédent, les objets statiques `sd1` et `sd2` sont créés et initialisés avant l'entrée dans `main`. Après la fin de ce programme à l’aide de la **retourner** instruction, première `sd2` est détruite, puis `sd1`. Le destructeur de la classe `ShowData` ferme les fichiers associés à ces objets statiques.   
  
 Une autre façon d'écrire ce code consiste à déclarer les objets `ShowData` avec portée de bloc, ce qui permet leur description lorsqu'ils sont hors de portée :  
  
```cpp 
int main() {  
   ShowData sd1, sd2( "hello.dat" );  
  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)