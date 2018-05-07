---
title: 'Comment : définir et consommer des énumérateurs dans c++ / CLI | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5c30b679b24e574d359a1f838785f0196f290d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Comment : définir et consommer des énumérateurs dans C++/CLI
Cette rubrique traite des énumérateurs dans c++ / CLI.  
  
## <a name="specifying-the-underlying-type-of-an-enum"></a>Spécification du type sous-jacent d’un enum  
 Par défaut, le type sous-jacent d’une énumération est `int`.  Toutefois, vous pouvez spécifier le type doit être signés ou non signés des formes de `int`, `short`, `long`, `__int32`, ou `__int64`.  Vous pouvez également utiliser `char`.  
  
```  
// mcppv2_enum_3.cpp  
// compile with: /clr  
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};  
  
int main() {  
   // fully qualified names, enumerator not injected into scope  
   day_char d = day_char::sun, e = day_char::mon;  
   System::Console::WriteLine(d);  
   char f = (char)d;  
   System::Console::WriteLine(f);  
   f = (char)e;  
   System::Console::WriteLine(f);  
   e = day_char::tue;  
   f = (char)e;  
   System::Console::WriteLine(f);  
}  
```  
  
 **Sortie**  
  
```Output  
sun  
0  
1  
2  
```  
  
## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Comment effectuer une conversion entre des énumérations managées et standards  
 Il n’existe aucune conversion standard entre un enum et un type intégral ; un cast n’est requis.  
  
```  
// mcppv2_enum_4.cpp  
// compile with: /clr  
enum class day {sun, mon, tue, wed, thu, fri, sat};  
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum  
  
int main() {  
   day a = day::sun;  
   day2 = sun;  
   if ((int)a == day2)  
   // or...  
   // if (a == (day)day2)  
      System::Console::WriteLine("a and day2 are the same");  
   else  
      System::Console::WriteLine("a and day2 are not the same");  
}  
```  
  
 **Sortie**  
  
```Output  
a and day2 are the same  
```  
  
## <a name="operators-and-enums"></a>Opérateurs et énumérations  
 Les opérateurs suivants sont valides sur les énumérateurs dans c++ / CLI :  
  
|Opérateur|  
|--------------|  
|== != \< > \<= >=|  
|+ -|  
|&#124; ^ & ~|  
|++ --|  
|sizeof|  
  
 Opérateurs &#124; ^ & ~ ++--sont définies uniquement pour les énumérations avec intégrale types, y compris les booléen ne pas sous-jacents.  Les deux opérandes doivent être du type énumération.  
  
 Le compilateur n’effectue aucune vérification statique ou dynamique du résultat d’une opération d’énumération ; une opération peut entraîner une valeur pas dans la plage des énumérateurs de valide de l’énumération.  
  
> [!NOTE]
>  C ++ 11 présente les types de classe enum dans le code non managé qui sont fondamentalement différentes classes d’énumération managée dans C + c++ / CLI. En particulier, le type de classe C ++ 11 enum ne prend pas en charge les opérateurs de mêmes que le type de classe d’énumération managée dans C + c++ / CLI et c++ / CLI le code source doit fournir un spécificateur d’accessibilité dans l’énumération managée de déclarations de classe afin de les distinguer des non managé (C++ 11) les déclarations de classe enum. Pour plus d’informations sur les classes enum dans C + c++ / CLI, C + c++ / CX et C ++ 11, consultez [classe enum](../windows/enum-class-cpp-component-extensions.md).  
  
```  
// mcppv2_enum_5.cpp  
// compile with: /clr  
private enum class E { a, b } e, mask;  
int main() {  
   if ( e & mask )   // C2451 no E->bool conversion  
      ;  
  
   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)  
      ;  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```  
  
```  
// mcppv2_enum_6.cpp  
// compile with: /clr  
private enum class day : int {sun, mon};  
enum : bool {sun = true, mon = false} day2;  
  
int main() {  
   day a = day::sun, b = day::mon;  
   day2 = sun;  
  
   System::Console::WriteLine(sizeof(a));  
   System::Console::WriteLine(sizeof(day2));  
   a++;  
   System::Console::WriteLine(a == b);  
}  
```  
  
 **Sortie**  
  
```Output  
4  
1  
True  
```  
  
## <a name="see-also"></a>Voir aussi  
 [enum, classe](../windows/enum-class-cpp-component-extensions.md)