---
title: ref new, gcnew (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 51aec80ee24d96cf08d55778e108492d16ecfcc9
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606183"
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new, gcnew  (extensions du composant C++)
Le **ref nouvelle** mot clé d’agrégation alloue une instance d’un type qui est le garbage collecté lorsque l’objet devienne inaccessible, et qui retourne un handle ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) vers l’objet alloué.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 Mémoire pour une instance d’un type qui est allouée par **ref nouvelle** est automatiquement désallouée.  
  
 Un **ref nouvelle** opération lève `OutOfMemoryException` s’il est impossible d’allouer de mémoire.  
  
 Pour plus d’informations sur la façon dont la mémoire pour les types natifs C++ est allouée et désallouée, consultez [le nouveau et supprimer des opérateurs](../cpp/new-and-delete-operators.md).  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Utilisez **ref nouvelle** d’allocation de mémoire pour les objets Windows Runtime dont vous voulez administrer automatiquement la vie. L'objet est automatiquement désalloué quand son nombre de références atteint zéro, ce qui se produit une fois que la dernière copie de la référence est hors de portée. Pour plus d’informations, consultez [classes et structs Ref](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 Mémoire d’un type managé (type référence ou valeur) est allouée par **gcnew**et libérée en utilisant le garbage collection.  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/clr`  
  
### <a name="examples"></a>Exemples  
  
 L’exemple suivant utilise **gcnew** allouer un objet de Message.  
  
```cpp  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 L’exemple suivant utilise **gcnew** pour créer un type valeur boxed à utiliser comme un type référence.  
  
```cpp  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
 **Sortie**  
  
```Output  
32  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)